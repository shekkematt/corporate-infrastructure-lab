# LAB-002 — Active Directory e DNS

## Objetivo

Implementar uma infraestrutura básica de identidade corporativa utilizando Active Directory Domain Services (AD DS) e DNS no Windows Server 2025.

O servidor DC01 será promovido a Domain Controller e será responsável inicialmente pela autenticação, gerenciamento de identidades e resolução de nomes do ambiente JG-LAB.

## Ambiente

### Servidor

- Hostname: DC01
- Sistema operacional: Windows Server 2025 Standard Evaluation
- IP: 10.10.10.10/24
- Hypervisor: Microsoft Hyper-V
- Rede virtual: JG-LAB

### Rede

- Rede: 10.10.10.0/24
- DC01: 10.10.10.10
- Host Hyper-V: 10.10.10.1

## Tecnologias

- Active Directory Domain Services (AD DS)
- Domain Controller (DC)
- DNS Server
- Group Policy
- PowerShell
- Windows Server 2025

## Atividades planejadas

- [ ] Instalar a função Active Directory Domain Services
- [ ] Instalar/configurar DNS Server
- [ ] Criar uma nova floresta e domínio
- [ ] Promover DC01 a Domain Controller
- [ ] Validar funcionamento do DNS
- [ ] Criar estrutura de Organizational Units (OUs)
- [ ] Criar usuários de laboratório
- [ ] Criar grupos de segurança
- [ ] Organizar usuários por departamentos
- [ ] Criar primeira Group Policy (GPO)
- [ ] Criar futura máquina CLIENT01
- [ ] Ingressar CLIENT01 no domínio
- [ ] Testar autenticação com usuário do domínio

## Conceitos estudados

### Active Directory

Serviço de diretório utilizado para centralizar usuários, computadores, grupos, autenticação e políticas de um ambiente Windows corporativo.

### Domain Controller

Servidor que executa os serviços do Active Directory e atende solicitações relacionadas ao domínio.

### DNS

Serviço responsável pela resolução de nomes para endereços IP.

No Active Directory, o DNS também é utilizado pelos computadores para localizar Domain Controllers e outros serviços do domínio.

### GPO

Group Policy Object.

Permite aplicar configurações e políticas de forma centralizada a usuários e computadores pertencentes ao domínio.

### OU

Organizational Unit.

Estrutura lógica utilizada dentro do Active Directory para organizar objetos como usuários, computadores e grupos.

## Arquitetura planejada

GODOFWAR (HOST)
10.10.10.1
    |
    |
    | JG-LAB
    |
    +--- DC01
         10.10.10.10
         |
         +--- AD DS
         +--- DNS

Futuramente:

    +--- CLIENT01
    +--- FS01

## Checkpoint

Antes da implementação do Active Directory foi criado o checkpoint:

`BASE-WINDOWS-NETWORK`

Esse checkpoint representa o estado funcional do Windows Server antes da instalação do AD DS e DNS.

## Resultado

Em andamento.

## Status

Em andamento.