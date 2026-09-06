# LAB-001 — Hyper-V e Windows Server

## Objetivo

Preparar a infraestrutura base do laboratório utilizando Hyper-V e Windows Server 2025.

## Ambiente

- Host: Windows 11 Pro
- Hypervisor: Microsoft Hyper-V
- VM: DC01
- Sistema operacional: Windows Server 2025
- Rede virtual: JG-LAB
- Rede: `10.10.10.0/24`

## Implementação

- Hyper-V habilitado no host
- Switch virtual JG-LAB criado
- VM DC01 criada
- Windows Server 2025 instalado
- Hostname alterado para `DC01`
- IP estático configurado: `10.10.10.10/24`
- Interface virtual do host configurada como `10.10.10.1/24`
- Comunicação entre host e servidor validada via ICMP
- Checkpoint base criado antes da implementação do Active Directory

## Arquitetura

```text
GODOFWAR
Windows 11 + Hyper-V
10.10.10.1
     |
     | JG-LAB
     | 10.10.10.0/24
     |
     +--- DC01
          Windows Server 2025
          10.10.10.10