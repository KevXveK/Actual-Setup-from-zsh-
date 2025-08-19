# Actual-Setup-from-zsh-
In this repository is my setup from zsh

1) Instalar pacotes básicos
   sudo apt update
   sudo apt install zsh git curl wget bat -y   # em Ubuntu/Pop o binário é "batcat"
2)Tornar o Zsh o shell padrão
  chsh -s "$(command -v zsh)
3)Clonar os plugins necessários
  mkdir -p ~/.zsh/plugins
  git clone https://github.com/marlonrichert/zsh-autocomplete ~/.zsh/plugins/zsh-autocomplete
  git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/plugins/zsh-autosuggestions
  git clone https://github.com/zsh-users/zsh-syntax-highlighting ~/.zsh/plugins/zsh-syntax-highlighting
4)Copiar o zshrc e aplicar as configurações
  source ~/.zshrc
5)Corrigir erro no completion do docker
  mkdir -p ~/.zsh/completions
  curl -L https://raw.githubusercontent.com/docker/cli/master/contrib/completion/zsh/_docker -o ~/.zsh/completions/_docker


