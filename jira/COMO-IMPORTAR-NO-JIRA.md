# Como importar o backlog no Jira

Arquivo: **`jira-import-backlog.csv`** (UTF-8 com BOM, pronto para o Jira Cloud).

> 💡 Dica: use um projeto **company-managed** do tipo **Scrum** — é o que melhor suporta importação via CSV com *Epic Link* e *Story Points*.

## Passo a passo (Jira Cloud)

1. **Crie o projeto** `EstoqueZap` (tipo *Scrum*, **company-managed**).
2. Vá em **⚙ Configurações → System → External System Import → CSV**
   (ou *Project settings → Import issues*).
3. **Faça upload** do arquivo `jira-import-backlog.csv` e selecione o encoding **UTF-8**.
4. Escolha o projeto de destino (`EstoqueZap`).
5. **Mapeie as colunas** (o nome no CSV → campo do Jira):

   | Coluna no CSV | Campo no Jira |
   |---|---|
   | Issue Type | Issue Type |
   | Summary | Summary |
   | Epic Name | Epic Name |
   | Epic Link | Epic Link |
   | Component | Component/s |
   | Priority | Priority |
   | Story Points | Story Points *(ou "Story point estimate")* |
   | Labels | Labels |
   | Description | Description |

6. Confirme. O Jira cria os **3 épicos** e vincula as **histórias/enablers** a eles
   (o *Epic Link* casa com o *Epic Name*).
7. Rode a importação. ✅

## Observações

- **Story Points:** se o campo não aparecer no mapeamento, ative-o no *board → Configurações → Estimation* (campo "Story Points"). Depois reimporte ou ajuste.
- **Componentes (= Features):** o importador cria os componentes automaticamente
  (Cadastro & Acesso, Gestão de Produtos, Registro de Vendas, Alertas de Ruptura, Dashboard, Infraestrutura, etc.).
- **Critérios de aceitação:** vão dentro do campo *Description* de cada história (assim importam sem precisar de campo customizado).
- **Enablers:** importados como *Task* com a label `enabler` (e `nfr` no caso do requisito não funcional EZ-3 — LGPD).
- Se algo no *Epic Link* não vincular, basta arrastar a história para o épico no *backlog* do Jira depois.

## Hierarquia adotada

**Épico** (MVP / Incremento 1 / Incremento 2) › **Feature** (Componente do Jira) › **História de usuário / Enabler**.
