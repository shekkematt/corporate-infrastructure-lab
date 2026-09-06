# LAB-002 — Active Directory e DNS

## Objetivo

Implantar o primeiro Domain Controller do ambiente JG-LAB utilizando Active Directory Domain Services e DNS.

## Ambiente

- Servidor: DC01
- Sistema operacional: Windows Server 2025
- IP: `10.10.10.10/24`
- Domínio: `jglab.test`
- NetBIOS: `JGLAB`
- Forest Functional Level: Windows Server 2025
- Domain Functional Level: Windows Server 2025

## Implementação

- Active Directory Domain Services instalado
- DC01 promovido a Domain Controller
- Nova floresta criada: `jglab.test`
- DNS Server instalado e integrado ao Active Directory
- Global Catalog habilitado
- Resolução direta validada
- Registros SRV do Active Directory validados
- Reverse Lookup Zone criada para `10.10.10.0/24`
- Registro PTR do DC01 criado
- Estrutura inicial de OUs criada
- Primeiro usuário de domínio criado

## Estrutura do Active Directory

```text
jglab.test
└── JG-LAB
    ├── Users
    │   ├── TI
    │   ├── Financeiro
    │   ├── RH
    │   └── Comercial
    ├── Computers
    ├── Groups
    └── Servers