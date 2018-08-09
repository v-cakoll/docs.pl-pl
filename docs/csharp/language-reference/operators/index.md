---
title: Operatory C#
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
ms.openlocfilehash: 2b0441dfebb6692cbea0d1ab7909d7b8f04490cb
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "34457611"
---
# <a name="c-operators"></a>Operatory C#
C# zawiera wiele operatorów, które są symbolami określającymi operacje (matematycznych, indeksowanie, wywołanie funkcji itp.) do wykonania w wyrażeniu. Możesz [przeciążenia](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) wiele operatorów, aby zmienić ich znaczenia w przypadku zastosowania do typu zdefiniowanego przez użytkownika.  
  
 Operacje na typach całkowitoliczbowych (takie jak `==`, `!=`, `<`, `>`, `&`, `|`) są ogólnie dozwolone w wyliczeniu (`enum`) typy.  
  
 Poniższe rozdziały zawierają listę operatorów języka C# od o najwyższym priorytecie do najniższego. Operatory w każdej sekcji udostępniać na tym samym poziomie pierwszeństwa.  
 
## <a name="primary-operators"></a>Operatory podstawowe  
 Są to najwyższy pierwszeństwo operatorów.
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) — dostęp do elementu członkowskiego.  
  
 [x? y](../../../csharp/language-reference/operators/null-conditional-operators.md) — wartość null, dostęp warunkowy elementu członkowskiego. Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.  
 
 [x? [t] ](../../../csharp/language-reference/operators/null-conditional-operators.md) — wartość null, dostęp warunkowy indeksu. Zwraca `null` Jeśli po lewej stronie operand ma wartość `null`.
 
 [f(x)](../../../csharp/language-reference/operators/invocation-operator.md) — wywołania funkcji.  
  
 [&#91;x&#93; ](../../../csharp/language-reference/operators/index-operator.md) — indeksowanie obiektu agregacji.  
   
 [x ++](../../../csharp/language-reference/operators/increment-operator.md) — zwiększenie przyrostkowe. Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest większa o jeden (zazwyczaj dodaje liczbę całkowitą 1).  
  
 [x —](../../../csharp/language-reference/operators/decrement-operator.md) — zmniejszenie przyrostkowe. Zwraca wartość x, a następnie aktualizuje lokalizację przechowywania z wartością x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).  
  
 [nowe](../../../csharp/language-reference/keywords/new-operator.md) — podczas tworzenia wystąpienia typu.  
  
 [TypeOf](../../../csharp/language-reference/keywords/typeof.md) — zwraca <xref:System.Type> obiekt reprezentujący argument.  
  
 [zaznaczone](../../../csharp/language-reference/keywords/checked.md) — umożliwia przepełnienie sprawdzania pod kątem operacji liczby całkowitej.  
  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) — wyłącza przepełnienie sprawdzania pod kątem operacji liczby całkowitej. Jest to domyślne zachowanie kompilatora.  
  
 [wartość Default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) — tworzy domyślną wartość typu T.  
  
 [Delegowanie](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) — deklaruje i zwraca wystąpienie delegata.  
  
 [Operator sizeof](../../../csharp/language-reference/keywords/sizeof.md) — zwraca rozmiar w bajtach argument typu.  
  
 [->](../../../csharp/language-reference/operators/dereference-operator.md) — wyłuskanie wskaźnika w połączeniu z dostępu do elementu członkowskiego.  
  
## <a name="unary-operators"></a>Operatory jednoargumentowe  
 Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [+ x](../../../csharp/language-reference/operators/addition-operator.md) — zwraca wartość x.  
  
 [-x](../../../csharp/language-reference/operators/subtraction-operator.md) — negacji liczbowych.  
  
 [\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) — negacji logicznej.  
  
 [~ x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) — uzupełnienie bitowe.  
  
 [++ x](../../../csharp/language-reference/operators/increment-operator.md) — przedrostkowe. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu z wartością x, który jest jednym większą (zazwyczaj dodaje liczbę całkowitą 1).  
  
 [--x](../../../csharp/language-reference/operators/decrement-operator.md) — przedrostkowe. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartości x, która jest mniejsza (zazwyczaj odejmuje liczbę całkowitą 1).  
  
 [(T) x](../../../csharp/language-reference/operators/invocation-operator.md) — typ rzutowania.  
  
 [await](../../../csharp/language-reference/keywords/await.md) — czeka `Task`.  
  
 [& x](../../../csharp/language-reference/operators/and-operator.md) — adres.  
  
 [* x](../../../csharp/language-reference/operators/multiplication-operator.md) — dereferencji.  
  
## <a name="multiplicative-operators"></a>Operatory mnożne  
 Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x * y](../../../csharp/language-reference/operators/multiplication-operator.md) — mnożenia.  
  
 [x / y](../../../csharp/language-reference/operators/division-operator.md) — dzielenia. Jeśli argumenty są liczbami całkowitymi, wynik jest liczbą całkowitą obcięte w kierunku zera (na przykład `-7 / 2 is -3`).  
  
 [x, % y](../../../csharp/language-reference/operators/remainder-operator.md) — resztę. Jeśli argumenty są liczbami całkowitymi, to zwraca resztę z dzielenia podziału x, y.  Jeśli `q = x / y` i `r = x % y`, następnie `x = q * y + r`.  
  
## <a name="additive-operators"></a>Operatory addytywne  
 Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x + y](../../../csharp/language-reference/operators/addition-operator.md) — Dodawanie.  
  
 [x – y](../../../csharp/language-reference/operators/subtraction-operator.md) — odejmowania.  
  
## <a name="shift-operators"></a>Operatory przesunięcia  
 Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x <\< y](../../../csharp/language-reference/operators/left-shift-operator.md) — przesunięcia bitów w lewo i wypełnić zero po prawej stronie.  
  
 [x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) — shift bits po prawej stronie. Jeśli Lewy argument operacji jest `int` lub `long`, a następnie po lewej stronie bity są wypełnione bitu znaku. Jeśli Lewy argument operacji jest `uint` lub `ulong`, a następnie po lewej stronie bity są wypełnione zero.  
  
## <a name="relational-and-type-testing-operators"></a>Operatory relacyjne i badania typu  
 Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) — mniejsze niż (wartość true, jeśli x jest mniejsza niż y).  
  
 [x > y](../../../csharp/language-reference/operators/greater-than-operator.md) — większa (wartość true, jeśli x jest większa niż y).  
  
 [x \<= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) — mniejsze niż lub równe.  
  
 [x > = y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) — większa lub równa.  
  
 [jest](../../../csharp/language-reference/keywords/is.md) — wpisz zgodności. Zwraca wartość PRAWDA, jeśli ocenianą lewy operand mogą być rzutowane na typ określony w prawy operand (typu statycznego).  
  
 [jako](../../../csharp/language-reference/keywords/as.md) — konwersja typu. Zwraca lewy operand rzutowany na typ określony przez prawy operand (typ statycznej), ale `as` zwraca `null` gdzie `(T)x` spowoduje zgłoszenie wyjątku.  
  
## <a name="equality-operators"></a>Operatory równości  
 Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x == y](../../../csharp/language-reference/operators/equality-comparison-operator.md) — równości. Domyślnie dla odwołania do typów innych niż `string`ten zwraca odwołania równości (test tożsamości). Jednak typów może doprowadzić do przeciążenia `==`, więc jeśli zgodne z zamiarami użytkownika jest, aby sprawdzić tożsamość, najlepiej użyć `ReferenceEquals` metody `object`.  
  
 [x! = y](../../../csharp/language-reference/operators/not-equal-operator.md) — są nierówne. Zobacz komentarz dotyczący `==`. Jeśli typem przeciążenia `==`, a następnie przeciąża musi `!=`.  
  
## <a name="logical-and-operator"></a>Operator logiczny AND  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x i y](../../../csharp/language-reference/operators/and-operator.md) — operatora logicznego lub bitowego AND. Zazwyczaj można użyć tego z typami całkowitymi i `enum` typów.  
  
## <a name="logical-xor-operator"></a>Logiczne XOR — Operator  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) — logicznych lub bitowe XOR. Zazwyczaj można użyć tego z typami całkowitymi i `enum` typów.  
  
## <a name="logical-or-operator"></a>Logiczne OR — Operator  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) — logicznych lub bitowe OR. Zazwyczaj można użyć tego z typami całkowitymi i `enum` typów.  
  
## <a name="conditional-and-operator"></a>Operator warunkowy AND  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x & & y](../../../csharp/language-reference/operators/conditional-and-operator.md) — operatora logicznego AND. Jeśli pierwszy operand zwróci wartość false, następnie C# nie może oszacować drugiego operandu.  
  
## <a name="conditional-or-operator"></a>Warunkowego lub operatora  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x &#124; &#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) — operator logiczny lub. Jeśli pierwszy argument zwraca wartość true, następnie C# nie może oszacować drugiego operandu.  
  
## <a name="null-coalescing-operator"></a>Operatorem łączenia wartości null  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x? y](../../../csharp/language-reference/operators/null-coalescing-operator.md) — zwraca `x` jeśli je ma wartość inną niż`null`; w przeciwnym razie zwraca `y`.  
  
## <a name="conditional-operator"></a>Operator warunkowy  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [t? x: y](../../../csharp/language-reference/operators/conditional-operator.md) — w przypadku testowania `t` daje w wyniku wartość true, a następnie oceniana i zwracana `x`; w przeciwnym razie oceniana i zwracana `y`.  
  
## <a name="assignment-and-lambda-operators"></a>Operatory Lambda i przypisanie  
 Te operatory mają wyższy priorytet niż następnej sekcji i niższy priorytet niż w poprzedniej sekcji.  
  
 [x = y](../../../csharp/language-reference/operators/assignment-operator.md) — przypisania.  
  
 [x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) — przyrostu. Dodaj wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość. Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, dodającego C# jako program obsługi zdarzeń.  
  
 [x-= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) — zmniejszanie. Odejmuje wartość `y` od wartości `x`, zapisują wynik w `x`i zwraca nową wartość. Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, który C# usuwa jako program obsługi zdarzeń  
  
 [x * = y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) — mnożenie i przypisanie. Mnoży wartość `y` wartość `x`, zapisują wynik w `x`i zwraca nową wartość.  
  
 [x / = y](../../../csharp/language-reference/operators/division-assignment-operator.md) — dzielenie i przypisanie. Dzieli wartość `x` przez wartość `y`, zapisują wynik w `x`i zwraca nową wartość.  
  
 [x % = y](../../../csharp/language-reference/operators/remainder-assignment-operator.md) — remainder przypisania. Dzieli wartość `x` przez wartość `y`, przechowywać resztę w `x`i zwraca nową wartość.  
  
 [x & = y](../../../csharp/language-reference/operators/and-assignment-operator.md) — i przypisanie. I wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.  
  
 [x &#124;= y](../../../csharp/language-reference/operators/or-assignment-operator.md) — i przypisanie. LUB wartość `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.  
  
 [x ^ = y](../../../csharp/language-reference/operators/xor-assignment-operator.md) — przypisanie XOR. XOR wartość z `y` z wartością `x`, zapisują wynik w `x`i zwraca nową wartość.  
  
 [x << = y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) — przypisania przesunięcia w lewo. Przesuwa wartość `x` po lewej stronie, `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.  
  
 [x >> = y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) — przypisania przesunięcia w prawo. Przesuwa wartość `x` bezpośrednio przez `y` miejscach, zapisują wynik w `x`i zwraca nową wartość.  
  
 [=>](../../../csharp/language-reference/operators/lambda-operator.md) — deklaracji lambda.  
  
## <a name="arithmetic-overflow"></a>Przepełnienie arytmetyczne  
 Operatory arytmetyczne ([+](../../../csharp/language-reference/operators/addition-operator.md), [ - ](../../../csharp/language-reference/operators/subtraction-operator.md), [ * ](../../../csharp/language-reference/operators/multiplication-operator.md), [ / ](../../../csharp/language-reference/operators/division-operator.md)) może generuje wyniki, które wykraczają poza zakres możliwych wartości dla typu liczbowego. Należy zapoznać się z sekcją na konkretnym operatorze, aby uzyskać szczegółowe informacje, ale ogólnie rzecz biorąc:  
  
- Arytmetyka przepełnienia liczb całkowitych zgłasza <xref:System.OverflowException> lub odrzuca najbardziej znaczące bity wyniku. Dzielenie liczby całkowitej przez zero zawsze generuje wyjątek <xref:System.DivideByZeroException>.  

   Jeśli występuje przepełnienie liczby całkowitej, co się stanie, zależy od kontekstu wykonywania, który może być [zaznaczony lub niezaznaczony](../../../csharp/language-reference/keywords/checked-and-unchecked.md). W kontekście sprawdzanym <xref:System.OverflowException> zgłaszany. W kontekście niesprawdzanym najbardziej znaczące bity wyniku są odrzucane, a wykonywanie jest kontynuowane. W związku z tym C# umożliwia wybranie obsługi lub zignorowanie przepełnienie. Domyślnie operacje arytmetyczne występują w *unchecked* kontekstu. 

   Oprócz operacje arytmetyczne rzutowania typu całkowitego do typu całkowitego mogą spowodować przepełnienie (np. Jeśli zrzutować [długie](../../../csharp/language-reference/keywords/long.md) do [int](../../../csharp/language-reference/keywords/int.md)) i podlegają wykonaniu sprawdzanemu lub niesprawdzanemu. Jednakże operatory bitowe i operatory przesunięcia nigdy nie powodują przepełnienia.  
   
-   Zmiennoprzecinkowe przepełnienia arytmetycznego lub dzielenie przez zero nigdy nie zgłasza wyjątek, ponieważ typy zmiennoprzecinkowe są oparte na standardzie IEEE 754, dlatego mają mechanizmy reprezentowania nieskończoności i NaN (nieliczbową).  
  
-   [Dziesiętna](../../../csharp/language-reference/keywords/decimal.md) przepełnienie arytmetyczne zawsze wyrzuca <xref:System.OverflowException>. Dzielenie dziesiętne przez zero zawsze generuje wyjątek <xref:System.DivideByZeroException>.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md) [operatory z możliwością przeciążenia](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
