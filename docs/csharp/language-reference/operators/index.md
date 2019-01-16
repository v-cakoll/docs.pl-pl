---
title: C#Operatory
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
ms.openlocfilehash: 6380fa4ec99f598be0d01db1061900520e94d5f1
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333411"
---
# <a name="c-operators"></a>C#Operatory

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

[x ++](increment-operator.md) — zwiększenie przyrostkowe. Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest większa o jeden (zazwyczaj dodaje liczbę całkowitą 1).

[x —](decrement-operator.md) — zmniejszenie przyrostkowe. Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).

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

[\!x](logical-negation-operator.md) — negacji logicznej.

[~ x](bitwise-complement-operator.md) — uzupełnienie bitowe.

[++ x](increment-operator.md) — przedrostkowe. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu z wartością x, który jest jednym większą (zazwyczaj dodaje liczbę całkowitą 1).

[--x](decrement-operator.md) — przedrostkowe. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartości x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).

[(T) x](invocation-operator.md) — typ rzutowania.

[await](../keywords/await.md) — czeka `Task`.

[& x](and-operator.md) — adres.

[* x](multiplication-operator.md) — dereferencji.

## <a name="multiplicative-operators"></a>Operatory multiplikatywne

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x * y](multiplication-operator.md) — mnożenia.

[x / y](division-operator.md) — dzielenia. Jeśli argumenty są liczbami całkowitymi, wynik jest liczbą całkowitą obcięte w kierunku zera (na przykład `-7 / 2 is -3`).

[x, % y](remainder-operator.md) — resztę. Jeśli argumenty są liczbami całkowitymi, to zwraca resztę z dzielenia podziału x, y.  Jeśli `q = x / y` i `r = x % y`, następnie `x = q * y + r`.

## <a name="additive-operators"></a>Operatory addytywne

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x + y](addition-operator.md) — Dodawanie.

[x – y](subtraction-operator.md) — odejmowania.

## <a name="shift-operators"></a>Operatory przesunięcia

Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x <\< y](left-shift-operator.md) — przesunięcia bitów w lewo i wypełnić zero po prawej stronie.

[x >> y](right-shift-operator.md) — shift bits po prawej stronie. Jeśli Lewy argument operacji jest `int` lub `long`, a następnie po lewej stronie bity są wypełnione bitu znaku. Jeśli Lewy argument operacji jest `uint` lub `ulong`, a następnie po lewej stronie bity są wypełnione zero.

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

[x == y](equality-comparison-operator.md) — równości. Domyślnie dla odwołania do typów innych niż `string`ten zwraca odwołania równości (test tożsamości). Jednak typów może doprowadzić do przeciążenia `==`, więc jeśli zgodne z zamiarami użytkownika jest, aby sprawdzić tożsamość, najlepiej użyć `ReferenceEquals` metody `object`.

[x! = y](not-equal-operator.md) — są nierówne. Zobacz komentarz dotyczący `==`. Jeśli typem przeciążenia `==`, a następnie przeciąża musi `!=`.

## <a name="logical-and-operator"></a>Operator logiczny AND

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x i y](and-operator.md) — operatora logicznego lub bitowego AND. Zazwyczaj można użyć tego z typami całkowitymi i `enum` typów.

## <a name="logical-xor-operator"></a>Operatora logicznego XOR

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x ^ y](xor-operator.md) — logicznych lub bitowe XOR. Zazwyczaj można użyć tego z typami całkowitymi i `enum` typów.

## <a name="logical-or-operator"></a>Operator logiczny OR

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x &#124; y](or-operator.md) — logicznych lub bitowe OR. Zazwyczaj można użyć tego z typami całkowitymi i `enum` typów.

## <a name="conditional-and-operator"></a>Operator warunkowy AND

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x & & y](conditional-and-operator.md) — operatora logicznego AND. Jeśli pierwszy operand zwróci wartość false, następnie C# nie może oszacować drugiego operandu.

## <a name="conditional-or-operator"></a>Operator warunkowy OR

Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.

[x &#124; &#124; y](conditional-or-operator.md) — operator logiczny lub. Jeśli pierwszy argument zwraca wartość true, następnie C# nie może oszacować drugiego operandu.

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

[x-= y](subtraction-assignment-operator.md) — zmniejszanie. Odejmuje wartość `y` od wartości `x`, zapisują wynik w `x`i zwraca nową wartość. Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, który C# usuwa jako program obsługi zdarzeń

[x * = y](multiplication-assignment-operator.md) — mnożenie i przypisanie. Mnoży wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość.

[x / = y](division-assignment-operator.md) — dzielenie i przypisanie. Dzieli wartość `x` przez wartość `y`, zapisują wynik w `x`i zwraca nową wartość.

[x % = y](remainder-assignment-operator.md) — remainder przypisania. Dzieli wartość `x` przez wartość `y`, przechowywać resztę w `x`i zwraca nową wartość.

[x & = y](and-assignment-operator.md) — i przypisanie. I wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.

[x &#124;= y](or-assignment-operator.md) — i przypisanie. LUB wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.

[x ^ = y](xor-assignment-operator.md) — przypisanie XOR. XOR wartość z `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.

[x << = y](left-shift-assignment-operator.md) — przypisania przesunięcia w lewo. Przesuwa wartość `x` po lewej stronie, `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.

[x >> = y](right-shift-assignment-operator.md) — przypisania przesunięcia w prawo. Przesuwa wartość `x` bezpośrednio przez `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.

[=>](lambda-operator.md) — deklaracji lambda.

## <a name="arithmetic-overflow"></a>Przepełnienie arytmetyczne

Operatory arytmetyczne ([+](addition-operator.md), [ - ](subtraction-operator.md), [ * ](multiplication-operator.md), [ / ](division-operator.md)) może generuje wyniki, które wykraczają poza zakres możliwych wartości dla typu liczbowego. Należy zapoznać się z sekcją na konkretnym operatorze, aby uzyskać szczegółowe informacje, ale ogólnie rzecz biorąc:

- Arytmetyka przepełnienia liczb całkowitych zgłasza <xref:System.OverflowException> lub odrzuca najbardziej znaczące bity wyniku. Dzielenie liczby całkowitej przez zero zawsze generuje wyjątek <xref:System.DivideByZeroException>.

   Jeśli występuje przepełnienie liczby całkowitej, co się stanie, zależy od kontekstu wykonywania, który może być [zaznaczony lub niezaznaczony](../keywords/checked-and-unchecked.md). W kontekście sprawdzanym <xref:System.OverflowException> zgłaszany. W kontekście niesprawdzanym najbardziej znaczące bity wyniku są odrzucane, a wykonywanie jest kontynuowane. W związku z tym C# umożliwia wybranie obsługi lub zignorowanie przepełnienie. Domyślnie operacje arytmetyczne występują w *unchecked* kontekstu.

   Oprócz operacje arytmetyczne rzutowania typu całkowitego do typu całkowitego mogą spowodować przepełnienie (np. Jeśli zrzutować [długie](../keywords/long.md) do [int](../keywords/int.md)) i podlegają wykonaniu sprawdzanemu lub niesprawdzanemu. Jednakże operatory bitowe i operatory przesunięcia nigdy nie powodują przepełnienia.

- Zmiennoprzecinkowe przepełnienia arytmetycznego lub dzielenie przez zero nigdy nie zgłasza wyjątek, ponieważ typy zmiennoprzecinkowe są oparte na standardzie IEEE 754, dlatego mają mechanizmy reprezentowania nieskończoności i NaN (nieliczbową).

- [Dziesiętna](../keywords/decimal.md) przepełnienie arytmetyczne zawsze wyrzuca <xref:System.OverflowException>. Dzielenie dziesiętne przez zero zawsze generuje wyjątek <xref:System.DivideByZeroException>.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#](../../index.md)
- [Operatory z możliwością przeciążenia](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [Słowa kluczowe języka C#](../keywords/index.md)