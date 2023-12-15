# Содержание:
* [Фронтенд](#javascript):
     * [Основные положения JS](#основные-положения)
         * [Работа с неймингом](#работа-с-неймингом)
         * [Работа с операторами](#работа-с-операторами)
         * [Работа с функциями](#работа-с-функциями)
         * [Работа с блоками кода](#работа-с-блоками-кода)
         * [Работа со строками кода](#работа-со-строками-кода)
         * [Работа с JS object и иными структурами данных](#работа-с-js-object-иными-структурами-данных)
         * [Работа с классами](#работа-с-классами)
         * [Работа с импортами и экспортами](#работа-с-импортами-и-экспортами)
         * [Комментарии](#комментарии)
         * [Работа с переменными](#работа-с-переменными)
         * [Работа с JSON](#работа-с-json)
     * [Правила оформления HTML](#правила-оформления-html)
     * [Правила работы с CSS, Tailwind](#правила-работы-с-css-tailwind)
     * [Правила работы с React.js](#правила-работы-с-reactjs)
     * [Структура проекта](#структура-проекта)
* [Бэкенд](#python-code-style-guideline-by-misty):
    * [Внешний вид кода](#внешний-вид-кода)
    * [Архитектура проекта, файловая система](#архитектура-проекта-файловая-система)
    * [База данных](#база-данных)
        

# Правила оформления ФронтЭнда by Alis:

# JavaScript

## Основные положения:

### Работа с неймингом
- Названия переменных в camelCase
- Названия функций в camelCase
- Названия классов в PascalCase 
- Переменные окружения и прочие глобльные константы обозначаются в SNAKE_CASE (+upper case)

### Работа с операторами

- Операторы отделяются пробелами от переменных, унарные не отделяются (соблюдать при синтаксической возможности)
- Точка с запятой `;` ставится без пробела по желанию, главное чтобы отстуствие `;` не меняло задуманное поведение
- В случаее, если операторы и `&&` или `||` делают условие слишком ддлинным, то:
    - после открывающей условие скобки обозначается новая строка
    - все условия записываются в круглых скобках как внутри блока кода, с идентом относительно ключевого слова
    - оператор и или и тп остаётся на строке c изначальным условием 
    - доп условие после него переносится на новую
    - закрывающая круглая скобка находится на новой строке на том же иденте что и ключевое слово
    - без пробела открывается новый блок кода
    - пример:
    ```
            if(
                a < 0 || 
                b < 19
            ){
                some code
            }
    ```
- Использование двоеточия `:`: пробел не ставится после 1 переменной и ставится перед второй `{key: value}`

### Работа с функциями
- `return` по возможности должен возвращат конкретную переменную, а не выражение:
```
    const x = a + b
    return x
```
- как НЕ надо
```
    return a+b
```
- Желательно использование стрелочных функций
- Передаваемые переменные не отделяются от круглых кобок и отделяются запятой с пробелом `(value1, value2)`
- Фигурная скобка после параметров не отделяется пробелом от параметров `(...){`
- Пример функции
```
        function showMessage(message){
            alert(message)
        }
```
- В стрелочной функции участок c параметрами, стрелкой и отрывающей фигурной скобкой `()=>{` пишется всегда слитно
- Пример стрелочной функции
```
        const showMessage = (message)=>{
            alert(message)
        }
```
- В случае большого количества передваемых аргументов:
    - после открывающей круглой скобки для параметров обозначается новая строка
    - все параметры записываются в круглых скобках как внутри блока кода, с идентом относительно объявления функции
    - на одной строке один параметр
    - закрывающая круглая скобка (и стрелка) находится на новой строке на том же иденте что и объявление функции
    - без пробела открывается новый блок кода
    - пример:
    ```
        const fn = (
            param1,
            param2
        )=>{
            some code
        }
    ```
- Применимо и к вызову функции с большим количеством аргументов
    ```
    const x = fn(
        param1,
        param2
    )
    ```

### Работа с блоками кода

- При открытии нового логического блока должен быть перенос строки и индентация
- Новый связаннй блок начинается на той же строке, на которой закрылся прошлый блок
- Условие в скобках не отделяется побелом от `if`, `else if`, `else` и тп
- Условие в скобках не отделяется побелом от открывающей фигурной скобки `{`
- К контструкции try catch и подобным применимы те же правила по возможности
- Закрывающая блок фигурная скобка `{` должна быть на том же инденте, что и открывающее блок ключевое слово
- Пример оформления связанных логических блоков(if else, try catch и тп):
```
        if(a == b){
            return true
        }else if(a > b){
            return false
        }else{
            throw new Error("Wrong input");
        }
```
- Пример оформления нестинга (вложенного кода). Прим. цепочка промисов:
```
        fetch(url,{
            someData,
            someParams
        }).then((data)=>{
            data.text().then((html)=>{
                setHtml(html)
            }).catch(()=>{
                setHtml("<h1>Error</h1>")
            })
        })...
```
### Работа со строками кода

- Максимальная длина строки 80 символов
- Индентация равна 4 проблам
- Раздельные логические блоки, декларации функций и тп разделяются 2 или 1 строками по усмотрению програмиста
- При наличии нескольких открывающих скобок на одной строке со следующими переносом строки и индентацией закрывающие скобки так же должны быть на одной строке. Прмер:
```
    fetch(url,{
        someData,
        someParams
    })
```

### Работа с js object и иными структурами данных

- js object, включающий в себя 1 параметр может быть задан в 1 строку, в этом случае фигурные скобки не отделябтся пробелами
```
        {key: value}
```
- js object, включающий более 1 параметра должен быть задан нестингом
```
        {
            keyOne: valueOne,
            keyTwo: valueTwo
        }
```
- Запятая в конце последнего параметра ставится по желанию
- К массивам, мапам и прочим структурами применяются те же првила

### Работа с классами

- Методы и свойства отделяются друг от друга 1 строкой
- Свойства друг от друга отделяются переносом строки
- Методы отделяются друг от друга 1 строкой
- Пример работы с классами
```
        class Rectangle {
            height = 0;
            width;

            constructor(height, width){
                this.height = height;
                this.width = width;
            }

            setHeight(height){
                this.height = height;
            }
        }
```

### Работа с импортами и экспортами

- Не дефолтный экспорт должен быть указан в одной строке с заданием экспортируемой сущности
- Дефолтный экспорт должен быть указан на отдельной строке
- Все иморты пришутся в верхней части файла
- Сначала указываются импорты из стандартных библиотек, затем из сторонних зависимостей, затем из файлов
- Ипорты отделяются от основного кода 2 строками
- Использование `require` импортов может быть допущено только при необходимости
- Использование импортов должно быть по стандарту `import ... from ...`


### Комментарии

- желательно использовать dockstring в следующем виде:
```
    /**
    * Вычисляет сумму двух чисел
    * @param {number} a Первое число
    * @param {number} b Второе число
    * @returns {number} Сумма чисел
    */
    function add(a, b) {
        return a + b;
    }
```
- Комментарии наинаются на том же инденте, что и блок кода, к которому относится комментарий, либо на том же инденте что и переменная
- Строка комментария должна быть над тем, к чему относится комментарий
```
    // комментарий к переменной x
    const x = 'x'
    // комментарий к функции
    const x = ()=>{
        // комментарий к y
        let y = x
        // комментарий к возврату
        return x
    }
```
- При комментировании участка кода, который может быть примером или оставлен "на всякий случай" обозначение комментария `//` должно находиться на 0 инденте
```
//      const someFunc = ()=>{
//          const someVariable = 69
//          const otherFunc = (message)=>{
//              alert(message)
//              return True
//          }
//          const x = otherFunc(someVariable)
//          return x
//      }
```

### Работа с переменными

- Использование ключевого слова var строго не рекомендуется
- Использование ключевого слова let допустимо только при намерении изменять переменную после

### Работа с json

- Все json должны быть оформлены в формате camelCase

# Правила оформления HTML:

- Пробелы между строками в вёрствке недопустимы
- При наличии содержимого у тега должен быть открывающий и закрывающий тег
- При отсуствии содержимого тег должен быть самозакрывающимся
- Содержимое тега, дочерние теги должны всегда быть индентированы относительно родительского тега
- При большом количестве параметров тега:
    - после открытия открывающего тега происходит перенос строки и идент
    - параметры записываются по одному в строке
    - зарыватся открывающий тег (самозакрывающийся тег) на том же и иденте, на котором он открылся
- Пример верстки:
```
    <myTag
        param1=''
        param2=''
        param3=''
    >
        content
    </myTag>
    <otherTag
        param1=''
        param2=''
        param3=''
    />
    <div class='divClass'>
        <span class='myClass'>
            some str content
            <myTag />
        </span>
    </div>
```

# Правила работы с CSS, tailwind:
- при слишком длинной строке tailwind строку заключить в кривые ковычки и перенести на тот же индент, где и ключевое слово `class`
```
    <div 
        class=`class class4 class5
        class2 class3`
    />
```
- классы должны быть разделены 1 строкой
- css в одном файле должен быть разделён на логические блоки, отмеченные комментарием и разделены 2 строками
```
    /* кнопки */
    .button{
        some styles
    }   

    .button1{
        some styles
    }


    /* выдвижное меню */
    .menu{
        some styles
    }
    ...
```
# Правила работы с React.js:
- Использовать строго функциональные компоненты и хуки
- Использовать компоненты - стрелочные функции
- Названия функциональных компонент в PascalCase
- Экспорт компоненты дефолтный, пишется отдельно внизу файла
- При подстановке кода в вёрстку `{js code}` `{` и `}` должны трактоваться как открывающий и закрывающий теги
- При использовании тернарных выражений в вёрстке:
    - полсе условия `?`, новая строка и идент
    - `:` на том же инденте что и условие
    - после `:` новая строка и индент
    - пример:
    ```
        <div>
            {
                x == 1 ?
                    <span>
                        Yes
                    </span>
                :
                    <myTag />
            }
        </div>
    ```
- `return` компоненты или внутри map должен всегда имет открывающую скобку без пробела после `return`, после неё новая строка и индент, закрывающую скобку на том же инденте, что и ключевое слово `return`
```
    return(
        <div />
    )
```
- хук useRef инициализируется без аргументов `const myRef = useRef()` 
- хук useState распаковывается на вэлью и сеттер в camelCase при инициализизации с ключевым словом const, сеттер всегда содержит название из set+valueName. `const [name, setName] = useState('Васян')`
- Маунт хук useEffect должен быть внизу компоненты, перед ретёрном
- Хуки useEffect желательно смещать вниз компоненты, useStte наверх
- Прочая компановка компоненты остаётся на усмотрение разработчика
- хук useEffect всегда содержит массив в конце на той же строке, что и закрывающая скобка срелочной функции - коллбэка, пример:
```
useEffect(()=>{
    some code
}, [value, value2])
```
- Стейты желательно указывать рядом друг с другом, разделяя их новой строкой
- При указании переменных разных типов, ref, state, variable и тп разделять их 1 строкой
- Пример компоненты:
```
import {useEffect, useState} from "react"
import URL from ../utils/url.js

const MyComponent = ()=>{
    const [divClass, setDivClass] = useState('myDefaultClass')
    const [arr, setArr] = useState([])

    const url = URL+'/api/get_list'
    
    const showMessage = (message)=>{
        alert(message)
    }

    useEffect(()=>{
        fetch(url).then((data)=>{
            data.json().then((parsedData)=>{
                setX(parsedData.text)
                setArr(parsedData.valuesList)
                showMessage('fetch is successfull')
            })
        }).catch((error)=>{
            showMessage('fetch is not successfull', error)
        })
    }, [])

    return(
        <>
            <div className={`${x} listClass`}>
                {
                    arr.map((value, index)=>{
                        return(
                            <span key={arr+index} className='item'>
                                {value.name}
                                <div className='classname'>
                                    {value.info}
                                </div>
                            </span>
                        )
                    })
                }
            </div>
        </>
    )
}
```

# Структура проекта
- react проекты должны использовать vite
- при Next js использовать app раутинг и соблюдать конвенцию Next.js
- при React js использовать конвенцию React.js
- стили долны быть в отдельной папке styles
- все статические файлы, картинки и видео хранятся в папке public на одном уровне с src
- все компоненты в папке components в папке src
- все файлы называются в camelCase по возможности
- при написании относительно крупных файлов, объединнённых в одну логичекую и/или функциональную группу, или при написании важного кода можно сделать дополнительную папку в src
- при написании небольших, не попадающих в крупные категории утилит помещать файлы в папку utils.js

## И помните, читаемость кода на первом месте, всегда думайте головой, руководствуйтесь логикой, пишите хороший код)

# Python Code Style Guideline by Misty
## Внешний вид кода
* Кейс: snake_case для названий переменных (SNAKE_CASE для названий констант), функций и методов. PascalCase для названий классов. Аббревиатуры строчными буквами. Ключи словарей - в snake_case. Ключи JSON-объектов в camelCase, но если два Python-приложения общаются посредством JSON - тогда ключи JSON-объекта в snake_case.
* **Индентация**: 4 пробела.
* **Type hints**: **Обязательно** использование при указании параметров функции и её return value (символ `->` окружается пробелами). В остальных случаях (объяление переменных, получение данных из внешних источников) - использование желательно, если это повысит читаемость кода. Оформение - без пробела перед двоеточием, пробел после доеточия, тип (Пример: `foo: int`); Если после тайп хинта идёт оператор `=`, вокруг этого оператора стоят пробелы (Пример: `foo: int = 1`). Злоупотребление тайп хинтами не рекомендуется. При указании сложного объекта (список, список словарей, словарь со списами и т.п.) в качесте тайп хинта, **обязательно** использовать полное описание типа объекта (не `: list`, а `" list[str]`), в этом могут помочь тайп алиасы. Использовать тип `Any` не запрещено в случае если практически невозможно предугадать тип объекта или если объект слишком сложный (генератор или корутина и т.п.).
* **Длина строки кода**: **строго** 80 символов.
* **Комментарии**: допустимы, *настоятельно* рекомендуется избегать откомментированного кода. Если коммантарий находится на той же строке, что и код, **необходимо** отступить два пробела от кода, поставить символ `#`, а затем отступить от этого символа ещё один пробел. Пример: 
    ```
    foo = 1  # Два пробела, символ, один пробел, текст комментария
    ```
* **Раздление пустыми строками**: две пустые строки до и после объявления функции и класса. Логические блоки внутри функции, метода или просто в коде разделяются одним пробелом, или, в случае, когда его не хватает, комментарием (такого вида: `# ------`)
* **Работа с операторами**: между любыми операторами всегда пробелы, кроме случаев работы с функциями - см. ниже.
* **Переносы скобок, работа с объектами**: 
    * Первая скобка остаётся на той же строке, вторая скобка **обязательно** переносится на новую строку в начало индентации. Содержимое между скобок индентируется на четыре пробела. В случае переноса скобок добавляется висящая запятая, в остальных случаях, висящая запятая запрещена. Пример:
        ```
        foo = [
            1,
            2,
            3,
        ]
        ```
    * Исключение - сложный объект (список словарей и прочее). В этом случае первостепенна читаемость кода. Рекомендуется переносить первую скобку на новую строку. Пример:
        ```
        foo = [
            {
                ‘bar’: 1,
                ‘baz’: 2,
            },
            {
                ‘bar’: 3,
                ‘baz’: 4
            },
        ]
        ```
    * При переносе выражения, бинарные операторы остаются на строке своего первого операнда. Пример:
        ```
        flag = False
        if (
            foo == 'Hello' and
            bar == 'World' and
            baz == '!' and
            not flag
        ):
        ```
* **Докстринги (DocStrings)**: использование *настоятельно* рекомендуется. Для VSCode советую вот это расширение (вставить эту строку в поиск расширений): `njpwerner.autodocstring`. С этим расширением будет создаваться докстринга следующего вида, причём заполнятся она будет атоматически:
    ```
    """_summary_

    Args:
        arg_1 (_type_): _description_
        arg_2 (_type_): _description_

    Returns:
        _type_: _description_
    """
    ```
* **Оформление функций и методов**: 
    * При объявлении функции или метода, правила переноса скобок и работы с тайп хинтами здесь работают как обычно. При вызове работают обычные правила, но передача keyword аргументов в функцию - исключение. Пробелы вокруг оператора присваивания **запрещены**.
    ```
    def some_very_very_long_function_name_with_many_args(
        arg_1: int = 1,
        arg_2: str | None = None,
        arg_3: list[dict[str, Any]] | None = None
    ) -> str:
        result = arg_2 * arg_1
        return result


    foo = some_very_very_long_function_name_with_many_args(
        arg_1=1000,
        arg_2='bar',
    )
    ```
    * Возвращать выражение - **запрещено**, исключение - тернарный оператор. Пример:
    ```
    def foo(a: int, b: int) -> int:
        return pow(a, b)  # Так делать нельзя
    

    def bar(a: int, b: int) -> int:
        c = pow(a, b)
        return c  # Надо делать так

    def baz(a: int, b: int, flag: bool) -> int:
        return a if flag else b  # Так можно
    ```
* **Переносы выражений, строк**: В случае если длина выражения или строки превышает лимит в 80 символов, есть два варианта.
    * Первый вариант - использование обратного слэша `\`. Рекомендуется использовать с выражениями, при условии, что потребуется только один обратный слэш. **Нельзя** переносить квадратные скобки. Оформлeние - без пробела перед символом, после переноса индентация уходит на четыре пробела. Пример:
    ```
    foo = bar['some_long_long_dictionary_key'].method_1().method_2().method_3()\
        .method_4()['key']
    ```
    * Второй вариант - использование круглых скобок `()`. Рекомендуется использовать со строками, а также с очень длинными цепочками методов, если одного `\` не хватает, чтобы уложиться в 80 символов. Пример:
    ```
    foo = (
        'foobarfoobarfoobarfoobarfoobarfoobarfoobarfoobarfoobarfoobarfoobar'
        'foobarfoobarfoobarfoobarfoobarfoobarfoobarfoobarfoobarfoobarfoobar'
        'foobarfoobarfoobarfoobarfoobarfoobarfoobarfoobarfoobarfoobarfoobar'
    )
    bar = (
        session.query(
            SomeModel.some_field,
            OtherModel.other_field,
        )
        .filter(SomeModel.some_field == 1)
        .group_by(OtherModel.other_field)
        .all()
    )
    ```
* **Импорты, работа с `__init__.py`**: 
    * Импорты: в первую очередь импортируются стандартные библиотеки, затем сторонние библиотеки, затем собственные модули. Между этими категориями отступы в одну строку, между импортами и кодом отступ в две строки. В случае, когда из модуля импортируется множество объектов, и они не помещаются в лимит в 80 символов, следует пользоваться круглыми скобками, соблюдая правила переноса. **wildcard-импорты (`from foo import *`) запрещены**. Пример:
        ```
        import os

        from foo import (
            bar_1,
            bar_2,
            bar_3,
            bar_4,
            bar_5,
        )

        from . import foobar


        baz = foobar.somefunc(bar_1, bar_2)
        ```
    * `__init__.py`: **wildcard-импорты запрещены**. Импортируются только необходимые файлы и подмодули, причём из верхних уровней абстракции. Файл `__init__.py` **всегда** оформляется следующим образом:
        ```
        from . import foo
        from . import bar
        from . import baz
        ```
* Логическое ветвление, операторы `if`, `elif`, `else`, `match`:
    * Использование `else`, когда в нём нет необходимости не возбраняется.
    * `match` или `if/else`?
        * `match`: использовать когда речь идёт о реакции на внешний инпут или флаг, либо когда функционал этого ключевого слова превышает функционал `if/else`.
        * `if/else`: использовать при логических развилках.
* Циклы, list (dict) comprehension:
    * Синтаксис `for: ... else:` **запрещён** если не поставлен разъясняющий комментарий.
    * По возможности испльзовать цикл `for`, а не `while`.
    * Если list comprehension сложнее одного `if` или тернарного оператора, для построения списка использовать **только** цикл.
    * Использовать dict comprehension не рекомендуется.
* Exceptions:
    * При использовании конструкции ключевых слов `else` и `finally` в сочетании с `try: ... except ... as ...: ...` **всегда** оставлять поясняющие комментарии.
    * Отлавливать **всегда** только конкретные исключения, выражения `except:` и `except Exception:` **строго запрещены**.
* **Прочее**: Если здесь что-то не указано - **обязательно** обращаться к PEP8 и/или примерам из документации Python. Если там нет однозначного ответа, первостепенна читаемость кода.
## Архитектура проекта, файловая система
* **Архитектура проекта**:
    * **Бэкенд-приложения**: Предполагается что на Python будут писаться бэкенд-приложения, в связи с этим должна использоваться стандартная модель MVC (Model, View, Controller).
        * Model - отдельная директория (модуль) для работы с базой данных. Здесь находятся как модели (как одним файлом, так и по отдельному файлу для каждой модели - в зависимости от числа моделей), так и функции для работы с базой данных.
        * View - файл с раутами API. Здесь должно быть минимум кода и логики и максимум документации. В FastAPI - это файл `main.py`. URL-адреса бэкенд приложения должны быть написаны в snake_case.
        * Controller - модуль, отвечающий за логику приложения. Если у проекта нет отдельной точки входа (`main.py`), она должна находится здесь. Файлы этого модуля должны разделяться по функционалу, если кода в файле слишком много, следует создать подмодуль. Например, все функции для работы с блокчейном - в отдельном файле `blockchain.py`, все функции для работы со сторонним API - в отдельном файле с названием этого API. Также в этом модуле может присутствовать подмодуль `utils`, в котором будут хранится файлы с часто используемыми сторонними функциями, которые могут быть использованы во всех подмодулях модуля `controllers`, например: `redis_cache.py`, `logs.py` и т.п. 
        **Важно**: нельзя допускать взаимодействие модулей напрямую между собой, только через верхний уровень абстракции (отдельный файл, в который импортируются все подмодули), исключением может являться только файл `data_processing.py` - файл для обработки данных такими библиотеками как Pandas (этот функционал в той или иной мере может быть востребован в любом модуле, но иногда он слишком важен, чтобы класть его в `utils`).
        * Внутренние константы приложения стоит хранить в `utils`, в файлу `constants.py`. Общие константы хранить в общих конфигах и/или в переменных окружения.
    * **Микросервиса для обработки данных и/или любой другой программы на Python**: в этом случае стоит придерживаться той же логики, что и в параграфе про Controller выше.
* **Файловая система**:
    * Кириллица в названии файлов **запрещена**.
    * Названия файлов **только** в snake_case, без пробелов и прочих символов (разрешены только буквы латинского алфавита, символ `_` и цифры).
    * При работе с файлами использовать **только** относительные адреса и библиотеку `pathlib`.

# База данных
* Тип базы данных определяется перед началом работы с проектом, по умолчанию - PostgreSQL.
* Все таблицы и поля в них должны быть записаны **строго** в snake_case.
* Архитектура базы данных, типы, отношения должны обговариваться на общем собрании.
* У проекта **всегда** должна быть актуальная схема базы данных
