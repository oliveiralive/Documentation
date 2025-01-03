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
2. Como você valida se essa atividade é maliciosa?
4. Quando você deve escalar isso para L2?

Perguntas para o Analista L2:
1. Como você confirma se o ransomware está ativo?
2. Quais registros ou ferramentas adicionais você examinaria para entender o escopo?

Perguntas para o analista L3:
1. Quais técnicas forenses avançadas você pode aplicar para analisar o ransomware?
2. Como você identificaria o vetor de ataque e evitaria mais comprometimento?

Perguntas para o gerente do SOC:
1. Como você prioriza as próximas etapas, garantindo o mínimo de interrupção operacional?
2. Quais estratégias de comunicação você implementaria para as partes interessadas internas e externas?


Fase 2: Contenção 
Insight 2: Disseminação da infecção
• A TI relata que três servidores no departamento financeiro estão inacessíveis.
• A análise do tráfego de rede mostra conexões em andamento com o IP externo (45.77.89.120).

Perguntas para o analista L1:
1. Quais etapas você deve seguir para isolar os sistemas afetados?
2. Como você documenta o incidente para análise posterior?

Perguntas para o analista L2:
1. Como você usa os dados de tráfego de rede para conter a ameaça?
2. Quais técnicas de mitigação devem ser aplicadas para evitar o movimento lateral?

Perguntas para o analista L3:
1. Como você analisa o malware para criar IoCs (indicadores de comprometimento) acionáveis?
2. Quais ferramentas avançadas podem ser usadas para avaliar o escopo completo dos ativos afetados?

Perguntas para o gerente do SOC:
1. Como você garante que as ações de contenção estejam alinhadas com as prioridades do negócio?
2. Quais recursos são necessários para recuperação imediata?


Fase 3: Análise da causa raiz 
Injeção 3: Vetor de ataque descoberto

• Os logs do gateway de e-mail revelam que o ransomware se originou de um e-mail de phishing enviado ao usuário_123, com um anexo malicioso chamado "invoice_0321.exe".

Perguntas para o analista L1:
1. Como você rastreia o e-mail de phishing até sua origem?
2. Quais indicadores você procuraria nos e-mails de outros usuários?

Perguntas para o analista L2:
1. Como você correlaciona o e-mail de phishing com a atividade do endpoint?
2. Quais recomendações você faria para fortalecer a segurança do e-mail?

Perguntas para o analista L3:
1. Como você usa a inteligência de ameaças para avaliar o risco de ataques semelhantes?
2. Quais medidas adicionais podem ser tomadas para fortalecer os endpoints?
   
Perguntas para o gerente do SOC:
1. Como você apresenta as descobertas à liderança executiva?
2. Como você aloca recursos para melhorias de longo prazo?
