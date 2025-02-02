Étape 1 : Installer le rôle de serveur de fichiers
Ouvrez Gestionnaire de serveur.
Cliquez sur Ajouter des rôles et fonctionnalités.
Dans l'Assistant, sélectionnez Installation basée sur un rôle ou une fonctionnalité, puis cliquez sur Suivant.
Sélectionnez votre serveur, cliquez sur Suivant.
Dans la liste des rôles, cochez Serveur de fichiers et de stockage > Services de fichiers > Serveur de fichiers.
Cliquez sur Suivant et Installer.
Une fois l’installation terminée, fermez l’Assistant.

Étape 2 : Créer le dossier principal et les sous-dossiers
Ouvrez l'Explorateur de fichiers.
Accédez à C:\.
Cliquez droit dans la fenêtre, sélectionnez Nouveau > Dossier, nommez-le Documents_Entreprise.
Ouvrez Documents_Entreprise, créez les sous-dossiers : RH, Comptabilité, et Direction en suivant la même méthode.

Étape 3 : Partager le dossier principal
Cliquez droit sur le dossier Documents_Entreprise, sélectionnez Propriétés.
Accédez à l’onglet Partage, cliquez sur Partager....
Dans la fenêtre, ajoutez :
Domain Users avec la permission Lecture.
Administrators avec la permission Lecture/Écriture.
Cliquez sur Partager, puis Terminer.

Étape 4 : 
Ouvrir la console de gestion des utilisateurs et groupes Active Directory
Sur le serveur Windows Server 2022, ouvrir Gestionnaire de serveur
Aller dans Outils → Utilisateurs et ordinateurs Active Directory
- Création des groupes
Dans le volet gauche, développer le nom de domaine
Users → Nouveau → Groupe
Les crée :
  Nom du groupe : RH, Comptabilité, Direction
- Pendant que nous y sommes, je vais ajouter deux utilisateurs pour nos tests plus tard, un dans le groupe RH : user1, et le second dans le groupe compta : user2.

Étape 5 : Configurer les permissions NTFS
Cliquez droit sur Documents_Entreprise, sélectionnez Propriétés, puis l’onglet Sécurité.
Cliquez sur Avancé.
Ajoutez des entrées pour chaque groupe :
RH : Accès lecture/écriture sur RH.
Comptabilité : lecture/écriture sur Comptabilité.
Direction : Accès complet sur Documents_Entreprise et tous les sous-dossiers.
Domain Users : Lecture seule sur Documents_Entreprise.
Appliquez les changements et fermez.

Étape 6 : Vérifier les partages
Dans Gestionnaire de serveur, accédez à Outils > Gestion des partages et du stockage.
Vérifiez que le partage Docs est bien listé et accessible.

Étape 7 : Configurer un lecteur réseau sur un poste client
Sur le poste Windows 10, ouvrez l'Explorateur de fichiers.
Cliquez sur Ce PC, puis sur Connecter un lecteur réseau.
Choisissez une lettre de lecteur (par exemple Z:).
Dans le champ Dossier, entrez : \\<NomDuServeur>\\Docs.
Cochez Se reconnecter à l’ouverture de session, cliquez sur Terminer.
Entrez les identifiants si nécessaire.
