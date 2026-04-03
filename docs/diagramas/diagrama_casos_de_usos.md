useCaseDiagram
    %% Definição dos Atores
    actor "Operador de Call Center" as OCC
    actor "Devedor" as D
    actor "Cobrador Externo" as CE
    actor "Sistema de Cartório" as SC <<System>>
    actor "Sistema (Automático)" as S <<System>>

    package "SIRC - Sistema de Cobrança" {
        usecase "UC01: Realizar Negociação\n(Via Call Center)" as UC01
        usecase "UC02: Autoatendimento\n(Portal do Devedor)" as UC02
        usecase "UC03: Acionar Cobrança Externa" as UC03
        usecase "UC04: Automação de Protesto" as UC04
        
        %% Relações Internas
        UC01 ..> UC03 : <<extend>> (Recusa)
        UC03 ..> UC04 : <<extend>> (Insucesso)
    }

    %% Relacionamentos Atores -> Casos de Uso
    OCC --> UC01
    D --> UC01
    D --> UC02
    S --> UC03
    CE --> UC03
    S --> UC04
    UC04 --> SC
