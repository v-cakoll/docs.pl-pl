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
ms.openlocfilehash: ac47b6d7fa4861d18646a23f442caccc4062852f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819310"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Operatory logiczne i bitowe w Visual Basic
Operatory logiczne, porównanie `Boolean` wyrażeń i zwrócenia `Boolean` wynik. `And`, `Or`, `AndAlso`, `OrElse`, I `Xor` operatory są *binarne* ponieważ przyjmują dwa argumenty operacji, podczas gdy `Not` operator jest *jednoargumentowe* z powodu jeden argument operacji. Niektóre z tych operatorów można również wykonać operacje logiczne bitowe dla wartości całkowitych.  
  
## <a name="unary-logical-operator"></a>Jednoargumentowy Operator logiczny  
 [Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) wykonuje logiczne *negacji* na `Boolean` wyrażenia. Daje przeciwną wartość logiczną swojego operandu. Jeśli wyrażenie ma `True`, następnie `Not` zwraca `False`; Jeśli wyrażenie ma `False`, następnie `Not` zwraca `True`. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Operatory dwuargumentowe logiczne  
 [Operatora](../../../../visual-basic/language-reference/operators/and-operator.md) wykonuje logiczne *połączeniu* na dwóch `Boolean` wyrażenia. Jeśli oba wyrażenia mają `True`, następnie `And` zwraca `True`. Jeśli co najmniej jedno z wyrażeń daje w wyniku `False`, następnie `And` zwraca `False`.  
  
 [Operatora Or](../../../../visual-basic/language-reference/operators/or-operator.md) wykonuje logiczne *rozłączenia* lub *włączenia* na dwóch `Boolean` wyrażenia. Jeśli wyrażenie zwraca `True`, lub oba zwrócić `True`, następnie `Or` zwraca `True`. Jeśli żadna wyrażenie `True`, `Or` zwraca `False`.  
  
 [Xor — Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) wykonuje logiczne *wykluczeń* na dwóch `Boolean` wyrażenia. Jeśli dokładnie jedno wyrażenie, które daje w wyniku `True`, ale nie obu `Xor` zwraca `True`. Jeśli oba wyrażenia mają `True` lub zwrócić oba `False`, `Xor` zwraca `False`.  
  
 W poniższym przykładzie pokazano `And`, `Or`, i `Xor` operatorów.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Zwarcie operacji logicznych  
 [AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md) jest bardzo podobny do `And` operatora, w tym również wykonuje logiczną na dwóch `Boolean` wyrażenia. Główną różnicą między nimi jest to, że `AndAlso` wykazuje *zwarcie* zachowanie. Jeśli pierwsze wyrażenie w `AndAlso` wyrażenie daje w wyniku `False`, a następnie drugie wyrażenie nie jest oceniany, ponieważ nie można zmienić, wynik końcowy i `AndAlso` zwraca `False`.  
  
 Podobnie [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje zwarcie logicznego rozłączenia dwóch `Boolean` wyrażenia. Jeśli pierwsze wyrażenie w `OrElse` wyrażenie daje w wyniku `True`, a następnie drugie wyrażenie nie jest oceniany, ponieważ nie można zmienić, wynik końcowy i `OrElse` zwraca `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Zwarcie wad  
 Zwarcie może zwiększyć wydajność przez nie obliczenia wyrażenia, którego nie można zmienić wynik operacji logicznej. Jednak jeśli to wyrażenie wykonuje dodatkowe akcje, zwarcie pomija tych akcji. Na przykład, jeśli wyrażenie zawiera wywołanie `Function` procedurę, że procedura nie jest wywoływana, jeśli wyrażenie jest zwartym i wszelkie dodatkowe kod zawarty w `Function` nie działa. W związku z tym funkcja mogą być uruchamiane tylko od czasu do czasu i może nie być poprawnie badane. Lub logiki programu może zależeć od kodu w `Function`.  
  
 Poniższy przykład ilustruje różnicę między `And`, `Or`i ich odpowiedniki short-circuiting.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 W poprzednim przykładzie, należy pamiętać, że niektóre ważne kod wewnątrz `checkIfValid()` nie jest uruchamiane, gdy wywołanie jest zwartym. Pierwszy `If` instrukcja wywołuje `checkIfValid()` mimo że `12 > 45` zwraca `False`, ponieważ `And` nie powodują pominięcie. Drugi `If` instrukcja wywołuje `checkIfValid()`, ponieważ gdy `12 > 45` zwraca `False`, `AndAlso` short-circuits drugie wyrażenie. Trzeci `If` instrukcja wywołuje `checkIfValid()` mimo że `12 < 45` zwraca `True`, ponieważ `Or` nie powodują pominięcie. Czwarty `If` instrukcja wywołuje `checkIfValid()`, ponieważ gdy `12 < 45` zwraca `True`, `OrElse` short-circuits drugie wyrażenie.  
  
## <a name="bitwise-operations"></a>Operacje bitowe  
 Operacje bitowe ocenić dwóch wartości całkowitych, w postaci pliku binarnego (podstawa 2). Ich porównanie usługi bits w odpowiednich miejscach i przypisywanie na podstawie porównania wartości. W poniższym przykładzie pokazano `And` operatora.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Poprzedni przykład ustawia wartość `x` 1. Dzieje się z następujących powodów:  
  
-   Wartości są traktowane jako dane binarne:  
  
     3 w formacie binarnym = 011  
  
     5 w formacie binarnym = 101  
  
-   `And` Operator porównuje reprezentacji binarnych jedną pozycję binarny (bity) w danym momencie. Jeśli oba bity na określonej pozycji 1, 1 jest umieszczany w tym miejscu, w wyniku. Jeśli bit albo ma wartość 0, 0 jest umieszczany w tym miejscu, w wyniku. W powyższym przykładzie wynik działania jest prawidłowy w następujący sposób:  
  
     011 (3 w formacie binarnym)  
  
     101 (5 w formacie binarnym)  
  
     001 (wynik, w formacie binarnym)  
  
-   Wynik jest traktowany jako dziesiętne. Wartość 001 jest binarna reprezentacja 1, więc `x` = 1.  
  
 Operatora testu koniunkcji `Or` operacji jest podobny, z tą różnicą, że 1 jest przypisana do bitu wyniku, jeśli jeden lub oba bitów w porównaniu jest 1. `Xor` przypisuje do bitu wyniku 1, jeśli dokładnie jeden stosunku liczby bitów (nie obie) ma wartość 1. `Not` przyjmuje jeden argument operacji i odwraca wszystkie bity, łącznie z bitem, przypisuje wartość do wyniku. Oznacza to, że dla podpisanej liczby dodatnie `Not` zawsze zwraca wartość ujemną i liczb ujemnych `Not` zawsze zwraca wartość dodatnią lub wartość zero.  
  
 `AndAlso` i `OrElse` operatorów nie obsługują operacje bitowe.  
  
> [!NOTE]
>  Operacje bitowe można wykonać na tylko w przypadku typów całkowitych. Wartości zmiennoprzecinkowe można przekonwertować do typów całkowitych, przed rozpoczęciem operacji na poziomie bitowym.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Wyrażenia logiczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory porównania w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory łączenia w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
