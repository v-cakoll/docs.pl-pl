---
title: Return — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: fe200add4e29fe4bbe0fdf335dcd94107b8ff1eb
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47113572"
---
# <a name="return-statement-visual-basic"></a>Return — Instrukcja (Visual Basic)
Zwraca kontrolę do kodu, który wywołał `Function`, `Sub`, `Get`, `Set`, lub `Operator` procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Część  
 `expression`  
 Wymagane w `Function`, `Get`, lub `Operator` procedury. Wyrażenie, która reprezentuje wartość zwracaną do wywołującego kodu.  
  
## <a name="remarks"></a>Uwagi  
 W `Sub` lub `Set` procedury `Return` instrukcja jest odpowiednikiem `Exit Sub` lub `Exit Property` instrukcji i `expression` nie musi zostać dostarczony.  
  
 W `Function`, `Get`, lub `Operator` procedury `Return` instrukcja musi zawierać `expression`, i `expression` musi być typu danych, który jest konwertowany na typ zwracany procedury. W `Function` lub `Get` procedury, masz także alternatywne przypisanie wyrażenia do nazwy procedury, która będzie służyć jako wartość zwracaną, a następnie wykonywanie `Exit Function` lub `Exit Property` instrukcji. W `Operator` procedury, należy użyć `Return expression`.  
  
 Może zawierać tyle `Return` instrukcji zgodnie z potrzebami w tej samej procedury.  
  
> [!NOTE]
>  Kod w `Finally` bloku, który jest uruchamiany po `Return` instrukcji w `Try` lub `Catch` blok jest napotkano, ale wcześniej `Return` wykonywania instrukcji. A `Return` instrukcji nie można uwzględnić w `Finally` bloku.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Return` instrukcji kilka razy, aby powrócić do kodu wywołującego, gdy procedura nie trzeba nic robić.  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
