---
title: MatchFin Empresas On-Demand — Flujo de Experiencia
---
flowchart TD

%% ══ ESTILOS ══
classDef entrada    fill:#0a0a0a,stroke:#1be28c,stroke-width:2px,color:#1be28c
classDef tenant     fill:#0d9960,stroke:#0d9960,stroke-width:1px,color:#ffffff
classDef accion     fill:#ededed,stroke:#5a6e73,stroke-width:1px,color:#000000
classDef decision   fill:#1be28c,stroke:#0d9960,stroke-width:2px,color:#000000
classDef express    fill:#5a6e73,stroke:#5a6e73,stroke-width:1px,color:#ffffff
classDef completo   fill:#0d9960,stroke:#1be28c,stroke-width:2px,color:#ffffff
classDef resultado  fill:#0a0a0a,stroke:#5a6e73,stroke-width:1px,color:#ededed
classDef monitoreo  fill:#0a0a0a,stroke:#1be28c,stroke-width:2px,color:#1be28c
classDef alerta     fill:#401e24,stroke:#401e24,stroke-width:1px,color:#ededed
classDef pack       fill:#1be28c,stroke:#0d9960,stroke-width:2px,color:#000000

%% ══════════════════════════════════════
%% BLOQUE 1 · INGRESO
%% ══════════════════════════════════════

    A(["`**LEAD**
    Campaña digital
    o gestión comercial`"]):::entrada

    A --> B["Landing / Login con Google"]:::accion
    B --> C["Acepta Términos y Condiciones"]:::accion
    C --> D["`**TENANT PRIVADO ACTIVO**
    Acceso permanente · Sin costo de alta
    Historial no vence`"]:::tenant

%% ══════════════════════════════════════
%% BLOQUE 2 · DASHBOARD + COMPRA
%% ══════════════════════════════════════

    D --> E["`**DASHBOARD**
    Saldo créditos ANÁLISIS
    Saldo créditos MONITOREO
    CUITs analizados / monitoreados`"]:::resultado

    E --> F{"`¿Tiene
    créditos?`"}:::decision

    F -- NO --> G["`**COMPRA DE PACK**
    Self-service · Pago online
    Precio en USD · Cobro ARS
    al tipo vendedor BNA del día`"]:::pack

    G --> H{"`¿Qué
    pack?`"}:::decision

    H -- "Análisis" --> H1["`Starter — 10 análisis
    Growth — 50 análisis ★
    Scale — 150 análisis
    Custom — a negociar`"]:::accion

    H -- "Monitoreo" --> H2["`Watch 5 — 5 CUITs
    Watch 20 — 20 CUITs
    Watch 50 — 50 CUITs`"]:::accion

    H1 & H2 --> E
    F -- SÍ --> I

%% ══════════════════════════════════════
%% BLOQUE 3 · ACTIVACIÓN ANÁLISIS
%% ══════════════════════════════════════

    I["`**INGRESA CUIT**
    a analizar`"]:::accion

    I --> J{"`¿Tipo de
    análisis?`"}:::decision

    J -- "Express · 0.5 créditos" --> K["`**ANÁLISIS EXPRESS**
    NOSIS + AFIP + MAV
    Score preliminar + alertas
    Sin balance requerido`"]:::express

    J -- "Completo · 1 crédito" --> L["`**ANÁLISIS COMPLETO**
    NOSIS + AFIP + MAV
    BeanCounter: OCR balance → 100+ ratios
    Score QUANT
    Informe IA narrativo`"]:::completo

    K --> M["`**RESULTADO**
    Registro congelado con fecha
    Disponible en tenant · Descargable PDF
    Se debita crédito del pack`"]:::resultado

    L --> M

%% ══════════════════════════════════════
%% BLOQUE 4 · DECISIÓN MONITOREO
%% ══════════════════════════════════════

    M --> N{"`¿Activar
    MONITOREO
    sobre este CUIT?`"}:::decision

    N -- NO --> O["`Continuar sin monitoreo
    CUIT queda en historial del tenant`"]:::accion

    N -- SÍ --> P{"`¿Tiene créditos
    de monitoreo?`"}:::decision

    P -- NO --> G
    P -- SÍ --> Q

%% ══════════════════════════════════════
%% BLOQUE 5 · MONITOREO ACTIVO
%% ══════════════════════════════════════

    Q["`**MONITOREO ACTIVADO**
    Cada 15 días: NOSIS + AFIP + MAV
    No aplica QUANT ni balance
    Backup situación mensual`"]:::monitoreo

    Q --> R{"`¿Cambio
    detectado?`"}:::decision

    R -- SÍ --> S["`**ALERTA enviada**
    Notificación al usuario`"]:::alerta
    R -- NO --> Q

    S --> T{"`¿Qué hacer
    con el CUIT?`"}:::decision

    T -- "Actualizar análisis" --> I
    T -- "Pausar monitoreo" --> U["`MONITOREO PAUSADO
    No consume créditos
    Se puede reactivar`"]:::resultado
    T -- "Mantener monitoreo" --> Q

%% ══════════════════════════════════════
%% BLOQUE 6 · RECURRENCIA
%% ══════════════════════════════════════

    O --> V{"`¿Siguiente
    acción?`"}:::decision
    U --> V

    V -- "Nuevo CUIT" --> I
    V -- "Actualizar análisis" --> I
    V -- "Recargar créditos" --> G
    V -- "Nuevo monitoreo" --> P
