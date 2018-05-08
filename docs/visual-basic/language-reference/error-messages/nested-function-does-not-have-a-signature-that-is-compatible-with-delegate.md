---
title: Funkcja zagnieżdżona nie ma podpisu zgodnego z delegatem &#39; &lt;element delegatename&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 94c53d30ad9aea9386fbb1be3e65fa31719f7a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>Funkcja zagnieżdżona nie ma podpisu zgodnego z delegatem &#39; &lt;element delegatename&gt;&#39;
Wyrażenia lambda zostanie przypisana do delegata, który ma niezgodny podpis. Na przykład w poniższym kodzie delegować `Del` zawiera dwa parametry liczby całkowitej.  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 Błąd jest wywoływany, jeśli wyrażenie lambda z jednym argumentem jest zadeklarowany jako typ `Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **Identyfikator błędu:** BC36532  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dostosuj definicji delegat lub wyrażenie lambda przypisanej tak, aby podpisy są zgodne.  
  
## <a name="see-also"></a>Zobacz też  
 [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
