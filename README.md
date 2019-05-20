# nsrComponents

При подключении скрипта на странице появляется объект ``nsrComponents``
У него имеются следующие методы: 

```mainPageRender``` - отрисовывает карту и таблицу для главной страницы. 
Вызывается с объектом ``options`` 

| Prop          | Value         | desc  |
| ------------- |:-------------:| -----:|
| leaderboardGroupName      | string | Название групового лидерборда ( брать здесь - https://www.sapsailing.com/sailingserver/api/v1/leaderboardgroups ) |
| tableName    | string      |   Опционально. Название таблицы лидеров для отрисовки ( если не указано, будет отрисована таблица последней гонки ) ( брать здесь - https://www.sapsailing.com/sailingserver/api/v1/leaderboards) |
| containers | Object      |    Объект с селекторами для отрисовки ( см. ниже ) |
| containers.table | cssSelector | селектор HTML элемента в который будет отрисована таблица|
| containers.map | cssSelector | селектор HTML элемента в который будет отрисована карта  |

```livePageRender``` - отрисовывает  селекты и карту для страницы LIVE. 
Вызывается с объектом ``options`` 

| Prop          | Value         | desc  |
| ------------- |:-------------:| -----:|
| leaderboardGroupName      | string | Название групового лидерборда ( брать здесь - https://www.sapsailing.com/sailingserver/api/v1/leaderboardgroups ) |
| containers | Object      |    Объект с селекторами для отрисовки ( см. ниже ) |
| containers.selects | cssSelector | селектор HTML элемента в который будет отрисованы селекты|
| containers.map | cssSelector | селектор HTML элемента в который будет отрисована карта  |


`renderTable` - отрисовывает таблицу лидеров 
Вызывается с двумя аругментами:
`tableName` - название гонки, брать отсюда - https://www.sapsailing.com/sailingserver/api/v1/leaderboards
`selector` - cssSelector HTML элемента куда будет отрисована таблица


Перевод - что бы установить английский язык для заголовков страниц разместить на странице следующий код  (в самом верху страницы)

```html

<script>
    window.nsrLocale = 'en';
</script>

```


Примеры использования 

### HTML
```html
<div id="selects"></div>
<div id="root"></div>

<div id="table1"></div>
<div id="table2"></div>
<div id="table3"></div>


<dit id="table"></dit>
<dit id="map"></dit>
```

### JavaScript
```javascript

const livePageRenderOptions = {
    leaderboardGroupName: 'Nord Stream Race 2018',
    containers: {
        selects: '#selects',
        map: '#root'
    }
};
nsrComponents.livePageRender(livePageRenderOptions);


const mainPageRenderOptions = {
      leaderboardGroupName: 'Nord Stream Race 2018',
      tableName: 'Nord Stream Race 2018 Overall',
      containers: {
          table: '#table',
          map: '#map'
      },
};

nsrComponents.mainPageRender(mainPageRenderOptions);


nsrComponents.renderTable('Nord Stream Race 2018 - Offshore Races Overall', '#table1');
nsrComponents.renderTable('Nord Stream Race 2018 - Inshore Races Overall', '#table2');
nsrComponents.renderTable('Nord Stream Race 2018 Overall', '#table3');

```

