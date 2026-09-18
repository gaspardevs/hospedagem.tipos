# 📦 Hospedagem de Mídias para Bots e Projetos

<p align="center">
  <strong>Uma central organizada para hospedar imagens, GIFs, vídeos, arquivos JSON e outros recursos públicos.</strong>
</p>

<p align="center">
  <a href="https://github.com/gaspardevs/hospedagem.tipos">Repositório</a> •
  <a href="https://github.com/gaspardevs/hospedagem.tipos/issues">Reportar problema</a> •
  <a href="https://github.com/gaspardevs/hospedagem.tipos/pulls">Contribuir</a>
</p>

---

## 📖 Sobre o projeto

O **Hospedagem de Mídias** é um repositório criado por **Gaspar Modz** para armazenar, organizar e disponibilizar arquivos utilizados em bots, APIs, sites e aplicações em geral.

A proposta é manter imagens, GIFs, vídeos e arquivos JSON centralizados em um único lugar. Assim, você pode atualizar uma mídia sem precisar alterar todo o código do seu projeto.

Os arquivos podem ser acessados por requisições HTTP usando links públicos do GitHub.

> ⚠️ **Importante:** o GitHub não deve ser tratado como uma CDN para arquivos muito grandes ou aplicações de alta escala. Para vídeos pesados e grande volume de acessos, considere utilizar serviços próprios de armazenamento, como Cloudinary, Amazon S3 ou Cloudflare R2.

---

## ✨ Recursos

- 📸 Hospedagem de imagens
- 🎞️ Hospedagem de GIFs
- 🎥 Hospedagem de vídeos
- 📄 Armazenamento de arquivos JSON
- 📂 Organização por categorias
- 🔗 Links públicos via `raw.githubusercontent.com`
- 🤖 Integração simples com bots
- 🌐 Compatibilidade com qualquer linguagem que aceite requisições HTTP
- 🔄 Atualização centralizada das mídias
- 🧩 Estrutura preparada para novos tipos de arquivo

---

## 📁 Estrutura do repositório

```text
hospedagem.tipos/
├── img/
│   ├── anime/
│   ├── beijo/
│   ├── abraço/
│   ├── memes/
│   └── reações/
│
├── gif/
│   ├── anime/
│   ├── memes/
│   └── reações/
│
├── video/
│   ├── anime/
│   ├── edits/
│   └── memes/
│
├── cases/
│   └── game2/
│
├── json/
│   ├── urls/
│   └── README.md
│
└── README.md
```

Cada pasta deve conter arquivos relacionados à mesma categoria. Use nomes simples, consistentes e fáceis de localizar.

---

## 🔗 Como acessar uma mídia

A forma recomendada é utilizar o endereço RAW do arquivo:

```text
https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/img/beijo/001.jpg
```

### Exemplos de links

**Imagem:**

```text
https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/img/beijo/001.jpg
```

**GIF:**

```text
https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/gif/anime/001.gif
```

**Vídeo:**

```text
https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/video/edits/001.mp4
```

> Prefira utilizar a branch `main` quando quiser que o link acompanhe as atualizações do arquivo. Para referenciar exatamente uma versão específica, use o SHA de um commit no lugar de `main`.

---

## 🤖 Integração com Node.js

### Enviando uma imagem

```js
const imageUrl =
  "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/img/beijo/001.jpg";

await conn.sendMessage(chatId, {
  image: { url: imageUrl },
  caption: "Exemplo de imagem hospedada no GitHub",
});
```

### Enviando um vídeo

```js
const videoUrl =
  "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/video/edits/001.mp4";

await conn.sendMessage(chatId, {
  video: { url: videoUrl },
  caption: "Exemplo de vídeo hospedado no GitHub",
});
```

### Enviando um GIF

```js
const gifUrl =
  "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/gif/anime/001.gif";

await conn.sendMessage(chatId, {
  video: { url: gifUrl },
  gifPlayback: true,
  caption: "Exemplo de GIF hospedado no GitHub",
});
```

> Os exemplos utilizam uma API compatível com `conn.sendMessage`. Adapte a implementação de acordo com a biblioteca utilizada no seu bot.

---

## 📄 Utilizando um arquivo JSON de URLs

Para evitar colocar vários links diretamente no código do bot, você pode organizar as mídias em um arquivo JSON.

### Exemplo de `json/urls/imagens.json`

```json
{
  "beijo": [
    "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/img/beijo/001.jpg",
    "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/img/beijo/002.jpg"
  ],
  "anime": [
    "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/img/anime/001.jpg"
  ]
}
```

### Carregando o JSON no Node.js

```js
const response = await fetch(
  "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/json/urls/imagens.json"
);

if (!response.ok) {
  throw new Error(`Não foi possível carregar o JSON: ${response.status}`);
}

const media = await response.json();
const randomImage = media.beijo[Math.floor(Math.random() * media.beijo.length)];

await conn.sendMessage(chatId, {
  image: { url: randomImage },
  caption: "Imagem selecionada aleatoriamente",
});
```

> O Node.js precisa estar em uma versão compatível com `fetch`. Em versões antigas, instale e utilize uma biblioteca como `node-fetch`.

---

## 🗂️ Padrão de organização

Para manter o projeto limpo e profissional, siga estas convenções:

```text
img/beijo/001.jpg
img/beijo/002.jpg
img/beijo/003.jpg

gif/reacoes/001.gif
gif/reacoes/002.gif

video/edits/001.mp4
video/edits/002.mp4
```

### Boas práticas

- Use nomes de pastas em minúsculas.
- Evite espaços e caracteres especiais nos nomes dos arquivos.
- Numere arquivos com três dígitos: `001`, `002`, `003`.
- Mantenha uma única categoria por pasta.
- Utilize extensões corretas: `.jpg`, `.png`, `.gif`, `.mp4` e `.json`.
- Comprima imagens e vídeos antes de enviá-los.
- Remova arquivos duplicados ou que não estejam sendo utilizados.
- Atualize os arquivos JSON quando adicionar ou remover mídias.

---

## 📚 Categorias sugeridas

### Imagens

- Abraços
- Beijos
- Reações
- Memes
- Anime
- Wallpapers
- Felicidade
- Tristeza
- Choro

### GIFs

- Anime
- Memes
- Reações
- Comédia
- Ações

### Vídeos

- Edits
- Anime
- Shorts
- Memes
- Clipes

---

## 🚀 Casos de uso

Este repositório pode ser utilizado em:

- Bots de WhatsApp
- Bots de Discord
- Bots de Telegram
- APIs REST
- Aplicações Node.js
- Sites e páginas web
- Sistemas de automação
- Projetos pessoais
- Protótipos e experimentos

---

## 🛠️ Adicionando uma nova mídia

1. Escolha a pasta correta (`img`, `gif` ou `video`).
2. Entre na categoria correspondente ou crie uma nova.
3. Adicione o arquivo seguindo o padrão de nomenclatura.
4. Atualize o arquivo JSON relacionado, quando necessário.
5. Faça o commit das alterações.
6. Teste o link RAW antes de utilizá-lo no seu projeto.

Exemplo de mensagem de commit:

```text
feat: adiciona novos gifs de reações
```

---

## 🤝 Contribuições

Contribuições são bem-vindas! Para colaborar:

1. Faça um fork deste repositório.
2. Crie uma branch para sua alteração.
3. Adicione ou organize as mídias.
4. Verifique se os links estão funcionando.
5. Abra um Pull Request com uma descrição clara.

Ao contribuir, adicione apenas arquivos que você tem autorização para compartilhar e respeite os direitos autorais das mídias.

---

## 📜 Licença e direitos autorais

Este repositório utiliza a licença MIT para o código e a estrutura do projeto. A licença não concede automaticamente direitos sobre imagens, GIFs, vídeos ou outros arquivos de terceiros.

Antes de utilizar ou redistribuir qualquer mídia, verifique se ela pode ser compartilhada e utilizada no seu projeto.

---

## 👤 Autor

Desenvolvido e organizado por **Gaspar Modz**.

- GitHub: [@gaspardevs](https://github.com/gaspardevs)
- Repositório: [hospedagem.tipos](https://github.com/gaspardevs/hospedagem.tipos)

---

<p align="center">
  ⭐ Se este repositório foi útil para você, deixe uma estrela!
</p>

<p align="center">
  Feito com dedicação para facilitar a criação de bots e projetos digitais.
</p>
