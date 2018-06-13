---
title: Operatory (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 76371985e340945793310247ec48d9b0cb747aed
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457933"
---
# <a name="operators-c-programming-guide"></a>Operatory (Przewodnik programowania w języku C#)
W języku C# *operator* jest element program, który jest stosowany do co najmniej jeden *operandy* w wyrażenia lub instrukcji. Operatory, które mają jeden operand, takich jak operator inkrementacji (`++`) lub `new`, są określane jako *jednoargumentowy* operatorów. Operatory, które przyjmują dwóch argumentów operacji, takich jak operatory arytmetyczne (`+`,`-`,`*`,`/`), są określane jako *binarne* operatorów. Jeden operator, operator warunkowy (`?:`), ma trzy operandy i jest jedyny operator trójargumentowy w języku C#.  
  
 Poniższa instrukcja języka C# zawiera jeden operator jednoargumentowy i jeden argument operacji. Operator inkrementacji `++`, modyfikuje wartość operandu `y`.  
  
 [!code-csharp[csProgGuideStatements#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_1.cs)]  
  
 Następująca instrukcja języka C# zawiera dwa operatory dwuargumentowe, z których każdy przyjmuje dwa argumenty operacji. Operator przypisania `=`, ma zmienna całkowitoliczbowa `y` oraz wyrażenia `2 + 3` jako argumentów. Wyrażenie `2 + 3` sam składa się z operator dodawania i dwóch argumentów operacji, `2` i `3`.  
  
 [!code-csharp[csProgGuideStatements#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_2.cs)]  
  
## <a name="operators-evaluation-and-operator-precedence"></a>Operatory, obliczenia i pierwszeństwo operatorów  
 Argument operacji może być prawidłowym wyrażeniem zawierającym kod o dowolnej długości i może składać się z dowolnej liczby podwyrażeń. W wyrażeniu, który zawiera wiele operatorów, kolejność stosowania operatorów jest określany przez *kolejność*, *kojarzenie*i nawiasy.  
  
 Każdy operator ma zdefiniowane pierwszeństwo. W wyrażeniu zawierającym wiele operatorów, które mają różne poziomy pierwszeństwa, pierwszeństwo operatorów określa kolejność wykonywania obliczeń tych operatorów. Na przykład następująca instrukcja przypisuje 3, aby `n1`.  
  
 `n1 = 11 - 2 * 4;`  
  
 Mnożenie jest wykonywane jako pierwsze, ponieważ mnożenie ma pierwszeństwo przed odejmowaniem.  
  
 W poniższej tabeli podzielone operatory na kategorie na podstawie typu wykonywanych przez nie operacji. Kolejność kategorii odpowiada pierwszeństwu operatorów.  
  
 **Operatory podstawowe**  
  
|Wyrażenie|Opis|  
|----------------|-----------------|  
|x[.](../../../csharp/language-reference/operators/member-access-operator.md)y<br /><br /> x?. y|Dostęp do elementu członkowskiego<br /><br /> Dostęp warunkowy element członkowski|  
|f[(x)](../../../csharp/language-reference/operators/invocation-operator.md)|Wywołanie metody i delegata|  
|a[&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md)<br /><br /> a?[x]|Dostęp do tablicy i indeksatora<br /><br /> Dostęp warunkowy tablicy i indeksatora|  
|x[++](../../../csharp/language-reference/operators/increment-operator.md)|Postinkrementacja|  
|x[--](../../../csharp/language-reference/operators/decrement-operator.md)|Postdekrementacja|  
|[Nowy](../../../csharp/language-reference/keywords/new-operator.md) T(...)|Utworzenie obiektu i delegata|  
|`new` T(...){...}|Utworzenie obiektu za pomocą inicjatora. Zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).|  
|`new` {...}|Inicjator obiektu anonimowego. Zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).|  
|`new` T [...]|Utworzenie tablicy. Zobacz [tablice](../../../csharp/programming-guide/arrays/index.md).|  
|[TypeOf](../../../csharp/language-reference/keywords/typeof.md)(T)|Uzyskanie obiektu System.Type dla typu T|  
|[zaznaczone](../../../csharp/language-reference/keywords/checked.md)(x)|Obliczenie wyrażenia w kontekście sprawdzanym|  
|[Zaznaczenie opcji](../../../csharp/language-reference/keywords/unchecked.md)(x)|Obliczenie wyrażenia w kontekście niesprawdzanym|  
|[domyślne](../../../csharp/language-reference/keywords/default.md) (T)|Uzyskanie wartości domyślnej typu T|  
|[Delegat](../../../csharp/language-reference/keywords/delegate.md) {}|Funkcja anonimowa (metoda anonimowa)|  
  
 **Operatory jednoargumentowe**  
  
|Wyrażenie|Opis|  
|----------------|-----------------|  
|[+](../../../csharp/language-reference/operators/addition-operator.md)x|Tożsamość|  
|[-](../../../csharp/language-reference/operators/subtraction-operator.md)x|Negacja|  
|[\!](../../../csharp/language-reference/operators/logical-negation-operator.md)x|Negacja logiczna|  
|[~](../../../csharp/language-reference/operators/bitwise-complement-operator.md)x|Negacja bitowa|  
|[++](../../../csharp/language-reference/operators/increment-operator.md)x|Preinkrementacja|  
|[--](../../../csharp/language-reference/operators/decrement-operator.md)x|Predekrementacja|  
|[(T)](../../../csharp/language-reference/operators/invocation-operator.md)x|Jawna konwersja wartości x na typ T|  
  
 **Operatory mnożenia**  
  
|Wyrażenie|Opis|  
|----------------|-----------------|  
|[*](../../../csharp/language-reference/operators/multiplication-operator.md)|Mnożenie|  
|[/](../../../csharp/language-reference/operators/division-operator.md)|Dzielenie|  
|[%](../../../csharp/language-reference/operators/modulus-operator.md)|Reszta|  
  
 **Operatory dodawania**  
  
|Wyrażenie|Opis|  
|----------------|-----------------|  
|x [ + ](../../../csharp/language-reference/operators/addition-operator.md) y|Dodawanie, łączenie ciągów, łączenie delegatów|  
|x [ - ](../../../csharp/language-reference/operators/subtraction-operator.md) y|Odejmowanie, usuwanie delegata|  
  
 **Operatory przesunięcia**  
  
|Wyrażenie|Opis|  
|----------------|-----------------|  
|x [ < \< ](../../../csharp/language-reference/operators/left-shift-operator.md) y|Przesunięcie w lewo|  
|x [ >> ](../../../csharp/language-reference/operators/right-shift-operator.md) y|Przesunięcie w prawo|  
  
 **Relacyjnych i wpisz operatory**  
  
|Wyrażenie|Opis|  
|----------------|-----------------|  
|x [ \< ](../../../csharp/language-reference/operators/less-than-operator.md) y|Mniejsze niż|  
|x [ > ](../../../csharp/language-reference/operators/greater-than-operator.md) y|Większe niż|  
|x [ \< = ](../../../csharp/language-reference/operators/less-than-equal-operator.md) y|Mniejsze niż lub równe|  
|x [ >= ](../../../csharp/language-reference/operators/greater-than-equal-operator.md) y|Większe niż lub równe|  
|x [jest](../../../csharp/language-reference/keywords/is.md) T|Zwraca wartość true, gdy x jest typu T; w przeciwnym razie zwraca wartość false|  
|x [jako](../../../csharp/language-reference/keywords/as.md) T|Zwraca wartość x jako wartość typu T lub zwraca wartość null, jeśli x nie jest typu T|  
  
 **Operatory równości**  
  
|Wyrażenie|Opis|  
|----------------|-----------------|  
|x [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) y|Równa się|  
|x [! =](../../../csharp/language-reference/operators/not-equal-operator.md) y|Nie równa się|  
  
 **Operatory logiczne, warunkowe i wartości Null**  
  
|Kategoria|Wyrażenie|Opis|  
|--------------|----------------|-----------------|  
|AND logiczne|x [ & ](../../../csharp/language-reference/operators/and-operator.md) y|Bitowe AND dla wartości całkowitych, logiczne AND dla wartości binarnych|  
|XOR logiczne|x [ ^ ](../../../csharp/language-reference/operators/xor-operator.md) y|Bitowe XOR dla wartości całkowitych, logiczne XOR dla wartości binarnych|  
|OR logiczne|x [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) y|Bitowe OR dla wartości całkowitych, logiczne OR dla wartości binarnych|  
|AND warunkowe|x [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) y|Wartość y jest obliczana tylko wtedy, gdy wartość x jest równa true|  
|OR warunkowe|x [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) y|Wartość y jest obliczana tylko wtedy, gdy wartość x jest równa false|  
|Łączenie wartości null|x [?](../../../csharp/language-reference/operators/null-coalescing-operator.md) t|Wynikiem jest wartość y, jeśli x ma wartość null; w przeciwnym razie wynikiem jest wartość x|  
|Warunkowe|x [?](../../../csharp/language-reference/operators/conditional-operator.md) y: z|Wynikiem jest wartość y, gdy wartość x jest równa true, lub z, gdy wartość x jest równa false|  
  
 **Przypisanie i operatory anonimowe**  
  
|Wyrażenie|Opis|  
|----------------|-----------------|  
|[=](../../../csharp/language-reference/operators/assignment-operator.md)|Przypisanie|  
|x op= y|Przypisanie złożone Obsługuje następujące operatory: [ += ](../../../csharp/language-reference/operators/addition-assignment-operator.md), [ -= ](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [ *= ](../../../csharp/language-reference/operators/multiplication-assignment-operator.md), [ /= ](../../../csharp/language-reference/operators/division-assignment-operator.md), [ %= ](../../../csharp/language-reference/operators/modulus-assignment-operator.md) , [&=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md), [!=](../../../csharp/language-reference/operators/not-equal-operator.md), [<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|  
|(T x) [ => ](../../../csharp/language-reference/operators/lambda-operator.md) y|Funkcja anonimowa (wyrażenie lambda)|  
  
## <a name="associativity"></a>Łączność  
 Gdy co najmniej dwa operatory w wyrażeniu mają takie samo pierwszeństwo, są obliczane na podstawie łączności. Operatory mające łączność do lewej strony są obliczane w kolejności od lewej do prawej. Na przykład `x * y / z` jest szacowana jako `(x * y) / z`. Operatory mające łączność do prawej strony są obliczane w kolejności od prawej do lewej. Na przykład operator przypisania ma łączność do prawej strony. Gdyby tak nie było, poniższy kod powodowałby wystąpienie błędu.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Innym przykładem operator trójargumentowy ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) jest prawo asocjacyjnej. Większość operatorów binarnych pozostało asocjacyjnej.  
  
 Niezależnie od tego, czy operatory w wyrażeniu mają łączność do lewej strony, czy do prawej, argumenty operacji każdego wyrażenia są obliczane najpierw od lewej strony do prawej. W poniższych przykładach pokazano kolejność obliczania operatorów i argumentów operacji.  
  
|Instrukcja|Kolejność obliczeń|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>Dodawanie nawiasów  
 Używając nawiasów, można zmienić kolejność określoną przez pierwszeństwo operatorów oraz łączność. Na przykład `2 + 3 * 2` zazwyczaj wynikiem 8, ponieważ operatory mnożenia mają pierwszeństwo przed operatory dodawania. Jednak jeśli wyrażenia jako `(2 + 3) * 2`, dodanie jest oceniane przed mnożenia i wynik wynosi 10. W poniższych przykładach pokazano kolejność obliczania w wyrażeniach z nawiasami. Tak jak w poprzednich przykładach argumenty operacji są obliczane przed zastosowaniem operatora.  
  
|Instrukcja|Kolejność obliczeń|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>Przeciążanie operatora  
 Można zmienić zachowanie operatorów dla niestandardowych klas i struktur. Ten proces jest nazywany *przeładowania operatora*. Aby uzyskać więcej informacji, zobacz [operatory z możliwością przeciążenia](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz [słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md) i [operatory C#](../../../csharp/language-reference/operators/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Instrukcje, wyrażenia i operatory](../../../csharp/programming-guide/statements-expressions-operators/index.md)
