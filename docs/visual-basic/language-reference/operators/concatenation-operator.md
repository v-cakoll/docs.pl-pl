---
title: "&amp;— Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76c8fc52a518dfe7850a5680b7d4f06f3d09bf73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a>&amp;— Operator (Visual Basic)
Tworzy połączenie ciągów dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Wszelkie `String` lub `Object` zmiennej.  
  
 `expression1`  
 Wymagany. Dowolne wyrażenie z typem danych rozszerzająca do `String`.  
  
 `expression2`  
 Wymagany. Dowolne wyrażenie z typem danych rozszerzająca do `String`.  
  
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
 [& = — operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory łączenia w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
