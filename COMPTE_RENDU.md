# Compte rendu — TP Intégration Continue GitHub Actions & Laravel

## Badge de statut
<!-- Collez ici le badge Markdown copié depuis GitHub Actions -->

## Réponses aux questions de réflexion

### Question 1 (Partie 1)
**Pourquoi l'étape "Récupération du code source" est-elle indispensable avant d'exécuter `php -v` ?**

Le runner GitHub Actions démarre sur une machine virtuelle vierge, sans aucun accès au code du dépôt. L'étape `actions/checkout@v4` clone le contenu du dépôt dans l'espace de travail du runner. Sans cette étape, les commandes suivantes du pipeline (composer install, php artisan test, etc.) n'auraient aucun fichier sur lequel s'exécuter.

### Question 2 (Partie 2 - Analyse d'erreur)
**Identifiez la ligne incriminée lors de l'échec simulé.**

Le test `test_the_application_returns_a_successful_response` dans `tests/Feature/ExampleTest.php` a échoué avec le message `Expected response status code [500] but received 200`, car l'assertion avait été volontairement modifiée de `assertStatus(200)` à `assertStatus(500)`.

## Captures d'écran
<!-- Insérez ici la capture de l'artefact de couverture de tests -->

## Réponses au quiz
1. B) /.github/workflows/ci.yml
2. B) En parallèle (simultanément sur deux runners indépendants)
3. B) L'enregistrer dans les "Repository Secrets" et l'appeler via ${{ secrets.VOTRE_SECRET }}
4. B) À conserver les dossiers de dépendances vendor entre les builds pour réduire drastiquement le temps de calcul
