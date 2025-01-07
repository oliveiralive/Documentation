# EXERCÍCIO DE MESA 2: DETECÇÃO DE EXFILTRAÇÃO DE DADOS  

**Objetivo:** Avaliar e aprimorar a capacidade da equipe do SOC de detectar, analisar e mitigar uma tentativa de exfiltração de dados 
por meio de um canal não autorizado.

**Cenário:** Sua organização, uma empresa multinacional de assistência médica, detecta tráfego de saída incomum originado de um endpoint 
de usuário. O tráfego é direcionado para um serviço de armazenamento em nuvem (Dropbox). Dados médicos sensíveis podem ter sido exfiltrados,
colocando a empresa em risco de não conformidade regulatória e de danos à reputação.

## Fase 1: Detecção Inicial e Triagem

**Inject 1:**  
- Um alerta do SIEM indica um grande volume de tráfego HTTPS de saída partindo de um único endpoint (192.168.2.45) para um domínio
  suspeito (subdomínio do Dropbox).  
- Logs do Vigilant mostram processos incomuns iniciados por um script PowerShell não autorizado no mesmo endpoint.

**Perguntas:**  
1. Quais são as ações imediatas para validar o alerta e realizar a triagem do incidente?
   R.**Análise de Logs:** Os analistas de Nível 1 do SOC devem revisar imediatamente os logs para verificar a autenticidade do alerta.
   É importante observar o volume e a frequência do tráfego de saída para o subdomínio do Dropbox e comparar esses dados com a atividade
   de referência (baseline) típica,
   *ja houve trafego parecido antes?
   *algum analista sabe do que se trata?

    **Revisão do Endpoint:** Os logs provenientes do endpoint afetado (192.168.2.45) devem ser examinados em busca de processos anormais 
    ou atividade de PowerShell, identificando especificamente qualquer acesso suspeito e processos em execução.
    
    **Confirmação de Atividade Suspeita:** Os analistas de Nível 2 (L2) devem corroborar as descobertas cruzando o tráfego de rede 
    com indicadores de comprometimento (IoCs) conhecidos, obtidos em feeds de inteligência de ameaças, dando ênfase ao tamanho do payload, 
    à frequência e à reputação do IP de destino.
    
    **Recomendação de Isolamento:** Caso a atividade seja confirmada como suspeita, o endpoint deve ser isolado para evitar maior vazamento de dados. Notifique imediatamente a equipe de resposta a incidentes para escalonamento do problema.


2. Quais ferramentas e técnicas os analistas de nível 1 (L1) e nível 2 (L2) podem usar para confirmar se ocorreu exfiltração de dados?
   R. Consulte os logs de rede em busca de grandes volumes de tráfego HTTPS de saída e conexões com domínios externos.
      Monitoramento de Integridade de Arquivos (FIM): Analise os padrões de acesso a arquivos no endpoint para determinar
      se arquivos sensíveis foram acessados e modificados.

      Análise de Hash: Compare os hashes de arquivos suspeitos (por exemplo, o do arquivo Project_Finance_Report.xlsm)
      com assinaturas maliciosas conhecidas em bancos de dados de inteligência de ameaças.

      Soluções DLP: Verifique as ferramentas de Data Loss Prevention (Prevenção de Perda de Dados) para quaisquer alertas
      que possam ter sido acionados por tentativas de upload de arquivos sensíveis para armazenamento em nuvem.

      Correlação de Atividade do Usuário: Correlacione os logs de atividade do usuário (izzmier@company.com)
      com o comportamento do endpoint para identificar discrepâncias, como anomalias de login ou uso não autorizado de aplicativos.



## Fase 2: Contenção
  Inject 2:
  
  O usuário (izzmier@company.com), cujo endpoint iniciou o tráfego, nega ter acessado o Dropbox recentemente.
  A análise de rede revela payloads criptografados sendo enviados para o destino.
  
  Perguntas:
  Como a equipe de SOC deve conter a atividade suspeita de exfiltração?
  R.  Desconectar o endpoint (192.168.2.45) da rede para interromper qualquer exfiltração em andamento.
      Bloquear o acesso do usuário ao sistema afetado até que a investigação seja concluída.
      Bloqueio de Tráfego para o Domínio Suspeito
      Configurar o firewall ou proxy para bloquear as conexões de saída para o subdomínio do Dropbox ou qualquer outro domínio identificado como suspeito.
      Revisar a lista de bloqueios em tempo real e monitorar tentativas de reconexão.
      Revisão e Revogação de Credenciais
      Suspender ou redefinir as credenciais da conta de usuário (izzmier@company.com), já que há indícios de uso indevido ou comprometimento das credenciais.
      Reforçar a autenticação multifator (MFA) onde possível.

  R.  Coleta e Preservação de Evidências
      Fazer cópias de logs (SIEM, EDR, proxy, firewall) e capturas de tráfego de rede (PCAPs) que indiquem a exfiltração.
      Garantir que toda a documentação e logs estejam armazenados de forma segura para análises futuras e possíveis ações legais ou de auditoria.
  
  R.  Comunicação Interna e Escalonamento
      Notificar a equipe de resposta a incidentes (CSIRT) e a gerência sobre os achados e as ações tomadas.
      Definir uma linha de comunicação clara para atualizações entre SOC, CSIRT e demais partes interessadas.
      
  Quais medidas podem ser implementadas para evitar vazamento adicional de dados?
  R.  Políticas de DLP (Data Loss Prevention)
      Configurar ou ajustar ferramentas de DLP para identificar e bloquear tentativas de envio de dados críticos para serviços de armazenamento em nuvem não autorizados.
      Estabelecer regras de prevenção de perda de dados específicas para arquivos médicos e outras informações confidenciais.
      Verificação de Configurações de Rede e Segmentação
      Revisar se há segmentação adequada dos sistemas que contêm dados sensíveis, limitando o acesso apenas a quem realmente precisa.
      Garantir que o tráfego para serviços em nuvem seja analisado e monitorado em tempo real.
      Aprimoramento de Monitoramento e Alertas
      Otimizar regras de SIEM e EDR para gerar alertas quando houver tráfego anormal, volume de dados elevado ou comportamentos fora do padrão.
      Implementar uso de threat intelligence feeds para correlacionar indicadores de comprometimento (IoCs) com conexões externas suspeitas.
      Reforço de Políticas de Senhas e MFA
      Garantir que todos os usuários utilizem senhas fortes, mudem-nas regularmente e adotem autenticação multifator sempre que possível.
      Realizar um review de privilégios para assegurar que os usuários tenham somente as permissões mínimas necessárias (princípio de menor privilégio).
      Treinamento de Conscientização em Segurança
      Fornecer treinamentos frequentes para os funcionários sobre boas práticas de segurança, principalmente em relação a exfiltração de dados e uso de serviços em nuvem.
      Reforçar a importância de reportar comportamentos suspeitos ou anomalias imediatamente.
