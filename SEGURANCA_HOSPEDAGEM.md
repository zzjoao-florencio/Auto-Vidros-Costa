# Auto Vidro Costa — o que depende da hospedagem

O site é estático (sem servidor, banco ou API própria). Isso elimina SQL Injection, CSRF e credenciais expostas, mas os itens abaixo **só funcionam se configurados no servidor/CDN**. A meta tag de CSP do HTML não substitui cabeçalhos HTTP.

## Cabeçalhos HTTP
```
Strict-Transport-Security: max-age=31536000; includeSubDomains
Content-Security-Policy: default-src 'none'; script-src 'sha256-Kmodu9VtNMzjlNKfItffKTTVf9V2kX9GW/o2TirxEdI='; style-src 'unsafe-inline' https://fonts.googleapis.com; font-src https://fonts.gstatic.com; img-src data:; connect-src 'none'; base-uri 'none'; form-action 'none'; frame-ancestors 'none'; object-src 'none'
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: camera=(), microphone=(), geolocation=(), payment=()
```
O hash do CSP muda se qualquer caractere do script for editado; recalcule (o `src/build.py` já faz isso).
Ative HTTPS e redirecione HTTP→HTTPS. Só ative HSTS depois de confirmar que o HTTPS funciona.

## Google Fonts
As fontes Barlow Condensed, Great Vibes e Manrope vêm do Google, que recebe o IP dos visitantes (já descrito na política de privacidade). Para eliminar isso, baixe os arquivos .woff2, hospede no próprio site e remova os domínios do Google do CSP.

## Outros
- GitHub: repositório privado, sem arquivos .env ou chaves; ative 2FA.
- Se um dia houver backend: validação no servidor, rate limiting, logs sem dados pessoais.
- O anti-spam do formulário (campo oculto, intervalo entre envios) roda só no navegador.

## Dados que o proprietário deve confirmar (em amarelo nos textos legais)
CNPJ · endereço · responsável pela privacidade · base legal validada por advogado · provedor de hospedagem e período de logs · prazo de retenção das conversas · foro.
