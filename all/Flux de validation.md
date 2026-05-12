```mermaid
flowchart LR

    start((Start)) --> A
    A(fa:fa-user DSIN/SERU) --> B[Exécution de la procédure]

    subgraph Exécution de la migration Windows 11 sur les postes de caisse ELISATH
        B --> C{Réussie ?}
    end

    subgraph Validation
        C -->|Oui| D["Validation opérationnelle<br/><br/>
                    · Lancement d’Elisath<br/>
                    · Ouverture de caisse<br/>
                    · Réalisation d’une opération de caisse<br/>
                    · Lecture et encodage d’un badge"]
        D --> Val{Réussie ?}
        Val -- Oui --> Prev (Prévenir DSI/AM| 
        J[Prévenir le RAF]
    end

    J --> fin((Fin))

    subgraph Investigation
        C -->|Non| E[Prévenir DSIN/AM]
        E --> F[Prévenir le RAF]
        E --> G[Investigation avec le support de l'éditeur si nécessaire]
        G --> H[Modification de la procédure]
        H --> I{Réussie ?}
        I -->|Oui| F
        I -->|Non| E
    end

    F -->|Planification de la nouvelle intervention| A

    %% --- STYLES ---
    classDef StartEndPoint fill:#c40466,stroke:#000,color:#fff,stroke-width:2px,font-size:16px,font-weight:bold;
    classDef decision      fill:#ffd54f,stroke:#f57f17,color:#000,stroke-width:2px;
    classDef error         fill:#e53935,stroke:#b71c1c,color:#fff,stroke-width:2px;

    %% --- AFFECTATION DES CLASSES ---
    class start,fin StartEndPoint;
    class C,I decision;
    class E,F,J error;

    %% --- “CEINTURE + BRETELLES” (force le style sur les 2 nœuds) ---
    style start font-size:32px,font-weight:bold
    style fin   font-size:32px,font-weight:bold

    %% --- Coide couleur ---
    %% Bleu marine #000080 un peu plus doux
    %% Midnight blue #191970 bleu nuit profond 
    %% Bleu foncé intense #080F70 plus “design”, légèrement grisé 
    %% Bleu foncé moderne #111184 un peu plus lumineux
    %% Orange #ffd54f
    %% Rouge #e53935
    %% Rose CAPI #c40466

```