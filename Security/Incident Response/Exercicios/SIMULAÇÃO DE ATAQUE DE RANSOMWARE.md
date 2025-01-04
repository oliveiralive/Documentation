EXERCÍCIOS
EXERCÍCIO DE MESA 1: SIMULAÇÃO DE ATAQUE DE RANSOMWARE

Objetivo: Simular um ataque de ransomware e avaliar a capacidade da equipe do SOC de responder em todas as funções (N1, N2, N3 e Gerente do SOC).

Cenário: Durante o monitoramento de rotina, o SOC observa atividade incomum na rede da empresa. 
Vários arquivos parecem estar criptografados e uma nota de resgate é descoberta exigindo pagamento em Bitcoin. 

O exercício começa com essa descoberta e prossegue pelo ciclo de vida de resposta a incidentes.

Alerta de segurança 
• ID do alerta: 3029
• Gravidade: alta
• IP de origem: 192.168.1.24
• IP de destino: 45.77.89.120
• Descrição: Grande transferência de dados de saída detectada eegistros de atividade de endpoint (EDR)

<img width="718" alt="image" src="https://github.com/user-attachments/assets/d5aa1a70-e4d5-48c8-aa1e-885524b46e94" />

Fase 1: Detecção e Triagem Iniciais 

Insight 1: Atividade Suspeita Descoberta
1. O Alerta relata tráfego de saída incomum para um IP não publico.
2. Os logs de segurança revelam um download de arquivo suspeito seguido por criptografia rápida de arquivo.
   
Perguntas para o Analista L1:
1. Quais ações iniciais você deve tomar ao receber o Alerta?
   R1. Revise os detalhes do alerta do SIEM: o Observe o IP de origem, o IP de destino e a descrição do alerta. o Verifique se o IP externo (45.77.89.120) é reconhecido ou sinalizado em bancos de dados de inteligência de ameaças.
      
2. Como você valida se essa atividade é maliciosa?
   R2. Ao Consultar logs do sistema de origem (192.168.1.24), Confirmar a presença de atividade de criptografia de arquivo e identificar processos associados, verificar notas de resgate ou arquivos executáveis ​​suspeitos (invoice_0321.exe).
   
3. Quando você deve escalar isso para L2?
   R3. A atividade de criptografia é confirmada.
       O IP externo é encontrado em relatórios de inteligência de ameaças.
       A nota de resgate está presente.

Perguntas para o Analista L2:
1. Como você confirma qual o tipo de ransonware impactou a maquina?
   R. Submeta um arquivo criptografado em plataformas como ID Ransonware (https://id-ransomware.malwarehunterteam.com/index.php?lang=en_US) para descobrir o tipo do Ransonware, tambem vale submeter o arquivo criptografado no binwalk (https://github.com/ReFirmLabs/binwalk) para mais detalhes, caso tenha acesso executavel do ransonware, execute-o em uma sandbox e procure os IPs que ele se comunica.
   
3. Quais registros ou ferramentas adicionais você examinaria para entender o escopo?
   R. Revise logs de firewall e Proxy buscando conexões externas de maquinas da rede com esses IPs suspeitos.
      Com os IOCs em maos, procure evidencias deles em outras maquinas.

Perguntas para o analista L3:
1. Quais técnicas forenses avançadas você pode aplicar para analisar o ransomware?
   R. Caso tenha a amostra do ransonware, faça uma analise estatica com o IDA Pro, execute o ransonware em um ambiente de laboratorio do Vigilant e analise o Threat Hunting da execução, tambem vale analiza-lo em execução com o (Process monitor da microsoft, procure os IPs que ele gera conexões) caso o hash do binario ja seja conhecido no Virustotal, analise as informações disponiveis, caso o virustotal nao possuir o hash malicioso em sua base, evite submeter o binario, alguns grupos de ransonwares podem monitorar a submsão de seus binarios destruindo suas infraestruturas ou mudando o comportamento, dificultando a analise.
   
3. Como você identificaria o vetor de ataque e evitaria mais comprometimento?
   R. é nescessario procurar de onde veio o binario malicioso, se veio de um email, ou se o servidor foi acessado e teve o binario distribuido na rede, via AD, por exemplo, apos recuperar o ambiente é importante melhorar as auditorias e processos de detecção e resposta.
   
Perguntas para o gerente do SOC:
1. Como você prioriza as próximas etapas, garantindo o mínimo de interrupção operacional?
   R. Inicie o checklist na pasta (Plan)
   
3. Quais estratégias de comunicação você implementaria para as partes interessadas internas e externas?
   R. Notifique os executivos sobre o potencial impacto comercial.
      o Prepare uma estratégia de comunicação externa para clientes afetados ou órgãos reguladores, se necessário.

Fase 2: Contenção 
Insight 2: Disseminação da infecção
• A TI relata que três servidores no departamento financeiro estão inacessíveis.
• A análise do tráfego de rede mostra conexões em andamento com o IP externo (45.77.89.120).

Perguntas para o analista L1:
1. Quais etapas você deve seguir para isolar os sistemas afetados?
   R. Desconecte imediatamente os sistemas afetados da rede para evitar uma propagação adicional.
   
2. Como você documenta o incidente para análise posterior?
   R. Colete informações orientadas no formulario (https://github.com/oliveiralive/Documentation/tree/main/Security/Incident%20Response/Coleta%20de%20Informações)

Perguntas para o analista L2:
1. Como você usa os dados de tráfego de rede para conter a ameaça?
  R. Utilize ferramentas disponiveis para bloquear os IPs publicos identificados na analise do malware
 
3. Quais técnicas de mitigação devem ser aplicadas para evitar o movimento lateral?
   R. O Vigilant pode bloquear os IPs dos servidores temporariamente ate que tenham sido recuperados, tambem é valido segmentar a rede e fazer bloqueios em regras de firewall limitando acessos de redes (segmentações).
   R. Resete senhas de contas impactadas (ou todas), analise usuarios em maquinas e persistencias, desabilite compartilhamentos de arquivos, e reveja privilégios para uma politica de ZeroThrust.

Perguntas para o analista L3:
1. Como você analisa o malware para criar IoCs (indicadores de comprometimento) acionáveis?
2. Quais ferramentas avançadas podem ser usadas para avaliar o escopo completo dos ativos afetados?

Perguntas para o gerente do SOC:
1. Como você garante que as ações de contenção estejam alinhadas com as prioridades do negócio?
   R. Trabalhe com a equipe de TI para identificar sistemas críticos que exigem recuperação imediata.  
   R. Avalie a necessidade de envolvimento de equipes de resposta a incidentes de terceiros ou de autoridades competentes.
   
3. Quais recursos são necessários para recuperação imediata?
   R. Aloque recursos técnicos para as equipes de contenção e recuperação.
   R. Designe especialistas em comunicação para lidar com atualizações internas e externas.

Fase 3: Análise da causa raiz 
Injeção 3: Vetor de ataque descoberto

• Os logs do gateway de e-mail revelam que o ransomware se originou de um e-mail de phishing enviado ao usuário_123, com um anexo malicioso chamado "invoice_0321.exe".

Perguntas para o analista L1:
1. Como você rastreia o e-mail de phishing até sua origem?
   R.Extraia o IP do remetente, o domínio e o caminho do e-mail para rastrear a origem.
   R.Faça a verificação cruzada com campanhas de phishing conhecidas em ferramentas de inteligência de ameaças.
   
2. Quais indicadores você procuraria nos e-mails de outros usuários?
  R.Use pesquisas de regex no gateway de e-mail para encontrar padrões (“invoice_*.exe”).
  R.Verifique se outros usuários receberam e-mails semelhantes ou clicaram no link malicioso.

Perguntas para o analista L2:
1. Como você correlaciona o e-mail de phishing com a atividade do endpoint?
   R.Combine o registro de data/hora do e-mail com os logs dos endpoints para confirmar a execução do arquivo malicioso.
   R.Verifique os logs de DNS para verificar a resolução de domínios associados ao e-mail de phishing.
   
3. Quais recomendações você faria para fortalecer a segurança do e-mail?
   R.Implemente filtros de e-mail mais robustos com sandboxing para anexos.
   R.Treine os funcionários para reconhecer tentativas de phishing.

Perguntas para o analista L3:
1. Como você usa a inteligência de ameaças para avaliar o risco de ataques semelhantes?
   R.Use plataformas como MISP ou Recorded Future para pesquisar as táticas e ferramentas do invasor.
   R.Confirme se a variante de ransomware está vinculada a um grupo APT ativo.
   
3. Quais medidas adicionais podem ser tomadas para fortalecer os endpoints?
   R. Implemente a lista de permissões de aplicativos, desative macros do oficce, atualize as maquinas, remova permissionamento administrador das maquinas de usuarios que não são administradores de sistema.
   
Perguntas para o gerente do SOC:
1. Como você apresenta as descobertas à liderança executiva?
   R. Crie um relatório detalhado que resuma a linha do tempo do ataque, a causa raiz e as ações de contenção.
   R. Destaque as lacunas na postura de segurança e proponha melhorias.
   
3. Como você aloca recursos para melhorias de longo prazo?
   R. Apresente Budgets para contratação de tecnologia e pessoal para os itens abaixo:
   Soluções que trarão maior visibilidade, gerencia e resposta a incidentes de segurança.
   Treinamento de funcionários.
