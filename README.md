# DPI Config

Progetto relativo alle generazione delle cofigurazioni standard suddivise per ambiente ed installazione dell'applicazione [DPI](https://gitlab.ente.regione.emr.it/parer/dpi). <br/><br/>


## Guida alle configurazioni  

Nella directory [conf](conf), vengono generate automaticamente dal modello CI/CD, le configurazioni per le diverenze installazioni di DPI per ogni ambiente, che saranno predisposte opportunamente secondo [guida ufficiale](https://parermine.regione.emilia-romagna.it/projects/parer/wiki/DPI_installazione_tomcat9).

## Modifica delle configurazioni  

La directory su cui agire è [filters](filters) su cui sono presenti i file statici con relativi placeholder, trattandosi di un progetto maven che utilizza l'apposito plugin, è necessario eventualmente agire sui file in cui è già presente una logica di "filtro" e, nell'eventualità le future evolutive dell'applicazione DPI impongano nuovi file, di modificare anche il pom.xml di progetto. Per la generazione dell'artifact finale è stata predisposta una apposista implementazione su pipeline Gitlab che produce il "pacchetto" attraverso il goal maven "package" e il profilo "full-build" che è stato opportuvamente configurato.