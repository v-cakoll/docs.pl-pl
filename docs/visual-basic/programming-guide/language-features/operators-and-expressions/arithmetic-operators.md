---
title: Operatory arytmetyczne w Visual Basic
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
ms.openlocfilehash: cd66d08eba973a796472fcbd40a6a84edbbb62ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655587"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Operatory arytmetyczne w Visual Basic
Operatory arytmetyczne służą do wykonywania wielu znanych operacje arytmetyczne, obejmujących obliczanie wartości liczbowych reprezentowany przez literały, zmienne, inne wyrażenia, funkcji i wywołaniach właściwości i stałe. Również są sklasyfikowane z operatorów arytmetycznych są operatory przesunięcia bitowego, które działają na poziomie poszczególnych bitów operandy i przesunięcia ich wzorców bit do lewej lub prawej.  
  
## <a name="arithmetic-operations"></a>Operacje arytmetyczne  
 Można dodać dwóch wartości w wyrażeniu razem z [+ — Operator](../../../../visual-basic/language-reference/operators/addition-operator.md), lub między sobą z odejmowania [-— Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), tak jak w poniższym przykładzie pokazano.  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 Używa również negacji [-— Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), ale zawierającą tylko jeden argument, jak w poniższym przykładzie pokazano.  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 Użyj mnożenia i dzielenia [* — Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md) i [/ — Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)odpowiednio, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 Zapis wykładniczy używa [^ — Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 Dzielenie liczby całkowitej odbywa się przy użyciu [\ — Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Dzielenie liczby całkowitej Zwraca iloraz, oznacza to, że liczba całkowita, która reprezentuje liczbę dzielnik można podzielić na dzielna bez uwzględnienia reszta. Zarówno dzielnik i dzielna muszą być typów całkowitych (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, i `ULong`) dla tego operatora. Wszystkie inne typy należy przekonwertować na typ całkowity najpierw. W poniższym przykładzie pokazano dzielenie liczby całkowitej.  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 Arytmetycznego modulo odbywa się przy użyciu [Mod Operator](../../../../visual-basic/language-reference/operators/mod-operator.md). Ten operator zwraca resztę po podzieleniu dzielnik do dzielna całkowitą liczbę razy. Jeżeli dzielnik i dzielna są typy całkowite, zwracana wartość jest dołączony. Jeśli dzielnik i dzielna typów zmiennoprzecinkowych, zwrócona wartość jest również zmiennoprzecinkowych. W poniższym przykładzie pokazano to zachowanie.  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>Próba dzielenia przez Zero  
 Dzielenie przez zero, ma różne wyniki, w zależności od typów danych związane. W wartości całkowitych podziałów (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zgłasza <xref:System.DivideByZeroException> wyjątku. W operacji dzielenia na `Decimal` lub `Single` typu danych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] również zgłasza <xref:System.DivideByZeroException> wyjątku.  
  
 W podziału liczb zmiennoprzecinkowych, w których `Double` typ danych nie jest wyjątek i wynikiem jest element członkowski klasy reprezentujące <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, lub <xref:System.Double.NegativeInfinity>, w zależności od dzielna. W poniższej tabeli przedstawiono różne wyniki próby dzielenia `Double` wartości przez zero.  
  
|Typ danych dzielna|Typ danych dzielnik.|Wartość dzielna|Wynik|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (nie ze sobą matematycznie zdefiniowanych numer)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Gdy catch <xref:System.DivideByZeroException> wyjątku, można użyć jej elementów członkowskich ułatwiające jego obsługa. Na przykład <xref:System.Exception.Message%2A> właściwość przechowuje tekst komunikatu dla wyjątku. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Operacje bitowe przesunięcia  
 Operacja bit-shift dokonuje arytmetycznego przesunięcia wzorca bitowego. Wzorzec znajduje się w argument operacji po lewej stronie, gdy argument operacji po prawej stronie określa liczbę pozycji, które mają zostać przesunięte ze wzorcem. Wzorzec można przesunięcia w prawo z [>> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md) lub w lewo z [<< Operator](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Typ danych argumentu wzorzec musi być `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`. Typ danych argumentu wielkość przesunięcia musi być `Integer` lub należy rozszerzyć do `Integer`.  
  
 Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bitów przesunąć poza jednym zakończeniu wynik nie są ponownie na drugim końcu. Pozycji z bitowego pojazdowy zmianę są ustawione w następujący sposób:  
  
-   0 dla arytmetyczne przesunięcie w lewo  
  
-   0 dla arytmetyczne przesunięcie w prawo z liczbą dodatnią  
  
-   0 dla arytmetyczne przesunięcie w prawo o typie danych bez znaku (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
-   1 w przypadku liczby ujemnej arytmetyczne przesunięcie w prawo (`SByte`, `Short`, `Integer`, lub `Long`)  
  
 Poniższy przykład przewiduje `Integer` wartość w lewo i w prawo.  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 Arytmetycznego przesunięcia nigdy nie generowanie wyjątków przepełnienia.  
  
## <a name="bitwise-operations"></a>Operacje bitowe  
 Oprócz operatorów logicznych, `Not`, `Or`, `And`, i `Xor` również wykonać arytmetyki bitowe stosowania na wartości liczbowe. Aby uzyskać więcej informacji, zobacz "Operator działania" w [logiczne i bitowe operatory w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Zabezpieczenie typów  
 Argumenty operacji należy tego samego typu. Na przykład, jeśli przeprowadzasz dodawania przy `Integer` zmiennej, należy dodać ją do innej `Integer` zmiennej, a powinien Przypisz wynik do zmiennej typu `Integer` również.  
  
 Jednym ze sposobów zapewnienia dobrej bezpieczne kodowanie rozwiązaniem jest użycie [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Jeśli ustawisz `Option Strict On`, Visual Basic automatycznie wykonuje *bezpieczne* konwersji. Na przykład, jeśli próbujesz dodać `Integer` zmienną `Double` zmiennej i przypisać wartości do `Double` zmiennej, operacja działa normalnie, ponieważ `Integer` można przekonwertować wartości `Double` bez utraty danych. Konwersje typu niebezpieczny z drugiej strony, spowodować błąd kompilatora z `Option Strict On`. Na przykład, jeśli próbujesz dodać `Integer` zmienną `Double` zmiennej i przypisać wartości do `Integer` zmiennej, wystąpi błąd kompilatora wyników, ponieważ `Double` zmiennej nie można niejawnie przekonwertować na typ `Integer`.  
  
 Jeśli ustawisz `Option Strict Off`, jednak Visual Basic umożliwia niejawnej konwersji zawężającej została wykonana, chociaż może spowodować nieoczekiwane utrata danych lub dokładności. Z tego powodu zaleca się, że używasz `Option Strict On` podczas pisania kodu produkcyjnego. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory arytmetyczne](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operatory Bit Shift](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operatory łączenia w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
