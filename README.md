# React-Lifecycle-Diagram

```plantuml
@startuml
node "Start and mount" {
Start --> [constructor]
[constructor] --> [getDerivedStateFromProps(before mount)]
[getDerivedStateFromProps(before mount)] --> [render (first time)]
[render (first time)] --> [componentDidMount]
[componentDidMount] --> [Running]
}

node "Update" {
[Running] --> [getDerivedStateFromProps(before update)] : props changed
[Running] --> [shouldComponentUpdate] : state changed
[getDerivedStateFromProps(before update)] --> [shouldComponentUpdate]
[shouldComponentUpdate] --> [Running] : false
[shouldComponentUpdate] --> [render (at update)] : true
[render (at update)] --> [getSnapshotBeforeUpdate]
[getSnapshotBeforeUpdate] --> [componentDidUpdate] : snapshot
[componentDidUpdate] --> [Running]
}

node "Unmount" {
[Running] --> [componentWillUnmount] : unmount
[componentWillUnmount] --> End
}

node "Error" {
[Running] --> [componentDidCatch] : child component error
[componentDidCatch] --> [Running]
}
@enduml
```

![test](http://www.plantuml.com/plantuml/png/ZLBDJW8n4BxtAHfEUE05F1WYuCt4I8m7iuUw7TWcxNGpdNenlhjC2XKtXN1Zv_lvlfcoJ6o8S_0AemKzsygdDcXrY1bvfhzL6IqM3_gZZvYOSi-HElNlg-1xu3MG-m9x434yKGml5CSq_uHT92YUTvswbLXS2T02wVdEKMBDBe1OjAQdbc6C2CXhPv_5g5EDMU6-PaI7-qxzgEC5taPh66Jn2jwsN1QXbBZNeynrFnZSWvtwf25cRrUdGYLFL4big-hsl2kkgZsVB7_8tXcVu2gx7jpm-QfC6LGBgqVReXaFllmejQ4Mku0qtl3iGaU1QkAN7XJhNxcYav1tv_sH9Z6v_5HDGj5kqFubR8WYjVrhoPNXVX3pVd3UwWff4B5gSQVxB05j3luN)
