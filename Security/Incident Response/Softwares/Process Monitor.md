## Introdução
O Process Monitor é uma ferramenta de monitoramento avançada para Windows que mostra em tempo real o sistema de arquivos, 
registros, processos e conexões, em forma de linha do tempo . o Process Monitor um utilitário essencial em seu kit de ferramentas de 
solução de problemas do sistema e de busca de software mal-intencionado.

Link de Download
https://learn.microsoft.com/pt-br/sysinternals/downloads/procmon




## Recursos basicos

![ProcessMonitor](https://github.com/user-attachments/assets/b26dcf88-1a6e-4976-b19b-f5929e054bf8)


1: Start e Stop na coleta de Logs

2: Auto Scroll (Deixar habilitado)

3: Limpar logs da tela

4: Criação de filtros, darei mais detalhes a frente

5: Colorir algum evento, processo, image... (pode ser util para destacar algo importante)

### Os itens abaixo mostram oque o processo analisado esta manipulando, é possivel ver por exemplo se esse processo esta escrevendo em arquivos de texto, editando registros ou fazendo conexões, mesmo que seja por exemplo conexões UDP, dificeis  de identificar de outras formas.

6: Mostrar atividades de registro manipulados pelo processo

7: Mostrar atividade de arquivos manipulados pelo processo

8: Mostrar atividade de conexões manipuladas pelo processo

9: Mostrar atividades de outros processos executados pelo processo 




## Uso do filtro
Abaixo criamos um filtro procurando tudo que o binario wazuh-agent.exe esta fazendo na maquina
![Screenshot 2025-01-14 at 11 23 47](https://github.com/user-attachments/assets/1b165caa-c2ba-4c34-9883-d483524b6820)


Para simplificar ainda mais deixei apenas o filtro de (8 Conexões)
![Screenshot 2025-01-14 at 11 28 24](https://github.com/user-attachments/assets/4f09447f-93dd-42fa-bd58-81f129afaf4b)


Podemos ver que o binario gera conexões apenas na porta de destino 1514, com destino ao ip 192.168.80.240.

Manipulando os filtros é possivel entender oque qualquer binario (malicioso ou não) esta fazendo, recomendo praticar o uso da ferramenta para melhor entendimento.

Dica, na aba Options, desative a resolução de name para facilitar a analise caso for analisar conexões


![Screenshot 2025-01-14 at 11 33 52](https://github.com/user-attachments/assets/d46e0161-9d94-44ad-8a58-4cf45fe9cfca)

Abaixo um video com casos de uso do proprio Mark Russinovich (Criador da ferramenta)

https://youtu.be/A_TPZxuTzBU?si=81Rfbrp3XfxCdccl&t=1719




