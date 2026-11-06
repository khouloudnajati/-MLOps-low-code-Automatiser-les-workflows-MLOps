# Orchestrateur ou integration continue ? (TP06)
 
| Critere                           | Prefect (orchestrateur) | GitHub Actions (CI) |
|-----------------------------------|-------------------------|---------------------|
| Ce qui declenche l'execution | Une planification (cron), un lancement manuel depuis l'interface ou un evenement configure. | Un evenement Git, comme un `git push`, ou un lancement manuel depuis l'onglet Actions. |
| Ou s'execute le traitement | Sur la machine locale via un serveur Prefect et un worker (ou `serve`). | Sur une machine virtuelle distante fournie par GitHub (runner Ubuntu). |
| Qui surveille, et ou | Prefect surveille les executions, les taches, leurs logs et leurs etats depuis son interface web. | GitHub Actions surveille les jobs et les etapes depuis l'onglet Actions du depot GitHub. |
| Ce qui se passe en cas d'echec | Le workflow passe a l'etat Failed. La tache fautive est identifiee et les taches suivantes ne s'executent pas. | Le job passe en echec (rouge). Les etapes suivantes sont interrompues et les logs permettent d'identifier l'erreur. |
| Type de tache adapte | Executer, orchestrer et surveiller des traitements ML recurrents : reentrainement, evaluation et deploiement. | Verifier automatiquement le code, les dependances et la qualite du pipeline a chaque modification. |
| Ce qui est versionne dans Git | Le code Python du workflow, les fichiers de configuration, le deploiement et les parametres de planification. | Le fichier YAML de configuration CI, les scripts de verification et les fichiers de dependances. |

## Conclusion (5 lignes)

Prefect est un orchestrateur qui permet d'executer, de planifier et de surveiller des workflows MLOps.
Il gere les differentes taches, leurs dependances, leurs executions et leurs erreurs.
GitHub Actions est une solution d'integration continue qui automatise la verification du code a chaque modification.
Il permet de detecter rapidement les erreurs et de verifier que le pipeline respecte les criteres de qualite.
Les deux outils sont complementaires : GitHub Actions valide les changements, tandis que Prefect orchestre les traitements recurrents.