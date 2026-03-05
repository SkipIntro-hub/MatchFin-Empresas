# MatchFin Empresas On-Demand — Flujo de Experiencia

```mermaid
flowchart TD

classDef entrada   fill:#0a0a0a,stroke:#1be28c,stroke-width:2px,color:#1be28c
classDef tenant    fill:#0d9960,stroke:#1be28c,stroke-width:2px,color:#ffffff
classDef accion    fill:#ededed,stroke:#5a6e73,stroke-width:1px,color:#000000
classDef decision  fill:#1be28c,stroke:#0d9960,stroke-width:2px,color:#000000
classDef express   fill:#5a6e73,stroke:#ededed,stroke-width:1px,color:#ffffff
classDef completo  fill:#0d9960,stroke:#1be28c,stroke-width:2px,color:#ffffff
classDef resultado fill:#1a1a1a,stroke:#5a6e73,stroke-width:1px,color:#ededed
classDef monitoreo fill:#0a0a0a,stroke:#1be28c,stroke-width:2px,color:#1be28c
classDef alerta    fill:#401e24,stroke:#6d8589,stroke-width:1px,color:#ededed
classDef pack      fill:#1be28c,stroke:#0d9960,stroke-width:2px,color:#000000

    A([LEAD - Campana digital o gestion comercial]):::entrada

    A --> B[Landing - Login con Google]:::accion
    B --> C[Acepta Terminos y Condiciones]:::accion
    C --> D[TENANT PRIVADO ACTIVO - Acceso permanente - Sin costo de alta - Historial no vence]:::tenant

    D --> E[DASHBOARD - Saldo creditos ANALISIS - Saldo creditos MONITOREO - CUITs analizados y monitoreados]:::resultado

    E --> F{Tiene creditos?}:::decision

    F -- NO --> G[COMPRA DE PACK - Self-service - Pago online - Precio USD - Cobro ARS tipo BNA del dia]:::pack

    G --> H{Que pack?}:::decision

    H -- Analisis --> H1[Starter 10 analisis / Growth 50 analisis / Scale 150 analisis / Custom a negociar]:::accion
    H -- Monitoreo --> H2[Watch 5 CUITs / Watch 20 CUITs / Watch 50 CUITs]:::accion

    H1 & H2 --> E
    F -- SI --> I

    I[INGRESA CUIT a analizar]:::accion

    I --> J{Tipo de analisis?}:::decision

    J -- Express 0.5 creditos --> K[ANALISIS EXPRESS - NOSIS + AFIP + MAV - Score preliminar + alertas - Sin balance requerido]:::express
    J -- Completo 1 credito --> L[ANALISIS COMPLETO - NOSIS + AFIP + MAV - BeanCounter OCR balance 100+ ratios - Score QUANT - Informe IA narrativo]:::completo

    K --> M[RESULTADO GUARDADO - Registro congelado con fecha - Disponible en tenant - Descargable PDF - Se debita credito del pack]:::resultado
    L --> M

    M --> N{Activar MONITOREO sobre este CUIT?}:::decision

    N -- NO --> O[Continuar sin monitoreo - CUIT queda en historial del tenant]:::accion
    N -- SI --> P{Tiene creditos de monitoreo?}:::decision

    P -- NO --> G
    P -- SI --> Q

    Q[MONITOREO ACTIVADO - Cada 15 dias NOSIS + AFIP + MAV - No aplica QUANT ni balance - Backup situacion mensual]:::monitoreo

    Q --> R{Cambio detectado?}:::decision

    R -- NO --> Q
    R -- SI --> S[ALERTA ENVIADA - Notificacion al usuario]:::alerta

    S --> T{Que hacer con el CUIT?}:::decision

    T -- Actualizar analisis --> I
    T -- Pausar monitoreo --> U[MONITOREO PAUSADO - No consume creditos - Reactivable en cualquier momento]:::resultado
    T -- Mantener monitoreo --> Q

    O --> V{Siguiente accion?}:::decision
    U --> V

    V -- Nuevo CUIT --> I
    V -- Actualizar analisis --> I
    V -- Recargar creditos --> G
    V -- Activar monitoreo --> P
```
