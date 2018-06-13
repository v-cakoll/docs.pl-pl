---
title: Odwołanie do symbolu i operatora (F#)
description: 'Więcej informacji na temat symbole i operatory, które są używane w języku programowania w języku F #.'
ms.date: 04/04/2018
ms.openlocfilehash: 79518b990f3a5c794f7658490bdadc2d5b985504
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566707"
---
# <a name="symbol-and-operator-reference"></a>Odwołanie do symbolu i operatora

> [!NOTE]
Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

Ten temat zawiera tabelę symboli i operatory, które są używane w języku F #.

## <a name="table-of-symbols-and-operators"></a>Tabela symboli i operatorów
Poniższa tabela opisuje symbole używane w języku F #, zawiera łącza do tematów, które dostarczają więcej informacji i zawiera krótki opis niektórych zastosowań symbolu. Symbole są uporządkowane według zestawu kolejność znaków ASCII.

|Symbol or — operator|Łącza|Opis|
|------------------|-----|-----------|
|`!`|[Komórki odwołań](../reference-cells.md)<br /><br />[Wyrażenia obliczeń](../computation-expressions.md)|<ul><li>Wyłuskań komórka odwołania.<br /></li><li>Po słowem kluczowym wskazuje zmodyfikowanej wersji zachowanie słowa kluczowego jako kontrolowane przez przepływ pracy.<br /></li><ul/>|
|`!=`|Nie dotyczy.|<ul><li>Nie jest używany w języku F #. Użyj `<>` operacjach nierówności.<br /></li><ul/>|
|`"`|[Literały](../literals.md)<br /><br />[Ciągi](../strings.md)|<ul><li>Rozgranicza ciąg tekstowy.<br /></li><ul/>|
|`"""`|[Ciągi](../strings.md)|Rozgranicza ciągu dosłownego wyrażenia tekstowego. Różni się od `@"..."` , można określić znak cudzysłowu przy użyciu pojedynczego cudzysłowu w ciągu.|
|`#`|[Dyrektywy kompilatora](../compiler-directives.md)<br /><br />[Typy elastyczne](../flexible-types.md)|<ul><li>Prefiksy dyrektywy preprocesora lub kompilatora, takich jak `#light`.<br /></li><li>Wskazuje, gdy jest używany z typem, *elastycznym typem*, które odwołuje się do typu lub jednego z jego typów pochodnych.<br /></li><ul/>|
|`$`|Brak dostępnych informacji więcej.|<ul><li>Używana wewnętrznie do niektórych generowane przez kompilator zmienna nazwy i funkcji.<br /></li><ul/>|
|`%`|[Operatory arytmetyczne](arithmetic-operators.md)<br /><br />[Cytaty kodu](../code-quotations.md)|<ul><li>Oblicza resztę liczby całkowitej.<br /></li><li>Używane do łączenia wyrażenia w cytaty kodu typu.<br /></li><ul/>|
|`%%`|[Cytaty kodu](../code-quotations.md)|<ul><li>Używane do łączenia wyrażenia w cytaty kodu bez typu.<br /></li><ul/>|
|`%?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza resztę liczby całkowitej po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|`&`|[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>Oblicza adres modyfikowalne wartości do użycia podczas współpracy z innych języków.<br /></li><li>Używane we wzorcach i.<br /></li><ul/>|
|`&&`|[Operatory logiczne](boolean-operators.md)|<ul><li>Oblicza operacji logicznych i.<br /></li><ul/>|
|`&&&`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Oblicza operacji i.<br /></li><ul/>|
|`'`|[Literały](../literals.md)<br /><br />[Automatyczna generalizacja](../generics/automatic-generalization.md)|<ul><li>Rozgranicza literał jednoznakowym.<br /></li><li>Wskazuje parametr typu ogólnego.<br /></li><ul/>|
|<code>&#96;&#96;...&#96;&#96;</code>|Brak dostępnych informacji więcej.|<ul><li>Rozgranicza identyfikator, który nie byłby identyfikatorem prawne, takie jak słowo kluczowe języka.<br /></li><ul/>|
|`( )`|[Typ jednostki](../unit-type.md)|<ul><li>Reprezentuje pojedynczą wartość typu jednostki.<br /></li><ul/>|
|`(...)`|[Krotki](../tuples.md)<br /><br />[Przeładowanie operatora](../operator-overloading.md)|<ul><li>Określa kolejność, w jakiej są oceniane wyrażenia.<br /></li><li>Rozgranicza spójnych kolekcji.<br /></li><li>Używane w definicjach operatora.<br /></li><ul/>|
|`(*...*)`||<ul><li>Rozgranicza komentarz, który może obejmować wiele wierszy.<br /></li><ul/>|
|<code>(&#124;...&#124;)</code>|[Wzorce aktywne](../active-patterns.md)|<ul><li>Rozgranicza aktywnego wzorca. Skrót *klipy bananów*.<br /></li><ul/>|
|`*`|[Operatory arytmetyczne](arithmetic-operators.md)<br /><br />[Krotki](../tuples.md)<br /><br />[Jednostki miary](../units-of-measure.md)|<ul><li>Gdy jest używany jako operator binarny, mnoży lewej i prawej stronie.<br /></li><li>W typach wskazuje parowania w spójnej kolekcji.<br /></li><li>Używane w jednostkach typy miary.<br /></li><ul/>|
|`*?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Mnoży lewej i prawej stronie, po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|`**`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Oblicza operacji potęgowania (`x ** y` oznacza `x` do potęgi równej `y`).<br /></li><ul/>|
|`+`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Jeśli użyto operatora binarnego, dodaje lewej i prawej stronie.<br /></li><li>Gdy jest używany jako operator jednoargumentowy, wskazuje wartość dodatnią. (Formalnie, tworzy tę samą wartość przy użyciu konta bez zmian.)<br /></li><ul/>|
|`+?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Dodaje lewej i prawej stronie, po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|`,`|[Krotki](../tuples.md)|<ul><li>Oddziela elementy spójnej kolekcji lub parametrów typu.<br /></li><ul/>|
|`-`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Gdy jest używany jako operator binarny, odejmuje z prawej strony z lewej strony.<br /></li><li>Gdy jest używany jako operator jednoargumentowy, wykonuje operację negacji.<br /></li><ul/>|
|`-`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Odejmuje z prawej strony z lewej strony, po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|`->`|[Funkcje](../functions/index.md)<br /><br />[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>Typy funkcji, rozgranicza argumenty i zwracać wartości.<br /></li><li>Zwraca wyrażenie (w wyrażeniach sekwencji); odpowiednikiem `yield` — słowo kluczowe.<br /></li><li>Używane w wyrażeniach dopasowania<br /></li><ul/>|
|`.`|[Elementy członkowskie](../members/index.md)<br /><br />[Typy pierwotne](../primitive-types.md)|<ul><li>Uzyskuje dostęp do elementu członkowskiego, a oddziela nazwy w pełni kwalifikowanej nazwy.<br /></li><li>Liczby zmiennoprzecinkowe określa separatorem dziesiętnym.<br /></li><ul/>|
|`..`|[Pętle: `for...in` wyrażenia](../loops-for-in-expression.md)|<ul><li>Określa zakres.<br /></li><ul/>|
|`.. ..`|[Pętle: `for...in` wyrażenia](../loops-for-in-expression.md)|<ul><li>Określa zakres wraz z przyrostem.<br /></li><ul/>|
|`.[...]`|[Tablice](../arrays.md)|<ul><li>Uzyskuje dostęp do elementu tablicy.<br /></li><ul/>|
|`/`|[Operatory arytmetyczne](arithmetic-operators.md)<br /><br />[Jednostki miary](../units-of-measure.md)|<ul><li>Dzieli po lewej stronie (licznik) przez po prawej stronie (dzielnik).<br /></li><li>Używane w jednostkach typy miary.<br /></li><ul/>|
|`/?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Dzieli po lewej stronie przez po prawej stronie, po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|`//`||<ul><li>Wskazuje początek jednowierszowego komentarza.<br /></li><ul/>|
|`///`|[Dokumentacja XML](../xml-documentation.md)|<ul><li>Wskazuje komentarza XML.<br /></li><ul/>|
|`:`|[Funkcje](../functions/index.md)|<ul><li>W adnotację typu oddziela nazwę parametru lub elementu członkowskiego z jego typu.<br /></li><ul/>|
|`::`|[Listy](../lists.md)<br /><br />[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>Tworzy listę. Element z lewej strony jest dołączany na początku na liście po prawej stronie.<br /></li><li>Używany w dopasowanie wzorca do rozdzielania części listy.<br /></li><ul/>|
|`:=`|[Komórki odwołań](../reference-cells.md)|<ul><li>Przypisuje wartość do komórka odwołania.<br /></li><ul/>|
|`:>`|[Rzutowanie i konwersje](../casting-and-conversions.md)|<ul><li>Konwertuje typ do typu, który jest wyżej w hierarchii.<br /></li><ul/>|
|`:?`|[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>Zwraca `true` Jeśli wartość zgodne z określonym typem; w przeciwnym razie zwraca `false` (operator typu testu).<br /></li><ul/>|
|`:?>`|[Rzutowanie i konwersje](../casting-and-conversions.md)|<ul><li>Konwertuje typu na typ, który jest niżej w hierarchii.<br /></li><ul/>|
|`;`|[Pełna składnia](../verbose-syntax.md)<br /><br />[Listy](../lists.md)<br /><br />[Rekordy](../records.md)|<ul><li>Oddziela wyrażenia (używana głównie w Pełna składnia).<br /></li><li>Oddziela elementy listy.<br /></li><li>Oddziela pola rekordu.<br /></li><ul/>|
|`<`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Oblicza less — od operacji.<br /></li><ul/>|
|`<?`|[Operatory dopuszczające wartość null](nullable-operators.md)|Oblicza less than operacji po prawej stronie jest typem zerowalnym.|
|`<<`|[Funkcje](../functions/index.md)|<ul><li>Redaguj dwie funkcje w kolejności odwrotnej; drugi jest wykonywana pierwszy (operator kompozycji wstecz).<br /></li><ul/>|
|`<<<`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Przesuwa bitów ilości po lewej stronie w lewo przez liczbę bitów określona po prawej stronie.<br /></li><ul/>|
|`<-`|[Wartości](../values/index.md)|<ul><li>Przypisuje wartość do zmiennej.<br /></li><ul/>|
|`<...>`|[Automatyczna generalizacja](../generics/automatic-generalization.md)|<ul><li>Rozgranicza parametrów typu.<br /></li><ul/>|
|`<>`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` Jeśli po lewej stronie nie równa się po prawej stronie; w przeciwnym razie zwraca wartość false.<br /></li><ul/>|
|`<>?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza "nie równa" operacji po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|`<=`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` Jeśli po lewej stronie jest mniejsza niż lub równa po prawej stronie; w przeciwnym razie zwraca `false`.<br /></li><ul/>|
|`<=?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza operacji "mniejsze niż lub równe" po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|<code>&lt;&#124;</code>|[Funkcje](../functions/index.md)|<ul><li>Przekazuje jego wynik wyrażenie po prawej stronie funkcji po lewej stronie (operator potoku wstecz).<br /></li><ul/>|
|<code>&lt;&#124;&#124;</code>|[Operatory. &#40; &#60; &#124; &#124; &#41; &#60;"U"T2", T1&#62; — funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhh-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Przekazuje krotki liczącej dwa argumenty po prawej stronie do funkcji po lewej stronie.<br /></li><ul/>|
|<code>&lt;&#124;&#124;&#124;</code>|[Operatory. &#40; &#60; &#124; &#124; &#124; &#41; &#60;U "T1,"T2", T3,"&#62; — funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhhh-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Przekazuje krotki liczącej trzech argumentów po prawej stronie do funkcji po lewej stronie.<br /></li><ul/>|
|`<@...@>`|[Cytaty kodu](../code-quotations.md)|<ul><li>Rozgranicza kod maszynowy oferty.<br /></li><ul/>|
|`<@@...@@>`|[Cytaty kodu](../code-quotations.md)|<ul><li>Rozgranicza kodu bez typu oferty.<br /></li><ul/>|
|`=`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` Jeśli po lewej stronie jest taki sam, z prawej strony; w przeciwnym razie zwraca `false`.<br /></li><ul/>|
|`=?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza "równego" operacji po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|`==`|Nie dotyczy.|<ul><li>Nie jest używany w języku F #. Użyj `=` dla operacji równości.<br /></li><ul/>|
|`>`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` po lewej stronie jest większa niż po prawej stronie, a w przeciwnym, funkcja zwraca `false`.<br /></li><ul/>|
|`>?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza operacji "większy niż" po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|`>>`|[Funkcje](../functions/index.md)|<ul><li>Redaguj dwie funkcje (operator kompozycji do przodu).<br /></li><ul/>|
|`>>>`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Bity zmian ilości po lewej stronie z prawej strony przez liczbę miejsc określony po prawej stronie.<br /></li><ul/>|
|`>=`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` Jeśli po lewej stronie jest większa niż lub równa po prawej stronie; w przeciwnym razie zwraca `false`.<br /></li><ul/>|
|`>=?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza operacji "większe lub równe" po prawej stronie jest typem zerowalnym.<br /></li><ul/>|
|`?`|[Parametry i argumenty](../parameters-and-arguments.md)|<ul><li>Określa opcjonalny argument.<br /></li><li>Używane jako operator dla wywołań metod i właściwości dynamicznych. Należy podać własne implementacji.<br /></li><ul/>|
|`? ... <- ...`|Brak dostępnych informacji więcej.|<ul><li>Używane jako operator ustawienie właściwości dynamicznych. Należy podać własne implementacji.<br /></li><ul/>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Odpowiednikiem odpowiedniego operatory bez? Prefiks, gdzie jest typu dopuszczającego wartości null po lewej stronie.<br /></li><ul/>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Odpowiednikiem odpowiedniego operatory bez? sufiks, gdzie jest typem zerowalnym po prawej stronie.<br /></li><ul/>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Wartość równoważna odpowiedniego operatory bez otaczających znaki zapytania, gdy obie strony są typy dopuszczające wartości zerowe.<br /></li><ul/>|
|`@`|[Listy](../lists.md)<br /><br />[Ciągi](../strings.md)|<ul><li>Łączy dwie listy.<br /></li><li>Po umieszczeniu przed ciąg literału, wskazuje ciąg interpretacji dokładnie, z nie interpretacji znaki specjalne.<br /></li><ul/>|
|`[...]`|[Listy](../lists.md)|<ul><li>Rozgranicza elementy listy.<br /></li><ul/>|
|<code>[&#124;...&#124;]</code>|[Tablice](../arrays.md)|<ul><li>Rozgranicza elementy tablicy.<br /></li><ul/>|
|`[<...>]`|[Atrybuty](../attributes.md)|<ul><li>Rozgranicza atrybutu.<br /></li><ul/>|
|`\`|[Ciągi](../strings.md)|<ul><li>Specjalne następny znak; używany w literałach znaków i ciąg.<br /></li><ul/>|
|`^`|[Statycznie rozwiązywane parametry typu](../generics/statically-resolved-type-parameters.md)<br /><br />[Ciągi](../strings.md)|<ul><li>Określa parametr typu, który musi zostać rozpoznane w czasie kompilacji, a nie w czasie wykonywania.<br /></li><li>Łączy ciągów.<br /></li><ul/>|
|`^^^`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Oblicza operacji wyłączny OR.<br /></li><ul/>|
|`_`|[Wyrażenia dopasowania](../match-expressions.md)<br /><br />[Typy ogólne](../generics/index.md)|<ul><li>Wskazuje wzorzec wieloznaczny.<br /></li><li>Określa anonimowe parametru ogólnego.<br /></li><ul/>|
|<code>&#96;</code>|[Automatyczna generalizacja](../generics/automatic-generalization.md)|<ul><li>Używana wewnętrznie w celu wskazania, parametru typu ogólnego.<br /></li><ul/>|
|`{...}`|[Sekwencje](../sequences.md)<br /><br />[Rekordy](../records.md)|<ul><li>Rozgranicza wyrażeniach sekwencji i obliczeń wyrażenia.<br /></li><li>Używane w definicjach rekordów.<br /></li><ul/>|
|<code>&#124;</code>|[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>Rozgranicza dopasowanie poszczególnych przypadków, poszczególne rozróżniane przypadki Unii i wartości wyliczenia.<br /></li><ul/>|
|<code>&#124;&#124;</code>|[Operatory logiczne](boolean-operators.md)|<ul><li>Oblicza Boolean lub operacji.<br /></li><ul/>|
|<code>&#124;&#124;&#124;</code>|[Operatory bitowe](bitwise-operators.md)|<ul><li>Oblicza lub operacji.<br /></li><ul/>|
|<code>&#124;></code>|[Funkcje](../functions/index.md)|<ul><li>Przekazuje jego wynik po lewej stronie do funkcji po prawej stronie (operator potoku do przodu).<br /></li><ul/>|
|<code>&#124;&#124;></code>|[Operatory. &#40; &#124; &#124; &#62; &#41; &#60;"U"T2", T1&#62; — funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hh%5d-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Przekazuje krotki liczącej dwa argumenty po lewej stronie do funkcji po prawej stronie.<br /></li><ul/>|
|<code>&#124;&#124;&#124;></code>|[Operatory. &#40; &#124; &#124; &#124; &#62; &#41; &#60;U "T1,"T2", T3,"&#62; — funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hhh%5d-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Przekazuje krotki liczącej trzech argumentów po lewej stronie do funkcji po prawej stronie.<br /></li><ul/>|
|`~~`|[Przeładowanie operatora](../operator-overloading.md)|<ul><li>Używane do deklarowania przeciążenia dla Jednoargumentowy operator negacji.<br /></li><ul/>|
|`~~~`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Oblicza bitowe nie operacji.<br /></li><ul/>|
|`~-`|[Przeładowanie operatora](../operator-overloading.md)|<ul><li>Używane do deklarowania przeciążenia jednoargumentowy minus operator.<br /></li><ul/>|
|`~+`|[Przeładowanie operatora](../operator-overloading.md)|<ul><li>Użyć do zadeklarowania przeciążenia jednoargumentowe plus operatora.<br /></li><ul/>|

## <a name="operator-precedence"></a>Kolejność wykonywania działań
W poniższej tabeli przedstawiono kolejność pierwszeństwa operatorów i innych słów kluczowych wyrażenie w języka F #, aby z najniższy priorytet najwyższy priorytet. Na liście również jest łączność, jeśli ma to zastosowanie.

|Operator|Łączność|
|--------|-------------|
|`as`|Prawe|
|`when`|Prawe|
|<code>&#124;</code> (potoku)|Lewe|
|`;`|Prawe|
|`let`|Nonassociative|
|`function`, `fun`, `match`, `try`|Nonassociative|
|`if`|Nonassociative|
|`->`|Prawe|
|`:=`|Prawe|
|`,`|Nonassociative|
|`or`, <code>&#124;&#124;</code>|Lewe|
|`&`, `&&`|Lewe|
|`:>`, `:?>`|Prawe|
|`!=`*Op*, `<` *op*, `>` *op*, `=`, <code>&#124;</code> *op*, `&` *op* , `&`<br /><br />(łącznie z `<<<`, `>>>`, <code>&#124;&#124;&#124;</code>, `&&&`)|Lewe|
|`^`*OP*<br /><br />(łącznie z `^^^`)|Prawe|
|`::`|Prawe|
|`:?`|Nie asocjacyjnej|
|`-`*Op*, `+` *op*|Dotyczy element infiksu używa tych symboli|
|`*`*Op*, `/` *op*, `%` *op*|Lewe|
|`**`*OP*|Prawe|
|`f x` (funkcja aplikacji)|Lewe|
|<code>&#124;</code> (dopasowania wzorca)|Prawe|
|Prefiks operatory (`+`*op*, `-` *op*, `%`, `%%`, `&`, `&&`, `!` *op*, `~` *op*)|Lewe|
|`.`|Lewe|
|`f(x)`|Lewe|
|`f<`*Typy*`>`|Lewe|
Język F # obsługuje niestandardowe przeładowania operatora. Oznacza to, zdefiniować własny operatorów. W poprzedniej tabeli *op* może być dowolną prawidłową sekwencją (prawdopodobnie pusta) znaków operator wbudowanych i zdefiniowanych przez użytkownika. W związku z tym można użyć tej tabeli można ustalić, jakie sekwencji znaków do użycia dla operatora niestandardowego do osiągnięcia żądany poziom priorytetu. Początkowe `.` znaki są ignorowane, gdy kompilator określa priorytet.

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](../index.md)

[Przeładowanie operatora](../operator-overloading.md)
