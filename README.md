# Simulação de Ataque de Força Bruta com Medusa e Kali Linux

Este projeto documenta uma auditoria de segurança prática realizada em ambiente controlado, utilizando o **Kali Linux** contra o alvo **Metasploitable 2**. O objetivo foi explorar vulnerabilidades de autenticação em diferentes serviços (FTP, HTTP e SMB) para validar conceitos de **Cybersecurity** e medidas de mitigação.

---

## Tecnologias e Ferramentas Utilizadas
* **Sistema Operacional:** [Kali Linux](https://www.kali.org/)
* **Alvo Vulnerável:** [Metasploitable 2](https://sourceforge.net/projects/metasploitable/) e [DVWA](https://dvwa.co.uk/)
* **Ferramenta de Auditoria:** [Medusa](https://github.com/jondonas/medusa)
* **Enumeração:** `Nmap`, `enum4linux` e `smbclient`
* **Documentação:** Markdown e GitHub

---

## 🛠️ Desenvolvimento do Projeto

### 1. Preparação do Ambiente e Wordlists
Para simular o ataque, foram criadas wordlists personalizadas de usuários e senhas comuns utilizando comandos de shell:

```bash
# Criando lista de usuários
echo -e "user\nadmin\nmsfadmin\nroot\nservice" > users.txt

# Criando lista de senhas (Password Spraying)
echo -e "123456\npassword\nqwerty\nmsfadmin\nWelcome123" > pass.txt
