---
title: Operatory porównania
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: e1feb08539e47ec6fda64aa1a1f8ec2cc19f7b62
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346065"
---
# <a name="comparison-operators-in-visual-basic"></a>Operatory porównania w Visual Basic
Operatory porównania porównują dwa wyrażenia i zwracają `Boolean` wartość, która reprezentuje relację ich wartości. Istnieją operatory do porównywania wartości liczbowych, operatorów do porównywania ciągów i operatorów do porównywania obiektów. Wszystkie trzy typy operatorów zostały omówione w tym dokumencie.  
  
## <a name="comparing-numeric-values"></a>Porównywanie wartości liczbowych  
 Visual Basic porównuje wartości liczbowe przy użyciu sześciu liczbowych operatorów porównywania. Każdy operator przyjmuje jako operandy dwa wyrażenia, które obliczają wartości numeryczne. W poniższej tabeli przedstawiono operatory i przedstawiono przykłady poszczególnych elementów.  
  
|Operator|Testowany warunek|Przykłady|  
|--------------|----------------------|--------------|  
|`=` (równość)|Czy wartość pierwszego wyrażenia jest równa wartości sekundy?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (nierówność)|Czy wartość pierwszego wyrażenia jest nierówna wartości sekundy?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (mniejsze niż)|Czy wartość pierwszego wyrażenia jest mniejsza niż wartość drugiego?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (większe niż)|Czy wartość pierwszego wyrażenia jest większa niż wartość drugiego?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (mniejsze niż lub równe)|Czy wartość pierwszego wyrażenia jest mniejsza lub równa wartości sekundy?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (większe lub równe)|Czy wartość pierwszego wyrażenia jest większa niż lub równa wartości sekundy?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Porównywanie ciągów  
 Visual Basic porównuje ciągi przy użyciu [operatora like](../../../../visual-basic/language-reference/operators/like-operator.md) oraz liczbowych operatorów porównania. Operator `Like` pozwala określić wzorzec. Ciąg jest porównywany z wzorcem i jeśli jest zgodny, wynik jest `True`. W przeciwnym razie wynik jest `False`. Operatory liczbowe umożliwiają porównanie wartości `String` na podstawie ich kolejności sortowania, jak pokazano w poniższym przykładzie.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Wynikiem powyższego przykładu jest `True`, ponieważ pierwszy znak w pierwszym ciągu sortuje przed pierwszym znakiem w drugim ciągu. Jeśli pierwsze znaki były równe, porównywanie będzie kontynuowane do następnego znaku w obu ciągach i tak dalej. Można również testować równość ciągów przy użyciu operatora równości, jak pokazano w poniższym przykładzie.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Jeśli jeden ciąg jest prefiksem innego, na przykład "AA" i "aaa", dłuższy ciąg jest traktowany jako większy niż krótszy ciąg. Ilustruje to poniższy przykład.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 Kolejność sortowania jest oparta na porównaniu binarnej lub porównującej tekst w zależności od ustawienia `Option Compare`. Aby uzyskać więcej informacji, zobacz [opcja porównania instrukcji](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Porównywanie obiektów  
 Visual Basic porównuje dwie zmienne odwołań do obiektów z [operatorem is](../../../../visual-basic/language-reference/operators/is-operator.md) i [operatorem IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md). Można użyć dowolnego z tych operatorów, aby określić, czy dwie zmienne referencyjne odwołują się do tego samego wystąpienia obiektu. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 W poprzednim przykładzie `x Is y` oblicza `True`, ponieważ obie zmienne odwołują się do tego samego wystąpienia. Ten wynik należy do poniższego przykładu.  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 W poprzednim przykładzie `x Is y` oblicza `False`, ponieważ chociaż zmienne odwołują się do obiektów tego samego typu, odwołują się do różnych wystąpień tego typu.  
  
 Jeśli chcesz przeprowadzić test dla dwóch obiektów, które nie wskazują tego samego wystąpienia, operator `IsNot` umożliwia uniknięcie clumsyego w sposób gramatyczny `Not` i `Is`. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 W poprzednim przykładzie `If a IsNot b` jest równoznaczne z `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Porównywanie typu obiektu  
 Można sprawdzić, czy obiekt jest określonego typu z wyrażeniem `TypeOf`...`Is`. Składnia jest następująca:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Gdy `typename` określa typ interfejsu, wyrażenie `TypeOf`...`Is` zwraca `True`, jeśli obiekt implementuje typ interfejsu. Gdy `typename` jest typem klasy, wyrażenie zwraca `True`, jeśli obiekt jest wystąpieniem określonej klasy lub klasy, która pochodzi od określonej klasy. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 W poprzednim przykładzie wyrażenie `TypeOf x Is Control` oblicza `True`, ponieważ typ `x` jest `Button`, który dziedziczy po `Control`.  
  
 Aby uzyskać więcej informacji, zobacz [operator typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Zobacz także

- [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operatory](../../../../visual-basic/language-reference/operators/index.md)
- [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory łączenia w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
