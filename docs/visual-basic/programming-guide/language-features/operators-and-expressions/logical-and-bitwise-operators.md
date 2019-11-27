---
title: Operatory logiczne i bitowe
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
ms.openlocfilehash: 55a246c0d56501a409ebbc7d0d0aa39ae9fa1770
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343596"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Operatory logiczne i bitowe w Visual Basic
Operatory logiczne porównują wyrażenia `Boolean` i zwracają wynik `Boolean`. Operatory `And`, `Or`, `AndAlso`, `OrElse`i `Xor` są *binarne* , ponieważ przyjmują dwa operandy, natomiast operator `Not` jest *jednoargumentowy* , ponieważ przyjmuje jeden operand. Niektóre z tych operatorów mogą również wykonywać bitowe operacje logiczne na wartościach całkowitych.  
  
## <a name="unary-logical-operator"></a>Jednoargumentowy operator logiczny  
 [Operator not](../../../../visual-basic/language-reference/operators/not-operator.md) wykonuje logiczne *negację* na wyrażeniu `Boolean`. Zwraca logiczne przeciwieństwo operandu. Jeśli wyrażenie zwróci wartość `True`, wówczas `Not` zwraca `False`; Jeśli wyrażenie zwróci wartość `False`, `Not` zwraca `True`. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Binarne operatory logiczne  
 [Operator and](../../../../visual-basic/language-reference/operators/and-operator.md) *wykonuje koniunkcję logiczną dla* dwóch wyrażeń `Boolean`. Jeśli oba wyrażenia są szacowane do `True`, wówczas `And` zwraca `True`. Jeśli co najmniej jedno wyrażenie jest szacowane do `False`, `And` zwraca `False`.  
  
 [Operator or](../../../../visual-basic/language-reference/operators/or-operator.md) *wykonuje logiczne* *rozłączenie lub włączenie* dwóch wyrażeń `Boolean`. Jeśli wyrażenie zwróci wartość `True`lub obie wartości są szacowane do `True`, `Or` zwraca `True`. Jeśli żadne wyrażenie nie ma wartości `True`, `Or` zwraca `False`.  
  
 [Operator XOR](../../../../visual-basic/language-reference/operators/xor-operator.md) wykonuje logiczne *wykluczenie* na dwóch wyrażeniach `Boolean`. Jeśli dokładnie jedno wyrażenie ma wartość `True`, ale nie oba, `Xor` zwraca `True`. Jeśli oba wyrażenia są szacowane do `True` lub obie wartości są szacowane do `False`, `Xor` zwraca `False`.  
  
 Poniższy przykład ilustruje operatory `And`, `Or`i `Xor`.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Operacje logiczne o krótkim obwodzie  
 [Operator AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) jest bardzo podobny do operatora `And`, w którym wykonuje również koniunkcję logiczną na dwóch wyrażeniach `Boolean`. Kluczową różnicą między tymi dwoma jest to, że `AndAlso` wykazuje zachowanie dotyczące *krótkiego obwodu* . Jeśli pierwsze wyrażenie w wyrażeniu `AndAlso` oblicza `False`, drugie wyrażenie nie jest oceniane, ponieważ nie może zmienić wyniku końcowego, a `AndAlso` zwraca `False`.  
  
 Podobnie [operator OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje krótkie, logiczne rozłączenie dwóch wyrażeń `Boolean`. Jeśli pierwsze wyrażenie w wyrażeniu `OrElse` oblicza `True`, drugie wyrażenie nie jest oceniane, ponieważ nie może zmienić wyniku końcowego, a `OrElse` zwraca `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Krótkoterminowe kompromisy  
 Krótkie obwody mogą zwiększyć wydajność, nie obliczając wyrażenia, które nie może zmienić wyniku operacji logicznej. Jeśli jednak to wyrażenie wykonuje dodatkowe akcje, krótkie obwody pomija te akcje. Na przykład jeśli wyrażenie zawiera wywołanie procedury `Function`, ta procedura nie jest wywoływana, jeśli wyrażenie jest krótkie, a żaden dodatkowy kod zawarty w `Function` nie zostanie uruchomiony. W związku z tym funkcja może działać tylko sporadycznie i może nie być testowana prawidłowo. Lub logika programu może zależeć od kodu w `Function`.  
  
 Poniższy przykład ilustruje różnicę między elementami `And`, `Or`i ich krótkich odpowiedników obwodów.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 W poprzednim przykładzie należy zauważyć, że jakiś istotny kod wewnątrz `checkIfValid()` nie jest uruchamiany, gdy wywołanie jest krótkie. Pierwsza instrukcja `If` wywołuje `checkIfValid()`, mimo że `12 > 45` zwraca `False`, ponieważ `And` nie jest krótkim obwodem. Druga instrukcja `If` nie wywołuje `checkIfValid()`, ponieważ `12 > 45` zwraca `False`, `AndAlso` drugie wyrażenie. Trzecia instrukcja `If` wywołuje `checkIfValid()` nawet wtedy, gdy `12 < 45` zwraca `True`, ponieważ `Or` nie jest krótkim obwodem. Czwarta instrukcja `If` nie wywołuje `checkIfValid()`, ponieważ `12 < 45` zwraca `True`, `OrElse` drugie wyrażenie.  
  
## <a name="bitwise-operations"></a>Operacje bitowe  
 Operacje bitowe obliczają dwie wartości całkowite w postaci binarnej (podstawowej 2) formularza. Porównują bity w odpowiednich pozycjach, a następnie przypisują wartości na podstawie porównania. Poniższy przykład ilustruje operator `And`.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Powyższy przykład ustawia wartość `x` na 1. Dzieje się tak z następujących powodów:  
  
- Wartości są traktowane jako dane binarne:  
  
     3 w postaci binarnej = 011  
  
     5 w postaci binarnej = 101  
  
- Operator `And` porównuje reprezentacje binarne, jedną pozycję binarną (bit) jednocześnie. Jeśli obie bity w danym położeniu są 1, to 1 zostanie umieszczony w tym położeniu w wyniku. Jeśli jeden bit ma wartość 0, wówczas wartość 0 jest umieszczana w tym położeniu w wyniku. W poprzednim przykładzie działa to w następujący sposób:  
  
     011 (3 w postaci binarnej)  
  
     101 (5 w postaci binarnej)  
  
     001 (wynik, w postaci binarnej)  
  
- Wynik jest traktowany jako decimal. Wartość 001 jest reprezentacją binarną 1, więc `x` = 1.  
  
 Operacja `Or` bitowego jest podobna, z tą różnicą, że wartość 1 jest przypisana do bitu wynik, jeśli jedna lub obie wartości w porównaniu z porównywanymi bitami są 1. `Xor` przypisuje 1 do bitu wynikowego, jeśli dokładnie jeden z porównywanych bitów (nie oba) wynosi 1. `Not` przyjmuje jeden operand i odwraca wszystkie bity, w tym bit znaku, i przypisuje tę wartość do wyniku. Oznacza to, że dla zapisywanych liczb dodatnich, `Not` zawsze zwraca ujemną wartość i dla liczb ujemnych, `Not` zawsze zwraca wartość dodatnią lub zero.  
  
 Operatory `AndAlso` i `OrElse` nie obsługują operacji bitowych.  
  
> [!NOTE]
> Operacje bitowe można wykonywać tylko w przypadku typów całkowitych. Aby można było wykonać operację bitową, wartości zmiennoprzecinkowe muszą być konwertowane na typy całkowite.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Wyrażenia logiczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory łączenia w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
