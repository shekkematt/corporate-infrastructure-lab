# INC-001 — Falha de inicialização do DC01

## Status

Resolvido.

## Ambiente

- Hypervisor: Microsoft Hyper-V
- VM: DC01
- Sistema operacional: Windows Server 2025
- Geração da VM: Generation 2 / UEFI
- Disco virtual: VHDX
- Rede: JG-LAB

## Sintoma

Após a instalação inicial do Windows Server 2025, a VM DC01 deixou de carregar o sistema operacional.

Durante a inicialização, o Hyper-V apresentou mensagens indicando falha ao localizar/carregar um sistema operacional no disco virtual.

Também foram observadas tentativas de inicialização pela mídia ISO e via PXE.

## Diagnóstico

Durante o troubleshooting foram realizadas as seguintes verificações:

- Conferência da ordem de boot no firmware UEFI.
- Validação das configurações de Secure Boot.
- Inicialização pela ISO do Windows Server para acesso ao ambiente de recuperação.
- Uso do DiskPart para verificar discos e volumes.
- Identificação de um disco virtual de 80 GB sem partições.
- Inspeção do VHDX através do PowerShell no host Hyper-V.
- Busca por outros arquivos VHDX e AVHDX.
- Validação dos discos associados à VM através do Hyper-V.

Comandos utilizados durante o diagnóstico:

```powershell
Get-VHD
Get-VMHardDiskDrive
Get-VMSnapshot
Get-ChildItem
```

No ambiente de recuperação também foram utilizados:

```text
diskpart
list disk
list volume
```

## Constatações

O primeiro arquivo `DC01.vhdx` encontrado possuía aproximadamente 36 MB físicos e apresentava os 80 GB virtuais totalmente não alocados.

Nenhuma instalação válida do Windows Server estava presente naquele disco.

Foi criado um novo disco virtual chamado:

`DC01-OS.vhdx`

Após a reinstalação, foi identificado que o Hyper-V havia criado automaticamente um checkpoint.

As alterações do sistema estavam sendo armazenadas em um arquivo diferencial `.avhdx`, enquanto o `.vhdx` permanecia como disco base.

## Resolução

O checkpoint automático foi removido corretamente através do Hyper-V.

O Hyper-V realizou a mesclagem do arquivo `.avhdx` com o disco base `DC01-OS.vhdx`.

Após a mesclagem:

- O AVHDX deixou de existir.
- O DC01 passou a apontar diretamente para `DC01-OS.vhdx`.
- O VHDX passou a possuir aproximadamente 15 GB de dados.
- O Windows Server voltou a inicializar normalmente.
- Os checkpoints automáticos foram desabilitados.
- Foi criado manualmente o checkpoint `BASE-WINDOWS-NETWORK`.