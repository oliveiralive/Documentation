```
Analise Inicial

1.1.1 Confirmar a existência do incidente (Entender se o incidente precisa de mais atenção ou apenas report)
1.1.2 Analisar os indicadores, (ex: verificar extenção do ransonware, tipo do binario executado, entender se ação potencialmente maliciosa foi feita por um funcionario autorizado)
1.1.3 Cadeia de Custódia (N de Serie de equipamentos, IPs, MacAdrrs) (Nomes, Cargos, Telefone e email dos responsaveis pela maquina ou sistema) (Nome e contatos do analista), (Data e Hora), (Local da ocorrencia)

1.2.1 Priorizar o tratamento do incidente com base no impacto
1.2.2 Impacto Funcional (Detalhar quals servidores e serviços estão indisponiveis)
1.2.3 Impacto Informacional (Detalhar quais dados sensiveis foram vazados ou corrompidos)

1.3.1 Correlacionar informações de diferentes fontes (Levantar outros logs, FIREWALL, IDS/IPS, Anti-Virus, Cloud) (Buscar logins com sucesso e falha, instalações, criação de usuarios...)
1.3.2 Mapear usuarios locais e persistencias
1.3.3 Avaliar regras de FIREWALL (Fazer topologia de acesso, mapeando as portas que as redes se falam)
1.3.4 Consultar bases de conhecimento externas (Levantar o maximo de informação externa sobre os IOCs identificados ate o momento, tipo do ataque, grupo de ransonware, ips usados e etc)

1.4 Estimar o esforço necessário para recuperação.

1.5.1 Relatar o incidente ao pessoal interno apropriado e às organizações externas relevantes
1.5.2 Notificar as equipes internas responsáveis (segurança, TI, gerência).
1.5.3 Informar partes externas (parceiros, provedores de serviços, autoridades) conforme necessário.

Contenção, Erradicação e Recuperação
2.1 Isolar sistemas/hosts afetados (desconectar da rede, bloquear acessos, reiniciar senhas).
2.2 Garantir preservação e integridade das evidências (Coletar logs, snapshots e informações relevantes antes de formatar maquinas)
2.3 Aplicar controles temporários para limitar danos. (Remover acessos, desabilitar VPNs, Fechar portas, Criar regras que limitem acessos a redes de nucleo)

Erradicar o incidente
3.1 Caso a maquina esteja criptografada e exista backup, pular para o passo 4.1, caso contrario seguir para passo 3.2
3.2 Identificar processos e drivers maliciosos, matar os processos, remover persistencias, deletar arquivos de malwares, analisar usuarios locais, revisao senhas, reiniciar e repetir (Ferramentas: Process Explorer, Process Monitor, Autoruns)
3.3 Identificar e mitigar todas as vulnerabilidades exploradas (Levantar vulnerabilidades do CISA e zera-las)
3.4 Se forem descobertos mais hosts afetados (por exemplo, novas infecções por malware), repetir os passos acima

Recuperar do incidente
4.1 Restaurar Backups
4.2 Retornar os sistemas afetados a um estado operacional
4.3 Confirmar que os sistemas afetados estão funcionando normalmente
4.4 Apos a restauração de backup, repetir passo 3.1 a 3.4 para garantir que maquinas estejam de fato limpas
4.5 Implementar monitoramento adicional para observar possíveis atividades suspeitas

Atividade Pós-Incidente
5.1. Elaborar um relatório final detalhado (timeline, impacto, ações tomadas).
5.2 Armazenar documentação em local seguro para auditorias futuras (Recomendado 3 anos)

5.3 Conduzir reunião de lições aprendidas
5.4 Reunir as partes envolvidas para discutir falhas, melhorias e próximos passos.
5.5 Atualizar políticas e procedimentos de segurança conforme as descobertas.

5.6 Implementar melhorias no processo
5.7 Revisar e aprimorar o plano de resposta a incidentes.
5.8 Treinar equipes para mitigar riscos identificados durante o incidente.

```

