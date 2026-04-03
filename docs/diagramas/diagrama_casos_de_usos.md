# Diagramas de Casos de Uso - SIRC

Estes diagramas representam as interações entre os atores e as funcionalidades do Sistema Integrado de Recuperação de Crédito.

---

## 1. Diagrama Geral (Visão do Sistema)

Este diagrama apresenta uma visão macro de como todos os atores interagem com os módulos principais do sistema.

```mermaid
useCaseDiagram
    actor "Devedor" as D
    actor "Operador Call Center" as OCC
    actor "Cobrador Externo" as CE
    actor "Sistema de Cartório" as SC <<System>>
    actor "Empresa Contratante" as EC

    package "SIRC - Sistema de Cobrança" {
        usecase "UC01: Realizar Negociação" as UC01
        usecase "UC02: Autoatendimento (Portal)" as UC02
        usecase "UC03: Gerar Fila de Discagem" as UC03
        usecase "UC04: Escalar Cobrança Externa" as UC04
        usecase "UC05: Efetuar Protesto" as UC05
        usecase "UC06: Realizar Repasse Financeiro" as UC06
    }

    D --> UC01
    D --> UC02
    OCC --> UC01
    OCC --> UC03
    CE --> UC04
    UC05 --> SC
    UC06 --> EC
