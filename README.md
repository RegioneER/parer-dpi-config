# DPI Config

Fonte template redazione documento:  https://www.makeareadme.com/.


# Descrizione

Progetto relativo alle generazione delle cofigurazioni standard suddivise per ambiente ed installazione dell'applicazione **DPI**. <br/><br/>


# Utilizzo

Il seguente progetto viene creato per esternalizzare le configurazioni, per singolo ambiente, dell'applicazione DPI, nello specifico il progetto viene creato a partire dalla configurazioni alla versione **2.6.0** del DPI che sono quindi le ultime ad essere presenti all'interno dell'applicativo stesso.

## Guida alle configurazioni  

Nella directory `conf`, vengono generate automaticamente dal modello CI/CD, le configurazioni per le diverse installazioni di DPI per ogni ambiente, che saranno predisposte opportunamente secondo le istruzioni presenti nel README ufficiale del progetto DPI.

## Versionamento dpi-config e dpi  

Il versionamento del progetto **dpi-config** segue direttamente quello dell'applicazione DPI, ossia, ad ogni nuovo versionamento di quest'ultimo seguirà anche il versionamento di questo progetto (esempio se creata la versione 3.0.0 di dpi si dovrà anche creare la relativa versione di dpi-config 3.0.0 indipendentemente se quest'ultimo è stato modificato o meno). 
Questa gestione delle versioni è utile per associare ad ogni nuova versione applicativa di dpi anche le relative configurazioni.
In caso di **sola modifica di dpi-config** non seguita quindi da modifiche applicative su **dpi**, si stabilisce la generazione di una nuova versione di **dpi-config** applicando un quarto numero alla versione da creare (esempio dpi alla versione 3.0.0 e dpi-config 3.0.0, in caso di sola modifica a dpi-config si crea la versione 3.0.0.**1**).


Esempio 1 (modifica a dpi che segue il versionamento di dpi-config)

Sul tag 2.6.0 le configurazioni hanno effettuato a **partire** dalla versione 2.6.0 del DPI e da quelle successive, le precedenti versioni avranno quindi configurazioni diverse e certamente non compatibili con quelle rilasciate.

Esempio 2 (modifica esclusiva a dpi-config)

Si crea la versione **2.6.0.1** di dpi-config che quindi è relativa alla versione **2.6.0** di dpi ma si evidenziano le sole modifiche alle configurazioni compatibili a partire da questa versione.


## Modifica delle configurazioni  

La directory su cui agire è `filters` su cui sono presenti i file statici con relativi placeholder, trattandosi di un progetto maven che utilizza l'apposito plugin, è necessario eventualmente agire sui file in cui è già presente una logica di "filtro" e, nell'eventualità le future evolutive dell'applicazione DPI impongano nuovi file, di modificare anche il pom.xml di progetto. Per la generazione dell'artifact finale è stata predisposta una apposita implementazione su pipeline Gitlab che produce il "pacchetto" attraverso il goal maven "package".


# Supporto

Mantainer del progetto è [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it/).

# Contributi

Se interessati a crontribuire alla crescita del progetto potete scrivere all'indirizzo email <a href="mailto:areasviluppoparer@regione.emilia-romagna.it">areasviluppoparer@regione.emilia-romagna.it</a>.

# Credits

Progetto di proprietà di [Regione Emilia-Romagna](https://www.regione.emilia-romagna.it/) sviluppato a cura di [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it/).

# Licenza

Questo progetto è rilasciato sotto licenza GNU Affero General Public License v3.0 or later ([LICENSE.txt](LICENSE.txt)).
