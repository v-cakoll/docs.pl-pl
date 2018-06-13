---
title: '&amp; — Operator (Visual Basic)'
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
ms.openlocfilehash: 28d8cdb22974d77edf055ab9b2c6c767872e6783
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604305"
---
# <a name="amp-operator-visual-basic"></a>&amp; — Operator (Visual Basic)
Tworzy połączenie ciągów dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wszelkie `String` lub `Object` zmiennej.  
  
 `expression1`  
 Wymagana. Dowolne wyrażenie z typem danych rozszerzająca do `String`.  
  
 `expression2`  
 Wymagana. Dowolne wyrażenie z typem danych rozszerzająca do `String`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ danych miary `expression1` lub `expression2` nie jest `String` , ale rozszerzenie do `String`, jest konwertowana na `String`. Jeśli jeden z typów danych nie są rozszerzane `String`, kompilator generuje błąd.  
  
 Typ danych miary `result` jest `String`. Jeśli jeden lub oba wyrażenia mają [nic](../../../visual-basic/language-reference/nothing.md) lub mieć wartość <xref:System.DBNull.Value?displayProperty=nameWithType>, są traktowane jako ciąg o wartości "".  
  
> [!NOTE]
>  `&` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
>  Handlowe "i" (&) znaków mogą służyć do identyfikowania zmienne jako typ `Long`. Aby uzyskać więcej informacji, zobacz [znaków typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `&` operatora, aby wymusić ciągów. Wynik jest wartością ciągu reprezentujący łączenia operandów dwa parametry.  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [&=, operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory łączenia w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
