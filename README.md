# 🏠 homelab-topology-v2 - Infraestrutura & Networking

Este repositório documenta a evolução da minha infraestrutura doméstica e laboratório de estudos. O projeto foca em virtualização, segurança de rede com firewall dedicado e alta performance.

**Status do Projeto:** 🚀 Em expansão (Aguardando placa Ethernet M.2 para o Gateway).

---

## 🖥️ Especificações de Hardware

Abaixo estão detalhados os nós de processamento e dispositivos que compõem o laboratório.

| Dispositivo | Processador | RAM | S.O. Instalado | Documentação/Link |
| :--- | :--- | :--- | :--- | :--- |
| **Main Server (Xeon)** | E5-2680 V4 (14C/28T) | 16GB DDR4 | [Proxmox VE](https://www.proxmox.com/) | [Link Oficial](https://github.com/proxmox) |
| **Firewall (MediaVue)** | AMD GX-424CC (4C/4T) | 16GB DDR3 | [OPNsense](https://opnsense.org/) | [Link Oficial](https://github.com/opnsense) |
| **Workstation (Acer)** | i7-13620H (RTX 4050) | 32GB DDR5 | [Windows 11 Pro](https://www.microsoft.com/software-download/windows11) | N/A |
| **Laptop (ThinkPad)** | i5-6300U | 16GB DDR3 | [Kubuntu Linux](https://kubuntu.org/) | [Link Oficial](https://kubuntu.org/) |
| **Mobile** | Snapdragon 8s Gen 4 | 12GB RAM | Android (HyperOS) | [Xiaomi POCO F7] |

---

## 🌐 Topologia de Rede (Lógica)

Este diagrama representa a arquitetura de rede planejada para o laboratório.

```mermaid
graph TD
    Internet((Internet)) --- Modem[Roteador Vivo Wi-Fi 6]
    Modem --- FW[Firewall MediaVue - OPNsense]
    FW --- Switch[Switch Mercusys MS105G]
    
    subgraph LAN_Cabeada [Rede Interna Cat6A]
        Switch --- Xeon[Servidor Xeon - Proxmox]
        Switch --- Nitro[Acer Nitro V15]
        Switch --- Xbox[Xbox One S]
    end
    
    subgraph WLAN [Rede Sem Fio Wi-Fi 6]
        Modem -.-> POCO[Xiaomi POCO F7]
        Modem -.-> T460[ThinkPad T460 - Externo/Home]
    end

---
🎒 Cenários de Uso

🏠 Cenário Doméstico
Focado em administração de servidores, virtualização via Proxmox, hospedagem de servidores de jogos (Minecraft) e backups redundantes em RAID 1.

🏫 Cenário Móvel (Faculdade)
Utilização do ThinkPad T460 com Kubuntu para desenvolvimento em Docker, estudos de automação e acesso remoto seguro aos serviços domésticos via VPN.

🛡️ Segurança e Privacidade

Endereçamento: Por segurança, IPs públicos e privados não são documentados neste repositório.

Credenciais: Chaves de acesso e senhas são gerenciadas via arquivos locais protegidos (.env).

Segmentação: Regras de firewall são projetadas para isolar o tráfego de serviços públicos da rede de gerenciamento pessoal.