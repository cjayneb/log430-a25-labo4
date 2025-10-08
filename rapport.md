# Labo 04 — Rapport

<img src="https://upload.wikimedia.org/wikipedia/commons/2/2a/Ets_quebec_logo.png" width="250"> \
Jean-Christophe Benoit \
Rapport de laboratoire \
LOG430 — Architecture logicielle \
Montréal, 10 octobre 2025 \
École de technologie supérieure

> J'ai crée ce PDF en utilisant le gabarit markdown (.md).

## Questions

### Question 1

> Quelle est la latence moyenne (50ème percentile) et le taux d'erreur observés avec 100 utilisateurs ? Illustrez votre réponse à l'aide des graphiques Locust (onglet Charts).

On observe que la latence moyenne a atteint un maximum de 97 ms et qu'aucune erreur est observée avec 100 utilisateur simultanés :
![alt text](image.png)

### Question 2

> À partir de combien d'utilisateurs votre application cesse-t-elle de répondre correctement (avec MySQL) ? Illustrez votre réponse à l'aide des graphiques Locust.

À partir de 83 utilisateurs simultanés, l'application arrête de répondre correctement, car elle commence à retourner plusieurs erreurs 500 aux clients. les erreurs sont une des suivantes :

- 500 - (mysql.connector.errors.DatabaseError) 1040 (HY000): Too many connections
- 500 - (mysql.connector.errors.InternalError) 1213 (40001): Deadlock found when trying to get lock; try restarting transaction
- Des erreur 500 génériques
  ![alt text](image-1.png)

### Question 3

> À partir de combien d'utilisateurs votre application cesse-t-elle de répondre correctement (avec MySQL + optimisation) ? Illustrez votre réponse à l'aide des graphiques Locust.

### Question 4

> À partir de combien d'utilisateurs votre application cesse-t-elle de répondre correctement (avec Redis + optimisation) ? Quelle est la latence et le taux d'erreur observés ? Illustrez votre réponse à l'aide des graphiques Locust.

### Question 5

> À partir de combien d'utilisateurs votre application cesse-t-elle de répondre correctement (avec Redis + Optimisation + Nginx load balancing) ? Quelle est la latence moyenne (50ème percentile) et le taux d'erreur observés ? Illustrez votre réponse à l'aide des graphiques Locust.

### Question 6

> Avez-vous constaté une amélioration des performances à mesure que nous avons mis en œuvre différentes approches d'optimisation ? Quelle a été la meilleure approche ? Justifiez votre réponse en vous référant aux réponses précédentes.

### Question 7

> Dans le fichier nginx.conf, il existe un attribut qui configure l'équilibrage de charge. Quelle politique d'équilibrage de charge utilisons-nous actuellement ? Consultez la documentation officielle Nginx si vous avez des questions.

## Observations additionnelles

### CI/CD

- Utilisation d'une VM Ubuntu 24.04 créée sur Microsoft Azure Portal for Students
- La VM héberge un self hosted runner pour exécuter le workflow de CI/CD et pour héberger les conteneurs déployés
- L'adresse IP public de la VM est 20.120.181.0 et les routes de l'API sont accessibles directement sur cette adresse en HTTP

### Problème(s) rencontré(s)

- Observations sur d’éventuels problèmes de setup ou de code rencontrés lors de l’exécution des activités (optionel).
- Problème avec le groupe de l'utilisateur sur la VM pour docker
- Installation de docker _from scratch_
