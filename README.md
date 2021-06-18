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

rectangle "getDerivedStateFromError(error)" as gdsfe
rectangle "componentDidCatch(error, info)" as cdc

em --|> gdsfe
gdsfe -------|> cdc
}

@enduml
```

![test](http://www.plantuml.com/plantuml/png/bLJTJXGn5BxlKpJB3IOiKUCL90O1lTA4WCJhOURip6HdskQqPTqWYV7A2nz1ZO-09aI2mZEKL_19F9qMjqjsrsMIxRRd_tpdPqkR38rj6wQ7jL0PPYr7o4qcoWRu2TkNLXGx4WKWV_oGwIehvAWM9HzaZGPsoXAzfXPWnWguaitOFsRn99fA9emCKOvULtK-5A0rVvAmdddMZcmayfTrMPc3uNYxiS3O943tsLsxgviFxkBcFTr-k3DtvIxSEJz9fNgv5DgWpOt4LOLIwGSzdcbEv5IAe31rpaimku3rCHG7H80NADizhnCqrxWNWs2WBFH0FU8hAckWH00nxRHLKe0mR-gcUKKucjNeTjIIIYs6cnwLzIBJ5HIf9e8e0ACqFVXAu_C_ekHdEjYjYodxHSiOvSRx_NTFOumi_1794tq8Z7v1WZmmxoMoIFjq2kElxZkXwj7zvSvduckgMgzty7G1T3U-OZ0Jcae9mdIPRYI4ATp1T4Y7y0E-osiF9EPmg8g9WO5TNflVg-XyKlLbYhuFEP39O4Z0MxENzDu8rU8kq9Mq3SrUD1XId9XPutGDm4NSSfkg__doYTCNdA7K_od8fY5h6mZ5t6mM1H1Jieipuh6n8uuufwzBwWUHAShVRCD08aJF2k4uUlRNn7EfZ-oyoLYWJ6MDVcu7np8MchU_-szsM6Z8b3AmKy_G476mK34wujFNX7wyVnY6AnHYWxhMhqz--_M2K31WFPyRjD0ZIv6C3BjBIDKVKRomTwRr6-t0d-xtCdiHMcN6IxH5IfZV7gATsd6sPImuw8SlPdTdk_JyUg4WpsZ9N5F0b-wCq-MZk_04Tzcxisg2oT10qDut-DJIZ95_ZYXn5VmvMV1pT-vEPl8gIA_nMWpaRHVbFlF9zWNMdJo1WKHEsHQ8mhRDNm00)
