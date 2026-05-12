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

        Val -->|Oui| PrevDSI(fa:fa-user Prévenir DSI/AM)
       
        PrevDSI --> fin((Fin))
        PrevDSI  --> PrevRAF(fa:fa-user Prévenir le RAF)
    end
    Val --> |Non| E
    subgraph Investigation
        C -->|Non| E(fa:fa-user Prévenir DSI/AM)
        E --> F(fa:fa-user Prévenir le RAF)
        E --> G[Investigation avec le support de l'éditeur si nécessaire]
        G --> H[Modification de la procédure]
        H --> I{Réussie ?}
        I -->|Oui| F
        I -->|Non| E
    end

    F -->|Planification de la nouvelle intervention| A

    %% --- STYLES ---
    classDef StartEndPoint fill:#c40466,stroke:#000,color:#fff,stroke-width:2px,font-size:32px,font-weight:bold;
    classDef Decision      fill:#ffd54f,stroke:#f57f17,color:#000,stroke-width:2px,font-size:24px,font-weight:bold;
    classDef Action      fill:#ffd54f,stroke:#f57f17,color:#000,stroke-width:2px,font-size:24px,font-weight:bold;
    classDef Error         fill:#e53935,stroke:#b71c1c,color:#fff,stroke-width:2px,font-size:24px,font-weight:bold;

    %% --- AFFECTATION DES CLASSES ---
    class start,fin StartEndPoint;
    class C,I,Val Decision;
    class E,F,PrevDSI,PrevRAF Error;
    class D 
    %% --- “CEINTURE + BRETELLES” (force le style sur les 2 nœuds) ---
    %%style start font-size:32px,font-weight:bold
    %%style fin   font-size:32px,font-weight:bold

    %% --- Codes couleur (commentaires) ---
    %% Bleu marine #000080
    %% Midnight blue #191970
    %% Bleu foncé intense #080F70
    %% Bleu foncé moderne #111184
    %% Orange #ffd54f
    %% Rouge #e53935
    %% Rose CAPI #c40466
```