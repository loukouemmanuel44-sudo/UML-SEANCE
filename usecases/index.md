1. LES ACTEURS

 Les acteurs du système hôtelier:

Client — Humain
Le client utilise le système pour consulter les disponibilités des chambres, effectuer une réservation, annuler une réservation si nécessaire et régler les frais liés à son séjour.

Agent de voyage — Humain
L’agent de voyage utilise le système pour consulter les disponibilités et effectuer une réservation au nom et pour le compte d’un client.

Receptionniste — Humain
Le gérant utilise le système pour administrer les différents hôtels, les catégories de chambres, les chambres et les tarifs. Il peut également consulter les informations concernant les arrivées et le taux d’occupation.

Service de paiement externe — Système externe
Le service de paiement externe intervient lors des paiements afin de traiter et de confirmer les transactions effectuées par les clients.

Temps — Temps
Le temps permet de déclencher certaines actions automatiques du système, notamment l’annulation à J-8 des réservations qui n’ont pas été confirmées.

Question: L'agent de voyage est-il le même acteur que le client, un acteur distinct, ou une
généralisation du client ? Justifiez en deux lignes. 

Reponse: L'agent de voyage est un acteur distinct du client.
 Il réserve une chambre pour le compte du client et possède donc un rôle différent dans le système.

2.Le diagramme de cas d'utilisation


@startuml
left to right direction

actor Client
actor "Agent de voyage"
actor Réceptionniste
actor "Service de paiement"
actor Temps

rectangle "Système de gestion de l'hôtel" {
    usecase "Consulter disponibilités" as UC1
    usecase "Réserver une chambre" as UC2
    usecase "Annuler une réservation" as UC3
    usecase "Payer les arrhes" as UC4
    usecase "Réserver pour le client" as UC5
    usecase "Payer les arrhes pour le client" as UC6
    usecase "Enregistrer l’arrivée" as UC7
    usecase "Saisir les consommations" as UC8
    usecase "Facturer le départ" as UC9
    usecase "Encaisser le paiement" as UC10
    usecase "Valider le paiement" as UC11
    usecase "Annulation automatique J-8" as UC12
    usecase "Arrivées du jour" as UC13
}

Client --> UC1
Client --> UC2
Client --> UC3
Client --> UC4

"Agent de voyage" --> UC5
"Agent de voyage" --> UC6

Réceptionniste --> UC7
Réceptionniste --> UC8
Réceptionniste --> UC9
Réceptionniste --> UC10

"Service de paiement" --> UC11

Temps --> UC12
Temps --> UC13

UC2 --> UC4 : <<include>>
UC9 --> UC10 : <<include>>
UC10 --> UC11 : <<include>>

UC2 --> UC12 : <<extend>>
UC3 --> UC4 : <<extend>>
@enduml

3.  Deux fiches textuelles

Fiche 1 — Réserver une chambre

Acteur principal : Client ou agent de voyage.

Précondition :

Les dates du séjour sont connues.
Le nombre de personnes est connu.
Une chambre adaptée doit être disponible.

Scénario nominal :

1.Le client indique ses dates de séjour.
2.Il indique le nombre d’occupants.
3.Le système vérifie les chambres disponibles.
4.Le système propose les chambres adaptées.
5.Le client choisit une chambre.
6.Le système enregistre la réservation.
7.Si nécessaire, le système demande les arrhes.
8.Le système confirme la réservation.

Alternatives :

À l’étape 3 : Si aucune chambre n’est disponible → le système informe le client.
À l’étape 4 : Si aucune chambre n’est adaptée au nombre d’occupants → le système propose une autre chambre.
À l’étape 7 : Si les arrhes ne sont pas versées → la réservation reste non confirmée.

Postcondition :
La réservation est enregistrée avec la chambre, les dates et le nombre d’occupants.

Fiche 2 — Facturer le départ

Acteur principal : Client.

Précondition :

Le client a terminé son séjour.
Son arrivée a été enregistrée.
Ses consommations ont été enregistrées.

Scénario nominal :

1.Le client demande sa facture.
2.Le système récupère les informations du séjour.
3.Le système calcule le prix de la chambre.
4.Le système ajoute les consommations.
5.Le système ajoute la taxe de séjour.
6.Le système affiche le montant total.
7.Le client effectue le paiement.
8.Le service de paiement confirme le paiement.
9.Le système valide la facture et termine le séjour.

Alternatives :

À l’étape 4 : aucune consommation → aucun montant supplémentaire n’est ajouté.
À l’étape 7 : le paiement est refusé → le système demande un autre moyen de paiement.
À l’étape 8 : le service de paiement ne confirme pas le paiement → la facture reste en attente.
