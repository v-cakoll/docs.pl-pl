---
title: Operatory logiczne i bitowe w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 371d28629b39fb2808ca018ea69da3306a31f50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656155"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Operatory logiczne i bitowe w Visual Basic
Operatory logiczne porównują `Boolean` wyrażeń i przywracać `Boolean` wynik. `And`, `Or`, `AndAlso`, `OrElse`, I `Xor` operatory są *binary* ponieważ podejmują dwóch argumentów operacji, podczas gdy `Not` operator jest *jednoargumentowy* z powodu jednego argumentu. Niektóre z tych operatorów można również wykonywać operacje logiczne bitowe wartości całkowite.  
  
## <a name="unary-logical-operator"></a>Jednoargumentowy Operator logiczny  
 [Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) wykonuje logiczną *negacji* na `Boolean` wyrażenia. Daje on logicznej przeciwieństwem jej argument. Jeśli wyrażenie ma `True`, następnie `Not` zwraca `False`; Jeśli wyrażenie ma `False`, następnie `Not` zwraca `True`. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a>Operatory logiczne binarne  
 [i operatora](../../../../visual-basic/language-reference/operators/and-operator.md) wykonuje logiczną *połączeniu* na dwóch `Boolean` wyrażenia. Jeśli oba wyrażenia mają `True`, następnie `And` zwraca `True`. Jeśli co najmniej jedno z wyrażeń daje w wyniku `False`, następnie `And` zwraca `False`.  
  
 [Lub Operator](../../../../visual-basic/language-reference/operators/or-operator.md) wykonuje logiczną *rozłączenia* lub *włączenia* na dwóch `Boolean` wyrażenia. Jeśli wyrażenie zwraca `True`, lub oba obliczać `True`, następnie `Or` zwraca `True`. Jeśli żadna wyrażenie `True`, `Or` zwraca `False`.  
  
 [Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) wykonuje logiczną *wykluczeń* na dwóch `Boolean` wyrażenia. Jeśli dokładnie jedno wyrażenie daje w wyniku `True`, ale nie oba `Xor` zwraca `True`. Jeśli oba wyrażenia mają `True` lub oba obliczać `False`, `Xor` zwraca `False`.  
  
 Poniższy przykład przedstawia `And`, `Or`, i `Xor` operatorów.  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a>Zwarcie logicznego operacji  
 [AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md) jest bardzo podobny do `And` operatora, w tym również wykonuje logiczną na dwóch `Boolean` wyrażenia. Najważniejsza różnica między nimi jest to, że `AndAlso` wykazuje *zwarcie* zachowanie. Jeśli pierwsze wyrażenie w `AndAlso` wyrażenie daje w wyniku `False`, a następnie drugie wyrażenie nie jest oceniany, ponieważ nie można zmienić wynik końcowy i `AndAlso` zwraca `False`.  
  
 Podobnie [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje zwarcie logicznego rozłączenia dwóch `Boolean` wyrażenia. Jeśli pierwsze wyrażenie w `OrElse` wyrażenie daje w wyniku `True`, a następnie drugie wyrażenie nie jest oceniany, ponieważ nie można zmienić wynik końcowy i `OrElse` zwraca `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Zwarcie kompromisy  
 Zwarcie może poprawić wydajność przez nie obliczenia wyrażenia, którego nie można zmienić wynik operacji logicznej. Jednak jeśli tego wyrażenia przeprowadza dodatkowych akcji, zwarcie pomija te akcje. Na przykład, jeśli wyrażenie zawiera wywołanie `Function` procedury, że procedura nie jest wywoływana, gdy wyrażenie jest zwartym i jakiegokolwiek dodatkowego kodu zawarte w `Function` nie działa. W związku z tym funkcja może być uruchamiany tylko od czasu do czasu i może nie być poprawnie badane. Lub logiki program może być zależna od kodu w `Function`.  
  
 Poniższy przykład przedstawia różnice między `And`, `Or`i ich odpowiedniki short-circuiting.  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 W poprzednim przykładzie, należy pamiętać, że niektóre ważne kodu wewnątrz `checkIfValid()` nie działa, gdy wywołanie jest zwartym. Pierwszy `If` wywołania instrukcji `checkIfValid()` mimo że `12 > 45` zwraca `False`, ponieważ `And` nie zwarcia. Drugi `If` nie mogą wywoływać instrukcji `checkIfValid()`, ponieważ podczas `12 > 45` zwraca `False`, `AndAlso` short-circuits drugie wyrażenie. Trzeci `If` wywołania instrukcji `checkIfValid()` mimo że `12 < 45` zwraca `True`, ponieważ `Or` nie zwarcia. Czwarta `If` nie mogą wywoływać instrukcji `checkIfValid()`, ponieważ podczas `12 < 45` zwraca `True`, `OrElse` short-circuits drugie wyrażenie.  
  
## <a name="bitwise-operations"></a>Operacje bitowe  
 Operacje bitowe ocenić dwóch wartości całkowitych na wartości w postaci pliku binarnego (podstawa 2). Ich porównać bitów w odpowiednich miejscach, a następnie przypisz wartości na podstawie porównania. Poniższy przykład przedstawia `And` operatora.  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 Powyższy przykład ustawia wartość `x` do 1. Dzieje się z następujących powodów:  
  
-   Wartości są traktowane jako dane binarne:  
  
     3 w formacie binarnym = 011  
  
     5 w postaci binarnej = 101  
  
-   `And` Operator porównuje binarne reprezentacje jedną pozycję binarne (bit) w czasie. Jeśli oba bity na określonej pozycji 1, 1 znajduje się w tym miejscu w wyniku. Jeśli albo bit ma wartość 0, 0 znajduje się w tym miejscu w wyniku. W powyższym przykładzie wynik działania jest prawidłowy w następujący sposób:  
  
     011 (3 w formacie binarnym)  
  
     101 (5 w formacie binarnym)  
  
     001 (wyniku w postaci binarnej)  
  
-   Wynik jest traktowane jako dziesiętne. Wartość 001 to binarna reprezentacja 1, więc `x` = 1.  
  
 Bitowe `Or` operacja jest podobny, z tą różnicą, że 1 jest przypisany do bitu wyniku, jeśli jednego lub obu porównaniu bitów jest 1. `Xor` przypisuje 1 bitu wyniku, jeśli jest dokładnie jeden z porównaniu usługi bits (nie obie) 1. `Not` przyjmuje jeden operand i odwraca wszystkie bity, łącznie z bitowego logowania i przypisuje wartość tego wyniku. Oznacza to, że dla podpisanej liczby dodatnie `Not` zawsze zwraca wartość ujemną, a liczby ujemne `Not` zawsze zwraca wartość dodatnią lub wartość zero.  
  
 `AndAlso` i `OrElse` operatory nie obsługują operacje bitowe.  
  
> [!NOTE]
>  Operacje bitowe mogą być wykonywane na tylko w przypadku typów całkowitych. Wartości zmiennoprzecinkowych muszą zostać skonwertowane do typów całkowitych przed kontynuowaniem operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory logiczne/bitowe (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Wyrażenia logiczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operatory łączenia w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
