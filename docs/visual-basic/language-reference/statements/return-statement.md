---
title: Return, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: cdb58e32c30c8e6c1662fb698ac5576c3f71258c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404203"
---
# <a name="return-statement-visual-basic"></a>Return — Instrukcja (Visual Basic)
Zwraca kontrolę do kodu, który wywołał `Function` `Sub` procedurę,,, `Get` `Set` lub `Operator` .  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Część  
 `expression`  
 Wymagane w `Function` procedurze, `Get` lub `Operator` . Wyrażenie, które reprezentuje wartość, która ma zostać zwrócona do kodu wywołującego.  
  
## <a name="remarks"></a>Uwagi  
 W `Sub` procedurze lub `Set` `Return` instrukcja jest równoznaczna z `Exit Sub` `Exit Property` instrukcją or i `expression` nie może być dostarczone.  
  
 W `Function` procedurze, `Get` , lub `Operator` , `Return` instrukcja musi zawierać `expression` , i `expression` musi oszacować do typu danych, który jest konwertowany na zwracany typ procedury. W `Function` procedurze lub `Get` można także przypisać wyrażenie do nazwy procedury, która ma stanowić wartość zwracaną, a następnie wykonuje `Exit Function` `Exit Property` instrukcję or. W `Operator` procedurze należy użyć `Return expression` .  
  
 `Return`W tej samej procedurze można dołączyć dowolną liczbę instrukcji.  
  
> [!NOTE]
> Kod w bloku jest `Finally` uruchamiany po `Return` `Try` napotkaniu instrukcji w bloku lub `Catch` , ale przed wykonaniem tej `Return` instrukcji. `Return`Instrukcja nie może być uwzględniona w `Finally` bloku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Return` instrukcji kilka razy, aby powrócić do kodu wywołującego, gdy procedura nie musi wykonywać żadnych innych czynności.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Zobacz też

- [Function, instrukcja](function-statement.md)
- [Sub, instrukcja](sub-statement.md)
- [Get — Instrukcja](get-statement.md)
- [Set — Instrukcja](set-statement.md)
- [Operator — Instrukcja](operator-statement.md)
- [Property — Instrukcja](property-statement.md)
- [Exit, instrukcja](exit-statement.md)
- [Try...Catch...Finally, instrukcja](try-catch-finally-statement.md)
