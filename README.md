# TP-5-part1-Keycloack# Sécurisation des Microservices avec Keycloak

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

## Partie 2 : Sécurisation des Microservices

### Projet : [E-commerce Micro-Services Spring | Angular](https://github.com/Amina-contact/e-commerce-Micro-services-Spring-Angular)

### Étapes de sécurisation :

1. **Ajouter des dépendances dans le fichier `pom.xml` :**
   ```xml
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-security</artifactId>
   </dependency>
   <dependency>
       <groupId>org.keycloak</groupId>
       <artifactId>keycloak-spring-boot-starter</artifactId>
   </dependency>
   ```

2. **Créer une classe de configuration Keycloak Adapter :**
   ```java
   @Configuration
   public class KeycloakAdapterConfig {
       @Bean
       KeycloakSpringBootConfigResolver springBootConfigResolver() {
           return new KeycloakSpringBootConfigResolver();
       }
   }
   ```

3. **Configurer la sécurité dans le projet :**
   ```java
   @KeycloakConfiguration
   @EnableGlobalMethodSecurity(prePostEnabled = true)
   public class SecurityConfig extends KeycloakWebSecurityConfigurerAdapter {
       @Override
       protected SessionAuthenticationStrategy sessionAuthenticationStrategy() {
           return new RegisterSessionAuthenticationStrategy(new SessionRegistryImpl());
       }

       @Override
       protected void configure(AuthenticationManagerBuilder auth) throws Exception {
           auth.authenticationProvider(keycloakAuthenticationProvider());
       }

       @Override
       protected void configure(HttpSecurity http) throws Exception {
           super.configure(http);
           http.csrf().disable();
           http.authorizeRequests().antMatchers("/h2-consol/**").permitAll();
           http.headers().frameOptions().disable();
           http.authorizeRequests().anyRequest().authenticated();
       }
   }
   ```

4. **Configurer l'autorisation dans le contrôleur :**
   - Ajoutez l'annotation :
     ```java
     @PreAuthorize("hasAuthority('ADMIN')")
     ```

5. **Tester les rôles :**
   - **Avec le rôle ADMIN** :
     - Accédez aux routes nécessitant des autorisations administratives.
   - **Avec le rôle USER** :
     - Vérifiez les restrictions appliquées pour un utilisateur standard.

---

## Conclusion
Cette implémentation montre comment intégrer **Keycloak** pour sécuriser une architecture de microservices, en gérant l'authentification et les autorisations de manière centralisée. Cela permet d'améliorer la sécurité et la modularité du système.
