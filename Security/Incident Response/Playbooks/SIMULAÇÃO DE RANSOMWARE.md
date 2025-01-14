EXERCÍCIOS
EXERCÍCIO DE MESA 1: SIMULAÇÃO DE ATAQUE DE RANSOMWARE

Objetivo: Simular um ataque de ransomware e avaliar a capacidade da equipe do SOC de responder em todas as funções (N1, N2, N3 e Gerente do SOC).

Cenário: Durante o monitoramento de rotina, o SOC observa atividade incomum na rede da empresa. 
Vários arquivos parecem estar criptografados e uma nota de resgate é descoberta exigindo pagamento em Bitcoin. 

O exercício começa com essa descoberta e prossegue pelo ciclo de vida de resposta a incidentes.

Alertas de segurança
• ID do alerta: 3029 e 3088
• Gravidade: alta
• IP de origem: 192.168.1.24
• IP de destino: 45.77.89.120
• Descrição: Grande transferência de dados de saída detectados, arquivos com extenção suspeita criados no servidor



## Fase 1: Detecção e Triagem Iniciais 

Insight 1: Atividade Suspeita Descoberta
1. O Alerta relata tráfego de saída incomum para um IP suspeito.
2. Os logs de segurança revelam um download de arquivo suspeito seguido por criptografia rápida de arquivo.
   
Perguntas para o Analista L1:
1. Quais ações iniciais você deve tomar ao receber o Alerta?
   
   R1. Revise os detalhes do alerta: IP de origem, o IP de destino e a descrição do alerta. o Verifique se o IP relatado no log (Ex: 45.77.89.120) é reconhecido ou sinalizado em bancos de dados de inteligência de ameaças, exemplos (https://www.abuseipdb.com), (https://www.criminalip.io), (https://www.virustotal.com/)
      
3. Como você valida se essa atividade é maliciosa?
   
   R2. Ao Consultar logs do sistema de origem (192.168.1.24), Confirmar a presença de atividade de criptografia de arquivo e identificar processos associados, verificar notas de resgate ou arquivos executáveis ​​suspeitos (ex: invoice_0321.exe).
   
5. Quando você deve escalar isso para L2?
   
   R3. A atividade de criptografia é confirmada.
       O IP externo é encontrado em relatórios de inteligência de ameaças.
       A nota de resgate está presente.
       Binario reportado pelo alerta presente na maquina (Não submeta o binario em bases como virustotal ou Metadefender ainda)

Perguntas para o Analista L2:
1. Como você confirma qual o tipo de ransonware impactou a maquina?

   R. Submeta um arquivo criptografado em plataformas como ID Ransonware (https://id-ransomware.malwarehunterteam.com/index.php?lang=en_US) ou No more ransom (https://www.nomoreransom.org/crypto-sheriff.php) para descobrir o tipo do Ransonware, tambem vale submeter o arquivo criptografado no binwalk (https://github.com/ReFirmLabs/binwalk) para mais detalhes.

   

Perguntas para o analista L3:
1. Quais técnicas forenses avançadas você pode aplicar para analisar o ransomware?

   R. Caso tenha a amostra do ransonware, faça uma analise estatica com o IDA Pro, execute o ransonware em um ambiente de laboratorio, analise sua execução com as ferramentas "Process monitor e Process Explorer e Autoruns" (https://github.com/oliveiralive/Documentation/tree/main/Security/Incident%20Response/Softwares) caso o hash do binario ja seja conhecido no Virustotal, analise as informações disponiveis, caso o virustotal nao possuir o hash malicioso em sua base, evite submeter o binario, alguns grupos de ransonwares podem monitorar a submsão de seus binarios destruindo suas infraestruturas ou mudando o comportamento, dificultando a analise.

3. Quais registros ou ferramentas adicionais você examinaria para entender o escopo?

   R. Revise logs de firewall e Proxy buscando conexões externas de maquinas da rede com esses IPs suspeitos encontrados.
      Com os IOCs em maos, procure conexões com origem ou destino para os IPs suspeitos encontrados, procure conexões que o ip de origem da maquina infectada efetuou, procure logins com sucesso do ip da maquina ou do usuario de origem.
   

   
Perguntas para o gerente do SOC:
1. Como você prioriza as próximas etapas, garantindo o mínimo de interrupção operacional?

   R. Inicie o checklist na pasta (Plan)
   
3. Quais estratégias de comunicação você implementaria para as partes interessadas internas e externas?

   R. Notifique os executivos sobre o potencial impacto comercial.
      o Prepare uma estratégia de comunicação externa para clientes afetados ou órgãos reguladores, se necessário.

## Fase 2: Contenção 
Insight 2: Disseminação da infecção
• A TI relata que três servidores no departamento financeiro estão inacessíveis.
• A análise do tráfego de rede mostra conexões em andamento com o IP externo (45.77.89.120).

Perguntas para o analista L1:
1. Quais etapas você deve seguir para isolar os sistemas afetados?

   R. Desconecte imediatamente os sistemas afetados da rede para evitar uma propagação adicional.
   
3. Como você documenta o incidente para análise posterior?

   R. Colete informações orientadas no formulario (https://github.com/oliveiralive/Documentation/tree/main/Security/Incident%20Response/Coleta%20de%20Informações)

Perguntas para o analista L2:
1. Como você usa os dados de tráfego de rede para conter a ameaça?

   R. Utilize ferramentas disponiveis (Firewall/EDR) para bloquear os IPs publicos identificados na analise do malware
 
3. Quais técnicas de mitigação devem ser aplicadas para evitar o movimento lateral?

   R. O EDR pode bloquear os IPs dos servidores temporariamente ate que tenham sido recuperados, coloque em quarentena os segmentos de rede afetados para isolar os sistemas criptografados e evitar movimento lateral. Isso pode ser feito bloqueando a comunicação entre os segmentos afetados usando regras de firewalls.
   R. Resete senhas de contas impactadas (ou todas), analise usuarios em maquinas e persistencias, desabilite compartilhamentos de arquivos, e reveja privilégios para uma politica de ZeroTrust.

   

Perguntas para o gerente do SOC:
1. Como você garante que as ações de contenção estejam alinhadas com as prioridades do negócio?
   R. Trabalhe com a equipe de TI para para criar ou atualizar um documento de sistemas críticos que exigem recuperação imediata.  
   R. Avalie a necessidade de envolvimento de equipes de resposta a incidentes de terceiros ou de autoridades competentes.
   
3. Quais recursos são necessários para recuperação imediata?
   R. Aloque recursos técnicos para as equipes de contenção e recuperação.
   R. Designe especialistas em comunicação para lidar com atualizações internas e externas.



## Fase 3: Erradicação e Recuperação

1. Quais etapas a SOC deve seguir para proteger os backups durante a analise?
   
R.Verifique a integridade do backup: verifique imediatamente se os backups estão intactos e não afetados pelo ransomware. Verifique se os backups não foram criptografados comparando hashes e extensões de arquivo.
Desconecte os sistemas de backup: certifique-se de que os sistemas de backup (tanto no local quanto na nuvem) estejam desconectados da rede ou isolados para impedir que o ransomware os tenha como alvo.
Autenticação de backup: verifique as autenticaçãos no sistema de backup e certifique-se de que as credenciais de backup estejam seguras.



Restauração do backup:
1 Priorizar a restauração de arquivos de um backup limpo conhecido antes que o ataque ocorresse.
Executar uma restauração completa para sistemas críticos para minimizar o tempo de inatividade.




## Fase 3: Análise da causa raiz 
Vetor de ataque descoberto

• Os logs do gateway de e-mail revelam que o ransomware se originou de um e-mail de phishing enviado ao usuário_123, com um anexo malicioso chamado "invoice_0321.exe".

Perguntas para o analista L1:
1. Como você rastreia o e-mail de phishing até sua origem?
   R.Extraia o IP do remetente, o domínio e o caminho do e-mail para rastrear a origem.
   R.Faça a verificação cruzada com campanhas de phishing conhecidas em ferramentas de inteligência de ameaças.
   
2. Quais indicadores você procuraria nos e-mails de outros usuários?
  R.Use pesquisas de regex no gateway de e-mail para encontrar padrões (“invoice_*.exe”).
  R.Verifique se outros usuários receberam e-mails semelhantes ou clicaram no link malicioso.
  R. Analisar playbook de phishing para mais detalhes (https://github.com/oliveiralive/Documentation/blob/main/Security/Incident%20Response/Playbooks/PHISHING.md)

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
