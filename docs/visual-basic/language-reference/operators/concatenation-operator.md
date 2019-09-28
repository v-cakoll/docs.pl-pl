---
title: Operator &amp; (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: aaa7c1b9ab7f6c920180d97b55c3bdeb23f00e02
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592247"
---
# <a name="amp-operator-visual-basic"></a>Operator &amp; (Visual Basic)
Generuje łączenie ciągów dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Każda zmienna `String` lub `Object`.  
  
 `expression1`  
 Wymagany. Każde wyrażenie z typem danych, które poszerza do `String`.  
  
 `expression2`  
 Wymagany. Każde wyrażenie z typem danych, które poszerza do `String`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ danych `expression1` lub `expression2` nie jest `String`, ale rozszerza do `String`, zostanie przekonwertowany na `String`. Jeśli jeden z typów danych nie zostanie rozszerzony do `String`, kompilator generuje błąd.  
  
 Typ danych `result` jest `String`. Jeśli co najmniej jedno wyrażenie zwróci wartość [Nothing lub nie](../../../visual-basic/language-reference/nothing.md) ma wartości <xref:System.DBNull.Value?displayProperty=nameWithType>, są traktowane jako ciąg o wartości "".  
  
> [!NOTE]
> Operator `&` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Znak handlowego "i" (&) może również służyć do identyfikowania zmiennych jako typu `Long`. Aby uzyskać więcej informacji, zobacz [Type characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa operatora `&` w celu wymuszenia łączenia ciągów. Wynikiem jest wartość ciągu reprezentująca połączenie dwóch operandów ciągu.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [&=, operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory łączenia w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
