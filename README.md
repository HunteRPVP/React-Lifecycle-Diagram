# React-Lifecycle-Diagram

```plantuml
@startuml
skinparam rectangle {
RoundCorner 20
shadowing false
}

rectangle Монтирование {

rectangle constructor
rectangle getDerivedStateFromProps #palegreen
rectangle componentWillMount #pink;line.dashed
rectangle render #lightblue
rectangle componentDidMount

constructor --> getDerivedStateFromProps
getDerivedStateFromProps ----> componentWillMount
componentWillMount --> render
render ---> componentDidMount
}

rectangle Обновление {

rectangle "empty " as e #transparent;line:transparent;text:transparent
rectangle " getDerivedStateFromProps " as gdsfp #palegreen
rectangle componentWillReceiveProps #pink;line.dashed
rectangle shouldComponentUpdate
rectangle componentWillUpdate #pink;line.dashed
rectangle " render " as r #lightblue
rectangle getSnapshotBeforeUpdate
rectangle componentDidUpdate

e --> gdsfp
gdsfp --> componentWillReceiveProps
componentWillReceiveProps --> shouldComponentUpdate
shouldComponentUpdate --> componentWillUpdate : " true"
componentWillUpdate --> r
r --> getSnapshotBeforeUpdate
getSnapshotBeforeUpdate --> componentDidUpdate
}

rectangle Размонтирование {

rectangle empty #transparent;line:transparent;text:transparent
rectangle componentWillUnmount

empty --------> componentWillUnmount
}

rectangle "Обработка ошибок" {

rectangle "empty  " as em #transparent;line:transparent;text:transparent

rectangle getDerivedStateFromError
rectangle componentDidCatch

em --> getDerivedStateFromError
getDerivedStateFromError -------> componentDidCatch
}
@enduml
```

![test](http://www.plantuml.com/plantuml/png/dLJTQXGn5BxFKuJfzOfuMQ4KMxqJf4MyZfEpCqCpoN1onX-a85xv428-mYeKItNx3EaRUMOpO0QIfRfNioVd--OxNxupnvuKqjWRuIywEoXKlKIeITd6WFmWpjnezOb32oWVFHI-LTgzxMmZryfu49T2_EqENy9jsDvz2jTt7_dfHzY4RRWELqoJTDNEUiAn9eT9jG4w1UpUW3udHV0CNVy2tU3bmQ0CD0XW5npzu2nOUjKPyvmb4lTrzkAnwImyqCgte9Ds1Ai1vO7fcfPUcn5oLAUTtZ49aIYKgzLHKPie7J2ASHcL8YESEsU1OjQPW5DTIw-_XkzXktFvLxZA-Ln1Fz1xMKdb9SW3GcNze90PTouTfWM2TvGMKfhY-96wqNuztEEMpg06veZ8VPVbMpSQZjoCVJbeHL1YZQTx-QhPtIYta0AUyTogWTzDJs3j429n8IVpeO0OZya14NtW_-MnHV5amXK6prQd_gmHXpmbuGZLybq92aKCTMdYV3rYCnuiG_cDL_vd-7sVpq1Cvt_7SZcUxUFcHjBL_3lAToqaLzCYiSuDhzCjQxu96yaFdram5y9DbLsgUQlwVzM__uFt5D5X8N8dYkfs6Z1UNWbSEf0BIvQab-8Oh1vxymS0)
