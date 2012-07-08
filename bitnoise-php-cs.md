1. Informacje ogólne
--------------------

- Pliki zawierają tylko `<?php` jako tagi.

- Tagu zamykającego `?>` nie wolno wstawiać w plikach zawierających tylko kod PHP.

- Pliki muszą być kodowane w UTF-8 bez BOM.

- Nazwy klas definiujemy jako `StudlyCaps`.

- Stałe klas nazywamy dużymi literami z podkreślnikami `FOO_BAR`.

- Nazwy metod defniujemy jako `camelCase`.

- Wcięcia w kodzie robimy na 4 spacje, nigdy tabulatory.

- Maksymalna ilość znaków w lini powinna oscylować w okolicach 80 znaków

- Dla klas i metod - nawias otwierający musi być w następnej lini po nazwie klasy/metody, zamykający musi
  być w kolejnej lini po zamknięciu ciała klasy/metody.

- Dla struktur musi być spacja po nazwie `if { }`, w przypadku metod nigdy `foo()`

- Dla struktur nawias otwierający musi być w tej samej lini, nawias zamykający musi być w następnej lini
  po ciele struktury.

2. Struktura
------------

- Po każdym przecinku musi być jedna spacja.

- Po i przed każdym operatorem dodajemy spację `$a = $b + $c;`

- Przed każdym zdefiniowanym return dodajemy pustą linię

- Defniujemy jedną klasę na plik

- Deklarujemy właściwości klasy przed metodami

- Deklarujemy publiczne metody klasy przed prywatnymi.

3. Nazewnictwo
---------------------

- Używaj camelCase, nie podkreślników dla zmiennych, funkcji, metod, argumentów

- Używaj podkreślników dla opcji, parametrów.

- Nazwy plików - TODO: do ustalenia

4. Dokumentacja
----------------
- Dodawaj bloki PHPDoc dla wszystkich klas, metod, i funkcji.

- Pomijaj tag @return jeśli metoda nic nie zwraca.

5. Deklaracje Namespace i Use
---------------------------------

Dodawaj pustą linię między deklaracje `namespace` i `use`

Przykład:

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... PHP code ...

```

6. Klasy i metody
-----------------------------------

### 6.1. Wzorzec formatowania


```php
<?php

namespace Btn;

class FooBar
{
    const SOME_CONST = 42;

    private $fooBar;

    /**
     * @param string $dummy Some argument description
     */
    public function __construct($dummy)
    {
        $this->fooBar = $this->transform($dummy);
    }

    /**
     * @param string $dummy Some argument description
     * @return string|null Transformed input
     */
    private function transformText($dummy, $options = array())
    {
        $mergedOptions = array_merge($options, array(
            'some_default' => 'values',
        ));

        if (true === $dummy) {
            return;
        }
        if ('string' === $dummy) {
            if ('values' === $mergedOptions['some_default']) {
                $dummy = substr($dummy, 0, 5);
            } else {
                $dummy = ucwords($dummy);
            }
        }

        return $dummy;
    }
}```

### 6.2. Właściwości klasy

Zmienne w definiowane w klasie zawsze powinny posiadać definicję zasięgu, nigdy nie używaj var do definiowania zmiennej w klasie

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public  $foo = null;
    private $bar = 1;
}
```

### 6.3. Metody i argumenty

Zasięg musi być zdefiniowany, formatowanie jak poniżej - spacja po każdym przecinku.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

Argumenty przy bardzo długich zapisach mogą być sformatowane jak poniżej.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```

### 6.4. Wywołania metod i funkcji.

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```
Lista argumentów może być podzielona na wiele lini.

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```


7. Struktury kontrolne
---------------------

Podstawowe zasady:

- spacja po każdej nazwie struktury `if ()`, `for ()`
- ciało struktury wcięte odpowiednio
- ciało struktury musi być zawsze domknięte w nawiasy

### 7.1. `if`, `elseif`, `else`

```php
<?php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```

`elseif` powinien być używany zamiast `else if`.

Grupuj złożone warunki w logiczne nawiasy
np. `if (($a == $b) || ($c == $d))`


### 7.2. `switch`, `case`

```php
<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```

### 7.3. `while`, `do while`

```php
<?php
while ($expr) {
    // structure body
}
```

### 7.4. `for`

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

### 7.5. `foreach`

```php
<?php
foreach ($iterable as $key => $value) {
    // foreach body
}
```

### 7.6. `try`, `catch`

```php
<?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
```

8. Inne warte zanotowania
-------------------------

- Dla stringów używaj pojedyńczych cudzysłowów.
`$string = 'some string';`

- Dla prostych warunków używaj operatora ternarnego
`$bool = isset($a) ? true : false;`

- Definiując tablice w wielu liniach zachowaj odpowiednie formatowanie:
```php
$arr = array(
    'first' => 'foo',
    'last'  => 'bar'
);

```

- Długie łańcuchy wywołań metod formatuj następująco:
```php

$this->getEntityManager()
  ->getRepository()
  ->find()
  ->limit(10)
;

```
- Wszystkie nazwy zmiennych powinny być znaczące i w języku angielskim.