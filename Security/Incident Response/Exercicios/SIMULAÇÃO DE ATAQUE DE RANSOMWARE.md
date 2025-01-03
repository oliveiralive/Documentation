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

Injeção 1: Atividade Suspeita Descoberta
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
