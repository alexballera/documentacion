# Alias de Terminal Personalizados

## Alias dinámicos para herramientas Node.js

```bash
alias node='dnode node'
alias npm='dnode npm'
alias npx='dnode npx'
alias yarn='dnode yarn'
```

## Utilidades y Navegación

```bash
alias py='python3'
alias pip='pip3'
alias serve='python3 -m http.server'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias mkdir='mkdir -p'
alias c='clear'
alias h='history'
alias update='sudo apt update && sudo apt upgrade -y'
```

## Atajos de Git

```bash
alias gs='git status'
alias gst='git status'
alias ga='git add'
alias gc='git commit'
alias gcm='git commit -m'
alias gca='git commit -a'
alias gp='git push'
alias gpl='git pull'
alias gl='git log --oneline'
alias glog='git log --oneline --graph --decorate --all'
alias gco='git checkout'
alias gcb='git checkout -b'
```

## Alias GitHub Copilot CLI

```bash
alias ask='gh copilot suggest'
alias explain='gh copilot explain'
alias cpl='gh copilot'
```

## Alias Docker básicos

```bash
alias d='docker'
alias dc='docker compose'
alias dps='docker ps'
alias dpsa='docker ps -a'
alias di='docker images'
alias dv='docker volume ls'
alias dn='docker network ls'
alias dcup='docker compose up'
alias dcupd='docker compose up -d'
alias dcdown='docker compose down'
alias dcbuild='docker compose build'
alias dclogs='docker compose logs -f'
alias dcps='docker compose ps'
alias dexec='docker exec -it'
alias dclean='docker system prune -f && docker volume prune -f'
alias dcleanall='docker system prune -a -f --volumes'
```

## Alias y utilidades adicionales

```bash
alias toolbox="/opt/jetbrains-toolbox/bin/jetbrains-toolbox"
alias secrets="$HOME/mcp-secrets/mcp-secrets.sh"
alias gemini='docker run --rm -it -e GEMINI_API_KEY=$GEMINI_API_KEY -v "$(pwd)":/app -w /app node:20-alpine npx @google/gemini-cli'
alias mcp='cd $HOME/mcp-servers'
alias mcptest='mcpask "test de conexión"'
```

---

> **Nota:** Todos estos alias están definidos en tu archivo `.bashrc` y pueden ser modificados según tus necesidades.
