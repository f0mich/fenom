Tag {foreach}
=============

Перебор значений массива или итератора

### {foreach}

Перебор значений массива $list

```smaert
{foreach $list as $value}
 <div>{$value}</div>
{/foreach}
```

Перебор ключей и значений массива $list

```smarty
{foreach $list as $key => $value}
 <div>{$key}: {$value}</div>
{/foreach}
```

Получение номера (индекса) итерации

```smarty
{foreach $list as $value index=$index}
 <div>№{$index}: {$value}</div>
{/foreach}
```

Определение первого элемента

```smarty
{foreach $list as $value first=$first}
 <div>{if $first} first item {/if} {$value}</div>
{/foreach}
```

Переменная `$first` будет иметь значение **TRUE**, если текущая итерация является первой.
Определение последнего элемента

```smarty
{foreach $list as $value last=$last}
 <div>{if $last} last item {/if} {$value}</div>
{/foreach}
```

Переменная `$last` будет иметь значение **TRUE**, если текущая итерация является последней.
Использование last замедляет работу цикла и требует от `$list` быть **countable**. Если есть возможность используйте **first** параметр.

### {break}

Тег `{break}` используется для выхода из цикла до достижения последней итерации. Если в цикле встречается тег `{break}`, цикл завершает свою работу, и далее, выполняется код, следующий сразу за блоком цикла

### {continue}

Тег `{continue}` используется для прерывания текущей итерации. Если в цикле встречается тег `{continue}`, часть цикла, следующая после тега, не выполняется, и начинается следующая итерация. Если текущая итерация была последней, цикл завершается.

### {foreachelse}

Тег {foreachelse} ограничивает код, который должен быть выполнен, если итерируемый объект пуст.

```smarty
{var $list = []}
{foreach $list as $value}
 <div>{if $last} last item {/if} {$value}</div>
{foreachelse}
 <div>empty</div>
{/foreach}
```

В блоке `{foreachelse}...{/foreach}` использование `{break}`, `{continue}` выбросит исключение `Aspect\CompileException` при компиляции