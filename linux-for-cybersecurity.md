
# 🐧 Linux para Cybersegurança — Guia Prático de Comandos

Guia focado no uso real de Linux em:
- Pentest
- CTF
- Laboratórios de segurança
- Pós-exploração
- Enumeração de sistemas

> Não é uma lista teórica. São comandos que um profissional de segurança realmente usa.

---

#  1. Navegação e Manipulação de Arquivos

## pwd
Mostra o diretório atual.

**Quando usar**
- Confirmar localização após ganhar shell
- Scripts automatizados

---

## ls
Lista arquivos.

| Comando | Função |
|---|---|
| `ls` | lista simples |
| `ls -l` | detalhes |
| `ls -la` | inclui arquivos ocultos |

**Uso em cyber**
- Encontrar arquivos sensíveis
- Descobrir permissões
- Identificar artefatos escondidos

---

## cd
Troca de diretório.

**Uso**
- Navegação em sistemas comprometidos

---

## tree
Mostra estrutura completa de diretórios.

**Uso**
- Mapear aplicações web
- Entender estrutura do sistema

---

## cp
Copia arquivos.

**Uso**
- Backup antes de modificar
- Duplicar configs

---

## mv
Move ou renomeia arquivos.

**Uso**
- Ocultar payloads
- Alterar nomes suspeitos

---

## rm
Remove arquivos.

**Uso**
- Limpeza de artefatos no laboratório

⚠️ Evite em ambientes reais sem autorização.

---

## find
Busca arquivos no sistema.

```bash
find / -name "*.conf" 2>/dev/null
---
## locate
- Busca rápida indexada
**uso**
- Encontrar binários específicos rapidamente

# 2. Usuários e Permissões

## whoami
- mostra o usuário atual
**uso**
-Verificar privilégio após exploração

## id
- Mostra UID e grupos.
**uso**
- Verificar acesso priviligediado
- Avaliar potencial de escalonamento

## chmod
- Altera permissãoes
``` chmod +x exploit.sh ```
**uso**
- 
