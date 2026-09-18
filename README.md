# 📦 Media Hub — Hospedagem de Mídias

<p align="center">
  <strong>Central pública de imagens, GIFs, vídeos e arquivos JSON para bots, APIs e aplicações.</strong>
</p>

<p align="center">
  <a href="https://github.com/gaspardevs/hospedagem.tipos">Repositório</a> •
  <a href="https://github.com/gaspardevs/hospedagem.tipos/tree/main/cases">Cases</a> •
  <a href="https://github.com/gaspardevs/hospedagem.tipos/tree/main/json">Arquivos JSON</a>
</p>

---

## 📖 Sobre

O **Media Hub** é um repositório criado por **Gaspar Modz** para armazenar e organizar mídias utilizadas em bots, APIs, sites e projetos Node.js.

Aqui você encontrará arquivos separados por tipo e categoria, prontos para serem acessados através de links públicos do GitHub. Dessa forma, seu projeto pode consumir uma mídia por URL sem precisar manter todos os arquivos dentro do código-fonte do bot.

### O que você encontra aqui?

- Imagens para comandos e interações
- GIFs de reações, memes e animações
- Vídeos, edits e conteúdos para bots
- Cases e exemplos de utilização
- Arquivos JSON com listas de URLs
- Estrutura simples para adicionar novas mídias

---

## ✨ Recursos

| Recurso | Descrição |
| --- | --- |
| 📸 Imagens | Arquivos `.jpg`, `.jpeg`, `.png` e outros formatos compatíveis |
| 🎞️ GIFs | Animações organizadas por categorias |
| 🎥 Vídeos | Edits, memes, clipes e outros vídeos |
| 📄 JSON | Listas de URLs prontas para integração |
| 🤖 Bots | Compatível com WhatsApp, Discord, Telegram e outros projetos |
| 🔗 Links públicos | Acesso direto por requisições HTTP |
| 📂 Organização | Pastas separadas por tipo e categoria |

---

## 📁 Estrutura do projeto

```text
hospedagem.tipos/
│
├── img/                    # Imagens
│   ├── anime/
│   ├── beijo/
│   ├── abraço/
│   ├── memes/
│   └── reações/
│
├── gif/                    # GIFs e animações
│   ├── anime/
│   ├── memes/
│   └── reações/
│
├── video/                  # Vídeos
│   ├── anime/
│   ├── edits/
│   └── memes/
│
├── cases/                  # Cases e exemplos de projetos
│   └── game2/
│
├── json/                   # Listas de URLs em JSON
│   ├── urls/
│   └── README.md
│
└── README.md
```

Cada categoria possui sua própria pasta para facilitar a localização, manutenção e utilização dos arquivos.

---

## 🔗 Como utilizar uma mídia

Para utilizar qualquer arquivo, abra a mídia no GitHub, clique em **Raw** e copie o endereço. Também é possível utilizar diretamente este padrão:

```text
https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/CAMINHO_DO_ARQUIVO
```

### Exemplos

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

> Substitua `CAMINHO_DO_ARQUIVO` pelo caminho real da mídia dentro do repositório.

---

## 🤖 Exemplos com Node.js

Os exemplos abaixo utilizam uma estrutura de envio compatível com bibliotecas que trabalham com `conn.sendMessage`.

### Enviar uma imagem

```js
const imageUrl =
  "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/img/beijo/001.jpg";

await conn.sendMessage(chatId, {
  image: { url: imageUrl },
  caption: "Imagem hospedada no Media Hub",
});
```

### Enviar um vídeo

```js
const videoUrl =
  "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/video/edits/001.mp4";

await conn.sendMessage(chatId, {
  video: { url: videoUrl },
  caption: "Vídeo hospedado no Media Hub",
});
```

### Enviar um GIF

```js
const gifUrl =
  "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/gif/anime/001.gif";

await conn.sendMessage(chatId, {
  video: { url: gifUrl },
  gifPlayback: true,
  caption: "GIF hospedado no Media Hub",
});
```

---

## 📄 Utilizando URLs por meio de JSON

Quando você possui muitas mídias, pode manter os links em um arquivo JSON e carregá-los no seu bot.

### Exemplo de arquivo JSON

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

### Carregar o JSON no Node.js

```js
const jsonUrl =
  "https://raw.githubusercontent.com/gaspardevs/hospedagem.tipos/main/json/urls/imagens.json";

const response = await fetch(jsonUrl);

if (!response.ok) {
  throw new Error(`Erro ao carregar o JSON: ${response.status}`);
}

const media = await response.json();
const images = media.beijo;
const randomImage = images[Math.floor(Math.random() * images.length)];

await conn.sendMessage(chatId, {
  image: { url: randomImage },
  caption: "Mídia selecionada aleatoriamente",
});
```

---

## 🗂️ Organização das mídias

Utilize nomes simples e numeração padronizada:

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

- Use nomes em minúsculas.
- Evite espaços e caracteres especiais nos nomes dos arquivos.
- Numere arquivos com três dígitos: `001`, `002`, `003`.
- Separe as mídias por tipo e categoria.
- Comprima arquivos antes de enviá-los.
- Atualize os arquivos JSON quando adicionar novas mídias.
- Teste o link RAW antes de utilizá-lo no seu projeto.

---

## 🚀 Onde utilizar

Este Media Hub pode ser integrado a:

- Bots de WhatsApp
- Bots de Discord
- Bots de Telegram
- APIs REST
- Aplicações Node.js
- Sites e páginas web
- Sistemas de automação
- Projetos pessoais e experimentais

---

## ➕ Como adicionar uma nova mídia

1. Escolha a pasta correta: `img`, `gif` ou `video`.
2. Escolha uma categoria existente ou crie uma nova.
3. Adicione o arquivo seguindo o padrão de nomes.
4. Atualize o JSON correspondente, se necessário.
5. Faça o commit da alteração.
6. Teste o link público da mídia.

Exemplo de commit:

```text
feat: adiciona novos gifs de reação
```

---

## ⚠️ Observações importantes

- Evite arquivos excessivamente grandes.
- O GitHub não é recomendado como CDN para aplicações de alta escala.
- Para vídeos pesados ou muitos acessos, considere Cloudinary, Amazon S3 ou Cloudflare R2.
- Não envie mídias que você não tem autorização para compartilhar.
- Respeite direitos autorais, licenças e regras das plataformas.

---

## 🤝 Contribuições

Contribuições são bem-vindas! Você pode colaborar adicionando mídias autorizadas, organizando categorias ou corrigindo links.

1. Faça um fork do projeto.
2. Crie uma branch para sua alteração.
3. Faça suas modificações.
4. Verifique se os arquivos estão organizados.
5. Abra um Pull Request com uma descrição clara.

---

## 👤 Autor

Desenvolvido e organizado por **Gaspar Modz**.

- GitHub: [@gaspardevs](https://github.com/gaspardevs)
- Repositório: [gaspardevs/hospedagem.tipos](https://github.com/gaspardevs/hospedagem.tipos)
- Canal: [WhatsApp](https://whatsapp.com/channel/0029Vb7vjQoK0IBrrGPBjV0G)

---

<p align="center">
  ⭐ Se este repositório foi útil para você, deixe uma estrela!
</p>

<p align="center">
  Feito com dedicação para facilitar a criação de bots e projetos digitais.
</p>
