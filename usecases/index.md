usecases/index.md

```mermaid
usecaseDiagram
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

