# DPI Config

Progetto relativo alle generazione delle cofigurazioni standard suddivise per ambiente ed installazione dell'applicazione [DPI](https://gitlab.ente.regione.emr.it/parer/dpi). <br/><br/>

## Introduzione

Il seguente progetto viene creato per esternalizzare le configurazioni, per singolo ambiente, dell'applicazione DPI, nello specifico il progetto viene creato a partire dalla configurazioni alla versione **2.6.0** del DPI che sono quindi le ultime ad essere presenti all'interno dell'applicativo stesso.

## Guida alle configurazioni  

Nella directory [conf](conf), vengono generate automaticamente dal modello CI/CD, le configurazioni per le diverenze installazioni di DPI per ogni ambiente, che saranno predisposte opportunamente secondo [guida ufficiale](https://parermine.regione.emilia-romagna.it/projects/parer/wiki/DPI_installazione_tomcat9).

## Versionamento dpi-config e dpi  

Il versionamento del progetto **dpi-config** segue direttamente quello dell'applicazione [DPI](https://gitlab.ente.regione.emr.it/parer/dpi), ossia, ad ogni nuovo versionamento di quest'ultimo seguirà anche il versionamento di questo progetto (esempio se creata la versione 3.0.0 di dpi si dovrà anche creare la relativa versione di dpi-config 3.0.0 indipendentemente se quest'ultimo è stato modificato o meno). 
Questa gestione delle versioni è utile per associare ad ogni nuova versione applicativa di dpi anche le relative configurazioni.
In caso di **sola modifica di dpi-config** non seguita quindi da modifiche applicative su **dpi**, si stabilisce la generazione di una nuova versione di **dpi-config** applicando un quarto numero alla versione da creare (esempio dpi alla versione 3.0.0 e dpi-config 3.0.0, in caso di sola modifica a dpi-config si crea la versione 3.0.0**.1**).


Esempio 1 (modifica a dpi che segue il versionamento di dpi-config)

Sul tag [2.6.0](https://gitlab.ente.regione.emr.it/parer/dpi-config/-/tags/2.6.0) le configurazioni hanno effettuato a **partire** dalla versione 2.6.0 del DPI e da quelle successive, le precedenti versioni avranno quindi configurazioni diverse e certamente non compatibili con quelle rilasciate.

Esempio 2 (modifica esclusiva a dpi-config)

Si crea la versione **2.6.0.1** di dpi-config che quindi è relativa alla versione **2.6.0** di dpi ma si evidenziano le sole modifiche alle configurazioni compatibili a partire da questa versione.


## Modifica delle configurazioni  

La directory su cui agire è [filters](filters) su cui sono presenti i file statici con relativi placeholder, trattandosi di un progetto maven che utilizza l'apposito plugin, è necessario eventualmente agire sui file in cui è già presente una logica di "filtro" e, nell'eventualità le future evolutive dell'applicazione DPI impongano nuovi file, di modificare anche il pom.xml di progetto. Per la generazione dell'artifact finale è stata predisposta una apposista implementazione su pipeline Gitlab che produce il "pacchetto" attraverso il goal maven "package".
