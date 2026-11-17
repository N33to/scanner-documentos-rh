# Scanner de documentos de RH

Aplicativo Windows local que recebe PDFs enormes com dezenas de documentos misturados (holerites, fichas de EPI, comprovantes, contratos), separa cada documento, identifica o tipo, a competência e o colaborador, e devolve um PDF por documento já renomeado, mais um relatório com o **nível de confiança** de cada decisão.

> **O código não é público** (o programa lida com dados pessoais). Este repositório traz a arquitetura em [ESTRUTURA.md](ESTRUTURA.md).

## O problema

No fechamento do mês, o RH recebia PDFs gigantes com documentos de várias pessoas embaralhados. Separar e renomear um por um é trabalho repetitivo e propenso a erro.

## Como funciona

1. **Texto nativo primeiro**; OCR só quando a página é imagem (com teste de rotação).
2. **Hierarquia de decisão, da camada mais barata para a mais cara:** regras determinísticas por categoria, heurísticas de normalização, casamento aproximado do nome com o cadastro de colaboradores (RapidFuzz) e, por último, revisão humana (`REVISAR` no relatório).
3. **Categorias entram por configuração**, não por código: um tipo novo de documento é um bloco novo em um arquivo de regras.
4. Cada lote gera relatório em CSV e um histórico, para medir se uma correção realmente melhorou o resultado.

## Decisões de engenharia

- **Processamento 100% local.** Documento, imagem e texto extraído nunca saem da máquina.
- **Originais intocados:** a saída vai sempre para uma pasta nova.
- **Cache de OCR por SHA-256** da imagem renderizada: reprocessar um lote já visto ficou **28× mais rápido** (18,9 s → 0,67 s nas páginas medidas), com saída idêntica.
- **Teste de regressão antes da correção** em todo bug real, com fixtures anonimizadas.
- **Nunca derruba o lote por causa de um arquivo ruim**: o erro vira linha no relatório e o resto segue.
- **Interface web com reserva:** a janela HTML/CSS/JS roda em WebView2; se não subir na máquina, o programa cai sozinho numa interface Tkinter.
- **Entrega verificada:** o empacotamento só roda com os testes verdes e confere o executável gerado.

## Stack

Python 3.12 · PyMuPDF · Tesseract + OpenCV · RapidFuzz · openpyxl · pywebview (WebView2) · HTML/CSS/JS · PyInstaller · Git
