# Os_administration
Le programme est un script de gestion des tâches écrit en Bash qui permet aux utilisateurs de créer, mettre à jour, supprimer, consulter et rechercher des tâches. Voici les choix de conception et les détails de l'organisation :

### Stockage des données
- *Stockage basé sur des fichiers* : Les tâches sont stockées dans un fichier texte simple nommé tasks.txt.
- *Format* : Chaque tâche est stockée sur une seule ligne avec des champs séparés par un délimiteur spécifique (quatre espaces). Les champs sont :
  1. ID de la tâche
  2. Titre
  3. Description
  4. Lieu
  5. Date d'échéance (YYYY-MM-DD)
  6. État de complétion (complétée/non complétée)

### Organisation du code
1. *Fonctions* : Le script est modularisé à l'aide de fonctions, chacune responsable d'une opération spécifique de gestion des tâches :
    - create_task() : Crée une nouvelle tâche.
    - update_task() : Met à jour une tâche existante.
    - delete_task() : Supprime une tâche par son ID.
    - task_info() : Affiche les informations d'une tâche spécifique par son ID.
    - list_tasks_by_day() : Liste les tâches pour une date spécifique, séparées en sections complétées et non complétées.
    - search_task_by_title() : Recherche des tâches par titre.
    - show_help() : Affiche les instructions d'utilisation.

2. *Création de tâche* :
    - *Vérification de l'existence du fichier* : Vérifie si le fichier tasks.txt existe et le crée si ce n'est pas le cas.
    - *Validation des entrées* : S'assure que le titre et la date d'échéance sont fournis et correctement formatés. Sinon, invite l'utilisateur jusqu'à ce que des entrées valides soient fournies.
    - *Génération d'ID de tâche* : Génère automatiquement un ID de tâche unique basé sur le dernier ID de tâche dans le fichier.
    - *Valeurs par défaut* : Définit des valeurs par défaut pour l'état de complétion si elles ne sont pas fournies.

3. *Mise à jour de tâche* :
    - Invite l'utilisateur à entrer l'ID de la tâche et le champ qu'il souhaite mettre à jour (titre, description, lieu, date d'échéance ou état de complétion).
    - Utilise awk pour modifier le champ spécifique de la tâche.

4. *Suppression de tâche* :
    - Invite l'utilisateur à entrer l'ID de la tâche à supprimer.
    - Utilise awk pour filtrer la tâche avec l'ID spécifié.

5. *Information sur les tâches* :
    - Demande l'ID de la tâche et affiche tous les détails de la tâche spécifiée à l'aide de awk.

6. *Liste des tâches* :
    - *Par jour* : Demande une date et liste les tâches pour cette date, divisées en tâches complétées et non complétées.
    - *Jour actuel* : Si aucun argument n'est fourni, liste les tâches pour la date actuelle.

7. *Recherche par titre* :
    - Demande un titre et recherche les tâches avec le titre correspondant, affichant toutes les correspondances.

8. *Aide et arguments en ligne de commande* :
    - Le script prend en charge les arguments en ligne de commande pour effectuer directement des opérations spécifiques.
    - Affiche les instructions d'utilisation si l'argument --help est passé ou si une commande inconnue est entrée.

### Gestion des erreurs et retour utilisateur
- *Validation des entrées* : S'assure que les champs requis (titre, date d'échéance) ne sont pas vides et que la date d'échéance est au format correct.
- *État de complétion par défaut* : Si l'utilisateur ne spécifie pas l'état de complétion, il est défini par défaut sur "non complétée".
- *Messages de retour* : Fournit des retours clairs à l'utilisateur après chaque opération (par exemple, tâche ajoutée, tâche mise à jour, tâche supprimée).
- *Commandes invalides* : Vérifie les commandes inconnues et fournit des instructions d'utilisation.

Dans l'ensemble, le script est conçu pour être convivial et robuste, garantissant que les tâches sont gérées efficacement grâce à une série d'opérations et de contrôles bien définis.
