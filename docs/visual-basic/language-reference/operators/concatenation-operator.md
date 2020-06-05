---
title: '&amp;, operator'
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
ms.openlocfilehash: d778c0c99d6d074fe8b73aaf3660074643e7e136
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371612"
---
# <a name="amp-operator-visual-basic"></a>&amp;Operator (Visual Basic)
Generuje łączenie ciągów dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Any `String` lub `Object` Variable.  
  
 `expression1`  
 Wymagany. Każde wyrażenie z typem danych, który jest poszerzany do `String` .  
  
 `expression2`  
 Wymagany. Każde wyrażenie z typem danych, który jest poszerzany do `String` .  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ danych `expression1` lub `expression2` nie jest `String` , ale jest rozszerzony do `String` , jest konwertowany na `String` . Jeśli jeden z typów danych nie jest rozszerzony do `String` , kompilator generuje błąd.  
  
 Typ danych `result` to `String` . Jeśli co najmniej jedno wyrażenie zwróci wartość [Nothing lub nie](../nothing.md) ma wartości <xref:System.DBNull.Value?displayProperty=nameWithType> , są traktowane jako ciąg o wartości "".  
  
> [!NOTE]
> `&`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Znak handlowego "i" (&) może również służyć do identyfikowania zmiennych jako typów `Long` . Aby uzyskać więcej informacji, zobacz [Type characters](../../programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `&` operatora w celu wymuszenia łączenia ciągów. Wynikiem jest wartość ciągu reprezentująca połączenie dwóch operandów ciągu.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [&= — operator](and-assignment-operator.md)
- [Concatenation — Operatory](concatenation-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory łączenia w Visual Basic](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
