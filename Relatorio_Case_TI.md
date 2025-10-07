
# Relatório – Case Analista de TI Suporte – Pleno

## 1. Integração e Extração de Dados
- Conexão realizada via API do ERP (exemplo Python/Power Query fornecido).
- Tratamento: normalização de clientes, preenchimento de meses faltantes, cálculo de indicadores de crédito e vendas.

Arquivos simulados gerados:
- `sales_history.csv` – histórico de vendas de 20 clientes × 24 meses.
- `credit_status.csv` – status de crédito e inadimplência dos clientes.

## 2. Modelagem de Dados (Power BI)
- Modelo estrela com tabelas DimCliente, DimVendedor, DimDate, FactVendas, FactCredito.
- Relacionamentos: Cliente–Vendas, Vendedor–Vendas, Data–Fatos.

### Medidas principais em DAX
- TotalVendas = SUM(FactVendas[amount])
- Crescimento_Mes = (VendasAtual - VendasAnterior)/VendasAnterior
- VendasRolling3 = Rolling 3 meses
- CreditoDisponivel = SUM(FactCredito[credit_available])
- PctUtilizacao = Dívida / Limite

## 3. Dashboard Proposto
**Página 1 – Visão Geral**
- KPIs de vendas, crescimento, clientes aptos/não aptos.
- Linha de tendência de vendas mensais.
- Barra por vendedor.
- Tabela top clientes com crédito e situação.

**Página 2 – Cliente Detalhe**
- Timeline de vendas do cliente.
- Indicadores de crédito, alerta visual para risco (>90% utilização ou queda >30%).

## 4. Insights – Clientes em Risco
### Cliente_17
- Queda de 62% nas vendas 3m.
- Crédito estourado (115%).
- **Risco alto.** Ação: bloqueio temporário, renegociação, cobrança ativa.

### Cliente_04
- 3 meses sem compras.
- Crédito disponível baixo (10%).
- **Risco médio.** Ação: campanha de reativação, oferta especial, revisar dívidas.

### Cliente_09
- Dívida crescente 4m, 92% limite usado.
- **Risco médio-alto.** Ação: limitar vendas, parcelar dívida, monitorar recebíveis.

## 5. Perguntas Provocadoras
**Para Comercial**
1. Quais clientes reduziram compras de forma abrupta (>50%)? Motivo: concorrência, qualidade, crédito?
2. Devemos automatizar bloqueio de pedidos quando uso de crédito >90%?

**Para Contábil**
1. Estamos provisionando perdas corretamente? Qual impacto no fluxo 3m?
2. Motivos mais frequentes de disputa/estorno? Podem ser evitados com ajustes contratuais?

## 6. Conclusão
- O modelo e dashboards permitem visão unificada de vendas + crédito.
- Insights possibilitam ação imediata sobre clientes em risco.
- Perguntas instigam melhorias comerciais e contábeis.
