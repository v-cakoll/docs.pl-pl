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
ms.openlocfilehash: edaaf09f5a984344f7e89c9da988c529774934e9
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583256"
---
# <a name="return-statement-visual-basic"></a>Return — Instrukcja (Visual Basic)
Zwraca kontrolę do kodu, który wywołał procedurę `Function`, `Sub`, `Get`, `Set` lub `Operator`.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Części  
 `expression`  
 Wymagane w procedurze `Function`, `Get` lub `Operator`. Wyrażenie, które reprezentuje wartość, która ma zostać zwrócona do kodu wywołującego.  
  
## <a name="remarks"></a>Uwagi  
 W procedurze `Sub` lub `Set`, instrukcja `Return` jest równoważna z `Exit Sub` lub `Exit Property` instrukcją i nie można podać `expression`.  
  
 W procedurze `Function`, `Get` lub `Operator` instrukcja `Return` musi zawierać `expression`, a `expression` musi oszacować do typu danych, który jest konwertowany na zwracany typ procedury. W procedurze `Function` lub `Get` można także przypisać wyrażenie do nazwy procedury, która ma stanowić wartość zwracaną, a następnie wykonać `Exit Function` lub `Exit Property` instrukcję. W procedurze `Operator` należy użyć `Return expression`.  
  
 Można dołączyć dowolną liczbę instrukcji `Return`, zgodnie z potrzebami w tej samej procedurze.  
  
> [!NOTE]
> Kod w bloku `Finally` jest uruchamiany po napotkaniu instrukcji `Return` w bloku `Try` lub `Catch`, ale przed wykonaniem tej instrukcji `Return`. Instrukcji `Return` nie można uwzględnić w bloku `Finally`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Return` kilka razy, aby powrócić do kodu wywołującego, gdy procedura nie musi wykonywać żadnych innych czynności.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Zobacz także

- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get, instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
