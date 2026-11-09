# Placement Test — como publicar no Netlify

## 1. Criar a chave da API (Claude Console)
1. Entre em platform.claude.com com o seu e-mail (é uma conta separada do Claude Pro).
2. Vá em **Billing**, clique em **Buy credits** e compre um valor pequeno para começar. Os créditos valem por 1 ano.
3. Vá em **API keys**, clique em **Create key**, dê o nome "placement-test" e copie a chave (começa com `sk-ant-`). Guarde-a, porque ela só aparece uma vez.

## 2. Subir os arquivos no GitHub
O Netlify Drop (arrastar a pasta) não roda a parte que corrige o teste, então use o GitHub:
1. Crie uma conta em github.com (se ainda não tiver).
2. Clique em **New repository**, dê o nome "placement-test", deixe como **Private** e crie.
3. Clique em **uploading an existing file** e arraste **todo o conteúdo** desta pasta (index.html, netlify.toml e a pasta netlify). Clique em **Commit changes**.

## 3. Publicar no Netlify
1. Entre em netlify.com com a sua conta do GitHub.
2. **Add new project > Import an existing project > GitHub** e escolha "placement-test".
3. Antes de publicar, em **Environment variables**, adicione:
   - Key: `ANTHROPIC_API_KEY`
   - Value: a chave que você copiou no passo 1
4. Clique em **Deploy**.

## 4. Receber os resultados por e-mail
1. No Netlify, abra o site e vá em **Forms**. Clique em **Enable form detection**.
2. Vá em **Deploys > Trigger deploy > Deploy site**, para o Netlify detectar o formulário.
3. Em **Forms > Form notifications > Add notification > Email notification**, escolha o formulário "placement-results" e coloque o seu e-mail.

Pronto: cada aluno que terminar o teste aparece em **Forms** e chega no seu e-mail, com nota, nível, questões erradas e os três textos de writing já corrigidos.

## 5. Nome do link (opcional)
Em **Domain management > Options > Edit site name**, mude o nome para algo como `renanlemes-placement` e o link vira renanlemes-placement.netlify.app.

## Dicas
- Para testar, faça o teste você mesmo uma vez e confira se o resultado chega por e-mail.
- Se a correção do writing falhar (por exemplo, sem créditos), o teste continua funcionando: o aluno recebe uma estimativa e o e-mail avisa "NOT MARKED".
- Para trocar o modelo de IA, adicione a variável `MODEL` no Netlify (o padrão é claude-sonnet-5-5).
