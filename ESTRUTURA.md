# Estrutura do projeto

Mapa das pastas e arquivos de código. O código-fonte não é publicado neste repositório
(é software de uso interno de uma empresa real); aqui fica a arquitetura.

```text
├── app/   # pipeline: leitura, OCR, classificação, nomeação, ponte com a interface web
│   ├── web/   # interface HTML/CSS/JS (WebView2)
│   │   ├── app.css
│   │   ├── app.js
│   │   ├── index.html
│   │   └── tema.css
│   ├── cache_utils.py
│   ├── construtoras.py
│   ├── employees.py
│   ├── extractor.py
│   ├── gui.py
│   ├── imagem_utils.py
│   ├── main.py
│   ├── ocr_utils.py
│   ├── pdf_splitter.py
│   ├── servidor.py
│   ├── test_extractor.py
│   ├── web_api.py
│   └── web_janela.py
├── scripts/   # empacotamento e conferências
│   ├── conferir_web.py
│   ├── dessaturar_assets.py
│   ├── diagnose.py
│   ├── preparar_planilha.py
│   └── rebuild.py
└── tests/   # suíte de testes
    ├── integration/
    │   ├── __init__.py
    │   ├── test_autocadastro_ancora.py
    │   ├── test_competencia_lote.py
    │   ├── test_persistencia_imediata.py
    │   └── test_pipeline_cadastro.py
    ├── regression/
    │   ├── __init__.py
    │   ├── test_ancoras_admissionais.py
    │   ├── test_aviso_competencia_gui.py
    │   ├── test_categorias_admissionais.py
    │   ├── test_categorias_rh.py
    │   ├── test_coluna_por_cabecalho.py
    │   ├── test_competencia_epi_data_entrega.py
    │   ├── test_competencia_ruido_ocr.py
    │   ├── test_comprovante_pix.py
    │   ├── test_conflito_cadastro_status.py
    │   ├── test_documentos_rescisorios.py
    │   ├── test_nome_cesta_ocr_parcial.py
    │   ├── test_nome_contrato_experiencia_sr_a.py
    │   ├── test_nome_higienizacao.py
    │   ├── test_nome_por_aproximacao.py
    │   ├── test_pagina_ilegivel.py
    │   ├── test_resgate_nome_pelo_cadastro.py
    │   └── test_vt_rotulo_funcionario.py
    ├── unit/
    │   ├── __init__.py
    │   ├── test_cache_utils.py
    │   ├── test_employees.py
    │   ├── test_ocr_binarizacao.py
    │   └── test_segunda_leitura.py
    ├── __init__.py
    ├── test_construtoras.py
    ├── test_servidor.py
    └── test_web_api.py
```

## Tamanho (linhas, sem bibliotecas de terceiros)

| Linguagem | Linhas |
|---|---:|
| Python | 12.322 |
| JavaScript | 555 |
| CSS | 541 |
| HTML | 165 |

_Arquivos: 54._
