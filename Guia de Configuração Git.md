# Guia de Configuração Git + GitHub via SSH no Ubuntu

---

## 1️⃣ Instalar Git (se ainda não estiver)
sudo apt update
sudo apt install git -y
# Explicação: Atualiza pacotes e instala Git.

---

## 2️⃣ Configurar usuário Git
git config --global user.name "SeuNome"
git config --global user.email "seuemail@dominio.com"
# Explicação: Define nome e email para commits.

---

## 3️⃣ Verificar se já existe chave SSH
ls ~/.ssh
# Explicação: Verifica se há chaves existentes.

---

## 4️⃣ Gerar nova chave SSH
ssh-keygen -t ed25519 -C "seuemail@dominio.com"
# Explicação: Cria uma chave segura. Pressione Enter em todos os prompts.

---

## 5️⃣ Copiar chave pública
cat ~/.ssh/id_ed25519.pub
# Explicação: Mostra a chave que será adicionada no GitHub.

---

## 6️⃣ Adicionar chave no GitHub
# No GitHub:
# 1. Settings → SSH and GPG keys
# 2. Clique em New SSH key
# 3. Title: Notebook Ubuntu
# 4. Cole a chave copiada do passo 5
# 5. Salve

---

## 7️⃣ Testar conexão SSH
ssh -T git@github.com
# Explicação: Testa se a chave funciona. Resposta esperada:
# Hi SeuUsuario! You've successfully authenticated, but GitHub does not provide shell access.

---

## 8️⃣ Configurar repositório para SSH
git remote set-url origin git@github.com:SeuUsuario/NomeDoRepo.git
# Verificar:
git remote -v
# Deve mostrar URLs SSH.

---

## 9️⃣ Fazer push e pull
git push origin main
git pull origin main
# Explicação: Funciona sem pedir usuário ou senha.

---

## 🔹 Dica extra
# Iniciar agente SSH e adicionar chave (se tiver colocado passphrase):
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
# Permite usar passphrase sem digitar sempre.

