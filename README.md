## Guia Prático de Git e GitHub com VSCode (Windows e macOS)
- Neste repositório, você encontrará um passo a passo prático sobre como utilizar Git e GitHub integrados ao VSCode, com instruções específicas tanto para Windows quanto para macOS.
- Git é uma ferramenta essencial, tanto para projetos pessoais quanto profissionais. Trata-se de um sistema de controle de versão que permite acompanhar o histórico de alterações dos arquivos, possibilitando restaurar versões anteriores do código e facilitando o trabalho colaborativo ou individual.
- Já o GitHub é uma plataforma de hospedagem de repositórios Git. Ele permite armazenar, compartilhar e colaborar em projetos que utilizam versionamento, tornando o desenvolvimento mais organizado e eficiente.

##### Pré-requisitos (Windows):
- Baixe e instale o [Git para Windows](https://git-scm.com/downloads).
- Baixe e instale o [Visual Studio Code](https://code.visualstudio.com).
- Tenha ou crie uma conta no [GitHub](https://github.com).

##### Pré-requisitos (macOS):
- Git já vem instalado, mas atualize (no terminal) com: `brew install git`.
- Baixe e instale o [Visual Studio Code](https://code.visualstudio.com).
- Tenha ou crie uma conta no [GitHub](https://github.com);


### ✅ 1. Configure o Git
- Após a instalação, é importante verificar se o Git foi instalado corretamente em sua máquina. Para isso, abra o terminal (no macOS) ou o Git Bash (no Windows) e execute o seguinte comando: `git --version` e se esse comando retornar alguma versão instalada, significa que o Git está pronto para uso.
- Em seguida, ainda no terminal (macOS) ou Git Bash (Windows), configure as informações iniciais do Git executando os comandos abaixo:
    - `git config --global user.name “Seu Nome”`;
    - `git config --global user.name “seu@email.com”`;
    - `git config --global core.editor "code --wait"`;

### ✅ 2. Conectando repositório local ao remoto.
- Para migrar um repositório local ao GitHub é necessário configurar uma chave SSH.
- [Aqui está o guia para gerar sua chave SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent), mas basicamente, basta acessar o terminal (macOS) ou o Git Bash (Windows) e executar o seguinte comando, substituindo pelo seu e-mail do GitHub: `ssh-keygen -t rsa 4096 -C seu@email.com`.
- Após executar o comando acima, apenas pressione `Enter` para todas as perguntas, aceitando os valores padrão de local de salvamento e senha.
- Depois visualize a chave SSH criada, usando o comando: `cat ~/.ssh/id_ed25519.pub` e copie tudo, incluindo o e-mail no final.
- Agora é somente adicionar a chave SSH ao GitHub, acesse: https://github.com/settings/ssh/new e em `Title`, dê qualquer nome, já em `Key`, cole toda a chave copiada e clique em `Add SSH key`.

### ✅ 3. Teste a conexão SSH
- No terminal (macOS) ou Git Bash (Windows), teste a conexão com: `ssh -T git@github.com` e se tudo estiver funcionando corretamente, você verá uma mensagem como: `Hi seu-usuario! You've successfully authenticated, but GitHub does not provide shell access.`
- Se falhar, você verá a mensagem: `Operation timed out`, então tente a porta alternativa: `ssh -T -p 443 git@ssh.github.com` e se funcionar, é preciso configurar o SSH para usar essa porta, então, no terminal (macOS), abra o arquivo com: `open -e ~/.ssh/config`, no Windows, acesse com algum editor de texto: `C:\Users\SeuNome\.ssh\config`.
- Adicione o seguinte conteúdo ao arquivo: `Host github.com Hostname ssh.github.com Port 443`, salve o arquivo e feche o editor.

### ✅ 4. Iniciando projetos com o Git