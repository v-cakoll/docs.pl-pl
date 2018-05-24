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
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="c-operators"></a>Operatory C#
C# zawiera wielu operatorów, które są symbole, które określają, jakie operacje (matematyczne, indeksowania, wywołanie funkcji itp.) w celu wykonania w wyrażeniu. Możesz [przeciążenia](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) wielu operatorów, aby zmienić ich znaczenia w przypadku zastosowania do typu zdefiniowanego przez użytkownika.  
  
 Operacje na typy całkowite (takich jak `==`, `!=`, `<`, `>`, `&`, `|`) są zwykle jest dozwolony w wyliczeniu (`enum`) typów.  
  
 Poniższe rozdziały zawierają listę operatory C# uruchamianie o najwyższym priorytecie do najniższego. Operatory w każdej sekcji udostępnianie na tym samym poziomie priorytetu.  
 
## <a name="primary-operators"></a>Operatory podstawowe  
 Są to najwyższy pierwszeństwo operatorów.
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) — dostęp do elementu członkowskiego.  
  
 [x?. y](../../../csharp/language-reference/operators/null-conditional-operators.md) — dostęp warunkowy element członkowski o wartości null. Zwraca `null` Jeśli lewego operandu daje w wyniku `null`.  
 
 [x? [y] ](../../../csharp/language-reference/operators/null-conditional-operators.md) -dostępu warunkowego indeks o wartości null. Zwraca `null` Jeśli lewego operandu daje w wyniku `null`.
 
 [f(x)](../../../csharp/language-reference/operators/invocation-operator.md) — wywołania funkcji.  
  
 [&#91;x&#93; ](../../../csharp/language-reference/operators/index-operator.md) — indeksowania obiektu agregacji.  
   
 [x ++](../../../csharp/language-reference/operators/increment-operator.md) — przyrostka inkrementacji. Zwraca wartość x, a następnie aktualizuje lokalizację magazynu o wartości x, które jest większe (zazwyczaj dodaje całkowitą 1).  
  
 [x--](../../../csharp/language-reference/operators/decrement-operator.md) — dekrementacji przyrostka. Zwraca wartość x, a następnie aktualizuje lokalizację magazynu o wartości x, które jest mniej (zazwyczaj odejmuje całkowitą 1).  
  
 [nowe](../../../csharp/language-reference/keywords/new-operator.md) — podczas tworzenia wystąpienia typu.  
  
 [TypeOf](../../../csharp/language-reference/keywords/typeof.md) — zwraca <xref:System.Type> obiekt reprezentujący argument.  
  
 [zaznaczone](../../../csharp/language-reference/keywords/checked.md) — umożliwia przepełnienie sprawdzanie operacji liczby całkowitej.  
  
 [Zaznaczenie opcji](../../../csharp/language-reference/keywords/unchecked.md) — wyłącza przepełnienie sprawdzanie operacji liczby całkowitej. Jest to domyślne zachowanie kompilatora.  
  
 [Default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) — tworzy domyślną wartość typu T.  
  
 [Delegowanie](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) — deklaruje i zwraca wystąpienie obiektu delegowanego.  
  
 [sizeof](../../../csharp/language-reference/keywords/sizeof.md) — zwraca rozmiar w bajtach argumentu typu.  
  
 [->](../../../csharp/language-reference/operators/dereference-operator.md) — wskaźnik dereferencji połączone z dostęp do elementu członkowskiego.  
  
## <a name="unary-operators"></a>Operatory jednoargumentowe  
 Tych operatorów mają wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [+ x](../../../csharp/language-reference/operators/addition-operator.md) — zwraca wartość x.  
  
 [-x](../../../csharp/language-reference/operators/subtraction-operator.md) — negacji liczbowych.  
  
 [\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) — logiczny negacji.  
  
 [~ x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) — dopełnienia bitowego.  
  
 [++ x](../../../csharp/language-reference/operators/increment-operator.md) — prefiks przyrostu. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartości x, które jest większe (zazwyczaj dodaje całkowitą 1).  
  
 [--x](../../../csharp/language-reference/operators/decrement-operator.md) — prefiks zmniejszenie. Zwraca wartość x po zaktualizowaniu lokalizacji magazynu o wartości x, które jest mniej (zazwyczaj odejmuje całkowitą 1).  
  
 [[T] x](../../../csharp/language-reference/operators/invocation-operator.md) — typ rzutowania.  
  
 [await](../../../csharp/language-reference/keywords/await.md) — oczekujące na `Task`.  
  
 [& x](../../../csharp/language-reference/operators/and-operator.md) — adres.  
  
 [* x](../../../csharp/language-reference/operators/multiplication-operator.md) — usuwania odwołań.  
  
## <a name="multiplicative-operators"></a>Operatory mnożne  
 Tych operatorów mają wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x * y](../../../csharp/language-reference/operators/multiplication-operator.md) — mnożenia.  
  
 [x / y](../../../csharp/language-reference/operators/division-operator.md) — dzielenia. Jeśli argumenty są liczbami całkowitymi, wyniku jest liczbą całkowitą obcięty w kierunku zera (na przykład `-7 / 2 is -3`).  
  
 [x % y](../../../csharp/language-reference/operators/remainder-operator.md) — pozostałe. Argumenty operacji są liczbami całkowitymi, to zwraca resztę podziału x przez y.  Jeśli `q = x / y` i `r = x % y`, następnie `x = q * y + r`.  
  
## <a name="additive-operators"></a>Operatory addytywne  
 Tych operatorów mają wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x + y](../../../csharp/language-reference/operators/addition-operator.md) — Dodawanie.  
  
 [x-y](../../../csharp/language-reference/operators/subtraction-operator.md) — odejmowanie.  
  
## <a name="shift-operators"></a>Operatory przesunięcia  
 Tych operatorów mają wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x <\< y](../../../csharp/language-reference/operators/left-shift-operator.md) — przesunięcia bitów w lewo i wypełnienie zera po prawej stronie.  
  
 [x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) — shift liczby bitów w prawo. Jeśli lewy operand jest `int` lub `long`, a następnie po lewej stronie bity są wypełnione z bitem. Jeśli lewy operand jest `uint` lub `ulong`, a następnie po lewej stronie bity są wypełniane zero.  
  
## <a name="relational-and-type-testing-operators"></a>Operatory relacyjne i testowania typu  
 Tych operatorów mają wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) — mniej niż (wartość true, jeśli x jest mniejsza niż y).  
  
 [x > y](../../../csharp/language-reference/operators/greater-than-operator.md) — większa niż (wartość true, jeśli x jest większa niż y).  
  
 [x \<= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) — mniejsze niż lub równe.  
  
 [x > = y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) — większa niż lub równe.  
  
 [jest](../../../csharp/language-reference/keywords/is.md) — wpisz zgodności. Zwraca wartość PRAWDA, jeśli obliczane lewy operand mogą być rzutowane na typ określony w prawy operand (typ statyczny).  
  
 [jako](../../../csharp/language-reference/keywords/as.md) — konwersja typu. Zwraca lewy operand rzutowany na typ określony przez prawy operand (typ statyczny), ale `as` zwraca `null` gdzie `(T)x` spowoduje zgłoszenie wyjątku.  
  
## <a name="equality-operators"></a>Operatory równości  
 Tych operatorów mają wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x == y](../../../csharp/language-reference/operators/equality-comparison-operator.md) — równości. Domyślnie dla odwołania do typów innych niż `string`, to zwraca odwołanie równości (test tożsamości). Jednak można przeciążać typy `==`, więc jeśli Twoje celem jest, aby sprawdzić tożsamość, najlepiej użyć `ReferenceEquals` metoda `object`.  
  
 [x! = y](../../../csharp/language-reference/operators/not-equal-operator.md) — jest nierówne. Zobacz komentarz dotyczący `==`. Jeśli typem overloads `==`, a następnie go muszą przeciążać `!=`.  
  
## <a name="logical-and-operator"></a>Operator logiczny AND  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x & y](../../../csharp/language-reference/operators/and-operator.md) — logicznych lub bitowego koniunkcji binarnej. Zazwyczaj służy ono z typami liczb całkowitych i `enum` typów.  
  
## <a name="logical-xor-operator"></a>Logiczne XOR — Operator  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) — logicznych lub bitowego XOR. Zazwyczaj służy ono z typami liczb całkowitych i `enum` typów.  
  
## <a name="logical-or-operator"></a>Logiczny OR Operator  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) — logicznych lub bitowego OR. Zazwyczaj służy ono z typami liczb całkowitych i `enum` typów.  
  
## <a name="conditional-and-operator"></a>Operator warunkowy AND  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x & & y](../../../csharp/language-reference/operators/conditional-and-operator.md) — operatora logicznego AND. Jeśli pierwszy argument operacji nie jest spełniony, następnie C# nie może oszacować drugiego argumentu operacji.  
  
## <a name="conditional-or-operator"></a>Warunkowy OR — Operator  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x &#124; &#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) — operatora logicznego OR. Jeśli pierwszy argument operacji daje w wyniku wartość true, następnie C# nie może oszacować drugiego argumentu operacji.  
  
## <a name="null-coalescing-operator"></a>Łączenie null — Operator  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x? y](../../../csharp/language-reference/operators/null-coalescing-operator.md) — zwraca `x` jeśli ją ma wartość inną niż`null`; w przeciwnym razie zwraca `y`.  
  
## <a name="conditional-operator"></a>Operator warunkowy  
 Ten operator ma wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [t? x: y](../../../csharp/language-reference/operators/conditional-operator.md) — Jeśli test `t` daje w wyniku wartość true, a następnie ocenić i zwracać `x`; w przeciwnym razie ocenić i zwracać `y`.  
  
## <a name="assignment-and-lambda-operators"></a>Przypisanie i operatory Lambda  
 Tych operatorów mają wyższy priorytet niż następnej sekcji i niższy priorytet niż poprzedniej sekcji.  
  
 [x = y](../../../csharp/language-reference/operators/assignment-operator.md) — przypisania.  
  
 [x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) — przyrostu. Dodaj wartość `y` wartość `x`, zapisać wynik w `x`i zwraca nową wartość. Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, która C# dodaje jako program obsługi zdarzeń.  
  
 [x-= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) — zmniejszyć. Odejmowanie wartość `y` od wartości `x`, zapisać wynik w `x`i zwraca nową wartość. Jeśli `x` wyznacza `event`, następnie `y` musi mieć odpowiednią funkcję, która C# usuwa jako program obsługi zdarzeń  
  
 [x * = y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) — przypisania mnożenia. Należy pomnożyć wartość `y` wartość `x`, zapisać wynik w `x`i zwraca nową wartość.  
  
 [x / = y](../../../csharp/language-reference/operators/division-assignment-operator.md) — przypisania dzielenia. Podziel wartość `x` przez wartość `y`, zapisać wynik w `x`i zwraca nową wartość.  
  
 [x % = y](../../../csharp/language-reference/operators/remainder-assignment-operator.md) — remainder przypisania. Podziel wartość `x` przez wartość `y`, przechowywać resztę w `x`i zwraca nową wartość.  
  
 [x & = y](../../../csharp/language-reference/operators/and-assignment-operator.md) — i przypisania. WARTOŚĆ `y` z wartością `x`, zapisać wynik w `x`i zwraca nową wartość.  
  
 [x &#124;= y](../../../csharp/language-reference/operators/or-assignment-operator.md) — przypisanie OR. LUB wartość `y` z wartością `x`, zapisać wynik w `x`i zwraca nową wartość.  
  
 [x ^ = y](../../../csharp/language-reference/operators/xor-assignment-operator.md) — XOR przypisania. XOR wartość z `y` z wartością `x`, zapisać wynik w `x`i zwraca nową wartość.  
  
 [x << = y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) — przypisania przesunięcia w lewo. Wartość przesunięcia `x` po lewej stronie przez `y` miejsca przechowywania wyników w `x`i zwraca nową wartość.  
  
 [x >> = y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) — przypisania przesunięcia w prawo. Wartość przesunięcia `x` prawo `y` miejsca przechowywania wyników w `x`i zwraca nową wartość.  
  
 [=>](../../../csharp/language-reference/operators/lambda-operator.md) — deklaracji lambda.  
  
## <a name="arithmetic-overflow"></a>Przepełnienie arytmetyczne  
 Operatory arytmetyczne ([+](../../../csharp/language-reference/operators/addition-operator.md), [ - ](../../../csharp/language-reference/operators/subtraction-operator.md), [ * ](../../../csharp/language-reference/operators/multiplication-operator.md), [ / ](../../../csharp/language-reference/operators/division-operator.md)) może dostarczyło wyników, które są poza zakresem możliwe wartości liczbowe rodzaju. Należy zapoznać się w sekcji na konkretnym operatorze, aby uzyskać więcej informacji, ale w ogólne:  
  
- Albo zgłasza przepełnienie arytmetyczne całkowitą <xref:System.OverflowException> lub odrzuca najbardziej znaczących bitów wyniku. Dzielenie liczby całkowitej przez zero zawsze zwraca <xref:System.DivideByZeroException>.  

   Gdy wystąpi przepełnienie liczby całkowitej, co się stanie, zależy od kontekstu wykonywania, który może być [zaznaczenie](../../../csharp/language-reference/keywords/checked-and-unchecked.md). W kontekście zaznaczone <xref:System.OverflowException> jest generowany. W kontekście niezaznaczone najbardziej znaczących bitów wyniku zostaną odrzucone i kontynuuje wykonywanie. W związku z tym C# umożliwia wybór obsługi lub ignorowanie przepełnienia. Domyślnie operacje arytmetyczne występują w *niezaznaczone* kontekstu. 

   Oprócz operacji arytmetycznej, rzutowania typu całkowitego — do całkowitych typów może spowodować przepełnienie (np. gdy rzutowania [długi](../../../csharp/language-reference/keywords/long.md) do [int](../../../csharp/language-reference/keywords/int.md)) i wymagają wykonania zaznaczać lub usuwać zaznaczenia. Jednak operatory bitowe i operatory przesunięcia nigdy nie spowodować przepełnienie.  
   
-   Nigdy nie zgłasza wyjątek zmiennoprzecinkowy przepełnienia arytmetycznego lub dzielenie przez zero, ponieważ typy zmiennoprzecinkowe są oparte na IEEE 754 i tak mają postanowienia reprezentujący nieskończoności i NaN (nieliczbową).  
  
-   [Decimal](../../../csharp/language-reference/keywords/decimal.md) zawsze zgłasza wyjątek przepełnienia arytmetycznego <xref:System.OverflowException>. Decimal dzielenie przez zero zawsze zwraca <xref:System.DivideByZeroException>.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md) [operatory z możliwością przeciążenia](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
