# Auto Vidro Costa — landing page

Página estática (HTML, CSS e JS num único arquivo). Tema preto e azul escuro com detalhes dourados, mobile-first.

- `index.html`: site pronto para publicar.
- `src/template.html` + `src/build.py`: fonte e script que gera o `index.html` (embute as fotos e recalcula o hash do CSP).
- `SEGURANCA_HOSPEDAGEM.md`: cabeçalhos e configurações que dependem da hospedagem.

## Atualizar contatos ou textos
Edite `src/template.html` (e a lista de contatos em `src/build.py`) e gere de novo com `python3 src/build.py`.
As fotos originais ficam em `img/` e `img2/` (no seu computador; não estão neste repositório).

## Adicionar fotos de trabalhos
Em `src/build.py`, na lista `works`, inclua `(número_da_foto, "Serviço", "Veículo")`. A "telinha" de rolagem se atualiza sozinha.
