# Fintegrity: Plataforma de Validación de Solvencia mediante IA Multimodal

> **Estado del Proyecto:** Postulación Semilla Inicia 2026  
> **Categoría:** Deep Tech / Fintech / AI  
> **Stack:** Python (PyTorch), Open Finance APIs, React.

---

## 1. Resumen Ejecutivo
**Fintegrity** es una infraestructura de auditoría algorítmica que reemplaza el análisis financiero manual por agentes de **Deep Reinforcement Learning (Deep RL)**. Utilizando el marco de la **Ley Fintech 21.521 (Chile)**, conectamos datos bancarios inmutables con análisis conductual del equipo fundador para emitir un "Sello de Confianza" dinámico en tiempo real.

---

## 2. Flujo de Usuario
El siguiente diagrama describe la interacción desde que la Startup conecta sus cuentas hasta que el Inversionista recibe el análisis de riesgo.

```mermaid
graph TD
    %% Nodos de Usuario
    User([Founder Startup]) -->|1. Login & Auth| Frontend[Plataforma Web Fintegrity]
    VC([Inversionista / VC]) -->|5. Acceso a Dashboard| Dashboard[Panel de Control VC]

    %% Flujo de Datos
    Frontend -->|2. Conexión OAuth 2.1| OpenFin{Gateway Open Finance}
    OpenFin -->|Extracción Inmutable| BankAPI["APIs Bancarias (Ley Fintech)"]
    
    Frontend -->|3. Upload Video Pitch & Founder Interview| VideoServ[Servidor de Medios]
    
    %% Motor de IA
    subgraph "CORE RL AGENT"
        BankAPI -->|Series Temporales| DataPrep("Anonimización & Limpieza")
        VideoServ -->|Vectores Conductuales| NLP_Vision("Modelo NLP + Vision")
        
        DataPrep & NLP_Vision --> Fusion[Fusión Multimodal]
        Fusion --> RL_Agent{{Agente Deep RL}}
        
        RL_Agent -->|10k Simulaciones Monte Carlo| RiskScore("Cálculo de Probabilidad de Quiebra")
    end
    
    %% Salida
    RiskScore -->|4. Generación de Certificado| Blockchain[Sello de Confianza Dinámico]
    Blockchain --> Dashboard
    RiskScore --> Dashboard
