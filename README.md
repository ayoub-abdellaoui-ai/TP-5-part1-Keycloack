# TP-5-part1-Keycloack

# Sécurisation des Microservices avec Keycloak

## Partie 1 : Configuration de Keycloak

### Étapes à suivre :
1. **Télécharger Keycloak 19**
   - [Lien de téléchargement officiel](https://www.keycloak.org/downloads)

2. **Démarrer Keycloak**
   - Utilisez la commande suivante :
     ```bash
     kc.bat start-dev
     ```

3. **Créer un compte Admin**

4. **Créer un Realm**

5. **Créer un client à sécuriser**

6. **Créer des utilisateurs**

7. **Créer des rôles**

8. **Affecter les rôles aux utilisateurs**

9. **Tester avec Postman** :
   - Tester l'authentification avec un mot de passe.
   - Analyser les contenus des deux JWT : Access Token et Refresh Token.
   - Tester l'authentification avec le Refresh Token.
   - Tester l'authentification avec Client ID et Client Secret.
   - Modifier les paramètres des Tokens Access Token et Refresh Token.

---

## Étapes à suivre avec captures d'écran :

### Créer une application qui permet de gérer des comptes respectant les patterns CQRS et Event Sourcing avec les Framework AXON et Spring Boot.

![image](https://github.com/user-attachments/assets/b17089a3-3a5a-47ce-b97c-1ea842ddee5d)

### Testing create account :
- **Créer un compte :**
![image](https://github.com/user-attachments/assets/fb096d2e-3595-47a7-b052-f7e55422916c)

- **Après exception :**
![image](https://github.com/user-attachments/assets/6d902224-2b19-4859-87d0-2b68054c5630)

- **Testing create account :**
![image](https://github.com/user-attachments/assets/668b205d-7150-457f-94aa-eb4a880a249a)

### Vérifier la base de données :
- **Voir les entrées dans `domain_event_entry` :**
![image](https://github.com/user-attachments/assets/6ad45da8-18c9-4bc3-9396-861370da1154)
![image](https://github.com/user-attachments/assets/5cb4e5ef-53d5-46b6-912d-237c1dfac35e)

- **Voir le contenu de l'événement :**
![image](https://github.com/user-attachments/assets/553ff720-f8df-4293-b582-e3ecf674e518)

- **Consulter `eventStore` :**
![image](https://github.com/user-attachments/assets/ee87857c-942a-4cf1-8abe-7e1f25cc1c76)

### Testing Credit et Debit :
- **Testing Credit :**
![image](https://github.com/user-attachments/assets/4c9f2767-3022-4f99-a252-8affcdebafc9)

- **Testing Debit :**
![image](https://github.com/user-attachments/assets/93ad49ec-c5a8-4ab6-9fb4-6efbed484de2)
![image](https://github.com/user-attachments/assets/23552395-887c-4d85-893d-65d090d76e8e)

---

## Conclusion
Cette implémentation montre comment intégrer **Keycloak** pour sécuriser une architecture de microservices, en gérant l'authentification et les autorisations de manière centralisée. Cela permet d'améliorer la sécurité et la modularité du système.
