---
title: Odwołanie do symbolu i operatora (F#)
description: Więcej informacji na temat symboli i operatorów, które są używane w języku programowania F#.
ms.date: 04/04/2018
ms.openlocfilehash: 0e36f6cfc75b7d2e79bcf7acb89d260fd4e9b1ad
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "47216831"
---
# <a name="symbol-and-operator-reference"></a>Odwołanie do symbolu i operatora

> [!NOTE]
Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.  Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.

Ten temat zawiera tabelę symboli i operatorów, które są używane w języku F#.

## <a name="table-of-symbols-and-operators"></a>Tabela symboli i operatorów

Poniższa tabela opisuje symbole używane w języku F# zawiera łącza do tematów, które zawierają więcej informacji i krótki opis niektórych zastosowań symbolu. Symbole są uporządkowane według zestawu, kolejności znaków ASCII.

|Symbol or — operator|Łącza|Opis|
|------------------|-----|-----------|
|`!`|[Komórki odwołań](../reference-cells.md)<br /><br />[Wyrażenia obliczeń](../computation-expressions.md)|<ul><li>Wyłuskania komórki odwołania.<br /></li><li>Po słowo kluczowe wskazuje zmodyfikowaną wersję zachowanie słowa kluczowego jako kontrolowana przez przepływ pracy.<br /></li></ul>|
|`!=`|Nie dotyczy.|<ul><li>Nie jest używany w języku F#. Użyj `<>` operacji nierówności.<br /></li></ul>|
|`"`|[Literały](../literals.md)<br /><br />[Ciągi](../strings.md)|<ul><li>Rozgranicza ciąg tekstowy.<br /></li></ul>|
|`"""`|[Ciągi](../strings.md)|Rozgranicza ciąg verbatim tekstowy. Różni się od `@"..."` , możesz wskazać znak cudzysłowu, za pomocą pojedynczego cudzysłowu w ciągu.|
|`#`|[Dyrektywy kompilatora](../compiler-directives.md)<br /><br />[Typy elastyczne](../flexible-types.md)|<ul><li>Prefiksy takich jak dyrektywa preprocesora lub kompilatora `#light`.<br /></li><li>W przypadku użycia z typem, oznacza *elastycznym typem*, która odnosi się do typu lub jednego z jego typów pochodnych.<br /></li></ul>|
|`$`|Brak dostępnych informacji więcej.|<ul><li>Używana wewnętrznie do niektórych generowanych przez kompilator zmiennych i funkcji nazw.<br /></li></ul>|
|`%`|[Operatory arytmetyczne](arithmetic-operators.md)<br /><br />[Cytaty kodu](../code-quotations.md)|<ul><li>Oblicza pozostałą liczbę całkowitą.<br /></li><li>Używane dla wyrażeń łączenie kodu z kontrolą typów ofert.<br /></li></ul>|
|`%%`|[Cytaty kodu](../code-quotations.md)|<ul><li>Używane do zestawiania łączy wyrażeń cytaty kodu bez typu.<br /></li></ul>|
|`%?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza resztę liczby całkowitej, po prawej stronie Typ dopuszczający wartość null.<br /></li></ul>|
|`&`|[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>Oblicza adres wartości modyfikowalne do użycia podczas współpracy z innymi językami.<br /></li><li>Używane we wzorcach i.<br /></li></ul>|
|`&&`|[Operatory logiczne](boolean-operators.md)|<ul><li>Oblicza wartość logiczna i operacji.<br /></li></ul>|
|`&&&`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Oblicza operacja bitowa AND.<br /></li></ul>|
|`'`|[Literały](../literals.md)<br /><br />[Automatyczna generalizacja](../generics/automatic-generalization.md)|<ul><li>Rozgranicza literał pojedynczych znaków.<br /></li><li>Wskazuje, parametr typu ogólnego.<br /></li></ul>|
|<code>&#96;&#96;...&#96;&#96;</code>|Brak dostępnych informacji więcej.|<ul><li>Rozgranicza identyfikator, który nie byłyby dozwolonym identyfikatorem, takich jak słowa kluczowego języka.<br /></li></ul>|
|`( )`|[Typ jednostki](../unit-type.md)|<ul><li>Reprezentuje pojedynczą wartość tego typu jednostki.<br /></li></ul>|
|`(...)`|[Krotki](../tuples.md)<br /><br />[Przeładowanie operatora](../operator-overloading.md)|<ul><li>Określa kolejność, w którym określeń są oceniane.<br /></li><li>Rozgranicza spójnej kolekcji.<br /></li><li>Używane w definicjach operatora.<br /></li></ul>|
|`(*...*)`||<ul><li>Rozgranicza komentarz, który może obejmować wiele wierszy.<br /></li></ul>|
|<code>(&#124;...&#124;)</code>|[Wzorce aktywne](../active-patterns.md)|<ul><li>Rozgranicza — aktywny wzorzec. Nazywane również *klipy banany*.<br /></li></ul>|
|`*`|[Operatory arytmetyczne](arithmetic-operators.md)<br /><br />[Krotki](../tuples.md)<br /><br />[Jednostki miary](../units-of-measure.md)|<ul><li>Gdy jest używana jako operator binarny, mnoży lewej i prawej stronie.<br /></li><li>W typach wskazuje parowania w krotce.<br /></li><li>Używane w jednostkach miary typów.<br /></li></ul>|
|`*?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Mnoży lewej i prawej stronie, gdy po prawej stronie jest typ dopuszczający wartość null.<br /></li></ul>|
|`**`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Oblicza operacji potęgowania (`x ** y` oznacza `x` do potęgi równej `y`).<br /></li></ul>|
|`+`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Gdy jest używana jako operator binarny, dodaje lewej i prawej stronie.<br /></li><li>Gdy jest używana jako operator jednoargumentowy, wskazuje wartość dodatnią. (Formalnie, tworzy tę samą wartość ze znakiem bez zmian.)<br /></li></ul>|
|`+?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Dodaje lewej i prawej stronie, gdy po prawej stronie jest typ dopuszczający wartość null.<br /></li></ul>|
|`,`|[Krotki](../tuples.md)|<ul><li>Oddziela elementów krotki, lub parametry typu.<br /></li></ul>|
|`-`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Gdy jest używana jako operator binarny, odejmuje po prawej stronie z lewej strony.<br /></li><li>Gdy jest używana jako operator jednoargumentowy, wykonuje operację negacji.<br /></li></ul>|
|`-`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Odejmuje po prawej stronie z lewej strony, gdy po prawej stronie jest typ dopuszczający wartość null.<br /></li></ul>|
|`->`|[Funkcje](../functions/index.md)<br /><br />[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>W funkcji typy rozgranicza argumenty i zwracać wartości.<br /></li><li>Daje w wyniku wyrażenia (wyrażenia sekwencji); odpowiednikiem `yield` — słowo kluczowe.<br /></li><li>Używać w wyrażeniach dopasowania<br /></li></ul>|
|`.`|[Elementy członkowskie](../members/index.md)<br /><br />[Typy pierwotne](../primitive-types.md)|<ul><li>Uzyskuje dostęp do elementu członkowskiego, a oddziela poszczególne nazwy w pełni kwalifikowanej nazwy.<br /></li><li>Określa separator dziesiętny liczb zmiennoprzecinkowych.<br /></li></ul>|
|`..`|[Pętle: `for...in` wyrażenia](../loops-for-in-expression.md)|<ul><li>Określa zakres.<br /></li></ul>|
|`.. ..`|[Pętle: `for...in` wyrażenia](../loops-for-in-expression.md)|<ul><li>Określa zakres wraz z przyrostem.<br /></li></ul>|
|`.[...]`|[Tablice](../arrays.md)|<ul><li>Uzyskuje dostęp do elementu tablicy.<br /></li></ul>|
|`/`|[Operatory arytmetyczne](arithmetic-operators.md)<br /><br />[Jednostki miary](../units-of-measure.md)|<ul><li>Dzieli po lewej stronie (licznik), po prawej stronie (dzielnik).<br /></li><li>Używane w jednostkach miary typów.<br /></li></ul>|
|`/?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Dzieli po lewej stronie przez po prawej stronie, gdy po prawej stronie jest typ dopuszczający wartość null.<br /></li></ul>|
|`//`||<ul><li>Wskazuje początek jednowierszowego komentarza.<br /></li></ul>|
|`///`|[Dokumentacja XML](../xml-documentation.md)|<ul><li>Wskazuje komentarz XML.<br /></li></ul>|
|`:`|[Funkcje](../functions/index.md)|<ul><li>W adnotacji typu oddziela nazwy parametru lub elementu członkowskiego z typu.<br /></li></ul>|
|`::`|[Listy](../lists.md)<br /><br />[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>Tworzy listę. Element po lewej stronie jest dołączony do listy po prawej stronie.<br /></li><li>Używane w dopasowywania do wzorca, aby oddzielić części listy.<br /></li></ul>|
|`:=`|[Komórki odwołań](../reference-cells.md)|<ul><li>Przypisuje wartości do komórki odwołania.<br /></li></ul>|
|`:>`|[Rzutowanie i konwersje](../casting-and-conversions.md)|<ul><li>Konwertuje typu do typu, który znajduje się wyżej w hierarchii.<br /></li></ul>|
|`:?`|[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>Zwraca `true` Jeśli wartość jest zgodny z określonym typem; w przeciwnym razie zwraca `false` (operator typu testu).<br /></li></ul>|
|`:?>`|[Rzutowanie i konwersje](../casting-and-conversions.md)|<ul><li>Konwertuje typu do typu, który jest niżej w hierarchii.<br /></li></ul>|
|`;`|[Pełna składnia](../verbose-syntax.md)<br /><br />[Listy](../lists.md)<br /><br />[Rekordy](../records.md)|<ul><li>Oddziela wyrażenia (używane głównie w Pełna składnia).<br /></li><li>Oddziela elementy listy.<br /></li><li>Oddziela pola rekordu.<br /></li></ul>|
|`<`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Oblicza mniej-niż operacji.<br /></li></ul>|
|`<?`|[Operatory dopuszczające wartość null](nullable-operators.md)|Oblicza less than operacji, gdy po prawej stronie jest typ dopuszczający wartość null.|
|`<<`|[Funkcje](../functions/index.md)|<ul><li>Redaguj dwie funkcje w odwrotnej kolejności; drugim jest wykonywany pierwszy (operator kompozycji ze starszymi wersjami).<br /></li></ul>|
|`<<<`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Przesuwa bity w ilości po lewej stronie po lewej stronie przez liczbę bitów określoną po prawej stronie.<br /></li></ul>|
|`<-`|[Wartości](../values/index.md)|<ul><li>Przypisuje wartość do zmiennej.<br /></li></ul>|
|`<...>`|[Automatyczna generalizacja](../generics/automatic-generalization.md)|<ul><li>Rozgranicza parametrów typu.<br /></li></ul>|
|`<>`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` Jeśli po lewej stronie nie równa się po prawej stronie; w przeciwnym razie zwraca wartość false.<br /></li></ul>|
|`<>?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza operacji "nie jest równe", gdy po prawej stronie jest typ dopuszczający wartość null.<br /></li></ul>|
|`<=`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` Jeśli po lewej stronie jest mniejsza niż lub równe po prawej stronie; w przeciwnym razie zwraca `false`.<br /></li></ul>|
|`<=?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza operacji "mniejsze niż lub równe", gdy po prawej stronie jest typ dopuszczający wartość null.<br /></li></ul>|
|<code>&lt;&#124;</code>|[Funkcje](../functions/index.md)|<ul><li>Przekazuje wynik wyrażenia po prawej stronie do funkcji po lewej stronie (operator potoku do tyłu).<br /></li></ul>|
|<code>&lt;&#124;&#124;</code>|[Operatory. &#40; &#60; &#124; &#124; &#41; &#60;"U T1,"T2,"&#62; — funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhh-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Przekazuje krotki dwa argumenty po prawej stronie do funkcji po lewej stronie.<br /></li></ul>|
|<code>&lt;&#124;&#124;&#124;</code>|[Operatory. &#40; &#60; &#124; &#124; &#124; &#41; &#60;U "T1,"T2", T3,"&#62; — funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-%5bhhh-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Przekazuje krotki trzech argumentów po prawej stronie do funkcji po lewej stronie.<br /></li></ul>|
|`<@...@>`|[Cytaty kodu](../code-quotations.md)|<ul><li>Rozgranicza oferty kod maszynowy.<br /></li></ul>|
|`<@@...@@>`|[Cytaty kodu](../code-quotations.md)|<ul><li>Rozgranicza kodu bez typu oferty.<br /></li></ul>|
|`=`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` Jeśli po lewej stronie jest równy po prawej stronie; w przeciwnym razie zwraca `false`.<br /></li></ul>|
|`=?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza operacji "equal", gdy po prawej stronie jest typ dopuszczający wartość null.<br /></li></ul>|
|`==`|Nie dotyczy.|<ul><li>Nie jest używany w języku F#. Użyj `=` operacji porównania.<br /></li></ul>|
|`>`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` po lewej stronie jest większa niż po prawej stronie; w przeciwnym razie, zwraca wartość `false`.<br /></li></ul>|
|`>?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza operacji "większe niż", gdy po prawej stronie jest typ dopuszczający wartość null.<br /></li></ul>|
|`>>`|[Funkcje](../functions/index.md)|<ul><li>Redaguj dwóch funkcji (do przodu kompozycji operator).<br /></li></ul>|
|`>>>`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Przesunięcia bitów w ilości po lewej stronie w prawo o liczbę miejsc określony po prawej stronie.<br /></li></ul>|
|`>=`|[Operatory arytmetyczne](arithmetic-operators.md)|<ul><li>Zwraca `true` Jeśli po lewej stronie jest większa lub równa po prawej stronie; w przeciwnym razie zwraca `false`.<br /></li></ul>|
|`>=?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Oblicza operacji "większe lub równe", gdy po prawej stronie jest typ dopuszczający wartość null.<br /></li></ul>|
|`?`|[Parametry i argumenty](../parameters-and-arguments.md)|<ul><li>Określa opcjonalny argument.<br /></li><li>Użyte jako operator wywołań metod i właściwości dynamicznych. Należy podać Twojej własnej implementacji.<br /></li></ul>|
|`? ... <- ...`|Brak dostępnych informacji więcej.|<ul><li>Używane jako operatorowi ustawienie właściwości dynamicznych. Należy podać Twojej własnej implementacji.<br /></li></ul>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Równoważne operatory odpowiedniego bez? Prefiks, gdzie typ dopuszczający wartość null jest po lewej stronie.<br /></li></ul>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Równoważne operatory odpowiedniego bez? sufiks, gdzie typ dopuszczający wartość null jest po prawej stronie.<br /></li></ul>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[Operatory dopuszczające wartość null](nullable-operators.md)|<ul><li>Równoważne operatory odpowiedniego bez otaczającego znaki zapytania, których typy dopuszczające wartości null w obie strony.<br /></li></ul>|
|`@`|[Listy](../lists.md)<br /><br />[Ciągi](../strings.md)|<ul><li>Łączy dwie listy.<br /></li><li>Podczas zastosowane przed ciągiem literału, wskazuje, że ciąg ma być interpretowany dosłownie, za pomocą interpretation znaki ucieczki.<br /></li></ul>|
|`[...]`|[Listy](../lists.md)|<ul><li>Rozgranicza elementy listy.<br /></li></ul>|
|<code>[&#124;...&#124;]</code>|[Tablice](../arrays.md)|<ul><li>Rozgranicza elementy tablicy.<br /></li></ul>|
|`[<...>]`|[Atrybuty](../attributes.md)|<ul><li>Rozgranicza atrybutu.<br /></li></ul>|
|`\`|[Ciągi](../strings.md)|<ul><li>Specjalne następnego znaku; używane w znakowe i literały.<br /></li></ul>|
|`^`|[Statycznie rozwiązywane parametry typu](../generics/statically-resolved-type-parameters.md)<br /><br />[Ciągi](../strings.md)|<ul><li>Określa parametry typu, które muszą być rozwiązane w czasie kompilacji, a nie w czasie wykonywania.<br /></li><li>Łączy ciągi.<br /></li></ul>|
|`^^^`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Oblicza operacja bitowa wyłączny OR.<br /></li></ul>|
|`_`|[Wyrażenia dopasowania](../match-expressions.md)<br /><br />[Typy ogólne](../generics/index.md)|<ul><li>Określa wzór symboli wieloznacznych.<br /></li><li>Określa anonimowe parametru ogólnego.<br /></li></ul>|
|<code>&#96;</code>|[Automatyczna generalizacja](../generics/automatic-generalization.md)|<ul><li>Używana wewnętrznie w celu wskazania, parametr typu ogólnego.<br /></li></ul>|
|`{...}`|[Sekwencje](../sequences.md)<br /><br />[Rekordy](../records.md)|<ul><li>Rozgranicza wyrażenia sekwencji i wyrażenia obliczeń.<br /></li><li>Używane w definicjach rekordów.<br /></li></ul>|
|<code>&#124;</code>|[Wyrażenia dopasowania](../match-expressions.md)|<ul><li>Rozgranicza dopasowanie poszczególnych przypadkach indywidualnych przypadkach złożenia dyskryminowanego i wartości wyliczenia.<br /></li></ul>|
|<code>&#124;&#124;</code>|[Operatory logiczne](boolean-operators.md)|<ul><li>Oblicza operacji logicznego OR.<br /></li></ul>|
|<code>&#124;&#124;&#124;</code>|[Operatory bitowe](bitwise-operators.md)|<ul><li>Oblicza operacja bitowa OR.<br /></li></ul>|
|<code>&#124;></code>|[Funkcje](../functions/index.md)|<ul><li>Przekazuje jego wynik po lewej stronie do funkcji po prawej stronie (operator potoku przesyłania dalej).<br /></li></ul>|
|<code>&#124;&#124;></code>|[Operatory. &#40; &#124; &#124; &#62; &#41; &#60;"U T1,"T2,"&#62; — funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hh%5d-%5d%5b%27t1%2c%27t2%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Przekazuje krotki dwa argumenty po lewej stronie do funkcji po prawej stronie.<br /></li></ul>|
|<code>&#124;&#124;&#124;></code>|[Operatory. &#40; &#124; &#124; &#124; &#62; &#41; &#60;U "T1,"T2", T3,"&#62; — funkcja](https://msdn.microsoft.com/visualfsharpdocs/conceptual/operators.%5b-hhh%5d-%5d%5b%27t1%2c%27t2%2c%27t3%2c%27u%5d-function-%5bfsharp%5d)|<ul><li>Przekazuje krotki trzech argumentów po lewej stronie do funkcji po prawej stronie.<br /></li></ul>|
|`~~`|[Przeładowanie operatora](../operator-overloading.md)|<ul><li>Używane do deklarowania przeciążenia dla Jednoargumentowy operator negacji.<br /></li></ul>|
|`~~~`|[Operatory bitowe](bitwise-operators.md)|<ul><li>Oblicza operatora testu koniunkcji nie operacji.<br /></li></ul>|
|`~-`|[Przeładowanie operatora](../operator-overloading.md)|<ul><li>Używane do deklarowania przeciążenia jednoargumentowy minus operator.<br /></li></ul>|
|`~+`|[Przeładowanie operatora](../operator-overloading.md)|<ul><li>Używane do deklarowania przeciążenia Jednoargumentowy operator plus.<br /></li></ul>|

## <a name="operator-precedence"></a>Kolejność wykonywania działań

W poniższej tabeli przedstawiono kolejność pierwszeństwa operatorów i innych słów kluczowych wyrażenia w języku F#, w kolejności od najniższego pierwszeństwa, aby najwyższy priorytet. Na liście również jest łączność, jeśli ma to zastosowanie.

|Operator|Łączność|
|--------|-------------|
|`as`|Prawe|
|`when`|Prawe|
|<code>&#124;</code> (potok)|Lewe|
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
|`!=`*Op*, `<` *op*, `>` *op*, `=`, <code>&#124;</code> *op*, `&` *op* , `&`<br /><br />(w tym `<<<`, `>>>`, <code>&#124;&#124;&#124;</code>, `&&&`)|Lewe|
|`^`*OP*<br /><br />(w tym `^^^`)|Prawe|
|`::`|Prawe|
|`:?`|Nie asocjacyjne|
|`-`*Op*, `+` *op*|Dotyczy wrostkowe używa tych symboli|
|`*`*Op*, `/` *op*, `%` *op*|Lewe|
|`**`*OP*|Prawe|
|`f x` (funkcja aplikacji)|Lewe|
|<code>&#124;</code> (dopasowania do wzorca)|Prawe|
|przedrostkowe operatory (`+`*op*, `-` *op*, `%`, `%%`, `&`, `&&`, `!` *op*, `~` *op*)|Lewe|
|`.`|Lewe|
|`f(x)`|Lewe|
|`f<`*Typy*`>`|Lewe|
Język F# obsługuje niestandardowe przeciążenia operatora. Oznacza to, czy można zdefiniować własne operatorów. W poprzedniej tabeli *op* może być dowolną prawidłową sekwencją (prawdopodobnie puste), znaków operatora, wbudowany lub zdefiniowany przez użytkownika. W związku z tym można użyć tej tabeli można określić, jakie sekwencji znaków, które mają używać dla niestandardowy operator, aby osiągnąć żądany poziom priorytetu. Początkowe `.` znaki są ignorowane, gdy kompilator określa priorytet.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](../index.md)
- [Przeładowanie operatora](../operator-overloading.md)
