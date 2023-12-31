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
