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
ms.openlocfilehash: 40076b2ad6606b4c565bcd39dbeea9e55da47211
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963320"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Operatory logiczne i bitowe w Visual Basic
Operatory logiczne porównują `Boolean` wyrażenia i `Boolean` zwracają wynik. `And`Operatory, `Not` ,, i są binarne, ponieważ przyjmują dwa operandy, natomiast operator jest jednoargumentowy, ponieważ przyjmuje jeden operand. `Or` `AndAlso` `OrElse` `Xor` Niektóre z tych operatorów mogą również wykonywać bitowe operacje logiczne na wartościach całkowitych.  
  
## <a name="unary-logical-operator"></a>Jednoargumentowy operator logiczny  
 [Operator not](../../../../visual-basic/language-reference/operators/not-operator.md) wykonuje logiczne *Negacja* dla `Boolean` wyrażenia. Zwraca logiczne przeciwieństwo operandu. Jeśli wyrażenie `True`zwróci wartość, a następnie `Not` zwraca `False`; Jeśli wyrażenie `False`zwróci wartość, a następnie `Not` zwraca `True`. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Binarne operatory logiczne  
 [Operator and](../../../../visual-basic/language-reference/operators/and-operator.md) wykonuje koniunkcję logiczną dla dwóch `Boolean` wyrażeń. Jeśli oba wyrażenia są szacowane `True`do, `And` następnie `True`zwraca wartość. Jeśli co najmniej jedno wyrażenie oblicza `False`wartość, a następnie `And` zwraca `False`.  
  
 [Operator or](../../../../visual-basic/language-reference/operators/or-operator.md) wykonuje logiczne rozłączenie lub *włączenie* dwóch `Boolean` wyrażeń. Jeśli wyrażenie `True`zwróci wartość, lub obie wartości oblicza do `True`, następnie `Or` zwraca wartość `True`. Jeśli wyrażenie nie zostanie oszacowane `True`, `Or` zwraca `False`.  
  
 [Operator XOR](../../../../visual-basic/language-reference/operators/xor-operator.md) wykonuje logiczne *wykluczenia* dla dwóch `Boolean` wyrażeń. Jeśli dokładnie jedno wyrażenie ma `True`wartość, ale nie oba, `Xor` zwraca `True`. Jeśli oba wyrażenia obliczają `True` wartość lub obie wartości `False`obliczają `False`do, `Xor` zwraca.  
  
 Poniższy przykład ilustruje `And`operatory, `Or`i `Xor` .  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Operacje logiczne o krótkim obwodzie  
 [Operator AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) jest bardzo podobny do `And` operatora, dzięki czemu wykonuje także koniunkcję logiczną dla dwóch `Boolean` wyrażeń. Kluczową różnicą między tymi dwoma są `AndAlso` te, które wykazuje zachowanie podczas *krótkiego obwodu* . `AndAlso` Jeśli pierwsze wyrażenie w wyrażeniu zwraca wartość `False`, drugie wyrażenie nie jest oceniane, ponieważ nie może zmienić wyniku końcowego i `AndAlso` zwraca wartość `False`.  
  
 Podobnie [operator OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje krótkie, logiczne rozłączenie dwóch `Boolean` wyrażeń. `OrElse` Jeśli pierwsze wyrażenie w wyrażeniu zwraca wartość `True`, drugie wyrażenie nie jest oceniane, ponieważ nie może zmienić wyniku końcowego i `OrElse` zwraca wartość `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Krótkoterminowe kompromisy  
 Krótkie obwody mogą zwiększyć wydajność, nie obliczając wyrażenia, które nie może zmienić wyniku operacji logicznej. Jeśli jednak to wyrażenie wykonuje dodatkowe akcje, krótkie obwody pomija te akcje. Na przykład jeśli wyrażenie zawiera wywołanie `Function` procedury, ta procedura nie jest wywoływana, jeśli wyrażenie jest krótkie, a jakikolwiek dodatkowy kod zawarty `Function` w nie zostanie uruchomiony. W związku z tym funkcja może działać tylko sporadycznie i może nie być testowana prawidłowo. Lub logika programu może zależeć od kodu w `Function`.  
  
 Poniższy przykład ilustruje różnicę między elementami `And`, `Or`i ich krótkimi odpowiednikami.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 W poprzednim przykładzie należy zauważyć, że jakiś istotny kod `checkIfValid()` wewnątrz nie jest uruchamiany, gdy wywołanie jest krótkie. Pierwsza `If` instrukcja wywołuje `checkIfValid()` choć `12 > 45` Returns`False`, ponieważ`And` nie jest krótka obwód. Druga `If` instrukcja nie wywołuje `checkIfValid()`, ponieważ gdy `12 > 45` zwraca `False`, `AndAlso` krótkie obwody drugie wyrażenie. Trzecia `If` instrukcja wywołuje `checkIfValid()` choć `12 < 45` Returns`True`, ponieważ`Or` nie jest krótkim obwodem. Czwarta `If` instrukcja nie wywołuje metody `checkIfValid()`, ponieważ gdy `12 < 45` zwraca `True`, `OrElse` krótkie obwody drugie wyrażenie.  
  
## <a name="bitwise-operations"></a>Operacje bitowe  
 Operacje bitowe obliczają dwie wartości całkowite w postaci binarnej (podstawowej 2) formularza. Porównują bity w odpowiednich pozycjach, a następnie przypisują wartości na podstawie porównania. Poniższy przykład ilustruje `And` operatora.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 Poprzedni przykład ustawia wartość `x` na 1. Dzieje się tak z następujących powodów:  
  
- Wartości są traktowane jako dane binarne:  
  
     3 w postaci binarnej = 011  
  
     5 w postaci binarnej = 101  
  
- `And` Operator porównuje reprezentacje binarne, jedną pozycję binarną (bit) jednocześnie. Jeśli obie bity w danym położeniu są 1, to 1 zostanie umieszczony w tym położeniu w wyniku. Jeśli jeden bit ma wartość 0, wówczas wartość 0 jest umieszczana w tym położeniu w wyniku. W poprzednim przykładzie działa to w następujący sposób:  
  
     011 (3 w postaci binarnej)  
  
     101 (5 w postaci binarnej)  
  
     001 (wynik, w postaci binarnej)  
  
- Wynik jest traktowany jako decimal. Wartość 001 jest reprezentacją binarną 1, więc `x` = 1.  
  
 Operacja bitowa `Or` jest podobna, z tą różnicą, że wartość 1 jest przypisana do bitu wynik, jeśli jedna lub obie wartości w porównaniu z porównaniem są 1. `Xor`przypisuje 1 do bitu wynikowego, jeśli dokładnie jeden z porównywanych bitów (nie oba) ma wartość 1. `Not`przyjmuje jeden operand i odwraca wszystkie bity, w tym bit znaku, i przypisuje tę wartość do wyniku. Oznacza to, że w przypadku podpisanych `Not` liczb dodatnich zawsze zwraca wartość ujemną, a dla `Not` liczb ujemnych zawsze zwraca wartość dodatnią lub zero.  
  
 Operatory `AndAlso` i`OrElse` nie obsługują operacji bitowych.  
  
> [!NOTE]
> Operacje bitowe można wykonywać tylko w przypadku typów całkowitych. Aby można było wykonać operację bitową, wartości zmiennoprzecinkowe muszą być konwertowane na typy całkowite.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Wyrażenia logiczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory łączenia w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Skuteczna kombinacja operatorów](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
