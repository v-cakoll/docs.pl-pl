---
title: Operatory arytmetyczne
ms.date: 07/20/2015
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
ms.openlocfilehash: d5f79f3e45fc887dcb32c959f04703253ade198c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389039"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Operatory arytmetyczne w Visual Basic
Operatory arytmetyczne są używane do wykonywania wielu znanych operacji arytmetycznych, które obejmują Obliczanie wartości liczbowych reprezentowanych przez literały, zmienne, inne wyrażenia, wywołania funkcji i właściwości oraz stałe. Również sklasyfikowane operatorami arytmetycznymi są operatory przesunięcia bitowego, które działają na poziomie poszczególnych bitów operandów i przesuwają wzorce bitów w lewo lub w prawo.  
  
## <a name="arithmetic-operations"></a>Operacje arytmetyczne  
 Można dodać dwie wartości w wyrażeniu razem z [operatorem +](../../../language-reference/operators/addition-operator.md)lub odjąć jeden od innego za pomocą [operatora-operator (Visual Basic)](../../../language-reference/operators/subtraction-operator.md), jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Negacja używa także [operatora-(Visual Basic)](../../../language-reference/operators/subtraction-operator.md), ale z tylko jednym operandem, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Mnożenie i dzielenie używają odpowiednio [operatora *](../../../language-reference/operators/multiplication-operator.md) i [operatora (Visual Basic)](../../../language-reference/operators/floating-point-division-operator.md), jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Potęgowanie używa [operatora ^](../../../language-reference/operators/exponentiation-operator.md), jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Dzielenie liczb całkowitych jest przeprowadzane za pomocą [operatora \ (Visual Basic)](../../../language-reference/operators/integer-division-operator.md). Dzielenie liczb całkowitych zwraca iloraz, czyli liczbę całkowitą, która reprezentuje liczbę przypadków, w których dzielnik może być podzielony na dzielną bez uwzględniania reszty. Dzielnik i dzielną muszą być typami całkowitymi (,,,,,, `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` i `ULong` ) dla tego operatora. Wszystkie inne typy muszą zostać najpierw przekonwertowane na typ całkowity. Poniższy przykład ilustruje dzielenie liczby całkowitej.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 Arytmetyka modulo jest przeprowadzana przy użyciu [operatora mod](../../../language-reference/operators/mod-operator.md). Ten operator zwraca resztę po podzieleniu dzielnika na całkowitą liczbę razy. Jeśli zarówno dzielnik, jak i dzielną są typami całkowitymi, zwrócona wartość jest całką. Jeśli dzielnik i dzielną są typami zmiennoprzecinkowymi, zwracana wartość jest również zmiennoprzecinkowa. Poniższy przykład ilustruje to zachowanie.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Próba dzielenia przez zero  
 Dzielenie przez zero ma różne wyniki w zależności od typów danych. W przypadku częściowych podziałów (,,,,,,, `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` `ULong` ) .NET Framework zgłasza <xref:System.DivideByZeroException> wyjątek. W operacjach dzielenia na `Decimal` `Single` Typ danych lub .NET Framework zgłasza również <xref:System.DivideByZeroException> wyjątek.  
  
 W przypadku przedziałów zmiennoprzecinkowych obejmujących `Double` Typ danych nie jest zgłaszany żaden wyjątek, a wynikiem jest element członkowski klasy reprezentujący <xref:System.Double.NaN> , <xref:System.Double.PositiveInfinity> lub <xref:System.Double.NegativeInfinity> , w zależności od dywidendy. Poniższa tabela podsumowuje różne wyniki próby podziału `Double` wartości przez zero.  
  
|Typ danych dywidendy|Dzielnik — typ danych|Wartość dywidendy|Wynik|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN>(nie jest to liczba matematycznie zdefiniowana)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\<2,0|<xref:System.Double.NegativeInfinity>|  
  
 Podczas przechwytywania <xref:System.DivideByZeroException> wyjątku można użyć jego członków, aby ułatwić jego obsługę. Na przykład <xref:System.Exception.Message%2A> Właściwość zawiera tekst komunikatu dla wyjątku. Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Operacje bitu Shift  
 Operacja bitu Shift wykonuje arytmetyczną zmianę wzorca bitowego. Wzorzec jest zawarty w argumencie operacji po lewej stronie, podczas gdy argument operacji po prawej stronie określa liczbę pozycji do przesunięcia wzorca. Możesz przesunąć wzorzec w prawo z [operatorem>> ](../../../language-reference/operators/right-shift-operator.md) lub z lewej strony [operatorem<< ](../../../language-reference/operators/left-shift-operator.md).  
  
 Typem danych operandu wzorca musi być,,,,,, `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` lub `ULong` . Typ danych operandu kwoty przesunięcia musi być `Integer` lub musi być rozszerzony na `Integer` .  
  
 Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu. Pozycje bitowe opuszczone przez zmianę są ustawiane w następujący sposób:  
  
- 0 dla arytmetycznego przesunięcia w lewo  
  
- 0 dla arytmetycznej zmiany liczby dodatniej  
  
- 0 dla operacji arytmetycznych po prawej stronie typu danych bez znaku ( `Byte` , `UShort` ,, `UInteger` `ULong` )  
  
- 1 w przypadku arytmetycznego przesunięcia liczby ujemnej ( `SByte` , `Short` , `Integer` lub `Long` )  
  
 Poniższy przykład przenosi `Integer` wartość w lewo i w prawo.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Przesunięcia arytmetyczne nigdy nie generują wyjątków przepełnienia.  
  
## <a name="bitwise-operations"></a>Operacje bitowe  
 Poza operatorami logicznymi, `Not` ,, `Or` `And` i `Xor` również przeprowadzać operacje arytmetyczne przy użyciu wartości numerycznych. Aby uzyskać więcej informacji, zobacz "Operacje bitowe" w [operatorach logicznych i bitowych w Visual Basic](logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Bezpieczeństwo typów  
 Operandy powinny być zwykle tego samego typu. Na przykład, jeśli dodasz `Integer` do zmiennej, należy dodać ją do innej `Integer` zmiennej i przypisać wynik do zmiennej typu `Integer` .  
  
 Jednym ze sposobów zapewnienia dobrego kodowania bezpiecznych typów jest użycie [instrukcji Option Strict](../../../language-reference/statements/option-strict-statement.md). Jeśli ustawisz `Option Strict On` , Visual Basic automatycznie wykonuje konwersje *bezpieczne dla typów* . Na przykład, jeśli spróbujesz dodać `Integer` zmienną do `Double` zmiennej i przypisać wartość do `Double` zmiennej, operacja jest przeprowadzana normalnie, ponieważ `Integer` wartość może zostać przekonwertowana na `Double` bez utraty danych. Niebezpieczne konwersje typu, z drugiej strony, powodują błąd kompilatora z `Option Strict On` . Na przykład, jeśli spróbujesz dodać `Integer` zmienną do `Double` zmiennej i przypisać wartość do `Integer` zmiennej, wynik błędu kompilatora, ponieważ `Double` zmienna nie może zostać niejawnie przekonwertowana na typ `Integer` .  
  
 Jeśli jednak zostanie ustawiona `Option Strict Off` , Visual Basic zezwala na niejawne konwersje zawężające, chociaż mogą spowodować nieoczekiwaną utratę danych lub precyzję. Z tego powodu zalecamy użycie `Option Strict On` podczas pisania kodu produkcyjnego. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Zobacz też

- [Operatory arytmetyczne](../../../language-reference/operators/arithmetic-operators.md)
- [Operatory Bit Shift](../../../language-reference/operators/bit-shift-operators.md)
- [Operatory porównania w Visual Basic](comparison-operators.md)
- [Operatory łączenia w Visual Basic](concatenation-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](logical-and-bitwise-operators.md)
- [Skuteczna kombinacja operatorów](efficient-combination-of-operators.md)
