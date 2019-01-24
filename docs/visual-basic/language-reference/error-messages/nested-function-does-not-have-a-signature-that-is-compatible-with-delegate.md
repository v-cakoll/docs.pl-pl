---
title: Funkcja zagnieżdżona nie posiada podpisu zgodnego z delegatem &#39; &lt;element delegatename&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: abfda4ee6064ec9ea54b8a3c383d10f8263a1458
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506410"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>Funkcja zagnieżdżona nie posiada podpisu zgodnego z delegatem &#39; &lt;element delegatename&gt;&#39;
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
