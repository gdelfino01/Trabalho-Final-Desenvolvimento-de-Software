*** Imagem Diagrama de Casos de USO ***

![`Diagrama de casos de Uso`](diagramaDeCasosDeUso.png)

*** Código Diagrama de Casos de USO plantUML ***

````


@startuml CasosDeUsoHappyFit
left to right direction

' Ator genérico com casos comuns '
actor "Usuário" as Usuario #LightBlue

' Atores especializados herdam de Usuário '
actor "Nutricionista" as N
actor "Cliente (Orientação)" as C
actor "Usuário Comum" as U
actor "Administrador" as A

Usuario <|-- N
Usuario <|-- C
Usuario <|-- U
Usuario <|-- A

' Casos de uso genéricos para todos os usuários '
usecase "UC001: Registrar-se" as UC001
usecase "UC002: Login" as UC002
Usuario --> UC001
Usuario --> UC002

' Casos de uso específicos de Nutricionista '
usecase "UC003: Cadastrar Cliente" as UC003
usecase "UC004: Criar Dieta" as UC004
usecase "UC005: Editar Dieta" as UC005
usecase "UC006: Excluir Dieta" as UC006
usecase "UC009: Gerenciar Receitas" as UC009
usecase "UC010: Compartilhar Receita" as UC010
N --> UC003
N --> UC004
N --> UC005
N --> UC006
N --> UC009
N --> UC010

' Casos de uso específicos de Cliente (Orientação) '
usecase "UC007: Visualizar Dieta" as UC007
usecase "UC008: Registrar Refeição" as UC008
C --> UC007
C --> UC008
C --> UC010

' Casos de uso específicos de Usuário Comum '
usecase "UC011: Definir Metas Nutricionais" as UC011
usecase "UC012: Salvar Receita Favorita" as UC012
usecase "UC015: Criar Plano Autônomo" as UC015
U --> UC007
U --> UC008
U --> UC011
U --> UC012
U --> UC015

' Casos de uso específicos de Administrador '
usecase "UC013: Gerenciar Usuários" as UC013
usecase "UC014: Monitorar Logs" as UC014
A --> UC013
A --> UC014

' Links invisíveis para layout quadrado '
Usuario -[hidden]-> N
N -[hidden]-> C
C -[hidden]-> A
A -[hidden]-> U
@enduml

````
