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
ms.openlocfilehash: 9f1d77ac27def556d94fac12dbde2f36d5b139de
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649762"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Operatory arytmetyczne w Visual Basic
Operatory arytmetyczne są używane do wykonywania wielu znanych operacje arytmetyczne, które obejmują obliczanie wartości liczbowych, reprezentowane przez literały, zmienne, innych wyrażeń, funkcji i wywołania właściwości i stałe. Również sklasyfikowane za pomocą operatorów arytmetycznych są bit-shift — operatory, które działają na poziomie pojedynczych bitów operandu- and -shift ich wzorców bitowych do lewej lub prawej strony.  
  
## <a name="arithmetic-operations"></a>Operacje arytmetyczne  
 Należy dodać dwie wartości w wyrażeniu wraz z [+ — Operator](../../../../visual-basic/language-reference/operators/addition-operator.md), lub jeden z innego za pomocą odejmowania [-— Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), tak jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Używa również negacji [-— Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), ale przy użyciu tylko jeden argument w poniższym przykładzie pokazano.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Użyj mnożenia i dzielenia [* — Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md) i [/ — Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), odpowiednio, tak jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Używa potęgowania [^ — Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), tak jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Dzielenie liczby całkowitej wykonuje się za pomocą [\ — Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Dzielenie liczby całkowitej Zwraca iloraz, czyli liczba całkowita, która reprezentuje liczbę razy dzielnik można podzielić dzielna bez uwzględnienia reszta. Dzielnik i dzielna muszą być typami całkowitoliczbowymi (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, i `ULong`) dla tego operatora. Wszystkie pozostałe typy musi zostać przekonwertowana na typ całkowitoliczbowy najpierw. W poniższym przykładzie pokazano dzielenie liczby całkowitej.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 Arytmetycznego modulo odbywa się przy użyciu [Mod — Operator](../../../../visual-basic/language-reference/operators/mod-operator.md). Ten operator zwraca resztę z dzielenia dzielnik do dzielna całkowitą liczbę razy. W przypadku dzielnik i dzielna typów całkowitych, zwrócona wartość jest typu całkowitego. Dzielnik i dzielna są typy zmiennoprzecinkowe, zwrócona wartość jest również zmiennoprzecinkowych. W poniższym przykładzie pokazano to zachowanie.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Próba dzielenia przez Zero  
 Dzielenie przez zero ma różne wyniki w zależności od typów danych związane. W całkowitego podziałów (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zgłasza <xref:System.DivideByZeroException> wyjątku. W operacji dzielenia na `Decimal` lub `Single` typu danych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] generuje również <xref:System.DivideByZeroException> wyjątku.  
  
 W zmiennoprzecinkowych podziału, w których `Double` typu danych, jest zgłaszany żaden wyjątek, a wynik jest składowej klasy reprezentujące <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, lub <xref:System.Double.NegativeInfinity>, w zależności od dzielna. W poniższej tabeli przedstawiono różne wyniki próby dzielenia `Double` wartość przez zero.  
  
|Dzielna — typ danych|Typ danych dzielnik.|Wartość dzielna|Wynik|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (nie liczba zdefiniowanych ze sobą matematycznie)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Jeśli przechwytujesz <xref:System.DivideByZeroException> wyjątku, można używać jej elementów członkowskich ułatwią Ci go obsłużyć. Na przykład <xref:System.Exception.Message%2A> właściwość przechowuje tekst komunikatu dla wyjątku. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Operacje bitowe przesunięcia  
 Operacji przesunięcia bitowego dokonuje arytmetycznego przesunięcia wzorca bitowego. Wzorzec znajduje się w argumencie operacji po lewej stronie, gdy argument operacji po prawej stronie określa liczbę pozycji, aby przenieść do wzorca. Wzorzec można przesunięcia w prawo przy użyciu [>> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md) lub w lewo z [<< Operator](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Typ danych argumentu operacji wzorzec musi być `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`. Typ danych argumentu wielkość przesunięcia musi być `Integer` lub muszą rozszerzać się `Integer`.  
  
 Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie. Pozycje bitów zwolnione w wyniku przez zmianę są ustawione w następujący sposób:  
  
- 0 w przypadku arytmetyczne przesunięcie w lewo  
  
- 0 w przypadku liczby dodatniej arytmetyczne przesunięcie w prawo  
  
- 0 w przypadku arytmetyczne przesunięcie w prawo o typie danych bez znaku (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
- 1 arytmetyczne przesunięcie w prawo liczby ujemnej (`SByte`, `Short`, `Integer`, lub `Long`)  
  
 Poniższy przykład przenosi `Integer` wartości po lewej stronie i w prawo.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Arytmetycznego przesunięcia nigdy nie generują wyjątki przepełnienia.  
  
## <a name="bitwise-operations"></a>Operacje bitowe  
 Oprócz operatorów logicznych `Not`, `Or`, `And`, i `Xor` również wykonywać bitowe operacje arytmetyczne, gdy jest używana w przypadku wartości numerycznych. Aby uzyskać więcej informacji, zobacz "Bitowe operacje" w [logiczne i bitowe operatory w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Bezpieczeństwo typów  
 Zwykle należy argumentów operacji tego samego typu. Na przykład, jeśli robią dodawania przy użyciu `Integer` zmiennych, należy dodać ją do innego `Integer` zmiennej, na które należy przypisać wynik do zmiennej typu `Integer` także.  
  
 Jednym ze sposobów, aby zapewnić dobrą bezpiecznegop typu kodowania rozwiązaniem jest użycie [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Jeśli ustawisz `Option Strict On`, Visual Basic automatycznie wykonuje *bezpieczny* konwersji. Na przykład, jeśli użytkownik próbuje dodać `Integer` zmienną `Double` zmiennej i przypisać wartość `Double` zmiennej, operacja działa normalnie, ponieważ `Integer` można przekonwertować wartości na `Double` bez utraty danych. Konwersje typu niebezpieczne, z drugiej strony, powodują błąd kompilatora przy użyciu `Option Strict On`. Na przykład, jeśli użytkownik próbuje dodać `Integer` zmienną `Double` zmiennej i przypisać wartość `Integer` zmiennej, błąd kompilatora powstaje, ponieważ `Double` zmiennej nie można niejawnie przekonwertować na typ `Integer`.  
  
 Jeśli ustawisz `Option Strict Off`, jednak języka Visual Basic umożliwia niejawne konwersje zawężające została wykonana, chociaż może spowodować nieoczekiwane utraty danych lub precyzji. Z tego powodu zaleca się, że używasz `Option Strict On` podczas pisania kodu produkcyjnego. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Operatory arytmetyczne](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operatory Bit Shift](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operatory porównania w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory łączenia w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
