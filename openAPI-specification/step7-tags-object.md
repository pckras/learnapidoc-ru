# Руководство OpenAPI Шаг 7: Объект `tags`

| [*Шаг 1: объект* `openapi`](step1-openapi-object.md) | --> | [*Шаг 2: объект* `info`](step2-info-object.md) | --> | [*Шаг 3: объект* `servers`](step3-servers-object.md) | --> | [*Шаг 4: объект* `paths`](step4-paths-object.md) | --> | [*Шаг 5: объект* `components`](step5-components-object.md) | --> | [*Шаг 6: объект* `security`](step6-security-object.md) | --> | [**Шаг 7: объект** `tags`](step7-tags-object.md) | --> | [*Шаг 8: объект* `externalDocs`](step8-externalDocs-object.md) |

Объект `tags` позволяет группировать пути (конечные точки) в Swagger UI.

[Определение `tags` на корневом уровне](#define)

[`tags` на уровне объекта `paths`](#level)

[Отображение в Swagger UI](#appearanse)

<a name="define"></a>
## Определение `tags` на корневом уровне

На корневом уровне [объект `tags`](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#tagObject) перечисляет все теги, которые используются в [объектах `operations`](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.2.md#operationObject) (которые появляются в объекте `paths`, как описано в [Шаге 4: объект `paths`](step4-paths-object.md) ). Вот пример объекта тегов для нашего API OpenWeatherMap:

```yaml
tags:
  - name: Current Weather Data
  description: "Get current weather details"
```

Здесь только один тег, но их может быть столько, сколько вы хотите (если у вас много конечных точек, имеет смысл создать несколько тегов для их группировки). Вы можете перечислить как `name`, так и `description` для каждого тега. `description`  отображается в виде подзаголовка для имени тега на дисплее пользовательского интерфейса Swagger.

<a name="level"></a>
## Тэги на уровне объекта `paths`

Объект `tags` на корневом уровне должен содержать список всех тегов (групп), которые вы хотите использовать в своем API. Затем в каждом объекте пути под `paths` вы указываете тег, под которым вы хотите сгруппировать этот путь.

Например, в объекте операций для `/current` пути мы использовали тег `Current Weather Data`:

```yaml
paths:
  /weather:
    get:
      tags:
      - Current Weather Data
```

Этот тег определен на глобальном уровне, поэтому путь `/weather` будет сгруппирован здесь.

<a name="appearanse"></a>
## Отображение в Swagger UI

Добавьте следующий код к корневому уровню документа OpenAPI в редакторе Swagger:

```yaml
tags:
  - name: Current Weather Data
  description: "Get current weather details"
```

Посмотрите, как описание отображается рядом со свернутым разделом «Данные о текущей погоде».

![tags](img/16.png)

> Тэг определен на корневом уровне


Все пути, имеющие одинаковый тег, сгруппированы на дисплее. Например, пути с тегом `Current Weather Data` будут сгруппированы под заголовком `Current Weather Data`. Каждое название группы представляет собой кнопку, которая сворачивает / разворачивает вложенную информацию.

![name](img/17.png)

Порядок тегов в объекте `tags` на корневом уровне определяет их порядок в интерфейсе Swagger. Кроме того, `descriptions`  появляются справа от имени тега.

В нашем примере спецификации OpenAPI теги не кажутся необходимыми, поскольку мы просто документируем один путь / конечную точку. (Кроме того, настроена [демо версию Swagger UI](swagger-ui-demo.md) для расширения раздела по умолчанию.) Но представьте, что у вас есть надежный API с более чем 30 путями описания. Вы наверняка захотите организовать пути в логические группы для навигации пользователей.

[🔙](step6-security-object.md)

[Go next ➡](step8-externalDocs-object.md)
