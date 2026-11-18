# Site Thory Tales — guide de mise en ligne (100 % gratuit)

Ce dossier contient ton site complet. Il n'a besoin ni de serveur ni de base de données.

```
thory-tales/
├── index.html              ← la page du site (tu n'y touches presque jamais)
├── assets/js/contenu.js    ← TOUT ton contenu : livres, salons, actus, bio, liens
├── assets/css/style.css    ← les couleurs et polices (variables en haut du fichier)
├── assets/js/site.js       ← le fonctionnement (ne pas modifier)
├── assets/img/             ← tes images : couvertures, portrait, image de partage
├── robots.txt, sitemap.xml ← pour Google
```

---

## 1. Mettre le site sur GitHub (gratuit)

1. Crée un compte sur **github.com**.
2. Clique sur **New repository**, nomme-le `thory-tales`, laisse-le en **Public** ou **Private** (les deux marchent), puis **Create repository**.
3. Sur la page du dépôt, clique sur **uploading an existing file**.
4. Glisse **le contenu** du dossier `thory-tales` (le fichier `index.html` et le dossier `assets`, pas le dossier parent), puis **Commit changes**.

## 2. Publier avec Cloudflare Pages (gratuit)

1. Crée un compte sur **dash.cloudflare.com**.
2. Menu **Workers & Pages** → **Create** → onglet **Pages** → **Connect to Git**.
3. Autorise GitHub et choisis le dépôt `thory-tales`.
4. Réglages de build : **Framework preset : None**, **Build command : vide**, **Build output directory : `/`**.
5. **Save and Deploy**. Ton site est en ligne à une adresse du type `thory-tales.pages.dev`.

Ensuite, chaque modification faite sur GitHub republie le site automatiquement en une minute.

## 3. Brancher ton nom de domaine thory-tales.com

1. Dans ton projet Cloudflare Pages : **Custom domains** → **Set up a custom domain** → tape `www.thory-tales.com`.
2. Cloudflare te propose deux options :
   - **Le plus simple :** transférer la gestion DNS de ton domaine chez Cloudflare (gratuit). Cloudflare te donne deux « nameservers » à recopier chez ton registrar (OVH, Gandi, IONOS…), dans la rubrique *Serveurs DNS*.
   - **Sinon :** chez ton registrar, crée un enregistrement **CNAME** `www` qui pointe vers `thory-tales.pages.dev`.
3. Ajoute aussi `thory-tales.com` (sans www) pour qu'il redirige vers la version www.
4. Compte de quelques minutes à 24 h pour la propagation. Le HTTPS (cadenas) est automatique et gratuit.

## 4. Activer la newsletter avec Brevo (gratuit jusqu'à 300 e-mails/jour)

1. Crée un compte sur **brevo.com** (société française, conforme RGPD).
2. **Contacts** → **Listes** → crée une liste « Lecteurs Thory Tales ».
3. **Contacts** → **Formulaires** → **Créer un formulaire d'inscription**. Ajoute les champs **EMAIL** et **PRENOM**, choisis ta liste, active la **double confirmation** (recommandé).
4. À l'étape **Partager**, choisis **Code HTML**. Dans ce code, repère l'adresse après `action="` (elle ressemble à `https://xxxx.sibforms.com/serve/...`).
5. Colle-la dans `assets/js/contenu.js`, ligne `brevoAction: ""`.

Le formulaire du site enverra alors les inscriptions directement dans ta liste Brevo.

## 5. Activer le formulaire de contact avec Web3Forms (gratuit)

1. Va sur **web3forms.com**, entre ton adresse e-mail, tu reçois une **Access Key**.
2. Colle-la dans `assets/js/contenu.js`, ligne `web3formsKey: ""`.

Les messages des visiteurs arriveront dans ta boîte mail.

## 6. Mettre à jour ton contenu

Tout se passe dans **`assets/js/contenu.js`**. Sur GitHub, ouvre le fichier, clique sur le crayon ✏️, modifie, puis **Commit changes**. Le site se met à jour tout seul.

**Ajouter un livre :** copie un bloc `{ … }` de la liste `livres`, colle-le à la suite (avec une virgule entre deux blocs) et change les textes.

**Ajouter une vraie couverture :** dépose l'image dans `assets/img/` (ex. `chant-des-englouties.jpg`, format portrait 2:3, environ 800 × 1200 px), puis écris `couverture: "assets/img/chant-des-englouties.jpg"`. Sans image, une couverture aux couleurs du livre est générée automatiquement.

**Lien d'achat :** mets le lien de ta page auteur dans `boutique`, ou le lien précis d'un livre dans son `lienAchat`.

**Ajouter un salon :** copie un bloc de `agenda`. Le champ `date` (format `2027-05-15`) sert au tri : une fois la date passée, le salon part tout seul dans « Salons passés ».

**Ajouter une actu :** copie un bloc de `actus`. Les six plus récentes s'affichent.

**Ta photo :** dépose `portrait.jpg` dans `assets/img/`, puis dans `index.html` remplace « Ta photo ici » par `<img src="assets/img/portrait.jpg" alt="Portrait de Thory">`.

**Image de partage (Facebook, Instagram, WhatsApp) :** dépose une image `partage.jpg` de 1200 × 630 px dans `assets/img/`.

## 7. À compléter avant l'ouverture

- [ ] Ton adresse e-mail de contact (`email` dans `contenu.js`)
- [ ] Les liens d'achat (`boutique` / `lienAchat`)
- [ ] Les couvertures et ta photo
- [ ] Les dates exactes des salons
- [ ] Les **mentions légales** dans `index.html` (nom, SIRET, adresse ou domiciliation) : obligatoires en France
- [ ] La clé Brevo et la clé Web3Forms

## Tester sur ton ordinateur

Double-clique sur `index.html` : le site s'ouvre dans ton navigateur, sans installation.

## Coût total

GitHub 0 € · Cloudflare Pages 0 € · Brevo 0 € · Web3Forms 0 €. Seul ton nom de domaine reste payant chez ton registrar, comme aujourd'hui.
