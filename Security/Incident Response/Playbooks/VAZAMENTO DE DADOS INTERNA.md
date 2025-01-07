**EXERCÍCIOS EXTRA**  
**EXERCÍCIO SIMULADO 4: VIOLAÇÃO POR AMEAÇA INTERNA**  

**Objetivo:** Avaliar a capacidade da equipe do SOC de detectar, investigar e mitigar um incidente de ameaça interna enquanto equilibra preocupações operacionais e de reputação.  

**Cenário:** Sua organização, um provedor de serviços de saúde, descobriu que registros sensíveis de pacientes foram acessados e exportados sem autorização. A violação de dados acionou alertas indicando um possível envolvimento interno.  

**Fase 1: Detecção e Triagem Inicial**

**Injeção 1:**  
- Um analista do SOC recebe um alerta do sistema de DLP (Prevenção contra Perda de Dados) indicando a exportação de arquivos sensíveis para um dispositivo USB externo por um funcionário do departamento de TI.  
- Os logs de endpoint mostram acesso anômalo a arquivos não relacionados ao cargo do funcionário.  

**Pontos de Discussão:**  

1. **Quais ações imediatas o SOC deve tomar para validar este alerta?**  
   **Resposta Esperada:**  
   - Revisar os logs do DLP para confirmar a tentativa de exfiltração de arquivos.  
   - Cruzar os dados com os logs de atividades do funcionário (acesso por crachá, horários de login).  
   - Alertar a equipe de Resposta a Incidentes (IR) para uma investigação mais aprofundada.  

2. **Como o SOC deve garantir que isso é uma ameaça interna e não uma invasão externa?**  
   **Resposta Esperada:**  
   - Examinar os logs de endpoint para verificar acessos não autorizados realizados pelo funcionário.  
   - Investigar possíveis usos indevidos de credenciais por terceiros.





**Fase 2: Investigação e Contenção**

**Injeção 2:**  
- A equipe de segurança de TI descobre que o funcionário utilizou acesso com nível de administrador para contornar restrições.  
- As atividades recentes do funcionário mostram um padrão de download e criptografia de grandes arquivos.  

**Pontos de Discussão:**  

1. **Quais medidas o SOC deve tomar para conter a ameaça interna?**  
   **Resposta Esperada:**  
   - Desabilitar imediatamente o acesso do funcionário a todos os sistemas.  
   - Proteger os sistemas afetados e preservar as evidências forenses.  
   - Iniciar um monitoramento aprimorado em sistemas sensíveis.  

2. **Quais evidências adicionais o SOC deve coletar para entender o alcance da violação?**  
   **Resposta Esperada:**  
   - Revisar os logs históricos em busca de atividades suspeitas anteriores realizadas pelo funcionário.  
   - Examinar as atividades de e-mail e mensagens para identificar indícios de intenção ou conluio.
  


**Fase 3: Análise da Causa Raiz**

**Injeção 3:**  
- A análise forense revela que o funcionário utilizou uma backdoor instalada meses atrás para acessar os sistemas sem ser detectado.  
- A backdoor estava oculta em uma atualização de software aparentemente inofensiva enviada para os servidores da empresa.  

**Pontos de Discussão:**  

1. **Como a equipe do SOC deve investigar e remediar a backdoor?**  
   **Resposta Esperada:**  
   - Realizar uma varredura completa no sistema para identificar Indicadores de Comprometimento (IoCs) relacionados à backdoor.  
   - Remover o código malicioso e substituir o pacote de atualização comprometido.  

2. **Como o SOC pode identificar se o insider tinha cúmplices externos?**  
   **Resposta Esperada:**  
   - Revisar os logs de comunicação em busca de IPs externos ou domínios suspeitos.  
   - Verificar registros financeiros em busca de transações inexplicáveis.

**Fase 4: Avaliação do Impacto nos Negócios**  

**Injeção 4:**  
- O departamento de RH informa que vários pacientes afetados já entraram em contato com a mídia, causando danos à reputação.  
- Um regulador local emitiu uma notificação solicitando detalhes sobre a violação.  

**Pontos de Discussão:**  

1. **Quais medidas devem ser tomadas para gerenciar a resposta regulatória e pública?**  
   **Resposta Esperada:**  
   - Coordenar com as equipes jurídicas e de relações públicas para elaborar uma declaração pública.  
   - Garantir que a declaração seja transparente, reconhecendo a situação, explicando as medidas tomadas para resolver o problema e destacando os esforços para evitar futuros incidentes.  
   - Preparar uma resposta detalhada para o regulador local, incluindo uma linha do tempo dos eventos, medidas de contenção e ações futuras para conformidade.
  

2. **Quais riscos operacionais precisam de atenção imediata?**  
   **Resposta Esperada:**  
   - Garantir a segurança contínua dos dados dos pacientes.  
   - Priorizar a correção de quaisquer vulnerabilidades remanescentes no ambiente de TI.  

---

**Fase 5: Recuperação e Medidas Pós-Incidente**  

**Injeção 5:**  
- A ameaça interna foi neutralizada, mas interrupções operacionais continuam devido ao aumento da fiscalização nos processos de acesso aos dados.  

**Pontos de Discussão:**  

1. **Quais estratégias de longo prazo podem prevenir futuras ameaças internas?**  
   **Resposta Esperada:**  
   - Implementar controle de acesso baseado em funções (RBAC) e limitar privilégios administrativos.  
   - Realizar verificações regulares de antecedentes dos funcionários e treinamentos de conscientização em segurança.  

2. **Como a organização pode melhorar suas capacidades de detecção de ameaças internas?**  
   **Resposta Esperada:**  
   - Implementar ferramentas de análise de comportamento de usuários (UBA) para monitorar atividades incomuns.  
   - Aperfeiçoar políticas de DLP para detectar e bloquear transferências de dados não autorizadas.    
