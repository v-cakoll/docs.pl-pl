---
title: Operatory języka C#
ms.date: 04/04/2018
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: f4267caeb6301950b9f6a8b9545a47b9f48e7920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689817"
---
# <a name="c-operators"></a>Operatory języka C#

C# zawiera wiele operatorów, które są symbolami określającymi operacje (matematycznych, indeksowanie, wywołanie funkcji itp.) do wykonania w wyrażeniu. Możesz [przeciążenia](../../programming-guide/statements-expressions-operators/overloadable-operators.md) wiele operatorów, aby zmienić ich znaczenia w przypadku zastosowania do typu zdefiniowanego przez użytkownika.

Operacje na typach całkowitoliczbowych (takie jak `==`, `!=`, `<`, `>`, `&`, `|`) są ogólnie dozwolone w wyliczeniu (`enum`) typy.

Poniższe rozdziały zawierają listę operatorów języka C# od o najwyższym priorytecie do najniższego. Operatory w każdej sekcji udostępniać na tym samym poziomie pierwszeństwa.

## <a name="primary-operators"></a>Operatory podstawowe

Są to najwyższy pierwszeństwo operatorów.

[x.y](member-access-operator.md) — dostęp do elementu członkowskiego.

[x? y](null-conditional-operators.md) — wartość null, dostęp warunkowy elementu członkowskiego. Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.

[x? [t] ](null-conditional-operators.md) — wartość null, dostęp warunkowy indeksu. Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.

[f(x)](invocation-operator.md) — wywołania funkcji.

[&#91;x&#93; ](index-operator.md) — indeksowanie obiektu agregacji.

[x ++](arithmetic-operators.md#increment-operator-) — zwiększenie przyrostkowe. Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest większa o jeden (zazwyczaj dodaje liczbę całkowitą 1).

[x —](arithmetic-operators.md#decrement-operator---) — zmniejszenie przyrostkowe. Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).

[nowe](../keywords/new-operator.md) — podczas tworzenia wystąpienia typu.

[TypeOf](../keywords/typeof.md) — zwraca <xref:System.Type> obiekt reprezentujący argument.

[zaznaczone](../keywords/checked.md) — umożliwia przepełnienie sprawdzania pod kątem operacji liczby całkowitej.

[unchecked](../keywords/unchecked.md) — wyłącza przepełnienie sprawdzania pod kątem operacji liczby całkowitej. Jest to domyślne zachowanie kompilatora.

[wartość Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) — tworzy domyślną wartość typu T.

[Delegowanie](../../programming-guide/statements-expressions-operators/anonymous-methods.md) — deklaruje i zwraca wystąpienie delegata.

[Operator sizeof](../keywords/sizeof.md) — zwraca rozmiar w bajtach argument typu.

[->](dereference-operator.md) — wyłuskanie wskaźnika w połączeniu z dostępu do elementu członkowskiego.

## <a name="unary-operators"></a>Operatory jednoargumentowe

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[+ x](addition-operator.md) — zwraca wartość x.

[-x](subtraction-operator.md) — negacji liczbowych.

[\!x](boolean-logical-operators.md#logical-negation-operator-) — negacji logicznej.

[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) — uzupełnienie bitowe.

[++ x](arithmetic-operators.md#increment-operator-) — przedrostkowe. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu z wartością x, który jest jednym większą (zazwyczaj dodaje liczbę całkowitą 1).

[--x](arithmetic-operators.md#decrement-operator---) — przedrostkowe. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartości x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).

[(T) x](invocation-operator.md) — typ rzutowania.

[await](../keywords/await.md) — czeka `Task`.

[& x](and-operator.md) — adres.

[* x](multiplication-operator.md) — dereferencji.

[TRUE — operator](../keywords/true-false-operators.md) — zwraca [bool](../keywords/bool.md) wartość `true` do wskazania, że argument jest zdecydowanie true.

[FALSE — operator](../keywords/true-false-operators.md) — zwraca [bool](../keywords/bool.md) wartość `true` do wskazania, że argument jest zdecydowanie false.

## <a name="multiplicative-operators"></a>Operatory multiplikatywne

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x * y](arithmetic-operators.md#multiplication-operator-) — mnożenia.

[x / y](arithmetic-operators.md#division-operator-) — dzielenia. Jeśli argumenty są liczbami całkowitymi, wynik jest liczbą całkowitą obcięte w kierunku zera (na przykład `-7 / 2 is -3`).

[x, % y](arithmetic-operators.md#remainder-operator-) — resztę. Jeśli argumenty są liczbami całkowitymi, to zwraca resztę z dzielenia podziału x, y.  Jeśli `q = x / y` i `r = x % y`, następnie `x = q * y + r`.

## <a name="additive-operators"></a>Operatory addytywne

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x + y](arithmetic-operators.md#addition-operator-) — Dodawanie.

[x – y](arithmetic-operators.md#subtraction-operator--) — odejmowania.

## <a name="shift-operators"></a>Operatory przesunięcia

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) — przesunięcia bitów w lewo i wypełnić zero po prawej stronie.

[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) — shift bits po prawej stronie. Jeśli Lewy argument operacji jest `int` lub `long`, a następnie po lewej stronie bity są wypełnione bitu znaku. Jeśli Lewy argument operacji jest `uint` lub `ulong`, a następnie po lewej stronie bity są wypełnione zero.

## <a name="relational-and-type-testing-operators"></a>Operatory relacyjne i badania typu

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x \< y](less-than-operator.md) — mniejsze niż (wartość true, jeśli x jest mniejsza niż y).

[x > y](greater-than-operator.md) — większa (wartość true, jeśli x jest większa niż y).

[x \<= y](less-than-equal-operator.md) — mniejsze niż lub równe.

[x > = y](greater-than-equal-operator.md) — większa lub równa.

[jest](../keywords/is.md) — wpisz zgodności. Zwraca wartość PRAWDA, jeśli ocenianą lewy operand mogą być rzutowane na typ określony w prawy operand (typu statycznego).

[jako](../keywords/as.md) — konwersja typu. Zwraca lewy operand rzutowany na typ określony przez prawy operand (typ statycznej), ale `as` zwraca `null` gdzie `(T)x` spowoduje zgłoszenie wyjątku.

## <a name="equality-operators"></a>Operatory równości

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x == y](equality-operators.md#equality-operator-) — równości. Domyślnie dla odwołania do typów innych niż `string`ten zwraca odwołania równości (test tożsamości). Jednak typów może doprowadzić do przeciążenia `==`, więc jeśli zgodne z zamiarami użytkownika jest, aby sprawdzić tożsamość, najlepiej użyć `ReferenceEquals` metody `object`.

[x! = y](equality-operators.md#inequality-operator-) — są nierówne. Zobacz komentarz dotyczący `==`. Jeśli typem przeciążenia `==`, a następnie przeciąża musi `!=`.

## <a name="logical-and-operator"></a>Operator logiczny AND

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

`x & y` — [operator logiczny oraz](boolean-logical-operators.md#logical-and-operator-) dla `bool` operandy lub [iloczynu bitowego AND logiczne](bitwise-and-shift-operators.md#logical-and-operator-) przypadku argumentów operacji typu całkowitoliczbowego.

## <a name="logical-xor-operator"></a>Operatora logicznego XOR

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

`x ^ y` — [XOR logiczne](boolean-logical-operators.md#logical-exclusive-or-operator-) dla `bool` operandy lub [iloczynu bitowego XOR logiczne](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) przypadku argumentów operacji typu całkowitoliczbowego.

## <a name="logical-or-operator"></a>Operator logiczny OR

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

`x | y` — [logiczne OR](boolean-logical-operators.md#logical-or-operator-) dla `bool` operandy lub [bitowe OR logiczne](bitwise-and-shift-operators.md#logical-or-operator-) przypadku argumentów operacji typu całkowitoliczbowego.

## <a name="conditional-and-operator"></a>Operator warunkowy AND

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) — operatora logicznego AND. Jeśli pierwszy operand zwróci wartość false, następnie C# nie może oszacować drugiego operandu.

## <a name="conditional-or-operator"></a>Operator warunkowy OR

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) — operator logiczny lub. Jeśli pierwszy argument zwraca wartość true, następnie C# nie może oszacować drugiego operandu.

## <a name="null-coalescing-operator"></a>Operatorem łączenia wartości null

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x? y](null-coalescing-operator.md) — zwraca `x` jeśli je ma wartość inną niż`null`; w przeciwnym razie zwraca `y`.

## <a name="conditional-operator"></a>Operator warunkowy

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[t? x: y](conditional-operator.md) — w przypadku testowania `t` daje w wyniku wartość true, a następnie oceniana i zwracana `x`; w przeciwnym razie oceniana i zwracana `y`.

## <a name="assignment-and-lambda-operators"></a>Operatory przypisania i Lambda

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x = y](assignment-operator.md) — przypisania.

[x += y](addition-assignment-operator.md) — przyrostu. Dodaj wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość. Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, dodającego C# jako program obsługi zdarzeń.

[x-= y](subtraction-assignment-operator.md) — zmniejszanie. Odejmuje wartość `y` od wartości `x`, zapisują wynik w `x`i zwraca nową wartość. Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję C# usuwa jako program obsługi zdarzeń.

[x * = y](arithmetic-operators.md#compound-assignment) — mnożenie i przypisanie. Mnoży wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość.

[x / = y](arithmetic-operators.md#compound-assignment) — dzielenie i przypisanie. Dzieli wartość `x` przez wartość `y`, zapisują wynik w `x`i zwraca nową wartość.

[x % = y](arithmetic-operators.md#compound-assignment) — remainder przypisania. Dzieli wartość `x` przez wartość `y`, przechowywać resztę w `x`i zwraca nową wartość.

[x & = y](boolean-logical-operators.md#compound-assignment) — i przypisanie. I wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.

[x &#124;= y](boolean-logical-operators.md#compound-assignment) — i przypisanie. LUB wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.

[x ^ = y](boolean-logical-operators.md#compound-assignment) — przypisanie XOR. XOR wartość z `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.

[x << = y](bitwise-and-shift-operators.md#compound-assignment) — przypisania przesunięcia w lewo. Przesuwa wartość `x` po lewej stronie, `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.

[x >> = y](bitwise-and-shift-operators.md#compound-assignment) — przypisania przesunięcia w prawo. Przesuwa wartość `x` bezpośrednio przez `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.

[=>](lambda-operator.md) — deklaracji lambda.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#](../../index.md)
- [Operatory z możliwością przeciążenia](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [Słowa kluczowe języka C#](../keywords/index.md)
