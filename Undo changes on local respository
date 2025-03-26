# Desfazendo alterações no repositório local

- Caso tenha rodado o comando git init na pasta errada, basta remover a pasta .git da pasta, usando rm -rf nome_da_pasta ou apagando manualmente
- Restaurar arquivo para último estado antes da alteração: git restore nome_do_arquivo
- Defazer um commit: utilizar comando git reset. Opções podem ser --soft, --mixed ou --hard. Na frente da opção, digitar id do commit, que pode ser obtido através do comando git log. Exemplo: git reset --soft 4d534db052bc550b41c5765e15c616830910e3ce
soft: Desfaz o commit e envia os arquivos alterados por este commit para a área de preparação (Changes to be commited)

mixed (comportamento padrão do git reset: Desfaz o commit e envia os arquivos alterados por este commit para a área de arquivos não rastreados (Untracked files)

hard: Desfaz o commit ignora completamente os arquivos alterados por este commit, como se nunca tivessem existido. Use esta opção com cuidado.

- Histórico de commits: git log
- Histórico detalhado de alterações: git reflog
- Desfazer um comando git add: git reset nome_do_arquivo
