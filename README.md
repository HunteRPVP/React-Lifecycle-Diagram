# React-Lifecycle-Diagram

```plantuml
@startuml
skinparam rectangle {
RoundCorner 20
shadowing false
}

skinparam linetype polyline
skinparam linetype ortho
skinparam arrowThickness 4
skinparam ArrowColor LightSkyBlue

rectangle Монтирование {

rectangle "constructor(props)" as con
rectangle "static getDerivedStateFromProps(props, state)" as gdsfp1 #palegreen
rectangle "componentWillMount()" as cwm #pink;line.dashed
rectangle "render()" as ren #lightblue
rectangle "componentDidMount()" as cdm

con --|> gdsfp1
gdsfp1 ----|> cwm
cwm --|> ren
ren ---|> cdm
}

rectangle Обновление {

rectangle "this.props" as props #transparent;line:transparent
rectangle "setState()" as state #transparent;line:transparent
rectangle "forceUpdate()" as fu #transparent;line:transparent
rectangle " static getDerivedStateFromProps(props, state) " as gdsfp #palegreen
rectangle "componentWillReceiveProps(nextProps)" as cwrp #pink;line.dashed
rectangle "shouldComponentUpdate(nextProps, nextState)" as scu
rectangle "❌    " as cross #transparent;line:transparent;text:red
rectangle "componentWillUpdate(nextProps, nextState)" as cwu #pink;line.dashed
rectangle " render() " as r #lightblue
rectangle "getSnapshotBeforeUpdate(prevProps, prevState)" as gsbu
rectangle "componentDidUpdate(prevProps, prevState, snapshot)" as cdu

props -D-|> gdsfp
state -D-|> gdsfp
fu -D-|> gdsfp
gdsfp --|> cwrp
cwrp --|> scu
scu -U---|> cross : "false         "
scu --|> cwu : " true"
cwu --|> r
r --|> gsbu
gsbu --|> cdu
}

rectangle Размонтирование {

rectangle empty #transparent;line:transparent;text:transparent
rectangle "componentWillUnmount()" as cwum

empty --------|> cwum
}

rectangle "Обработка ошибок" {

rectangle "empty  " as em #transparent;line:transparent;text:transparent

rectangle "static getDerivedStateFromError(error)" as gdsfe
rectangle "componentDidCatch(error, info)" as cdc

em --|> gdsfe
gdsfe -------|> cdc
}

rectangle "Описание методов" {

rectangle "constructor(props)\nконструктор компонента React" as conCom
rectangle "static getDerivedStateFromProps(props, state)\nвызывается непосредственно\nперед вызовом метода\nrender, как при начальном монтировании,так\nи при последующих обновлениях." as gdsfpCom #palegreen
rectangle "componentWillMount()\nвызывается непосредственно\n перед монтированием." as cwmCom #pink;line.dashed
rectangle "render()\nединственный обязательный метод\n в классовом компоненте." as renCom #lightblue
rectangle "componentDidMount()\nвызывается сразу после\n монтирования (то есть, вставки\n компонента в DOM)." as cdmCom

rectangle "componentWillReceiveProps(nextProps)\nвызывается до того, как\n смонтированный компонент\n получит новые пропсы." as cwrpCom #pink;line.dashed
rectangle "Используйте shouldComponentUpdate(nextProps, nextState),\n чтобы указать необходимость следующего\n рендера на основе изменений\n состояния и пропсов." as scuCom
rectangle "componentWillUpdate(nextProps, nextState)\nвызывается непосредственно перед рендером\n при получении новых пропсов или состояния." as cwuCom #pink;line.dashed
rectangle "getSnapshotBeforeUpdate(prevProps, prevState)\nвызывается прямо перед\n этапом «фиксирования» (например, перед\n добавлением в DOM)." as gsbuCom
rectangle "componentDidUpdate(prevProps, prevState, snapshot)\nвызывается сразу после обновления." as cduCom

rectangle "componentWillUnmount()\nвызывается непосредственно перед\n размонтированием и удалением компонента." as cwumCom

rectangle "getDerivedStateFromError(error)\nметод жизненного цикла\n вызывается после возникновения\n ошибки у компонента-потомка." as gdsfeCom
rectangle "componentDidCatch(error, info)\nметод жизненного цикла\n вызывается после возникновения\n ошибки у компонента-потомка." as cdcCom

conCom -[hidden]-> gdsfpCom
gdsfpCom -[hidden]-> cwmCom
cwmCom -[hidden]-> renCom
renCom -[hidden]-> cdmCom
cdmCom -[hidden]-> cwrpCom
cwrpCom -[hidden]-> scuCom
scuCom -[hidden]-> cwuCom
cwuCom -[hidden]-> gsbuCom
gsbuCom -[hidden]-> cduCom
cduCom -[hidden]-> cwumCom
cwumCom -[hidden]-> gdsfeCom
gdsfeCom -[hidden]-> cdcCom

}

@enduml
```

![test](http://www.plantuml.com/plantuml/png/rLRDRjj64BxpAHRAnG4aeIrwIe0WZTsU6hHm6lJGzC28QuamjIIMP5oZ3U2VkcvXjxxsq1QzzwAwKIF_0tc2vIlqIVeDHvHNB6b9pga2H2vtTcQ_-MPsTXx6YQkJj1yuyRgl8bUxVQ5b9t5LDv3YQsSrJ9Mt76ebjNZl7IVkkLwuuQkkM7E3M3el7Kily9LCDYCfeZ3Of8ygMQYJNcW9NAt3ZSzwVcTToJWMxrkY3qYq70QX5X_xtLxoP7tpKP1Anxa6Q7unb-OYsp6ZR0kZOpCm5sPaXa1khMfqGXKdEkqaeLwAT1Z5Tnl2ZGMcxLMW8l4xeYkJ5Qdz5z9xWWdvaGxxdv8EQpP5JBDieEl5Qz6xuaxa1hAhfLJJc_QZK4cLVEu7mMFmc2oDjzteGyLNw_U9bRRdnZtfsPfQAa_gyMfyY3i1-VySpbTkiE9xK_QzlkF0Dz5gVVDWZD7X5wPeaY0u-FCAdUDMWaMa_NAAuz_Cds2Ls3qpmqf-avuVjtDwSW3vIDn9jAjYX188Sq_lMHDJlCiaPvhXCx_pQw-5kYEVHjwrWRLqVcsnKD35TTJd2Vggx4YOP4DAVfNaeo89T7Hp5iIzC0syvS8WkyXc61E6JDoOjqvgg__pww70ZpVJOJmZ8FSJMBkdfLVhpIm0S2czsIDH93QZqZLvtKK-A3U2_yaZYV0MqOsqV37UcORMpjtuULftCcvGHbZ7-nG79tKSJjxMokJiE9oGzWmopFxCdtoMAAmEFVYJOeA_Q3tbmyM1k2SQUVaKnQ_1YzX0IdA1SYKRi3IUrexcGUugFVWJa4kdzNVKmDVcV9wwAFjHiZb7MjWJzUcX-bCrBaKHuWrQunzxLwek3Iel03b0aRa4u5Cp41Xy3xIOCAUDKgbXavn0ihye-FdA_OTQuwAGzBokyxMbTzbDEZrUtHI-MWkBPEeG0HmcDf0_XSK6blo7Z2l4R7iIBmHo25OkpIiAOsFclVPCWK4A_NQsasrbk-QKjBCjGTCmTaL2gkAO7eXLwNQIuYf4fRdrROXjZxC3ynf_v1f11e0ZGLlHblZOmkWLeS82R4yN2fIkp90bWlN9IS9f-prufhXkDE44Z9yASmMb4LaVPFkOESiECMQrohmVDJ45JUmuAhGPbpdBSUrcFsK_G6aFkLU-xRAZRAzzNVX1q_mN_cs94HOpTMVPdBUBTWAOvkie00SceNrXxmXm9xdZsH52C81WI9oom0e5uJf64C3C0FhRHRIgacl8uB0nmCtVmDJmbVCqmFIk5JV0gUO62ak4M42Vpi5X4xXf1F4ni8wWMNaUuDtA9u_lZddrY5TdqTkznWCwm2AdyIzpMMGoSC2L2X-O-WgGqCW_pv2o-z3O4PoiM3w4X2pWkPqTj2TTnipaC3y311iz98hD2SLFBD1_DCcHVMXH3Xq8c81xd4hP8ISxIVRmfEI3mnmNKJg0GoA7R6sHjrWxfB2J0JoWmxwIfwFyZgD5t96Uv5IoNJoFE0smpYA5TDj5gmI_5krqRb_fxEDi-qRH1N2kI7PWsQdH9BZPNiaFU0RcHXK-5u5Fw-E-U9zLxpTGOUVpAHyf5Z_IWS8KbOStVsJV0kyfm9REwPipiKJHPGPW1XQQqvR059NaGL6GkVJPHvNxFxZxLYtWGgMdyfeeoaOEPNQVzBQPnEUajjbZbaPq6767sjnLrhv9slJBw6SqI71ZSa48ytT-CYyOBXSxaNrdHdnf07AbppQnk5780gammGMzK2uQGuZ8iKf7MlI90GGGir_SVy6n-Nku_uLRQ23pQ77t9bfVz7pFa-hBreD9h-Bme2Jbdi71gopX2zkXLrd7Onslh5FSCWwzIxAYrFAhf9MoKbaoESxyBgDWBQ_A7WF4kooRn9y7PKscaNhnXr9vQJ_u5m00)
