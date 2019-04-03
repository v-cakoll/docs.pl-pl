---
title: Funkcja zagnieżdżona nie posiada podpisu zgodnego z delegatem „<delegatename>”.
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 04eae6d2c6d64e8a0f46ae3c2801a7eb6d893dca
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822295"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>Funkcja zagnieżdżona nie posiada podpisu zgodnego z delegatem "\<element delegatename >"
Wyrażenie lambda ma przypisane do delegata, który ma niezgodny podpis. Na przykład w poniższym kodzie delegować `Del` zawiera dwa parametry liczby całkowitej.  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 Błąd jest zgłaszany, jeśli wyrażenie lambda z jednym argumentem jest zadeklarowany jako typ `Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **Identyfikator błędu:** BC36532  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dostosowanie definicji delegat lub wyrażenie lambda przypisane tak, aby podpisy są zgodne.  
  
## <a name="see-also"></a>Zobacz także

- [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
