*** Imagem Diagrama de Sequência - Registro ***


![`Diagrama de sequência Registro`](./diagramaDeSequenciaRegistro.png)



*** Código Diagrama de Sequência - Registro plantUML ***

````

@startuml Seq_RegistrarSe
actor Cliente
participant Sistema
participant BancoDeDados as DB

Cliente -> Sistema : UC001: registrarUsuario(dadosCadastro)
activate Sistema
Sistema -> DB : inserirUsuario(dadosCadastro)
activate DB
DB --> Sistema : confirmaInsercao(idUsuario)
deactivate DB
Sistema --> Cliente : retornaSucesso(codigo)
deactivate Sistema
@enduml


````




*** Imagem Diagrama de Sequência - Login ***


![`Diagrama de sequência Login`](./diagramaDeSequenciaLogin.png)



*** Código Diagrama de Sequência - Login plantUML ***

````

@startuml Seq_Login
actor Usuario
participant Sistema
participant BancoDeDados as DB

Usuario -> Sistema : UC002: autenticar(email, senha)
activate Sistema
Sistema -> DB : buscarUsuario(email)
activate DB
DB --> Sistema : userRecord
deactivate DB
alt credenciais válidas
    Sistema --> Usuario : retornaToken(jwt)
else
    Sistema --> Usuario : retornaErro(401)
end
deactivate Sistema
@enduml

````



*** Imagem Diagrama de Sequência - Dieta ***


![`Diagrama de sequência Dieta`](./diagramaDeSequenciaDieta.png)



*** Código Diagrama de Sequência - Dieta plantUML ***

````

@startuml Seq_CriarDieta
actor Nutricionista
participant Sistema
participant BancoDeDados as DB

Nutricionista -> Sistema : UC004: criarDieta(dadosDieta)
activate Sistema
Sistema -> DB : salvarDieta(dadosDieta)
activate DB
DB --> Sistema : confirmaSalvamento(idDieta)
deactivate DB
Sistema --> Nutricionista : retornaDieta(idDieta)
deactivate Sistema
@enduml


````



*** Imagem Diagrama de Refeição - Dieta ***


![`Diagrama de sequência Dieta`](./diagramaDeSequenciaDieta.png)



*** Código Diagrama de Refeição - Dieta plantUML ***

````

@startuml Seq_CriarDieta
actor Nutricionista
participant Sistema
participant BancoDeDados as DB

Nutricionista -> Sistema : UC004: criarDieta(dadosDieta)
activate Sistema
Sistema -> DB : salvarDieta(dadosDieta)
activate DB
DB --> Sistema : confirmaSalvamento(idDieta)
deactivate DB
Sistema --> Nutricionista : retornaDieta(idDieta)
deactivate Sistema
@enduml


````