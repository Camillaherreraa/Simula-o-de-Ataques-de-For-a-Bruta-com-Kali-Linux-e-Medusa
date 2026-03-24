# Projeto: Simulação de Ataques de Força Bruta com Kali Linux e Medusa

## Descrição

Este projeto tem como objetivo demonstrar, de forma prática e estruturada, a execução de ataques de força bruta em um ambiente controlado, utilizando o Kali Linux e a ferramenta Medusa.

Foram abordados cenários comuns de vulnerabilidade em serviços de rede, incluindo FTP, aplicações web (DVWA) e SMB, com foco tanto na exploração quanto na análise de medidas de mitigação.

---

## Ambiente de Testes

O ambiente foi configurado utilizando máquinas virtuais no VirtualBox:

- Kali Linux (máquina atacante)
- Metasploitable 2 (máquina vulnerável)

### Configuração de Rede

- Tipo: Rede interna (Internal Network)
- Nome da rede: lab
- Comunicação direta entre as máquinas virtuais

---

## Ferramentas Utilizadas

- Kali Linux
- Medusa
- Nmap
- DVWA (Damn Vulnerable Web Application)
- Metasploitable 2

---

## Metodologia

O projeto foi dividido em três etapas principais:

1. Reconhecimento dos serviços disponíveis
2. Execução de ataques de força bruta
3. Análise dos resultados e proposição de medidas de mitigação

---

## Reconhecimento com Nmap

Inicialmente, foi realizado um scan para identificar os serviços ativos na máquina alvo:

```bash
nmap -sV 192.168.0.10
