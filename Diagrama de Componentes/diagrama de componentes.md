*** Imagem Diagrama de Componentes ***

![`Diagrama de Componentes`](./diagrama%20de%20componentes.png)

*** Código Diagrama de Componentes plantUML ***

````
@startuml ArquiteturaHappyFit

package "Frontend" {
  component "Web App React" as WebUI
}

package "Backend - API REST" {
  component "API Gateway (Node.js/Express)" as APIGW
  component "Auth Service" as Auth
  component "User Service" as UserSvc
  component "Diet Service" as DietSvc
  component "Recipe Service" as RecipeSvc
  component "Notification Service" as NotifSvc
}

database "Banco de Dados PostgreSQL" as DB

component "Serviço de E-mail / Push Externo" as ExternalNotif <<external>>

' Fluxo de chamadas internas '
WebUI --> APIGW : chamadas HTTP/HTTPS
APIGW --> Auth : JWT authentication
APIGW --> UserSvc : gerenciar usuários
APIGW --> DietSvc : CRUD de dietas
APIGW --> RecipeSvc : CRUD de receitas
APIGW --> NotifSvc : enviar requisição de notificação

' Persistência de dados '
Auth --> DB : valida e armazena credenciais
UserSvc --> DB : operações de usuário
DietSvc --> DB : operações de dieta
RecipeSvc --> DB : operações de receita
NotifSvc --> DB : leitura/escrita de registros de notificação

' Integração externa '
NotifSvc --> ExternalNotif : enviar notificação
@enduml


````
