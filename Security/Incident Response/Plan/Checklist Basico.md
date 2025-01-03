Analise Inicial

1.0 Confirmar a existência do incidente (Entender se o incidente precisa de mais atenção ou apenas report)
1.1 Analisar os indicadores, (ex: verificar extenção do ransonware, tipo do binario executado, entender se ação potencialmente maliciosa foi feita por um funcionario autorizado)
1.2 Correlacionar informações de diferentes fontes (Levantar outros logs, FIREWALL, IDS/IPS, Anti-Virus, Cloud) (Buscar logins com sucesso e falha, instalações, criação de usuarios...)
1.3 Mapear usuarios locais e persistencias
1.4 Avaliar regras de FIREWALL
1.5 Consultar bases de conhecimento externas (Levantar o maximo de informação externa sobre os IOCs identificados ate o momento, tipo do ataque, grupo de ransonware, ips usados e etc)


1.7 Priorizar o tratamento do incidente com base no impacto
1.8 Impacto Funcional (Detalhar quals servidores e serviços estão indisponiveis)
1.9 Impacto Informacional (Detalhar quais dados sensiveis foram vazados ou corrompidos)

1.10 Estimar o esforço necessário para recuperação.

1.11 Relatar o incidente ao pessoal interno apropriado e às organizações externas relevantes
1.11.1 Notificar as equipes internas responsáveis (segurança, TI, gerência).
1.11.2 Informar partes externas (parceiros, provedores de serviços, autoridades) conforme necessário.

Contenção, Erradicação e Recuperação
2. Garantir preservação e integridade das evidências (Coletar logs, snapshots e informações relevantes antes de formatar maquinas)
3. Conter o incidente (Excluir regras de firewall, Remover persistencias, )
3.1 Isolar sistemas/hosts afetados (bloquear acessos, desconectar da rede, reiniciar senhas).
3.2 Aplicar controles temporários para limitar danos. (Remover acessos, desabilitar VPNs, Fechar portas, Criar regras que limitem acessos a redes de nucleo)

Erradicar o incidente
6.0 Restaurar Backups se nescessário
6.1 Identificar e mitigar todas as vulnerabilidades exploradas (Levantar vulnerabilidades do CISA e zera-las)
6.2 Remover malwares, materiais inadequados, persistencias e usuarios locais
6.3 Identificar processos e drivers maliciosos, matar os processos, remover persistencias, deletar arquivos de malwares, reiniciar e repetir
6.4 (Ferramentas: Process Explorer)
6.3 Se forem descobertos mais hosts afetados (por exemplo, novas infecções por malware), repetir os passos acima) para identificar todos os outros hosts afetados, e em seguida conter e erradicar o incidente nesses sistemas

Recuperar do incidente
7.0 Restaurar Backups se nescessário
7.1 Retornar os sistemas afetados a um estado operacional
7.2 Confirmar que os sistemas afetados estão funcionando normalmente
7.3 Apos a restauração de backup, repetir passo 6.0 a 6.2 para garantir que maquinas estejam de fato limpas
7.3 Implementar monitoramento adicional para observar possíveis atividades suspeitas

Atividade Pós-Incidente
8. Elaborar um relatório final detalhado (timeline, impacto, ações tomadas).
8.1 Armazenar documentação em local seguro para auditorias futuras (Recomendado 3 anos)

9.0 Conduzir reunião de lições aprendidas
9.1 Reunir as partes envolvidas para discutir falhas, melhorias e próximos passos.
9.2 Atualizar políticas e procedimentos de segurança conforme as descobertas.

10.0 Implementar melhorias no processo
10.1 Revisar e aprimorar o plano de resposta a incidentes.
10.2 Treinar equipes para mitigar riscos identificados durante o incidente.
