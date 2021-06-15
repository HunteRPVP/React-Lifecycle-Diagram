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
rectangle "componentWillUpdate(nextProps, nextState)" as cwu #pink;line.dashed
rectangle " render() " as r #lightblue
rectangle "getSnapshotBeforeUpdate(prevProps, prevState)" as gsbu
rectangle "componentDidUpdate(prevProps, prevState, snapshot)" as cdu

props -D-> gdsfp
state -D-> gdsfp
fu -D-> gdsfp
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

![test](http://www.plantuml.com/plantuml/png/bLHVQnGn47_FfmZNbmezKHzRa6AhRu9KnETqCxUtT3S9awHLf61z4lmAAdw4MYZMQliPSj_8oSqkjrVkpkj2iiba_izlPjS7XI4sjV17bN4ALICHYg1CMOFy80viD7hFeW6KJnu9FrRQdbIcb2DLUn2dGiouqzTqcsucdzBLv2ETBj9vkabNwPBKzBW6XJK-O2o2nKs7rla70wcy97AVY_mALI5B2Fk0rJ7erqI05sYRLrc69RTaPWDMK6e_Se_bXbCrb0XWveqspXemuMrLroyfgB3PcZrfIAGoHpjrPU2XLduCkY-9O3HWoqqNkL5NvJWSrX4M6jYlz9n-tGX1iSdXy6dhek0VKOYM7H2qydjMBsX9VY39-Vn-JpyfepcpVzBbmjocR_bvyeKU9cVfWYw_9sTK4Qh5r9jfrkH6G6Ky5HjCc8QztIFC5G72DEqS2oTxVUcHnGBUE3rJC8hhIyjx8K3E8B0E0WwW05B9YWoy2zDJXmXqgo7XnpRMUgzJo27Er6n9EdBYshmLSQad_nKkJk9gRsI7KCu1BW5eIRKqof7luHbGQRhAE8JZrd8-zYoN_Z0kW_WAOIf9QwVhW2W40s-utpM1O2pr2AFOlt4bkJ_G2ThubbD9gts9Sfk23XXXG2nCHO7vpzxJrlBgUAUPVj1u-fN-hZEoe77X_MhaxWIgMf-mlE2ccHi_iH623GpvuyZkzFuWDp_vU4uZu9RylKxdaWwVqrKcfEl1dK706XaHqDpNzxwc1Vtt7D7Y9kHzDdgNJiCz5OenSs_9oeni1uk20kUvn_BJNSwIG0odOXUCZatz3m00)
