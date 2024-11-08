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
**`Operating system of target`**
```
nmap -O TARGET_IP
```
**`Version of the services running on the target`**
```
nmap -sV TARGET_IP
```
**`Increase the verbosity`**
```
nmap -v TARGET_IP
```
**`Increase the verbosity second-level`**
```
nmap -vv TARGET_IP
```
**`Save nmap results in three major formats (normal, XML, and grepable)`**
```
nmap -oA <filename> <target_ip>
```
**`Save nmap results in normal format - file.txt`**
```
nmap -oN <filename> <target_ip>
```
**`Aggressive scanning.`**
It enables a number of features in one go, including: 
- OS detection (-O),
- Version detection (-sV),
- Script scanning (-sC),
- Traceroute (--traceroute)
```
nmap -A TARGET_IP
```
**`Timing template`**
It sets the timing template to aggressive, which increases the speed of the scan but can also lead to increased network noise and possible errors. 
```
nmap -T5 TARGET_IP
```


Certo! Ecco una spiegazione dettagliata di queste opzioni di `nmap`, che è uno strumento potente per la scansione di rete:

### 1. `-f` (Fragment Packets)
- **Descrizione**: Questa opzione frammenta i pacchetti inviati da Nmap in segmenti più piccoli (tipicamente di 8 byte ciascuno).
- **Scopo**: Serve a eludere alcuni sistemi di rilevamento delle intrusioni (IDS) o firewall che possono avere difficoltà a ricomporre pacchetti frammentati e quindi a rilevare la scansione.
- **Uso**: `nmap -f <target>`
- **Considerazioni**: Anche se può aiutare a bypassare alcune difese, non è una garanzia contro sistemi di protezione più avanzati e può generare traffico di rete insolito.

### 2. `--mtu <valore>`
- **Descrizione**: Specifica una dimensione personalizzata per il massimo unità di trasmissione (MTU) dei pacchetti inviati. L'MTU è la dimensione massima del pacchetto che può essere trasmesso senza frammentazione.
- **Scopo**: Viene utilizzato per personalizzare ulteriormente il traffico della scansione e potenzialmente bypassare alcune difese di rete che si basano su una dimensione MTU specifica.
- **Uso**: `nmap --mtu 32 <target>` (dove `32` è un esempio di valore MTU).
- **Considerazioni**: L'uso di un valore MTU non standard può interferire con la comunicazione normale e causare comportamenti imprevisti in alcune reti.

### 3. `--scan-delay <ms>`
- **Descrizione**: Imposta un ritardo specifico in millisecondi tra l'invio di ciascun pacchetto durante la scansione.
- **Scopo**: Può essere utile per scansioni più "stealthy", riducendo la possibilità di rilevamento da parte di sistemi di difesa che controllano l'elevato numero di pacchetti in un breve periodo di tempo.
- **Uso**: `nmap --scan-delay 100ms <target>` (dove `100ms` rappresenta un esempio di ritardo di 100 millisecondi tra i pacchetti).
- **Considerazioni**: Una scansione con ritardo elevato sarà meno rilevabile, ma anche molto più lenta.

### 4. `-badsum`
- **Descrizione**: Invia pacchetti TCP o UDP con checksum non validi.
- **Scopo**: Questo tipo di pacchetto è progettato per non ricevere una risposta da host conformi agli standard, poiché il pacchetto sarà scartato. Tuttavia, a volte firewall o IDS meno sofisticati potrebbero rispondere in modo inappropriato, aiutando a identificare la loro presenza.
- **Uso**: `nmap -badsum <target>`
- **Considerazioni**: È un'opzione utilizzata principalmente per test di ricerca e sviluppo, e non per scansioni pratiche o efficaci. Inviare pacchetti con checksum errati può comunque sembrare sospetto a un monitoraggio di rete.

Queste opzioni sono generalmente usate per personalizzare e rendere più complessa la scansione, sia per eludere le difese che per condurre test di sicurezza avanzati.
