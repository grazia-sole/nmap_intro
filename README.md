# NMAP

## Enumerazione e Scansione delle Porte per la Sicurezza

In cybersecurity, la conoscenza del sistema o della rete target è fondamentale. Prima di ogni tentativo di attacco, è necessario eseguire una corretta enumerazione per identificare i servizi attivi. Il primo passo è spesso una scansione delle porte, che permette di mappare le porte aperte e capire quali servizi sono in ascolto. Ogni dispositivo ha 65535 porte, molte delle quali sono riservate per scopi specifici: ad esempio, il servizio HTTP usa la porta 80, mentre HTTPS usa la porta 443. Tuttavia, le configurazioni possono variare, specialmente in contesti di CTF, quindi la scansione accurata delle porte è indispensabile.

## Perché usare Nmap?
Nmap è lo strumento standard per le scansioni delle porte grazie alla sua flessibilità e alla potenza del motore di scripting, che può rilevare vulnerabilità e, in alcuni casi, persino sfruttarle. Nmap si connette a ciascuna porta del target e determina se è aperta, chiusa o filtrata (di solito da un firewall), permettendo di identificare i servizi disponibili per ulteriori indagini.

![image](https://github.com/user-attachments/assets/79feea49-bc86-449e-9188-3015f167d08e)

Le connessioni di rete avvengono tra due porte: una porta aperta in ascolto sul server e una porta selezionata casualmente sul tuo computer. Ad esempio, quando ti connetti a una pagina web, il tuo computer può aprire la porta 49534 per connettersi alla porta 443 del server.

Come nell'**esempio precedente**, il diagramma mostra cosa accade quando ti connetti contemporaneamente a numerosi siti web. Il tuo computer apre una porta diversa, con un numero elevato scelto casualmente, che usa per tutte le comunicazioni con il server remoto.

Ogni computer ha un totale di 65535 porte disponibili; tuttavia, molte di queste sono registrate come porte standard. Ad esempio, un servizio web HTTP si trova quasi sempre sulla porta 80 del server, un servizio HTTPS sulla porta 443, Windows NETBIOS sulla porta 139 e SMB sulla porta 445. È importante notare, tuttavia, che soprattutto in contesti CTF (Capture The Flag), anche queste porte standard possono essere modificate, rendendo ancora più essenziale un'enumerazione accurata del target.

Porte disponibili per ogni computer: 65535 

## Comandi principali

**`SYN - Scan`**
```
nmap -sS TARGET_IP
```
**`UDP - Scan`**
```
nmap -sU TARGET_IP
```


