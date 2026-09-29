## Session
  Session   Koneksi Figma MCP Server
  Continue  opencode -s ses_f15a53254ffeKOz12dKcUf4KkS

  Session   Koneksi ke file Figma PRAK ECOMM
  Continue  opencode -s ses_f153f132dffeckqBmkC69iZaiq

## Setup MCP di Laptop Lain
1. Clone/copy folder proyek ini, lalu bikin file config dari template:
   ```bash
   cp opencode.jsonc.example opencode.jsonc
   ```
2. Isi token Figma kamu di `opencode.jsonc` (lihat bagian **Token Expired** di bawah cara dapatkannya).

   > `opencode.jsonc` sudah masuk `.gitignore` karena berisi token rahasia.
   > Dua MCP (`figma` + `pdf-reader`) sudah dikonfigurasi di level proyek — tidak ada lagi config global.

## Token Expired
Token Figma berlaku ±30 hari. Kalau sudah expired (error 401 saat manggil tool Figma), refresh pakai tool [`gberaudo/opencode-mcp-figma`](https://github.com/gberaudo/opencode-mcp-figma) (sudah ada di folder `opencode-mcp-figma/`):

```bash
cd opencode-mcp-figma
npm i
npm run build
npm start https://mcp.figma.com/mcp   # login Figma di browser
```

Token baru ada di `opencode-mcp-figma/mcp-auth.json` (field `access_token`). Lalu:

1. Tempel token baru ke `opencode.jsonc` (field `headers.Authorization`, ganti `Bearer ...`).
2. Restart service: `opencode service restart`

## Catatan

