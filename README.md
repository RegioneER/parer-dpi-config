# DPI Config

Progetto relativo alle generazione delle cofigurazioni standard suddivise per ambiente ed installazione dell'applicazione [DPI](https://gitlab.ente.regione.emr.it/parer/dpi). <br/><br/>

## Introduzione

Il seguente progetto viene creato per esternalizzare le configurazioni, per singolo ambiente, dell'applicazione DPI, nello specifico il progetto viene creato a partire dalla configurazioni alla versione **2.6.0** del DPI che sono quindi le ultime ad essere presenti all'interno dell'applicativo stesso.

## Guida alle configurazioni  

Nella directory [conf](conf), vengono generate automaticamente dal modello CI/CD, le configurazioni per le diverenze installazioni di DPI per ogni ambiente, che saranno predisposte opportunamente secondo [guida ufficiale](https://parermine.regione.emilia-romagna.it/projects/parer/wiki/DPI_installazione_tomcat9).

## Rilascio delle configurazioni  

Il rilascio delle configurazioni prevede, come precondizione **fondamentale**, un nuovo rilascio dell'applicativo [DPI](https://gitlab.ente.regione.emr.it/parer/dpi) questo comporta la modifica del progetto [DPI Config](https://gitlab.ente.regione.emr.it/parer/dpi-config) come da istruzioni (vedi paragrafo successivo) e al termine delle opportune modifiche, si dovrà creare un **git tag** con la seguente logica ossia, un nuovo tag dovrà **necessariamente** riportare **da quale versione del DPI le configurazioni hanno effetto**. Le modifiche delle configurazioni infatti dovranno tracciare da quale versione applicativa del DPI saranno valide in quanto, non si prevede alcuna retrocompatibilità (o si può garantire la "robustezza" all'indietro) qualora vengano modificate una o più configurazioni. 

Esempio

Sul tag [2.6.0](https://gitlab.ente.regione.emr.it/parer/dpi-config/-/tags/2.6.0) le configurazioni hanno effettuato a **partire** dalla versione 2.6.0 del DPI e da quelle successive, le precedenti versioni avranno quindi configurazioni diverse e certamente non compatibili con quelle rilasciate.

La creazione del git tag su questo progetto è, per il momento, **manuale** è quindi importante osservare delle convenzioni ben specifiche, naturalmente l'approccio più semplifice, prevece che il nome del tag riporti esattamente la release applicativa del DPI con la naming convention: X.Y.Z. 

## Modifica delle configurazioni  

La directory su cui agire è [filters](filters) su cui sono presenti i file statici con relativi placeholder, trattandosi di un progetto maven che utilizza l'apposito plugin, è necessario eventualmente agire sui file in cui è già presente una logica di "filtro" e, nell'eventualità le future evolutive dell'applicazione DPI impongano nuovi file, di modificare anche il pom.xml di progetto. Per la generazione dell'artifact finale è stata predisposta una apposista implementazione su pipeline Gitlab che produce il "pacchetto" attraverso il goal maven "package".
