# 🐧 Linux para Cybersegurança — Guia Prático de Comandos

Guia focado no uso real de Linux em:
- Pentest
- CTF
- Laboratórios de segurança
- Pós-exploração
- Enumeração de sistemas

> Não é uma lista teórica. São comandos que um profissional de segurança realmente usa em cenários reais.

---

# 📁 1. Navegação e Manipulação de Arquivos

## pwd
Mostra o diretório atual.

**Quando usar**
- Confirmar localização após ganhar shell
- Scripts automatizados
- Orientação em sistemas desconhecidos

---

## ls
Lista arquivos e diretórios.

| Comando | Função |
|---|---|
| `ls` | lista simples |
| `ls -l` | detalhes |
| `ls -la` | inclui arquivos ocultos |

**Uso em segurança**
- Encontrar arquivos sensíveis
- Descobrir permissões
- Identificar artefatos ocultos

---

## cd
Altera o diretório atual.

**Uso**
- Navegação em sistemas comprometidos
- Acesso a diretórios críticos

---

## tree
Mostra a estrutura completa de diretórios.

⚠️ Pode não estar instalado por padrão  
Instalação: `sudo apt install tree`

**Uso**
- Mapear aplicações web
- Entender organização do sistema

---

## cp
Copia arquivos.

**Uso**
- Backup antes de modificar arquivos
- Duplicação de configurações

---

## mv
Move ou renomeia arquivos.

**Uso**
- Alterar nomes de arquivos
- Organizar artefatos

---

## rm
Remove arquivos.

**Uso**
- Limpeza em laboratório
- Remoção de arquivos temporários

⚠️ Nunca usar em ambientes reais sem autorização.

---

## find
Busca arquivos no sistema.
`find / -name "*.conf" 2>/dev/null`

**Uso**
- Buscar arquivos de configuração
- Descobrir dados sensíveis

---

## locate
Busca rápida baseada em índice.

**Uso**
- Encontrar binários rapidamente
- Descobrir caminhos conhecidos

---

# 👤 2. Usuários e Permissões

## whoami
Mostra o usuário atual.

**Uso**
- Confirmar contexto após exploração

---

## id
Mostra UID, GID e grupos do usuário.

**Uso**
- Verificar privilégios
- Avaliar potencial de escalonamento

---

## chmod
Altera permissões de arquivos.
`chmod +x exploit.sh`

**Uso**
- Tornar arquivos executáveis

---

## chown
Altera o dono de um arquivo.

**Uso**
- Controle de acesso quando permitido

---

## sudo -l
Lista permissões sudo do usuário.

**Uso crítico**
- Identificar comandos executáveis como root
- Vetor clássico de escalonamento de privilégio

---

# 🌐 3. Rede (Essencial em Pentest)

## ip a
Mostra interfaces e endereços IP.

**Uso**
- Identificar interfaces de rede
- Mapear ambiente interno

---

## ip route
Mostra tabela de rotas.

**Uso**
- Descobrir redes acessíveis

---

## ping
Testa conectividade com um host.

**Uso**
- Verificar hosts ativos

---

## ss -tulnp
Lista portas abertas e processos associados.

**Uso**
- Identificar serviços em execução

---

## netstat -tulnp
Ferramenta legada para portas e conexões.

⚠️ Pode não estar instalada em sistemas modernos.

---

## arp -a
Mostra dispositivos na rede local (LAN).

**Uso**
- Descobrir hosts na mesma rede

---

## nc (netcat)
Ferramenta de rede multifuncional.
`nc -lvnp 4444`

**Uso**
- Listener de shell reverso
- Transferência de dados
- Conexões TCP/UDP

---

# 🕵️ 4. Enumeração do Sistema (Pós-Exploração)

Enumeração é o processo de coletar o máximo de informações após obter acesso inicial.

Objetivos:
- Identificar usuários e privilégios
- Descobrir serviços vulneráveis
- Encontrar vetores de escalonamento
- Mapear o ambiente

---

## Informações do sistema

### uname -a
Mostra informações do sistema e kernel.

### uname -r
Mostra versão do kernel.

### cat /etc/os-release
Mostra versão da distribuição Linux.

**Uso**
- Identificar vulnerabilidades conhecidas

---

## Usuários e autenticação

### cat /etc/passwd
Lista usuários do sistema.

**O que observar**
- Usuários com shell ativo
- Contas de serviço

---

### cat /etc/shadow
Contém hashes de senha (requer root).

**Uso**
- Extração de hashes após escalonamento

---

## Privilégios

### sudo -l
Verifica permissões sudo.

### id
Confirma grupos e privilégios.

---

## Processos e serviços

### ps aux
Lista todos os processos.

### top / htop
Monitoramento em tempo real.

**O que analisar**
- Serviços rodando como root
- Processos incomuns

---

## Variáveis e ambiente

### env
Mostra variáveis de ambiente.

**Uso**
- Encontrar credenciais
- Descobrir caminhos úteis

---

## Histórico e contexto

### history
Mostra histórico de comandos.

**Uso**
- Descobrir ações administrativas
- Encontrar credenciais

---

## Informações do host

### hostname
Mostra nome da máquina.

---

## Diretórios importantes
`ls -la /home
ls -la /root`

**Uso**
- Buscar arquivos sensíveis
- Identificar usuários ativos

---

## Busca de arquivos SUID (crítico)
`find / -perm -4000 2>/dev/null`

**Uso**
- Encontrar binários com privilégios elevados
- Possível escalonamento de privilégio

---

# 🎯 Checklist Prático de Enumeração

Após obter shell:

### 1. Identidade e privilégios
- whoami
- id
- sudo -l

### 2. Sistema
- uname -a
- uname -r
- cat /etc/os-release
- hostname

### 3. Usuários
- cat /etc/passwd
- ls -la /home

### 4. Processos
- ps aux
- ss -tulnp

### 5. Credenciais potenciais
- env
- history
- arquivos de configuração

### 6. Escalonamento
- find / -perm -4000 2>/dev/null

---

# 📦 5. Transferência de Arquivos

## Download
- wget
- curl

## Transferência via SSH
- scp

## Servidor HTTP temporário
`python3 -m http.server`

## Transferência direta
- nc (netcat)

## Codificação para transporte
- base64

## Empacotamento
- tar

---

# 🧠 6. Manipulação de Texto

## Visualização
- cat
- less

## Busca e filtragem
- grep

## Processamento de colunas
- cut
- sort
- uniq

## Processamento avançado
- awk
- sed

---

# 🧭 Mentalidade Operacional em Pós-Exploração

Ordem lógica de raciocínio:

1. Quem sou eu no sistema?
2. Quais permissões eu tenho?
3. O que está rodando?
4. Onde estão os dados sensíveis?
5. Existe caminho para root?

Enumeração é um processo de decisão.

