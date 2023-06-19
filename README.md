# ansibleEsercizio1
Made playbook module for ssh and configuring nginx with jinja 2 using templating

Esercizio Ansible #1
Requisiti

VSCode
Docker Desktop
WSL 2 - Ubuntu 22.04+
Ansible (ultima release)


Base: realizzare un playbook Ansible che esegua le seguenti attività localmente alla WSL:

Installare un web server nginx;
Configurare il web server per ascoltare su porta 8080;
Sostituire la pagina web default con una generata tramite un template molto semplice composto dal testo: "Ciao da <NOME OS> alla versione <VERSIONE OS>", sostituendo dinamicamente i valori dei due placeholders;
Tip: Ansible fornisce dei meccanismi built-in per estrarre automaticamente queste informazioni;
Testare che la pagina risponda con HTTP code 200.


Bonus 1:

Eseguire manualmente un container Ubuntu 22.04 usando l'immagine ufficiale di Canonical su Docker Hub;
Configurare manualmente l'accesso in SSH al container mediante username "ubuntu" e password "ubuntu2023!";
Non è necessario buildare una nuova immagine, è sufficiente eseguire i comandi di configurazione direttamente all'interno del container;
Riseguire il playbook dalla WSL ma assicurandosi questa volta che la configurazione avvenga sul container (via SSH).
Tip: attenzione a separare l'esecuzione dei task locali (quelli da eseguire sulla WSL) da quelli sull'host remoto (il container).


Bonus 2:

Configurare l'accesso al container via SSH mediante una chiave generata ad-hoc (RSA o ed25519) e disattivare l'accesso mediante password;
Automatizzare tutti gli step precedenti e salvare il report dell'esecuzione in un file di testo.


Esercizio Ansible #2
Requisiti

VM Windows Server 2016 con a bordo il tool chocolatey per l'installazione dei pacchetti
Utente: Administrator
Password: Cognome123!
IP: _____._____._____._____

Il server viene fornito già configurato per essere raggiungibile via WinRM (su porta 5986 con certificato self-signed) per accesso tramite Ansible e RDP per accesso grafico.
VSCode
WSL 2 - Ubuntu 22.04
Ansible (ultima release)


Base: realizzare un playbook Ansible che si connetta al server via WinRM e applichi le seguenti configurazioni:

Prima di procedere, comunicare ad uno degli amministratori che si sta iniziando a lavorare sull'istanza, in modo che possano effettuare uno snapshot per ripristinare eventualmente la VM in caso di problemi;
Modificare l'hostname a "vm-cognome" e riavviare il server se necessario;
Installare il web server IIS (Internet Information Services) di Microsoft mediante le funzionalità di Windows Server;
Installare 7zip, notepad++ e Chrome all'ultima release mediante il tool chocolatey;
Il web server IIS viene fornito con un sito web di default, modificarne la configurazione in modo che risponda sulla porta 8888 e che il sito sia raggiungibile solo se chiamato con FQDN fake-site.mycompany.com (binding);
Tip: per testare il funzionamento ti serve davvero un record DNS?
Come ultimo step del playbook creare un file di log all'interno del server nel percorso "C:\<UUID RANDOM>_deploy.log" con il seguente contenuto:

Ansible Version: <VERSIONE DI ANSIBLE>
OS Version: <VERSIONE OS>
Ora completamento: <DATA-ORA ATTUALE>
