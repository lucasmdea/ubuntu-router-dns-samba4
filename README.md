# Servidor Linux como Router, DNS e Samba4

Este repositório contém um guia passo a passo para instalação e configuração de um servidor Debian/Ubuntu (Desktop ou Server) atuando como:

- 🌐 Router entre rede LAN e WAN
- 📡 Servidor DNS
- 🏢 Controlador de Domínio com Samba4 (Active Directory)
- 🖥️ Ingresso de máquinas Windows no domínio

## 📌 Ambiente de trabalho
- 2 interfaces de rede:
  - WAN: acesso à Internet
  - LAN: rede interna
- Clientes Windows ingressando no domínio
- Controle centralizado de usuários

## 📚 Conteúdo

1. Introdução
2. Requisitos
3. Configuração de Rede (LAN/WAN)
4. DNS
5. Samba4 (AD DC)
6. Segurança

## 🛠️ Tecnologias utilizadas

- Ubuntu Server
- Samba4
- Bind9 / DNS interno do Samba
- iptables / nftables
- Windows 10 / 11 (clientes)

# Configuração Inicial do Sistema

## Configurando 
Podemos iniciar o projeto fazendo algumas configurações (opicionais) para facilitar a nossa experiência durante o projeto.
Logue como root utilizando as credenciais criadas na instalação do sistema e atualize e faça o upgrade dos pacotes instalados.

```bash
apt update && apt upgrade -y
```
OBS1: Caso você tenha algum problema de biblioteca de pacotes, comente a busca por atualizações via DVD da iso.
Utilize um editor de texto para fazer essa alteração, nesse caso será utilizado o Nano:
```bash
nano -l /etc/apt/souces.list
```
Comente a primeira linha: 
```
# deb cdrom: [Debian GNU/Linux 13.3.0 _Trixie_ - Official amd64 DVD Binary-1 with firmaware 20260110-11:00]/ trixie contrib main non-free-firmware
```
OBS2: Caso você tenha interesse em utilizar os comando de copiar e colar para agilizar a conclusão do projeto:
Primeiro, será necessário instalar o serviço de SSH para o acesso externo caso a partir de um outro computador na rede LAN

```bash
apt install openssh-server
```
Após a instalação, caso o serviço já não esteja instalado, prosiga para habilitar a conexão remota ao servidor
Edite o arquivo de configuração do SSH
nano -l /etc/ssh/sshd_config

Linha 38 PubkeyAuthentication yes
Linha 57 PasswordAuthentication yes

instale o serviço "sudo" através do comando apt install sudo

modifique o usuário que você criou na instalação sistema operacional
usermod -aG sudo seu_usuario





## 📄 Licença

Este projeto é livre para estudo e uso educacional.
