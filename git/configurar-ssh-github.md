# Configurar SSH com o GitHub

**Problema:** `git push` falhava com `Permission denied (publickey)`.

**Causa:** a chave SSH existia no PC (`~/.ssh/id_ed25519`), mas não estava cadastrada na conta do GitHub.

**Solução:**

```bash
# 1. Gerar a chave (se ainda não existir)
ssh-keygen -t ed25519 -C "seu-email"

# 2. Copiar a chave PÚBLICA (Windows / Git Bash)
cat ~/.ssh/id_ed25519.pub | clip

# 3. Colar em github.com/settings/ssh/new (campo "Key"; "Title" é só um apelido)

# 4. Testar
ssh -T git@github.com
# Hi <usuario>! You've successfully authenticated...
```

**Dica:** use a URL SSH no remote: `git@github.com:<usuario>/<repo>.git`.
