# Diagrama de Bucle Causal - Cuenca del Piray Guazú

Aquí está el diagrama que ilustra las dinámicas de la cuenca:

```mermaid
%% Pega TU código Mermaid EXACTAMENTE AQUÍ dentro de este bloque
graph TD
    subgraph Factores de Degradación
        Def[Deforestación Margen Arroyo]
        AgroQ[Uso de Agroquímicos]
        IndUrb[Actividad Industrial/Urbana]
        DescEff[Descarga Efluentes s/Tratar]
    end

    subgraph Estado del Sistema
        CobVeg[Cobertura Vegetal Ribereña]
        Ero[Erosión del Suelo]
        Sed[Sedimentos en Arroyo]
        Qual[Calidad del Agua]
        Caudal[Caudal del Arroyo] --|- Dilución|--> ConcentCont[Concentración Contaminantes]
        ConcentCont --"-"--> Qual
    end

    subgraph Impactos y Respuestas
        Biodiv[Biodiversidad Acuática/Ribereña]
        Conciencia[Conciencia Comunitaria/Preocupación]
        Reg[Regulaciones Ambientales]
        Cumpl[Cumplimiento/Fiscalización]
        RefProg[Programas de Reforestación]
        TratEff[Inversión en Tratamiento Efluentes]
    end

    %% Relaciones y Bucles

    %% Bucle R1: Deforestación y Erosión (Refuerzo Negativo)
    Def --"-"--> CobVeg;
    CobVeg --"-"--> Ero;
    Ero --"+"--> Sed;
    Sed --"-"--> Qual;
    Sed --"-"--> Biodiv;

    %% Influencias sobre Calidad del Agua
    AgroQ --"-"--> Qual;
    IndUrb --"+"--> DescEff;
    DescEff --"-"--> Qual;
    CobVeg --|+ Filtro|--> Qual; % Más cobertura mejora calidad

    %% Bucle B1: Respuesta a la Contaminación (Equilibrio)
    Qual --"-"--> Conciencia; % Peor calidad -> Más conciencia
    Conciencia --"+"--> Reg;
    Conciencia --"+"--> TratEff; % Presión para tratar efluentes
    Reg --"+"--> Cumpl;
    Cumpl --"-"--> DescEff;
    Cumpl --"-"--> AgroQ; % Regulaciones pueden limitar agroquímicos
    TratEff --"-"--> DescEff; % Más tratamiento -> Menos descarga sin tratar

    %% Bucle B2: Respuesta de Reforestación (Equilibrio con Retraso)
    Ero --"+"--> Conciencia; % Erosión visible -> Más conciencia
    CobVeg --"-"--> Conciencia; % Menos cobertura -> Más conciencia
    Conciencia --"+"--> RefProg;
    RefProg --|+ {RETRASO}|--> CobVeg; % Reforestación restaura cobertura (tarda tiempo)

    %% Otros Impactos
    Qual --"-"--> Biodiv;
    CobVeg --"+"--> Biodiv;

    %% Estilos (Opcional, para resaltar nodos clave)
    style Qual fill:#f9d,stroke:#333,stroke-width:2px
    style Conciencia fill:#ccf,stroke:#333,stroke-width:2px
    style Def fill:#fec,stroke:#333,stroke-width:2px
