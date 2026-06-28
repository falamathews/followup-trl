# Gerador de Follow Up de Importação — TRL Internacional

Dashboard que **roda no navegador** (sem servidor). A Luh **cola as linhas da planilha**,
confere a prévia e **gera o PDF consolidado** (capa-panorama + uma ficha por processo),
no padrão visual do cliente. Documento: `AC.FLW.OP.IMP.02`.

Arquivos: **`index.html`** (a dashboard) e **`logos.js`** (logos embutidas). Só isso.

---

## Publicar online (GitHub Pages) — ~2 min

1. No GitHub: **New repository** → nome `followup-trl` → **Create**.
   *(Pode ser público sem medo: o repositório só tem o gerador — nenhum dado de cliente fica salvo aqui.
   Se preferir privado, o Pages exige plano pago; nesse caso use a Netlify, abaixo.)*
2. **Add file → Upload files** → arraste `index.html` e `logos.js` → **Commit changes**.
3. **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main` / `root` → **Save**.
4. Aguarde ~1 min. A URL aparece no topo da página de Pages:
   `https://<seu-usuario>.github.io/followup-trl/`
5. Mande essa URL para a Luh (favoritar).

**Alternativa ainda mais rápida (sem git):** acesse `app.netlify.com/drop` e **arraste a pasta** com
os dois arquivos. Sai uma URL na hora (e funciona com repositório privado/sem repositório).

---

## Como a Luh usa (toda semana)

1. Abre a URL.
2. (Opcional) ajusta **Cliente**, **Emissão** e a **logo do cliente** (padrão: Girando Sol).
3. Na planilha, seleciona as linhas dos processos **incluindo a linha de título**, copia (Ctrl+C)
   e **cola (Ctrl+V)** no campo → **Processar colagem**.
4. Confere a prévia. Se algum **status** vier vazio/errado, ajusta no menu (ele acende a trilha).
5. **Gerar PDF (salvar)** → abre o diálogo de impressão → **Salvar como PDF**.

> **Importante no diálogo de impressão:** deixe **“Gráficos em segundo plano” (Background graphics) LIGADO**
> e margens em **Padrão**, senão as cores/gradientes não saem no PDF.

---

## O que ele entende da colagem

Mapeia as colunas **pelo título** (em qualquer ordem). Títulos reconhecidos:
`processo`, `cliente`, `modalidade`, `follow`, `etd` (ou “embarque”), `eta` (ou “chegada”),
`prontidão`, `produtos`, `fornecedor`, `tipo de carga`, `status`.

- **status**: `A Chegar` · `Atracado` · `Aguardando Registro` · `Registrado` (acende a trilha; ajustável na prévia).
- **produtos**: separe por `;` → vira um chip cada.
- Sem linha de título, ele assume a ordem: processo, cliente, modalidade, follow, etd, eta, prontidão, produtos, fornecedor, tipo de carga, status.

## Trocar/ajustar

- **Outro cliente**: preencha o nome em *Cliente* e envie a logo dele no campo *Logo do cliente*.
- **Cores/identidade**: as variáveis estão no topo do `<style>` em `index.html` (`--navy`, `--orange`, `--yellow`…).
- **Trocar a logo da TRL** pela oficial: substitua o valor `trl` em `logos.js` por outro data URI (base64).

Nada é enviado a servidor — a colagem e o PDF acontecem 100% no navegador da Luh.
