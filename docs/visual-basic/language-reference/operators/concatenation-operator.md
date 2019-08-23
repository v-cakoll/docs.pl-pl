---
title: '&amp;Operator (Visual Basic)'
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
ms.openlocfilehash: d387b2dfdbb3fefe357364f7b2a3dde155cbd489
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968353"
---
# <a name="amp-operator-visual-basic"></a>&amp;Operator (Visual Basic)
Generuje łączenie ciągów dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagane. Any `String` lub`Object` Variable.  
  
 `expression1`  
 Wymagany. Każde wyrażenie z typem danych, który jest poszerzany `String`do.  
  
 `expression2`  
 Wymagana. Każde wyrażenie z typem danych, który jest poszerzany `String`do.  
  
## <a name="remarks"></a>Uwagi  
 `expression1` Jeśli typ `String`danych lub `expression2` nie `String` jest, ale jest rozszerzony do `String`, jest konwertowany na. Jeśli jeden z typów danych nie jest rozszerzony do `String`, kompilator generuje błąd.  
  
 Typ `result` danych to `String`. Jeśli co najmniej jedno wyrażenie zwróci wartość [Nothing lub nie](../../../visual-basic/language-reference/nothing.md) ma wartości <xref:System.DBNull.Value?displayProperty=nameWithType>, są traktowane jako ciąg o wartości "".  
  
> [!NOTE]
> Operator może być przeciążony, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. `&` Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Znak handlowego "i" (&) może również służyć do identyfikowania zmiennych `Long`jako typów. Aby uzyskać więcej informacji, zobacz [Type characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `&` operatora w celu wymuszenia łączenia ciągów. Wynikiem jest wartość ciągu reprezentująca połączenie dwóch operandów ciągu.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [&=, operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory łączenia w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
