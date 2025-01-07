**EXERCÍCIO SIMULADO 6: ATAQUE À CADEIA DE SUPRIMENTOS**  

**Objetivo:** Avaliar a capacidade da equipe do SOC de detectar, investigar e responder a um comprometimento originado de um fornecedor/terceiro confiável.  

**Cenário:** Sua organização utiliza uma solução de software amplamente adotada fornecida pela IzzmierTech Solutions. 
Uma atualização recente da IzzmierTech entregou inadvertidamente malware como parte de um comprometimento na cadeia de suprimentos. 
Atividades incomuns foram detectadas em sua rede, levantando preocupações sobre um comprometimento maior.  

---

**Fase 1: Conscientização Inicial**  

**Injeção 1:**  
- Relatórios e alertas de inteligência sobre ameaças indicam que o servidor de atualização da IzzmierTech foi comprometido, distribuindo atualizações contaminadas com malware para todos as maquinas de um cliente.  
- O SOC detecta tráfego de saída de vários endpoints para domínios suspeitos vinculados a servidores C2 (Command and Control) de malware.  

**Pontos de Discussão:**  

1. **Quais são as prioridades imediatas do SOC ao receber esta informação?**  
   **Resposta Esperada:**  
   - Validar se a organização aplicou a atualização comprometida.  
   - Identificar os sistemas afetados e isolá-los da rede para evitar propagação adicional.  

2. **Quais fontes de informação o SOC deve analisar para confirmar a extensão do comprometimento?**  
   **Resposta Esperada:**  
   - Examinar logs da maquina, logs de DNS e logs de proxy em busca de Indicadores de Comprometimento (IoCs).  (analisar item 3.2 do plano de resposta https://github.com/oliveiralive/Documentation/blob/main/Security/Incident%20Response/Plan/Checklist%20Basico.md)
   - Revisar logs de atualização de sistemas para identificar máquinas que receberam a atualização comprometida.  

---

**Fase 2: Investigação e Contenção do Malware**  

**Injeção 2:**  
- O SOC descobre que o malware instala uma backdoor, permitindo que os atacantes executem comandos remotamente.  
- Sistemas internos mostram sinais de reconhecimento de dados, incluindo Scans em busca de compartilhamentos de arquivos sensíveis.  

**Pontos de Discussão:**  

1. **Quais ações devem ser tomadas para conter a ameaça imediatamente?**  
   **Resposta Esperada:**  
   - Isolar os sistemas comprometidos para evitar acessos não autorizados adicionais.  
   - Revogar credenciais administrativas em sistemas afetados e redefinir senhas.  
   - Monitorar em tempo real as comunicações de rede para identificar e bloquear conexões com servidores C2.  

2. **Como o SOC deve investigar o alcance das atividades do malware?**  
   **Resposta Esperada:**  
   - Analisar logs de acesso e scans de rede para entender movimentação lateral na rede.  
   - Revisar logs de arquivos e compartilhamentos de rede para determinar se dados sensíveis foram acessados ou exfiltrados.  
   - Realizar uma análise forense em sistemas comprometidos para identificar comandos executados e arquivos alterados pelo malware.


**Fase 3: Objetivos do Ator de Ameaça e Avaliação de Impacto**  

**Injeção 3:**  
- Os atacantes utilizam o malware para exfiltrar dados financeiros sensíveis para um servidor externo.  
- Algumas contas comprometidas pertencem a usuários com altos privilégios, levantando preocupações sobre acessos adicionais.  

**Pontos de Discussão:**  

1. **Quais estratégias o SOC deve adotar para detectar e prevenir exfiltrações adicionais de dados?**  
   **Resposta Esperada:**  
   - Monitorar o tráfego de saída em busca de padrões incomuns, especialmente transferências de grandes volumes de dados.  
   - Implementar soluções de Prevenção contra Perda de Dados (DLP) para impor restrições no acesso a dados sensíveis e bloquear transferências não autorizadas.  

2. **Como o SOC deve proteger contas com altos privilégios para mitigar riscos potenciais?**  
   **Resposta Esperada:**  
   - Forçar a redefinição de senhas para todas as contas privilegiadas.  
   - Implementar autenticação multifator (MFA) imediatamente para todas as contas críticas.

**Fase 4: Coordenação Externa e Mitigação**  

**Injeção 4:**  
- A IzzmierTech confirma que seu servidor de atualização de software foi completamente comprometido e orienta todos os clientes a desinstalarem a atualização afetada.  
- Autoridades reguladoras entram em contato com a organização, solicitando um relatório do incidente e garantias sobre medidas de segurança futuras.  

**Pontos de Discussão:**  

1. **Qual é o papel do SOC para garantir conformidade com as exigências regulatórias?**  
   **Resposta Esperada:**  
   - Colaborar com as equipes jurídicas e de conformidade para preparar um relatório detalhado do incidente.  
   - Fornecer evidências das ações tomadas para proteger os sistemas e mitigar riscos futuros.  

2. **Quais estratégias de comunicação a organização deve usar com a IzzmierTech?**  
   **Resposta Esperada:**  
   - Solicitar Indicadores de Comprometimento (IoCs) detalhados e suporte técnico para auxiliar na investigação e limpeza.  
   - Negociar garantias de segurança da cadeia de suprimentos para o futuro com a IzzmierTech.  

---

**Fase 5: Recuperação e Lições Aprendidas**  

**Injeção 5:**  
- Todos os sistemas afetados foram restaurados, mas o incidente revelou falhas na gestão de riscos de fornecedores e no teste de atualizações.  

**Pontos de Discussão:**  

1. **Quais medidas de longo prazo devem ser implementadas para melhorar a gestão de fornecedores?**  
   **Resposta Esperada:**  
   - Implemente avaliações mais rigorosas de fornecedores, incluindo auditorias regulares de segurança.  
   - Exija que fornecedores terceirizados sigam práticas seguras de desenvolvimento de software (SDLC).  

2. **Como os processos do SOC podem ser aprimorados para detectar comprometimentos na cadeia de suprimentos mais rapidamente?**  
   **Resposta Esperada:**  
   - Incorporar análises comportamentais para detectar atividades incomuns em sistemas e redes.  
   - Criar um procedimento robusto de teste e validação de patches antes da implantação.  
  
