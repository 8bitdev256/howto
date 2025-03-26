#Criar chave SSH na conta do GitHub

- Na conta do GitHub, acessar Settings -> SSH and GPG keys -> clicar no link "Generating SSH keys" ou "connecting to GitHub using SSH keys";
 - Clicar no link "Verificar se há chaves SSH"
 - Na pasta do seu usuário ("~"), Rodar comando "ls -al ~/.ssh" para verificar se existem chaves SSH no computador
 - Se não houverem chaves cadastradas no computador, você receberá uma resposta do terminal parecida com "ls: cannot access ~/.ssh: No such file or directory"
 - Caso exista, as chaves sem extensão .pub são as chaves privadas e as chaves com extensão .pub são as chaves públicas.
 - No link anterior onde foi clicado na opção "Verificar se há chaves SSH", clique na opção "Gerar nova chave SSH"
 - Cole o texto abaixo, substituindo o email usado no exemplo pelo seu endereço de email do GitHub:
	ssh-keygen -t ed25519 -C "your_email@example.com"
 - Se estiver usando um sistema herdado que não dá suporte ao algoritmo Ed25519, ao invés do comando informado anteriormente, use o comando abaixo:
 	ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
 - No próximo passo, o terminal solicitará uma senha (passphrase). Digite uma senha de sua preferência e tecle Enter
 - Serão geradas as chaves pública e privada
 - Rode o comando abaixo para iniciar o agente SSH em segundo plano;
	eval "$(ssh-agent -s)"
 - Caso o terminal retorne algo como "Agent pid 1278", significa que o agente SSH foi iniciado com sucesso em segundo plano
 - Rode o comando abaixo para adicionar sua chave SSH privada ao agente SSH:
	ssh-add ~/.ssh/id_ed25519
 - Digite a senha (passphrase) definida nos passos anteriores
 - Caso o terminal retorne algo como "Identity added: ~/.ssh/id_ed25519 (your_email@example.com)", significa que a chave foi adicionada com sucesso
 - No link anterior onde foi clicado na opção "Gerar nova chave SSH", clique na opção "Adicionar uma nova chave SSH"
 - Na conta do GitHub, acessar Settings -> SSH and GPG keys e clicar em "New SSH key"
 - Defina um título de sua preferência para a chave. Normalmente é utilizado um título que descreve a finalidade da chave
 - Em "Key type", escolha a opção "Authentication Key"
 - A tipo de chave "Signing Key" (chave de assinatura) serve para você registrar uma chave apenas para commits
 - No terminal, digite o comando abaixo para acessar o diretório de chaves:
	cd ~/.ssh
 - Em seguida, digite o comando abaixo para listar as chaves existentes no diretório atual:
	ls
 - Serão exibidas duas chaves, uma privada (sem extensão, de nome "id_ed25519") e uma pública (extensão .pub, de nome "id_ed25519.pub")
 - Para visualizar o conteúdo do arquivo que contém a chave pública, digite o comando abaixo:
	cat id_ed25519.pub
 - De volta à conta do GitHub, copie a chave retornada pelo terminal e cole no campo "Key", incluindo o email que é exibido no final da chave
 - Digite sua senha do GitHub ou o código de autenticação de dois fatores para confirmar a operação, caso tenha configurado a autenticação de dois fatores na sua conta
 - A partir de agora, para clonar repositórios usando a chave SSH, utilize sempre a opção "SSH" ao invés de "HTTPS" para copiar o link do respositório que deseja clonar
 - Ao rodar o "git clone link_do_repositorio" pela primeira vez, será solicitado que confirme se deseja continuar. Basta digitar yes no terminal e teclar Enter
 - Digite a senha (passphrase) definida nos passos anteriores
