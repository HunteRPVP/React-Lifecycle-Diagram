# React-Lifecycle-Diagram

```plantuml
@startuml
skinparam rectangle {
RoundCorner 20
shadowing false
}

rectangle Монтирование {

rectangle "constructor(props)" as con
rectangle "static getDerivedStateFromProps(props, state)" as gdsfp1 #palegreen
rectangle "componentWillMount()" as cwm #pink;line.dashed
rectangle "render()" as ren #lightblue
rectangle "componentDidMount()" as cdm

con --> gdsfp1
gdsfp1 ----> cwm
cwm --> ren
ren ---> cdm
}

rectangle Обновление {

rectangle "Новые свойства" as props #transparent;line:transparent
rectangle "setState()" as state #transparent;line:transparent
rectangle "forceUpdate()" as fu #transparent;line:transparent
rectangle " static getDerivedStateFromProps(props, state) " as gdsfp #palegreen
rectangle "componentWillReceiveProps(nextProps)" as cwrp #pink;line.dashed
rectangle "shouldComponentUpdate(nextProps, nextState)" as scu
rectangle "❌" as cross #transparent;line:transparent;text:red
rectangle "componentWillUpdate(nextProps, nextState)" as cwu #pink;line.dashed
rectangle " render() " as r #lightblue
rectangle "getSnapshotBeforeUpdate(prevProps, prevState)" as gsbu
rectangle "componentDidUpdate(prevProps, prevState, snapshot)" as cdu

props -D-> gdsfp
state -D-> gdsfp
fu -D-> gdsfp
gdsfp --> cwrp
cwrp --> scu
scu -U---> cross : " false"
scu --> cwu : " true"
cwu --> r
r --> gsbu
gsbu --> cdu
}

rectangle Размонтирование {

rectangle empty #transparent;line:transparent;text:transparent
rectangle "componentWillUnmount()" as cwum

empty --------> cwum
}

rectangle "Обработка ошибок" {

rectangle "empty  " as em #transparent;line:transparent;text:transparent

rectangle "getDerivedStateFromError(error)" as gdsfe
rectangle "componentDidCatch(error, info)" as cdc

em --> gdsfe
gdsfe -------> cdc
}
@enduml
```

![test](http://www.plantuml.com/plantuml/png/bLJFJjmy4B_xAQnmuPFOJssF85MeqDugLI3KiuadsOZ4jiOsjAgG2gTAxIEKge-mL4AbjF0CtbVeazJERBJP5RiiEJZZyVoVtyosTGATRsfcZofb18g68-HEgB86_e7jQQ_aZaO5o9yzONOef3wfLCaBKLjWfunDfSFNS1Tkn-VXUlmnKZ_2ADo6wt0LpVIaibmhwz3dJkEwGMtiVnaNbaTsNoh6vQgSb-1s0QjZaFkH0QzGDs-I3cbky2G6PA2KjZ1F-PeHDPG8e6QTDaOhKEvjLTUlOr9kVUBsf8agbJhQgYi5_qjXXo3xcWXA0awauuMlrLKvT8UrXtiTx5Ponhvi68kvyS7W-IH4Hh_8IRmO04j191hRe1Md1zdCrVTRk0otRML_XwjxQnikqlFuStmOdqMvk_1hV3O-JxreeschnjSS2cMDG52kJNkpnvXf0hYsx9GB5NjrxK9Z3WT6JWqKVdLj_YW4y2a4La707kGGJP8X1UzSItM8GBCS4dQeVIrtEeEK8fcXc1AvFqMcpNrV_U_55tA4sZxGZ2qNBMqYo8MPFEWyF_7Bi-4Tmgc6k03WPSI24YRcxbv0eR7hh44uddXEPCzpQG_zeX5PeXnREl7JJP1dZ80xsEs6Y14MUup2zs-419elD2mUT4kji7aKFMXdZ5gmoJFQPrdxHbg-PJlqa4LruYB3zAVCqa6oqiyDwlSm2Z_3drNM8JJ6lLy513t6OZ2ePcQr-OOnSZ2WZpARsojPMYmnnb6u37Sntfimuf7u5AuJ8znaSqk6B19Qe7bix7rBzypsIqIDwv3EwLfVk6btXCk79Bt1ArNe3Z8vOq0xbVJRaq-B40LEsJOewPlw7m00)
