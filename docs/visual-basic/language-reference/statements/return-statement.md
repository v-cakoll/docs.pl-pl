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
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957674"
---
# <a name="return-statement-visual-basic"></a>Return — Instrukcja (Visual Basic)
Zwraca kontrolę do kodu, który wywołał `Function`procedurę `Sub`, `Get`, `Set`, lub `Operator` .  
  
## <a name="syntax"></a>Składnia  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>Części  
 `expression`  
 Wymagane w `Function`procedurze, `Get`lub. `Operator` Wyrażenie, które reprezentuje wartość, która ma zostać zwrócona do kodu wywołującego.  
  
## <a name="remarks"></a>Uwagi  
 `Set` `Exit Property` `Exit Sub` `expression` W procedurze `Sub` lubinstrukcjajestrównoznacznazinstrukcją`Return` or i nie może być dostarczone.  
  
 `Get` `Operator` `expression`W procedurze `expression` ,, lub, instrukcja musi zawierać, i musi oszacować do typu danych, który jest konwertowany na zwracany typ procedury. `Return` `Function` W procedurze `Get` `Exit Function` lub można także przypisać wyrażenie do nazwy procedury, która ma stanowić wartość zwracaną, a następnie wykonuje instrukcję or `Exit Property`. `Function` W procedurze należy użyć `Return expression`. `Operator`  
  
 W tej samej procedurze można `Return` dołączyć dowolną liczbę instrukcji.  
  
> [!NOTE]
> Kod `Finally` w bloku jest uruchamiany `Try` `Return` po napotkaniu instrukcji w bloku lub `Catch` , ale przed wykonaniem tej `Return` instrukcji. Instrukcja nie może być uwzględniona `Finally` w bloku. `Return`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Return` instrukcji kilka razy, aby powrócić do kodu wywołującego, gdy procedura nie musi wykonywać żadnych innych czynności.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Zobacz także

- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
