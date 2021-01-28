# Чистый код Javascript!

### 1. Make LET(const), Not Var!

Для объявления переменных используйте let или const. var  в прошлом.

`плохой пример`
``` js
var count = [a, b, c]
```
`хороший пример`
``` js
let count = [a, b, c];
const counts = [a, b, c];
```

### 2. Зарезервированные слова.

__НЕ__ используйте зарезервированные слова в качестве ключей объектов. Они не будут работать в IE8.

`плохой пример`
``` js 
let superman = {
  default: {clark: 'kent'};
}
```
`хороший пример`
```js
let superman = {
  defaults: {clark: 'kent'};
};
```

### 3. Объявление функций.

Никогда не объявляйте функции внутри блока кода - например if, else, while и т.д. Единственное исключение — блок функции. Вместо этого присваивайте функцию уже объявленной через let переменной. Условное объявление функций работает, но в различных браузерах работает по-разному.

`плохо`
``` js
if (currentUser) {
  function test() {
    console.log('bad boy');
  };
};
```

`хорошо`
``` js
let test;
if (currentUser) {
  test = function test() {
    console.log('good boy');
  };
};  
```

### 4. Arguments

Никогда не используйте аргумент функции arguments, он будет более приоритетным над объектом arguments, который доступен без объявления для каждой функции.

`плохой пример`
``` js
function nop(name, options, arguments) {
  console.log('bad');
}
```
`хороший пример`
``` js
function yup(name, options, args) {
  console.log('good');
};
```

### 5. Точка с запятой.

Точки с запятой: точки с запятой необязательны в JavaScript, ведь компилятор JS автоматически добавит их, если нужно. Но это МОЖЕТ привести к ошибкам, поэтому лучше привыкнуть к добавлению точек с запятой. Просто сделайте это!

### 6. camelCase.

Наименование: имена функций и переменных должны быть наглядными. Всегда используйте camelCase. Чтобы все было единообразно и легко читалось, переменные всегда должны начинаться с существительного, а функции - с глагола и самое главное на английском. Можно использовать отдельные символы в качестве имен переменных в контексте цикла или callback-функции (функции обратного вызова), но не в других местах.

`плохой пример`
``` js
const naidiuseRnAme_
```
`хороший пример`
``` js
const userNameFound;
```

### 7. Скобки при создании объектов (массивы).

Для создания объекта используйте фигурные скобки, не создавайте объекты через конструктор new Object (для массивов соответственно - квадратные скобки).

`плохой пример`
``` js
let item = new Object();

let items = new Array():
```
`хороший пример`
``` js
let item = {};

let items = [];
```

### 8. Комментарии.

Используйте /** ... */ для многострочных комментариев. 
Используйте // для комментариев в одну строку. Размещайте комментарии на новой строке над темой комментария. Добавляйте пустую строку над комментарием.
Префикс TODO помогает другим разработчикам быстро понять, что вы указываете на проблему, к которой нужно вернуться в дальнейшем, или если вы предлагете решение проблемы, которое должно быть реализовано. Эти комментарии отличаются от обычных комментариев, так как не описывают текущее поведение, а призывают к действию, например TODO -- нужно реализовать интерфейс. Такие комментарии также автоматически обнаруживаются многими IDE и редакторами кода, что позволяет быстро перемещаться между ними.

`плохой пример`
``` js
function getType() {
  console.log('проверяем тип...');
  // задаем тип по умолчанию 'no type'
  var type = this._type || 'no type';

  return type;
}
```
`хороший пример`
``` js
function getType() {
  console.log('проверяем тип...');

  // задаем тип по умолчанию 'no type'
  let type = this._type || 'no type';

  return type;
};
```
``` js
function Calculator() {

  // TODO FIXME: тут не нужно использовать глобальную переменную
  total = 0;

  return this;
};
```

### 9. Геттеры и сеттеры.

Функции универсального доступа к свойствам не требуются. 
Если вам необходимо создать функцию для доступа к переменной, используйте раздельные функции getVal() и setVal('hello').

`плохой пример`
``` js
dragon.age();
dragon.age(25);
```
`хороший пример`
``` js
dragon.getAge();
dragon.setAge(25);
```

### 10. Длина строки.

Никто не любит читать длинные горизонтальные строки кода. Лучше всего разбивать их. Максимальную длину строки согласовывают в команде. Обычно это 80 или 120 символов.

`плохой пример`
``` js
let str = Рабочая группа TC39 организации Ecma International - это группа JavaScript-разработчиков, теоретиков и авторов движков JavaScript, которые вместе с сообществом занимаются поддержкой и развитием языка JavaScript.
```
`хороший пример`
``` js
let str = `
  Рабочая группа TC39 организации Ecma International -
  это группа JavaScript-разработчиков, теоретиков и авторов движков JavaScript,
  которые вместе с сообществом занимаются поддержкой и развитием языка JavaScript.
`;
