# 🧠 AI + SQL Demo — Come scrivere query con l’aiuto dell’intelligenza artificiale

Questa repository contiene il **database di esempio** utilizzato nel video YouTube  
🎥 *“Come usare l’AI per scrivere query SQL (senza farti fregare)”*  
pubblicato sul canale [Mirco Miglietta Data](https://youtube.com/@mircomigliettadata).

---

## 💡 Obiettivo
Dimostrare come usare l’intelligenza artificiale per:
- Generare query SQL a partire da istruzioni in linguaggio naturale  
- Migliorare i prompt per ottenere codice più preciso e leggibile  
- Capire e **validare i risultati** generati dall’AI

L’AI può accelerare il lavoro, ma non sostituisce la competenza tecnica:  
> “L’AI ti scrive la query, ma sei tu a garantirne la qualità.” 💡

---

## 🧱 Struttura del database

Il database è pensato per simulare un piccolo scenario di vendite, con tabelle in **inglese** per generare volutamente errori di naming durante la demo AI.

| Tabella | Descrizione |
|----------|--------------|
| `customers` | Anagrafica clienti |
| `payment_methods` | Metodi di pagamento (cash, credit_card, etc.) |
| `sales` | Registro vendite con date, importi e riferimenti ai clienti |

---

## ⚙️ Installazione

1. Clona la repo  
   ```bash
   git clone https://github.com/<tuo-username>/sql-ai-demo.git
   cd sql-ai-demo
   ```

2. Importa lo script in **MySQL Workbench** o nel tuo ambiente MySQL 8.x  
   ```sql
   SOURCE sql_ai_demo_en.sql;
   ```

3. Verifica la connessione e testa la view:  
   ```sql
   SELECT * FROM v_sales_2024;
   ```

4. Prova la stored procedure:  
   ```sql
   CALL sp_total_sales_by_customer_method(2024);
   ```

---

## 🧩 Esempio di query usata nel video

```sql
SELECT
  c.customer_name AS Customer,
  pm.method_name  AS PaymentMethod,
  SUM(s.amount)   AS TotalSales
FROM sales s
JOIN customers c ON c.id = s.customer_id
JOIN payment_methods pm ON pm.id = s.payment_method_id
WHERE YEAR(s.sale_date) = 2024
GROUP BY c.customer_name, pm.method_name
ORDER BY TotalSales DESC;
```

---

## 📺 Risorse
- 🎬 Video completo: *Come usare l’AI per scrivere query SQL (senza farti fregare)*  
- 📘 Tutorial correlato: *Come farti spiegare e correggere una query passo passo*  
- 🔗 Canale YouTube: [@MircoMigliettaData](https://youtube.com/@mircomigliettadata)

---

## 🧑‍🏫 Autore
**Mirco Miglietta**  
Formatore e consulente in ambito **Data Analysis, SQL e AI Generativa**.  
👉 [LinkedIn](https://www.linkedin.com/in/mirco-miglietta-056995105) | [YouTube](https://youtube.com/@mircomigliettadata)
