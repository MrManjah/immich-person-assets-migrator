# Immich Asset Transfer Script

Ce script permet de récupérer les assets assignés à une personne spécifique dans votre bibliothèque Immich personnelle et de les réimporter dans la bibliothèque familiale.

## Configuration

1. Éditez le fichier `config.json` avec vos informations :
   - `url`: L'URL de votre instance Immich (ex: "http://localhost:2283")
   - `my_x_api_key`: Votre clé API personnelle
   - `family_x_api_key`: La clé API de la bibliothèque familiale
   - `person_id`: L'ID de la personne (récupérable via l'API à l'adresse : `{{url}}/api/search/person?name=John`)

## Installation

Créez un environnement virtuel et installez les dépendances :
```
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Utilisation

### Mode test (pour compter les assets sans transfert)
Lancez le script en mode test pour valider le nombre d'assets :
```
python immich_transfer.py --test
```

### Mode transfert complet
Lancez le script pour effectuer le transfert :
```
python immich_transfer.py
```

Le script va :
1. Récupérer la liste des assets pour la personne spécifiée
2. Télécharger chaque asset
3. Les uploader dans la bibliothèque familiale

## Notes

- Assurez-vous que les clés API ont les permissions nécessaires.
- Les fichiers téléchargés temporairement sont supprimés après l'upload.
- Vérifiez les logs pour les erreurs.