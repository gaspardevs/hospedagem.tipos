# 📦 HOSPEDAGEM.TIPOS

# 📖 Sobre

O **Media Hub** é um repositório criado para armazenar e organizar arquivos de mídia utilizados por bots.

Seu principal objetivo é centralizar todos os links em um único lugar, facilitando a manutenção e evitando a necessidade de modificar o código do bot sempre que uma mídia precisar ser alterada.

As mídias podem ser utilizadas em qualquer projeto que faça requisições HTTP para obter arquivos diretamente do GitHub.

---

# ✨ Recursos

- 📸 Hospedagem de imagens
- 🎞️ Hospedagem de GIFs
- 🎥 Hospedagem de vídeos
- 📂 Organização por categorias
- 🚀 Fácil integração com bots
- 🌐 Links públicos
- 🔄 Atualização simples das mídias

---

# 📁 Estrutura

Exemplo da estrutura do repositório:

```
Media-Hub
│
├── img/
│   ├── beijo/
│   ├── abraço/
│   ├── tapa/
│   └── ...
│
├── gif/
│   ├── anime/
│   ├── memes/
│   └── ...
│
├── video/
│   ├── edits/
│   ├── anime/
│   └── ...
│
└── README.md
```

Cada pasta contém arquivos organizados por categoria.

---

# 🔗 Utilização

As mídias podem ser acessadas através do link RAW do GitHub.

Exemplo:

```
https://raw.githubusercontent.com/USUARIO/REPOSITORIO/main/img/beijo/01.jpg
```

ou

```
https://raw.githubusercontent.com/USUARIO/REPOSITORIO/main/video/edit/01.mp4
```

Esses links podem ser utilizados diretamente em bots, APIs ou qualquer aplicação.

---

# 🤖 Exemplo em Node.js

```javascript
const image = "https://raw.githubusercontent.com/USUARIO/REPOSITORIO/main/img/beijo/01.jpg"

await conn.sendMessage(chatId,{
    image:{url:image},
    caption:"Exemplo"
})
```

Vídeo:

```javascript
const video = "https://raw.githubusercontent.com/USUARIO/REPOSITORIO/main/video/edit/01.mp4"

await conn.sendMessage(chatId,{
    video:{url:video}
})
```

GIF:

```javascript
const gif = "https://raw.githubusercontent.com/USUARIO/REPOSITORIO/main/gif/anime/01.gif"

await conn.sendMessage(chatId,{
    video:{url:gif},
    gifPlayback:true
})
```

---

# 📂 Categorias

O repositório pode conter diferentes tipos de mídia.

Exemplo:

## Imagens

- Abraço
- Beijo
- Tapa
- Chorar
- Feliz
- Triste
- Anime
- Wallpapers

## GIFs

- Anime
- Meme
- Reação
- Engraçados

## Vídeos

- Edit
- Anime
- Shorts
- Memes

---

# ⚙ Organização

Cada categoria possui diversos arquivos numerados.

Exemplo:

```
beijo/

001.jpg
002.jpg
003.jpg
004.jpg
005.jpg
...
```

Isso facilita a seleção aleatória das mídias.

---

# 🚀 Vantagens

- Não aumenta o tamanho do bot.
- Fácil atualização das mídias.
- Organização simples.
- Compartilhamento rápido.
- Funciona com qualquer linguagem de programação.
- Compatível com APIs.
- Links permanentes através do GitHub.

---

# 💡 Recomendações

Para obter melhor desempenho:

- Utilize arquivos otimizados.
- Evite vídeos extremamente grandes.
- Organize as mídias por categoria.
- Utilize nomes simples para pastas.
- Numere os arquivos em sequência.

---

# 📌 Casos de Uso

Este repositório pode ser utilizado em:

- Bots de WhatsApp
- Bots de Discord
- Bots de Telegram
- APIs
- Sites
- Aplicações Node.js
- Projetos pessoais

---

# 🤝 Contribuições

Contribuições são bem-vindas.

Caso encontre algum arquivo com problema ou queira adicionar novas mídias, fique à vontade para abrir um Pull Request.

---

# 📜 Licença

Este projeto está licenciado sob a licença MIT.

Você pode utilizar este repositório em projetos pessoais ou comerciais, respeitando os termos da licença.

---

# ❤️ Créditos

Projeto desenvolvido para servir como central de armazenamento de mídias utilizadas por bots e aplicações.

Caso utilize este repositório, considere deixar uma ⭐ para apoiar o projeto.

---

<p align="center">
⭐ Se este projeto foi útil para você, deixe uma estrela no repositório!
</p>
