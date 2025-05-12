# BC-Olist

- Olist est implanté et n’opère qu’au Brésil.

- C’est une entreprise 100% numérique. En effet, les opérations commerciales sont entièrement gérées en ligne).

- Service e-commerce pour les vendeurs.

- Connecte les (petits) commerçants aux places de marché les plus importantes du Brésil (Amazon, Bahia, Walmart, ...).

- Offre des services de logistique et de gestion des stocks aux vendeurs.

- Ne vend rien directement aux consommateurs.



# Votre mission

Objectif :
Aider les chefs d'entreprise dans leur processus de prise de décision.


Le PDG d'Olist, vous a chargé de donner un sens à l'ensemble des données afin de formuler des recommandations sur la question suivante :

**Comment accroître la satisfaction des clients d’Olist ?**

# La data

Informations sur environ 100 000 commandes effectuées entre 2016 et 2018.
Des données réelles !
Les informations identifiables ont été anonymisées.
Documentation complète disponible dans le dictionnaire mis à disposition.

## Le déroulement pour chaque vendeur


Le vendeur rejoint Olist et met en ligne à disposition d’Olist ses catalogues de produits.
Olist affiche ces catalogues sur les plateformes commerciales existantes (Amazon, Bahia, Walmart, ...).
Le vendeur reçoit une notification dès qu'un produit est vendu.
Le vendeur transmet les articles commandés à des transporteurs logistiques tiers.

Attention : Plusieurs vendeurs peuvent être impliqués dans la commande d'un client !


## Le déroulement pour le client


Le client parcourt les produits sur  les plateformes commerciales (Amazon, Bahia, Walmart, ...).
Il achète les produits listés via Olist.store.
Il obtient une date prévue pour la livraison, en tenant compte de l’estimation de l'heure d'arrivée.
Le client reçoit la/les commande(s) et laisse un commentaire.

Remarque : entre 2016 et mi-2018, un avis pouvait être laissé dès l'envoi de la commande, ce qui signifie qu'un client pouvait potentiellement laisser un avis pour un produit qu'il n'avait pas encore reçu !


**Vous devrez faire une présentation dans un premier temps sous slides, qui contient au minimum le contexte, la problématique, ainsi que la conclusion qui contient des RECOMMANDATIONS faites au client, dans le but d'améliorer la satisfaction des clients d'Olist. Aussi, vous utiliserez un dashboard pour convaincre le client, pour que les recommandations soit logiques à ses yeux. Pour rappel, la recommandation est l'élément central d'une présentation réalisée par un data analyst. En effet, à vous d'être convaincant, pour que vos arguments soient entendus. Il est donc nécessaire de développer un minimum d'expertise métier sur le sujet, pour être à l'aise avec ses recommandations.** Le client n'est pas data analyst, mais souhaiterait comprendre la démarche. Il faudra donc s'attacher à expliquer vos choix sans rentrer dans un trop grand niveau technique, autrement dit : vulgariser.
Le juré examinateur, lors de la partie question, peut vous poser des questions sur le code qui est contenu dans votre google colab. Il est donc indispensable de mettre à disposition dans les pièces soumises pour le passage oral, votre travail exploratoire contenu dans un google colab.



## Livrables attendus
Le client souhaite une présentation avec des slides (sous format pdf) et un tableau de bord intéractif (Power BI, Tableau ou autre outil de BI).  

/!\ Attention /!\ :  
Votre production, bien que devant valider des compétences du Bloc 4, doit être pertinente au sujet données (exploitable dans une optique business).

La présentation contiendra à minima ces éléments :
- Rappel du contexte et de la problématique
- Recommandations
- Analyse exploratoire des données
- Méthodologie, outils et langages utilisés
- Votre tableau de bord contient des graphiques pertinents, lisibles et inclusifs.
- Votre tableau de bord contient au moins une visualisation de données interactive pertinente.
- Votre tableau de bord contient au moins une carte représentant des informations géographiques.
- Votre tableau de bord contient au moins un tableau croisé.
- L'ensemble des graphiques et visuels doit être lisible par tous (prise en compte des personnes en situation de handicap visuel).
- Réponse à la question métier : Recommandations pour accroître la satisfaction des clients d'Olist.

## Dictionnaire des datasets

# `customers_dataset`

Cette table contient des informations sur le client et sa localisation. Utilise-le pour identifier les clients uniques dans le jeu de données des commandes et pour trouver le lieu de livraison des commandes.

`customer_id` : clé de l'ensemble de données des commandes. Chaque commande a un customer_id unique.  
`customer_unique_id` : identifiant unique d'un client.  
`customer_zip_code_prefix` : cinq premiers chiffres du code postal du client.  
`customer_city` : nom de la ville du client.
`customer_state` : État du client.


# `geolocation_dataset`

Ce jeu de données contient des informations sur les codes postaux brésiliens et les coordonnées lat/lng. Utilise-le pour tracer des cartes et trouver les distances entre les vendeurs et les clients.

`geolocation_zip_code_prefix` : 5 premiers chiffres du code postal.   
`geolocation_lat` : latitude.   
`geolocation_lng` : longitude.  
`geolocation_city` : nom de la ville.  
`geolocation_state` : état


# `order_items_dataset`

Ce jeu de données comprend des données sur les articles achetés dans le cadre de chaque commande.

⚠️ Si 3 articles sont achetés dans une commande, le jeu de données affichera une ligne par article. Si le même produit est acheté deux fois, 2 lignes seront affichées.

`order_id` : identifiant unique de la commande.  
`order_item_id` : numéro séquentiel identifiant le nombre d'articles inclus dans la même commande.   
`product_id` : identifiant unique du produit.  
`seller_id` : identifiant unique du vendeur.   
`shipping_limit_date` : indique la date limite d'expédition du vendeur pour le transfert de la commande au partenaire logistique.   
`price` : prix de l'article.  
`freight_value` : valeur du fret de l'article (si une commande comporte plus d'un article, la valeur du fret est répartie entre les articles).   


# `order_payments_dataset`

Ce jeu de données comprend des données sur les options de paiement des commandes.

`order_id` : identifiant unique d'une commande.  
`payment_sequential` : un client peut payer une commande avec plus d'un mode de paiement. Si c'est le cas, une séquence sera créée pour accueillir tous les paiements.   
`payment_type` : mode de paiement choisi par le client.   
`payment_installments` : nombre de versements choisis par le client.   
`payment_value` : valeur de la transaction.   


# `order_reviews_dataset`

Cet ensemble de données comprend des données sur les évaluations faites par un client.

Après qu'un client ait acheté un produit dans la boutique Olist, un vendeur est informé de la nécessité d'exécuter cette commande. Une fois que le client a reçu le produit, ou que la date de livraison estimée est arrivée, le client reçoit une enquête de satisfaction par e-mail où il peut laisser une note sur son expérience d'achat et écrire quelques commentaires.

`review_id` : identifiant unique de l'avis.  
`order_id` : identifiant unique de la commande.   
review_score : note allant de 1 à 5 donnée par le client dans une enquête de satisfaction.   
`review_comment_title` : titre du commentaire laissé par le client, en portugais.  
`review_comment_message` : message de l'avis laissé par le client, en portugais.   
`review_creation_date` : indique la date à laquelle l'enquête de satisfaction a été envoyée au client.  
`review_answer_timestamp` : indique l'horodatage de la réponse à l'enquête de satisfaction.  

# `orders_dataset`

Il s'agit de l'ensemble de données principal. Pour chaque commande, vous pouvez trouver toutes les autres informations.

`order_id` : identifiant unique de la commande.  
`customer_id` : clé de l'ensemble de données sur les clients. Chaque commande a un numéro de client unique.  
`order_status` : référence au statut de la commande (livrée, expédiée, etc.).  
`order_purchase_timestamp` : indique l'horodatage de l'achat.  
`order_approved_at` : indique l'horodatage de l'approbation du paiement.  
`order_delivered_carrier_date` : indique l'horodatage de la commande, c'est-à-dire la date à laquelle elle a été remise au partenaire logistique.
order_delivered_customer_date : indique la date réelle de livraison de la commande au client.  
`order_estimated_delivery_date` : indique la date de livraison estimée qui a été communiquée au client au moment de l'achat.  



# `products_dataset`

Ce jeu de données comprend des données sur les produits vendus par Olist.

`product_id` : identifiant unique du produit.  
`product_category_name` : catégorie racine du produit, en portugais.   
`product_name_length` : nombre de caractères extraits du nom du produit.  
`product_description_length` : nombre de caractères extraits de la description du produit.  
`product_photos_qty` : nombre de photos publiées du produit.  
`product_weight_g` : poids du produit mesuré en grammes.  
`product_length_cm` : longueur du produit mesurée en centimètres.  
`product_height_cm` : hauteur du produit mesurée en centimètres.  
`product_width_cm` : largeur du produit mesurée en centimètres.   


# `sellers_dataset`

Ce jeu de données comprend des données sur les vendeurs qui ont exécuté les commandes passées sur Olist. Utilisez-le pour trouver l'emplacement du vendeur et pour identifier le vendeur qui a exécuté chaque produit.

`seller_id` : identifiant unique du vendeur.  
`seller_zip_code_prefix` : 5 premiers chiffres du code postal du vendeur.  
`seller_city` : nom de la ville du vendeur.  
`seller_state` : État du vendeur.  
`product_category_name_translation`: Traduit le nom de la catégorie du produit en anglais.   
`product_category_name` : nom de la catégorie en portugais.  
`product_category_name_english` : nom de la catégorie en anglais
