# ===============================
# Configuração personalizada do Zsh
# ===============================

# Histórico
HISTFILE=~/.zsh_history
HISTSIZE=5000
SAVEHIST=5000
setopt HIST_IGNORE_ALL_DUPS     # ignora duplicados
setopt HIST_IGNORE_SPACE        # não salva comandos iniciados com espaço
setopt SHARE_HISTORY            # compartilha histórico entre sessões

# Melhorias de usabilidade
setopt AUTO_CD                  # permite "cd pasta" só digitando "pasta"
setopt CORRECT                  # sugere correção para comandos
zstyle ':completion:*' menu select
zstyle ':completion:*' list-colors "${(s.:.)LS_COLORS}"

# ===============================
# Plugins (instalados manualmente em ~/.zsh/plugins)
# ORDEM IMPORTA: autocomplete → autosuggestions → syntax-highlighting (sempre por último)
# ===============================

# Autocomplete em tempo real (tipo fish)
if [[ -r ~/.zsh/plugins/zsh-autocomplete/zsh-autocomplete.plugin.zsh ]]; then
  source ~/.zsh/plugins/zsh-autocomplete/zsh-autocomplete.plugin.zsh
else
  # fallback: completion nativo
  autoload -Uz compinit
  compinit
fi

# Sugestões do histórico
[[ -r ~/.zsh/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh ]] \
  && source ~/.zsh/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh

# Syntax highlighting (deve ser o último plugin a ser carregado)
[[ -r ~/.zsh/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh ]] \
  && source ~/.zsh/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

# ===============================
# Integração com bat (cat melhorado)
# ===============================
# Ubuntu/Pop usam "batcat"; outras distros costumam usar "bat"
if command -v bat >/dev/null 2>&1; then
  alias cat='bat -pp'
elif command -v batcat >/dev/null 2>&1; then
  alias cat='batcat -pp'
fi

# ===============================
# Prompt personalizado
# ===============================
setopt PROMPT_SUBST  # permite usar funções/comandos dentro do PROMPT

git_prompt() {
  local b
  b=$(git rev-parse --abbrev-ref HEAD 2>/dev/null) || return 0
  [[ -n $b ]] && printf ' (%s%s%s)' '%F{green}' "$b" '%f'
}

# usuario@host:~/dir (branch) [HH:MM:SS] $
PROMPT='%F{cyan}%n@%m%f:%F{yellow}%~%f$(git_prompt) [%F{blue}%*%f] $ '

#Comando para erro do completion do Docker
fpath=(~/.zsh/completions $fpath)
autoload -Uz compinit
compinit

# ===============================
# Fim do ~/.zshrc
# ===============================
