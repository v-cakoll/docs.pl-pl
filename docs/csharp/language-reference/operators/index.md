---
title: C#Operatory — C# odwołanie
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
ms.openlocfilehash: b6a1cc3ced3205037eb5b83ac3841efbfbd1b5b9
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331215"
---
# <a name="c-operators-c-reference"></a>C#Operatory (C# odwołanie)

C#udostępnia wiele wstępnie zdefiniowanych operatorów obsługiwanych przez typy wbudowane. Na przykład [Operatory arytmetyczne](arithmetic-operators.md) wykonują operacje arytmetyczne przy użyciu operandów wbudowanych typów liczbowych i logicznych [Operatory logiczne](boolean-logical-operators.md) wykonują operacje logiczne przy użyciu operandów [bool](../keywords/bool.md) .

Typ zdefiniowany przez użytkownika może przeciążać pewne operatory, aby zdefiniować odpowiednie zachowanie dla operandów tego typu. Aby uzyskać więcej informacji, zobacz przeciążanie [operatora](operator-overloading.md).

W poniższych sekcjach znajdują się C# operatory zaczynające się od najwyższego pierwszeństwa. Operatory w każdej sekcji mają ten sam poziom pierwszeństwa.

## <a name="primary-operators"></a>Operatory podstawowe

Są to operatory najwyższej kolejności.

[x. y](member-access-operators.md#member-access-operator-) — dostęp do elementu członkowskiego.

[x?. y](member-access-operators.md#null-conditional-operators--and-) – null warunkowy dostęp do elementu członkowskiego. Zwraca `null` wartość, jeśli argument operacji po lewej stronie ma `null`wartość.

[x? [y]](member-access-operators.md#null-conditional-operators--and-) -null element tablicy warunkowej lub dostęp do indeksatora typu. Zwraca `null` wartość, jeśli argument operacji po lewej stronie ma `null`wartość.

[f (x)](member-access-operators.md#invocation-operator-) — wywołanie metody lub delegat wywołania.

dostęp do elementu Array [&#91;x&#93; ](member-access-operators.md#indexer-operator-) lub typu indeksatora.

[x + +](arithmetic-operators.md#increment-operator-) — przyrostek Przyrostkowy. Zwraca wartość x, a następnie aktualizuje lokalizację magazynu o wartości x, która jest większa (zazwyczaj dodaje liczbę całkowitą 1).

[x--](arithmetic-operators.md#decrement-operator---) — zmniejszenie przyrostu. Zwraca wartość x, a następnie aktualizuje lokalizację magazynu o wartości x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).

[nowe](new-operator.md) — Tworzenie wystąpienia typu.

[typeof](type-testing-and-conversion-operators.md#typeof-operator) — zwraca <xref:System.Type> obiekt reprezentujący operand.

[zaznaczone](../keywords/checked.md) — włącza sprawdzanie przepełnienia dla operacji całkowitych.

[](../keywords/unchecked.md) unchecked — wyłącza sprawdzanie przepełnienia dla operacji całkowitych. Jest to domyślne zachowanie kompilatora.

[Default (T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) — tworzy wartość domyślną typu T.

[nameof](nameof.md) — umożliwia uzyskanie prostej (niekwalifikowanej) nazwy zmiennej, typu lub składowej jako ciągu stałej.

[Delegate](delegate-operator.md) — deklaruje i zwraca wystąpienie delegata.

[sizeof](../keywords/sizeof.md) — zwraca rozmiar operandu typu w bajtach.

[stackalloc](stackalloc.md) — przydziela blok pamięci na stosie.

[->](pointer-related-operators.md#pointer-member-access-operator--)– wskaźnik pośredni połączony z dostępem do elementu członkowskiego.

## <a name="unary-operators"></a>Operatory jednoargumentowe

Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[+ x](addition-operator.md) — zwraca wartość x.

[-x](subtraction-operator.md) — Negacja liczbowa.

x — Negacja logiczna. [ \!](boolean-logical-operators.md#logical-negation-operator-)

[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) — uzupełnienie bitowe.

[+ + x](arithmetic-operators.md#increment-operator-) — przyrost prefiksu. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartość x, która jest większa (zazwyczaj dodaje liczbę całkowitą 1).

[--x](arithmetic-operators.md#decrement-operator---) — zmniejszenie prefiksu. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartość x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).

[(T) x](type-testing-and-conversion-operators.md#cast-operator-) — rzutowanie typów.

[await](../keywords/await.md) — czeka na `Task`.

[& x](pointer-related-operators.md#address-of-operator-) — adres zmiennej.

[* x](pointer-related-operators.md#pointer-indirection-operator-) — wskaźnik pośredni lub wyłuskanie.

[true operator](true-false-operators.md) — zwraca `true` wartość [logiczną](../keywords/bool.md) , aby wskazać, że operand ma wartość true.

[operator false](true-false-operators.md) — zwraca `true` wartość [logiczną](../keywords/bool.md) , aby wskazać, że operand ma wartość false.

## <a name="multiplicative-operators"></a>Operatory multiplikatywne

Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[x * y](arithmetic-operators.md#multiplication-operator-) — mnożenia.

dzielenie [x/y](arithmetic-operators.md#division-operator-) . Jeśli operandy są liczbami całkowitymi, wynik jest liczbą całkowitą obciętym do zera (na `-7 / 2 is -3`przykład).

[x% y](arithmetic-operators.md#remainder-operator-) — reszta. Jeśli operandy są liczbami całkowitymi, to zwraca resztę dzielenia x przez y.  If `q = x / y` i `r = x % y`, then `x = q * y + r`.

## <a name="additive-operators"></a>Operatory addytywne

Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

Dodawanie [x + y](arithmetic-operators.md#addition-operator-) .

[x – y](arithmetic-operators.md#subtraction-operator--) — odejmowanie.

## <a name="shift-operators"></a>Operatory przesunięcia

Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) — przesunięcie w lewo i wypełnienie z zerem po prawej stronie.

[x > > y](bitwise-and-shift-operators.md#right-shift-operator-) — prawo do usługi BITS. Jeśli argument operacji po lewej `int` stronie `long`ma wartość lub, lewe bity są wypełnione bitem znaku. Jeśli Lewy argument operacji jest `uint` lub `ulong`, lewy bity są wypełnione zerem.

## <a name="relational-and-type-testing-operators"></a>Operatory relacyjne i testowe typu

Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[ x\< y](comparison-operators.md#less-than-operator-) – mniejsze niż (true, jeśli x jest mniejsze niż y).

[x > y](comparison-operators.md#greater-than-operator-) – większe niż (true, jeśli x jest większe niż y).

[ x\<= y](comparison-operators.md#less-than-or-equal-operator-) – mniejsze niż lub równe.

[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – większe niż lub równe.

[jest](type-testing-and-conversion-operators.md#is-operator) — zgodność typów. Zwraca `true` czy oszacowany operand z lewej strony może być rzutowany na typ określony przez prawy operand.

Konwersja typu " [as](type-testing-and-conversion-operators.md#as-operator) ". Zwraca rzutowanie lewego operandu do typu określonego przez prawy operand, ale `as` zwraca `null` , gdzie `(T)x` zostałby zgłosić wyjątek.

## <a name="equality-operators"></a>Operatory równości

Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[x = = t](equality-operators.md#equality-operator-) — równość. Domyślnie dla typów odwołań innych niż `string`, zwraca równość odwołania (test tożsamości). Jednak typy mogą przeciążać `==`, więc jeśli chcesz przetestować tożsamość, najlepszym rozwiązaniem jest `ReferenceEquals` użycie metody w `object`.

[x! = y](equality-operators.md#inequality-operator-) — nie równa się. Zobacz komentarz dla `==`. W przypadku przeciążenia `==`typów, należy przeciążać `!=`.

## <a name="logical-and-operator"></a>Operator logiczny AND

Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

`x & y`— [logiczne i](boolean-logical-operators.md#logical-and-operator-) dla `bool` operandów lub [koniunkcji bitowej oraz](bitwise-and-shift-operators.md#logical-and-operator-) dla operandów typów całkowitych.

## <a name="logical-xor-operator"></a>Logiczny operator XOR

Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

`x ^ y`— [logiczna XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) dla `bool` operandów lub [bitowe logiczne XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) dla operandów typów całkowitych.

## <a name="logical-or-operator"></a>Operator logiczny OR

Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

`x | y`— [logiczne lub](boolean-logical-operators.md#logical-or-operator-) dla `bool` operandów lub [koniunkcji logicznej lub](bitwise-and-shift-operators.md#logical-or-operator-) dla operandów typów całkowitych.

## <a name="conditional-and-operator"></a>Operator warunkowy i

Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) — koniunkcja i. W `x` przypadku wartości zwraca `false`wartość, `y` a następnie nie jest szacowana.

## <a name="conditional-or-operator"></a>Operator warunkowy OR

Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[ &#124; x &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) — logiczne lub. W `x` przypadku wartości zwraca `true`wartość, `y` a następnie nie jest szacowana.

## <a name="null-coalescing-operator"></a>Operator łączenia wartości null

Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[x?? y](null-coalescing-operator.md) — zwraca `x` czy nie jest-`null`; w przeciwnym razie zwraca `y`.

## <a name="conditional-operator"></a>Operator warunkowy

Ten operator ma wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[t? x: y](conditional-operator.md) — Jeśli test `t` ma wartość true, należy obliczyć i zwrócić `x`; w przeciwnym razie obliczyć i zwrócić `y`.

## <a name="assignment-and-lambda-operators"></a>Przypisanie i operatory lambda

Te operatory mają wyższy priorytet niż Następna sekcja i niższy priorytet niż poprzednia sekcja.

[x = y](assignment-operator.md) — przypisanie.

[x + = y](arithmetic-operators.md#compound-assignment) — przyrost. Dodaj wartość `y` do `x`wartości, Zapisz wynik w `x`i zwróć nową wartość. Jeśli `x` wyznacza C# [zdarzenie, musi być](../keywords/event.md)odpowiednią metodą, która dodaje jako procedurę obsługi zdarzeń. `y`

[x-= y](arithmetic-operators.md#compound-assignment) – zmniejszenie. Odejmij wartość `y` od `x`wartości, Zapisz wynik w `x`i zwróć nową wartość. Jeśli `x` wyznacza C# [zdarzenie, musi być](../keywords/event.md)odpowiednią metodą, która usuwa jako procedurę obsługi zdarzeń. `y`

[x * =](arithmetic-operators.md#compound-assignment) przypisanie do mnożenia y. Pomnóż wartość `y` do `x`wartości, Zapisz wynik w `x`i zwróć nową wartość.

przypisanie dzielenia [x/= y](arithmetic-operators.md#compound-assignment) . Podziel wartość `x` przez `y`wartość, Zapisz wynik w `x`i zwróć nową wartość.

przypisanie do pozostałej liczby [x% = y](arithmetic-operators.md#compound-assignment) . Podziel wartość `x` przez `y`wartość, Zapisz resztę w `x`i zwróć nową wartość.

[x & = y](boolean-logical-operators.md#compound-assignment) — i przypisanie. I wartość `y` z `x`wartością, Zapisz wynik w `x`i zwróć nową wartość.

[x &#124;= y](boolean-logical-operators.md#compound-assignment) — lub przypisanie. Lub wartość `y` o `x`wartości, Zapisz wynik w `x`i zwróć nową wartość.

[x ^ = y](boolean-logical-operators.md#compound-assignment) — przypisanie XOR. XOR wartość `y` o `x`wartości, Zapisz wynik w `x`i zwróć nową wartość.

[x < < = y](bitwise-and-shift-operators.md#compound-assignment) — przypisanie do lewej przesunięcia. Przenieś wartość z `x` lewej strony według `y` miejsc, Zapisz wynik w `x`i zwróć nową wartość.

[x > > = y](bitwise-and-shift-operators.md#compound-assignment) — przypisanie do prawej strony. Przesuń wartość `x` w `y`prawowedługmiejsc ,Zapiszwynikizwróćnowąwartość`x`.

[=>](lambda-operator.md)— Deklaracja lambda.

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory](../../programming-guide/statements-expressions-operators/operators.md)
