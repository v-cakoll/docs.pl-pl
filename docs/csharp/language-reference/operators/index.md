---
title: C#Operatorzy — C# odwołania
ms.date: 04/30/2019
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
ms.openlocfilehash: 99cf5b42700779a3eb48eb6452365056f5fa89ba
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306581"
---
# <a name="c-operators-c-reference"></a>C#operatory (C# odwołania)

C#zawiera szereg wstępnie zdefiniowanych operatory obsługiwane przez typy wbudowane. Na przykład [operatorów arytmetycznych](arithmetic-operators.md) wykonywać operacji arytmetycznych na wartościach operandy wbudowanych typów liczbowych i [logiczna operatorów logicznych](boolean-logical-operators.md) wykonywać operacje logiczne z [bool ](../keywords/bool.md) argumentów operacji.

Typ zdefiniowany przez użytkownika może doprowadzić do przeciążenia operatorów, aby zdefiniować odpowiednie zachowanie w przypadku argumentów operacji typu. Aby uzyskać więcej informacji, zobacz [operator](../keywords/operator.md) artykułu — słowo kluczowe.

Na poniższej liście sekcje C# operatorów, począwszy od najniższej najwyższy priorytet. Operatory w każdej sekcji udostępniać na tym samym poziomie pierwszeństwa.

## <a name="primary-operators"></a>Operatory podstawowe

Są to najwyższy pierwszeństwo operatorów.

[x.y](member-access-operators.md#member-access-operator-) — dostęp do elementu członkowskiego.

[x? y](member-access-operators.md#null-conditional-operators--and-) — wartość null, dostęp warunkowy elementu członkowskiego. Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.

[x? [t] ](member-access-operators.md#null-conditional-operators--and-) — wartość null elementu tablicy warunkowego lub wpisz dostęp indeksatora. Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.

[f(x)](member-access-operators.md#invocation-operator-) — metody wywołania lub delegować wywołania.

[&#91;x&#93; ](member-access-operators.md#indexer-operator-) — element w tablicy, lub wpisz dostęp indeksatora.

[x ++](arithmetic-operators.md#increment-operator-) — zwiększenie przyrostkowe. Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest większa o jeden (zazwyczaj dodaje liczbę całkowitą 1).

[x —](arithmetic-operators.md#decrement-operator---) — zmniejszenie przyrostkowe. Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).

[nowe](../keywords/new-operator.md) — podczas tworzenia wystąpienia typu.

[TypeOf](type-testing-and-conversion-operators.md#typeof-operator) — zwraca <xref:System.Type> obiekt reprezentujący argument.

[zaznaczone](../keywords/checked.md) — umożliwia przepełnienie sprawdzania pod kątem operacji liczby całkowitej.

[unchecked](../keywords/unchecked.md) — wyłącza przepełnienie sprawdzania pod kątem operacji liczby całkowitej. Jest to domyślne zachowanie kompilatora.

[wartość Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) — tworzy domyślną wartość typu T.

[nameof](../keywords/nameof.md) -uzyskuje proste (niekwalifikowanej) Nazwa zmiennej, typu lub składowej jako ciąg stałej.

[Delegowanie](../../programming-guide/statements-expressions-operators/anonymous-methods.md) — deklaruje i zwraca wystąpienie delegata.

[Operator sizeof](../keywords/sizeof.md) — zwraca rozmiar w bajtach argument typu.

[stackalloc](stackalloc.md) -przydziela blok pamięci na stosie.

[->](pointer-related-operators.md#pointer-member-access-operator--) — operację wskaźnika pośredniego w połączeniu z dostępu do elementu członkowskiego.

## <a name="unary-operators"></a>Operatory jednoargumentowe

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[+ x](addition-operator.md) — zwraca wartość x.

[-x](subtraction-operator.md) — negacji liczbowych.

[\!x](boolean-logical-operators.md#logical-negation-operator-) — negacji logicznej.

[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) — uzupełnienie bitowe.

[++ x](arithmetic-operators.md#increment-operator-) — przedrostkowe. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu z wartością x, który jest jednym większą (zazwyczaj dodaje liczbę całkowitą 1).

[--x](arithmetic-operators.md#decrement-operator---) — przedrostkowe. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartości x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).

[(T) x](type-testing-and-conversion-operators.md#cast-operator-) — typ rzutowania.

[await](../keywords/await.md) — czeka `Task`.

[& x](pointer-related-operators.md#address-of-operator-) — adres zmiennej.

[* x](pointer-related-operators.md#pointer-indirection-operator-) — operację wskaźnika pośredniego lub wyłuskania.

[TRUE — operator](true-false-operators.md) — zwraca [bool](../keywords/bool.md) wartość `true` do wskazania, że argument jest zdecydowanie true.

[FALSE — operator](true-false-operators.md) — zwraca [bool](../keywords/bool.md) wartość `true` do wskazania, że argument jest zdecydowanie false.

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

[x \< y](comparison-operators.md#less-than-operator-) — mniejsze niż (wartość true, jeśli x jest mniejsza niż y).

[x > y](comparison-operators.md#greater-than-operator-) — większa (wartość true, jeśli x jest większa niż y).

[x \<= y](comparison-operators.md#less-than-or-equal-operator-) — mniejsze niż lub równe.

[x > = y](comparison-operators.md#greater-than-or-equal-operator-) — większa lub równa.

[jest](type-testing-and-conversion-operators.md#is-operator) — wpisz zgodności. Zwraca `true` Jeśli ocenianą Lewy argument operacji może być rzutowany na typ określony przez prawy operand.

[jako](type-testing-and-conversion-operators.md#as-operator) — konwersja typu. Zwraca lewy operand rzutowany na typ określony przez prawy operand, ale `as` zwraca `null` gdzie `(T)x` spowoduje zgłoszenie wyjątku.

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

## <a name="assignment-and-lambda-operators"></a>Operatory przypisania i lambda

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x = y](assignment-operator.md) — przypisania.

[x += y](arithmetic-operators.md#compound-assignment) — przyrostu. Dodaj wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość. Jeśli `x` wyznacza [zdarzeń](../keywords/event.md), następnie `y` musi być odpowiednia metoda który C# dodaje jako program obsługi zdarzeń.

[x-= y](arithmetic-operators.md#compound-assignment) — zmniejszanie. Odejmuje wartość `y` od wartości `x`, zapisują wynik w `x`i zwraca nową wartość. Jeśli `x` wyznacza [zdarzeń](../keywords/event.md), następnie `y` musi być odpowiednia metoda który C# usuwa jako program obsługi zdarzeń.

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

- [C#Odwołanie](../index.md)
- [Operatory](../../programming-guide/statements-expressions-operators/operators.md)
- [Operatory z możliwością przeciążenia](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
