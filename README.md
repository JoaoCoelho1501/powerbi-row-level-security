# Segurança em Power BI: Row Level Security e Object-Level Security

> Modelo Power BI de incidentes de cibersegurança com RLS dinâmico e segurança ao nível de métricas (OLS) para 8 perfis de utilizador.

**Mestrado em Business Intelligence & Analytics (ISCAP)**, 2025/26

## O problema
Os dados de incidentes de segurança são sensíveis. Cada perfil (analista do SOC, gestor, auditoria, gestores regionais) só deve ver os dados e as métricas de que precisa.

## O que foi feito
- **Modelo em estrela**: tabela de factos `Facts_Cyber_Security` ligada a 10 dimensões, incluindo a dimensão tempo. As relações são Many-to-One e unidirecionais.
- **Medidas DAX** organizadas em pastas: volume, risco, severidade, impacto na privacidade, princípios CIA e eficácia de resposta.
- **RLS dinâmico** com `Security_Table` e `USERPRINCIPALNAME()`.
- **Metric Security (OLS)**: tabelas de dimensão escondidas consoante o papel.
- **8 papéis**: Analista_SOC, Gestor, Auditoria e 5 gestores regionais.

> Nota: o `USERPRINCIPALNAME()` não funciona no teste local do Power BI Desktop. A validação foi feita com *View as role*.

## Estrutura
```
powerbi/  ficheiro .pbix (abrir no Power BI Desktop)
docs/     relatório com a implementação e testes por papel
```

## Stack
`Power BI Desktop` · `DAX` · `RLS` · `OLS` · `Star schema`

## Autores
Débora Jesus · João Coelho
