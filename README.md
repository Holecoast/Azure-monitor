# Monitoramento de Máquinas Virtuais no Azure

> Guia prático para configurar e gerenciar o monitoramento de VMs no Microsoft Azure, com foco em visibilidade e resposta a eventos críticos.

## Conteúdo

- Azure Monitor
- Logs de Atividade
- Alertas Personalizados
- Diagnóstico e Análise
- Dicas Rápidas
- Recursos Úteis

## Azure Monitor

- Habilite métricas e logs de diagnóstico da VM pelo portal Azure.
- Configure a integração com um Log Analytics Workspace.
- Utilize dashboards personalizados para acompanhar o uso de recursos e eventos em tempo real.
- Exemplos de métricas úteis:
  - Uso de CPU
  - Latência de disco
  - Bytes de rede enviados/recebidos
  - Status da VM

## Logs de Atividade

- Navegue até `Monitor > Activity Log` para ver eventos recentes.
- Para detectar ações como exclusão de VMs, use consultas com KQL (Kusto Query Language):

```kql
AzureActivity
| where OperationNameValue == "Microsoft.Compute/virtualMachines/delete"
| project TimeGenerated, ResourceGroup, Resource, Caller, StatusValue
```

- Os logs incluem quem realizou a ação, quando, e qual recurso foi afetado.

## Alertas Personalizados

1. Acesse `Monitor > Alerts` e clique em "Nova regra de alerta".
2. Selecione o recurso (por exemplo, a VM ou grupo de recursos).
3. Escolha o sinal "Log de Atividade".
4. Defina a condição: operação = "Delete Virtual Machine".
5. Configure ações como:
   - Envio de e-mail
   - Notificações via SMS ou push
   - Chamada de webhook
   - Execução de Logic App ou Azure Function

## Diagnóstico e Análise

- Use o **Log Analytics** para consultas avançadas e correlação de eventos.
- O **Azure Advisor** fornece recomendações sobre desempenho, segurança e custo.
- O **Microsoft Defender for Cloud** oferece insights de segurança e proteção contra ameaças.

## Dicas Rápidas

- Utilize **Resource Locks** do tipo `CanNotDelete` para proteger VMs críticas contra exclusão acidental.
- Aplique **RBAC** (controle baseado em função) para limitar permissões.
- Configure **Automation Accounts** para executar scripts de resposta automática.
- Use **Tags** para categorizar recursos e facilitar a gestão e o monitoramento em larga escala.

## Recursos Úteis

- Documentação do Azure Monitor: https://learn.microsoft.com/pt-br/azure/azure-monitor/
- Referência de KQL: https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference
- Guia de alertas no Azure: https://learn.microsoft.com/pt-br/azure/azure-monitor/alerts/alerts-overview

## Licença

MIT

Este material tem fins educacionais e foi criado para apoiar o aprendizado em monitoramento no Microsoft Azure.
