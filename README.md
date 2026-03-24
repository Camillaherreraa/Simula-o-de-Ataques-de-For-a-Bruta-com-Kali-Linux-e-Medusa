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


Ataque de Força Bruta em FTP

Foi utilizado o Medusa para realizar tentativas de autenticação no serviço FTP.

medusa -h 192.168.0.10 -u msfadmin -P wordlist.txt -M ftp

Resultado observado:

Identificação de credenciais válidas com base em combinações simples de usuário e senha
Ataque em Aplicação Web (DVWA)

Foi utilizado o DVWA para simular um cenário de autenticação vulnerável.

Procedimentos realizados:

Acesso à aplicação via navegador
Configuração do nível de segurança como "low"
Submissão de múltiplas tentativas de login utilizando wordlists

Resultado observado:

Validação de credenciais por ausência de mecanismos de proteção contra força bruta
Password Spraying em SMB

Foi realizada a enumeração de usuários e posterior tentativa de autenticação em massa.

Enumeração:

nmap --script smb-enum-users 192.168.0.10

Ataque:

medusa -h 192.168.0.10 -U users.txt -P passwords.txt -M smbnt

Resultado observado:

Identificação de acessos válidos utilizando combinações comuns de senha
Wordlists Utilizadas

Exemplo de wordlist simples utilizada nos testes:

123456
password
admin
msfadmin
root
Medidas de Mitigação

Com base nos testes realizados, foram identificadas as seguintes recomendações:

FTP
Desativar autenticação anônima
Utilizar políticas de senha forte
Implementar limitação de tentativas de login
Aplicações Web
Implementar CAPTCHA ou mecanismos equivalentes
Adotar autenticação multifator (MFA)
Monitorar tentativas de login suspeitas
SMB
Definir políticas de bloqueio de conta
Utilizar senhas complexas
Desativar versões inseguras do protocolo (como SMBv1)
Conclusão

O projeto evidenciou como sistemas com configurações inadequadas podem ser facilmente comprometidos por ataques de força bruta.

Também reforça a importância de boas práticas de segurança, como:

uso de senhas fortes
controle de tentativas de autenticação
atualização e configuração adequada dos serviços
