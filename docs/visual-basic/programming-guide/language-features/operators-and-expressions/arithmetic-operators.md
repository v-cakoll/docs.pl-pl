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
ms.openlocfilehash: 8ded8d7111bd37cf8762a202b728e814aa5a082b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352657"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Operatory arytmetyczne w Visual Basic
Operatory arytmetyczne są używane do wykonywania wielu znanych operacji arytmetycznych, które obejmują Obliczanie wartości liczbowych reprezentowanych przez literały, zmienne, inne wyrażenia, wywołania funkcji i właściwości oraz stałe. Również sklasyfikowane operatorami arytmetycznymi są operatory przesunięcia bitowego, które działają na poziomie poszczególnych bitów operandów i przesuwają wzorce bitów w lewo lub w prawo.  
  
## <a name="arithmetic-operations"></a>Operacje arytmetyczne  
 Można dodać dwie wartości w wyrażeniu razem z [operatorem +](../../../../visual-basic/language-reference/operators/addition-operator.md)lub odjąć jeden od innego za pomocą [operatora-operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Negacja używa także [operatora-(Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), ale z tylko jednym operandem, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Mnożenie i dzielenie używają odpowiednio [operatora *](../../../../visual-basic/language-reference/operators/multiplication-operator.md) i [operatora (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Potęgowanie używa [operatora ^](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Dzielenie liczb całkowitych jest przeprowadzane za pomocą [operatora \ (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Dzielenie liczb całkowitych zwraca iloraz, czyli liczbę całkowitą, która reprezentuje liczbę przypadków, w których dzielnik może być podzielony na dzielną bez uwzględniania reszty. Zarówno dzielnik, jak i dzielną muszą być typami całkowitymi (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`i `ULong`) dla tego operatora. Wszystkie inne typy muszą zostać najpierw przekonwertowane na typ całkowity. Poniższy przykład ilustruje dzielenie liczby całkowitej.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 Arytmetyka modulo jest przeprowadzana przy użyciu [operatora mod](../../../../visual-basic/language-reference/operators/mod-operator.md). Ten operator zwraca resztę po podzieleniu dzielnika na całkowitą liczbę razy. Jeśli zarówno dzielnik, jak i dzielną są typami całkowitymi, zwrócona wartość jest całką. Jeśli dzielnik i dzielną są typami zmiennoprzecinkowymi, zwracana wartość jest również zmiennoprzecinkowa. Poniższy przykład ilustruje to zachowanie.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Próba dzielenia przez zero  
 Dzielenie przez zero ma różne wyniki w zależności od typów danych. W przypadku podziałów całkowitych (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`) .NET Framework zgłasza wyjątek <xref:System.DivideByZeroException>. W operacjach dzielenia na typ danych `Decimal` lub `Single` .NET Framework zgłasza również wyjątek <xref:System.DivideByZeroException>.  
  
 W przypadku przedziałów zmiennoprzecinkowych obejmujących typ danych `Double`, żaden wyjątek nie jest zgłaszany, a wynik jest składową klasy reprezentującą <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>lub <xref:System.Double.NegativeInfinity>, w zależności od dywidendy. W poniższej tabeli zestawiono różne wyniki próby podzielenia wartości `Double` przez zero.  
  
|Typ danych dywidendy|Dzielnik — typ danych|Wartość dywidendy|Wynik|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (nie jest to liczba matematycznie zdefiniowana)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Gdy przechwytujesz wyjątek <xref:System.DivideByZeroException>, możesz użyć jego członków, aby ułatwić jego obsługę. Na przykład właściwość <xref:System.Exception.Message%2A> przechowuje tekst komunikatu dla wyjątku. Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Operacje bitu Shift  
 Operacja bitu Shift wykonuje arytmetyczną zmianę wzorca bitowego. Wzorzec jest zawarty w argumencie operacji po lewej stronie, podczas gdy argument operacji po prawej stronie określa liczbę pozycji do przesunięcia wzorca. Możesz przesunąć wzorzec w prawo z [operatorem > >](../../../../visual-basic/language-reference/operators/right-shift-operator.md) lub z lewej strony przy użyciu [operatora < <](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Typem danych operandu wzorca musi być `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`lub `ULong`. Typ danych operandu kwoty przesunięcia musi być `Integer` lub musi być rozszerzony, aby `Integer`.  
  
 Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu. Pozycje bitowe opuszczone przez zmianę są ustawiane w następujący sposób:  
  
- 0 dla arytmetycznego przesunięcia w lewo  
  
- 0 dla arytmetycznej zmiany liczby dodatniej  
  
- 0 dla operacji arytmetycznych po prawej stronie typu danych bez znaku (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
- 1 w celu przesunięcia w prawo arytmetyczne liczby ujemnej (`SByte`, `Short`, `Integer`lub `Long`)  
  
 Poniższy przykład przenosi wartość `Integer` w lewo i w prawo.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Przesunięcia arytmetyczne nigdy nie generują wyjątków przepełnienia.  
  
## <a name="bitwise-operations"></a>Operacje bitowe  
 Oprócz operatora logicznego, `Not`, `Or`, `And`i `Xor` wykonują również operacje arytmetyczne bitowe, gdy są używane na wartościach numerycznych. Aby uzyskać więcej informacji, zobacz "Operacje bitowe" w [operatorach logicznych i bitowych w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Bezpieczeństwo typów  
 Operandy powinny być zwykle tego samego typu. Na przykład, jeśli dodajesz zmienną `Integer`, należy ją dodać do innej zmiennej `Integer` i należy przypisać wynik do zmiennej typu `Integer`.  
  
 Jednym ze sposobów zapewnienia dobrego kodowania bezpiecznych typów jest użycie [instrukcji Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Jeśli ustawisz `Option Strict On`, Visual Basic automatycznie wykonuje konwersje *bezpieczne dla typów* . Na przykład, jeśli spróbujesz dodać zmienną `Integer` do zmiennej `Double` i przypisać wartość do zmiennej `Double`, operacja będzie powtarzana, ponieważ wartość `Integer` można przekonwertować na `Double` bez utraty danych. Niebezpieczne konwersje typu, z drugiej strony, powodują błąd kompilatora z `Option Strict On`. Na przykład, jeśli spróbujesz dodać zmienną `Integer` do zmiennej `Double` i przypisać wartość do zmiennej `Integer`, wynik błędu kompilatora, ponieważ zmienna `Double` nie może zostać niejawnie przekonwertowana na typ `Integer`.  
  
 Jeśli jednak ustawisz `Option Strict Off`, Visual Basic zezwala na niejawne konwersje zawężające, chociaż mogą spowodować nieoczekiwaną utratę danych lub precyzję. Z tego powodu zalecamy używanie `Option Strict On` podczas pisania kodu produkcyjnego. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Operatory arytmetyczne](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operatory Bit Shift](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory łączenia w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
