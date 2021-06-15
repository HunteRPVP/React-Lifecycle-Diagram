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

rectangle "empty " as e #transparent;line:transparent;text:transparent
rectangle " static getDerivedStateFromProps(props, state) " as gdsfp #palegreen
rectangle "componentWillReceiveProps(nextProps)" as cwrp #pink;line.dashed
rectangle "shouldComponentUpdate(nextProps, nextState)" as scu
rectangle "componentWillUpdate(nextProps, nextState)" as cwu #pink;line.dashed
rectangle " render() " as r #lightblue
rectangle "getSnapshotBeforeUpdate(prevProps, prevState)" as gsbu
rectangle "componentDidUpdate(prevProps, prevState, snapshot)" as cdu

e --> gdsfp
gdsfp --> cwrp
cwrp --> scu
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

![test](http://www.plantuml.com/plantuml/png/dLHVQnD147_VJp4aBn4IKHyhI37LDq4QnEVjxUHoz6xtcDrj5Ic8Jtu84Jz258gbsdw6xJTozlRYNKeIsWQoDpStVtxpcvdTjqwIyrKfx76XQqco0iBCIPsN29_4eV5QJGrf97ZsHDY5LEQqq3dCPMbHd0dHMOTluJfStNm95pUVMVeLbk4gN8Hp3jEp6cH6MqS-SuP6DPdQFXg0jC3glXNZSaK6ERe3fE84rOmL-9fCzJRw9CynH3DC0N9bv_LJ6DQon9mGzNhIgZOQjNjVbEKRBigDshId5RiK-lXvMMXyhAHTeEfx4cg5r5hp2mpB8b-uezBZnWG7XLgBhoeXk3QOJ5wq44Lwi2Rg68288A9C3MWDwGDxhlFxFVnaHYEpVyBvHcwngjr7Q18Z31r9RRcdZAgfRg-lSFZ1zHNzC70lzg6Z_oxi7sA67385qeoYaLRTe7ftE-p2-59DLm7VrOeXT6764CLPDnKsyrkHx7HESFnkDD1EHyi1RHaEvd6cPStOtKkS6y8sSqruqcQEOYzpRe_yjl7QuSmjQVEifiyBWTtifT6BxmtLWe_q5cdYV_l5mnuNvCZZW4sIbWJ5PqB6Hskh_AqX_S5h_plylSjLaARruMEwtanThQsrhuH82IRfbogxjLE3k5ICSSchTSruByCIMFZAO5aHBWSR5wpTiEg-sFkHDkpMAo938undTwLjlMMcqcMBP3s6Gi_DgkLPBFn_pr4q9tGaiC6Ps4UjV5N-0m00)
