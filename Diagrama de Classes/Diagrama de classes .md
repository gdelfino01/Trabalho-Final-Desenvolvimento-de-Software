*** Imagem Diagrama de Componentes ***

![`Diagrama de Classes`](./diagrama%20de%20classes.png)

*** Código Diagrama de Componentes plantUML ***

````
@startuml ClassesHappyFit

' Definição das classes principais '
class Usuario {
  +id: Integer
  +nome: String
  +email: String
  +senha: String
  +login(): boolean
  +registrar(): Usuario
}

class Nutricionista {
  +criarDieta(d: Dieta): Dieta
  +editarDieta(d: Dieta): Dieta
  +removerDieta(dietaId: Integer): void
  +gerenciarReceitas(): List<Receita>
}

class Cliente {
  +visualizarDieta(dietaId: Integer): Dieta
  +registrarRefeicao(r: Refeicao): Refeicao
  +enviarFeedback(texto: String): void
}

class Administrador {
  +gerenciarUsuario(u: Usuario): void
  +monitorarLogs(): List<Log>
}

class Dieta {
  +id: Integer
  +nome: String
  +descricao: String
  +status: DietaStatus
}

class Refeicao {
  +id: Integer
  +dataHora: DateTime
}

class ItemRefeicao {
  +quantidade: Double
  +unidade: String
}

class Receita {
  +id: Integer
  +nome: String
  +instrucoes: String
}

class Ingrediente {
  +nome: String
  +calorias: Double
}

' Classe de Log com referência ao usuário que gerou a ação '
class Log {
  +timestamp: DateTime
  +acao: String
  +usuario: Usuario
}


' Relações de herança '
Usuario <|-- Nutricionista
Usuario <|-- Cliente
Usuario <|-- Administrador

' Relações de associação principal '
Nutricionista "1" --> "*" Dieta
Cliente "1" --> "*" Refeicao
Dieta "1" --> "*" Refeicao
Dieta "1" --> "*" Receita
Refeicao "1" --> "*" ItemRefeicao
Receita "1" --> "*" Ingrediente

' Associação de logs: cada log é gerado por um usuário e pode ser monitorado por administrador '
Usuario "1" <-- "*" Log : gera
Administrador "1" --> "*" Log : monitora

@enduml

````
