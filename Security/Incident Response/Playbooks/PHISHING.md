## ** Guia de Resposta a Incidentes de Phishing**

### **1. Analisar o E-mail: Procure a resposta para as perguntas abaixo**
- Quando o email foi enviado?
- Qual é o endereço SMTP do e-mail?
- Qual é o endereço do remetente?
- O endereço do remetente parece suspeito (Domain Look-alike?)?
- O conteúdo do e-mail é suspeito?
- Há anexos ou links no e-mail?

---

### **2. Há anexos ou URLs no e-mail?**
- **Sim:** Vá para a o item 3.
- **Não:** Finalize a análise.

---

### **3. Analisar URLs/Anexos**
- Use os seguintes serviços/produtos:
  - **Metadefender**
  - **AlienVault**
  - **VirusTotal**
  - **Hybrid Analysis**

---

### **4. O arquivo/URL é malicioso?**
- **Sim:** Continue para o item 5.
- **Não:** Finalize a análise.

---

### **5. O e-mail foi entregue ao usuário?**
- **Sim:** 
  - Ação: Exclua o e-mail do destinatário.
- **Não:** Finalize a análise.

---

### **6. O arquivo ou URL malicioso foi aberto?**
- **Sim:** Continue para análise de cabeçalhos.
- **Não:** Finalize a análise.

---

### **7. Análise de Cabeçalhos**
- Baixe e analise o arquivo EML do e-mail.
- Revise os detalhes do e-mail:
  - Analise o SPF, DKIM e os cabeçalhos.
  - A análise dos cabeçalhos pode ajudar a detectar se o remetente é legítimo.
- Pergunta: Tente entender se o email foi falsificado?  

---

### **8. Contenção**
- Os sistemas que foram expostos ao ataque cibernético devem ser isolados.
- O impacto do ataque deve ser mitigado, (Analisar item 3.2 do plano de resposta https://github.com/oliveiralive/Documentation/blob/main/Security/Incident%20Response/Plan/Checklist%20Basico.md)

---

### **9. Lições Aprendidas**
- Perguntas a serem respondidas:
  - Como esse ataque aconteceu?
  - Que medidas podem ser implementadas para evitar ataques semelhantes no futuro?
  - Quais proteções adicionais devem ser implementadas para aumentar a segurança?

---

### **10. Artefatos**
- Documente quaisquer artefatos encontrados durante a investigação.

---

### **11. Nota do Analista**
- Insira suas observações e comentários sobre a análise.

---
