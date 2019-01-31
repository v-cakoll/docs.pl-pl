---
title: Funkcja zagnieżdżona nie posiada podpisu zgodnego z delegatem „<delegatename>”.
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: ea6f230715520cb35809d57db76b300da326ec9a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283468"
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
