---
title: Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu &#39;Select Case&#39; — instrukcja
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: c492615850ec089fe35c1ae4eaba90a741e30f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu &#39;Select Case&#39; — instrukcja
Nie można użyć wyrażenia lambda wyrażenia testu w `Select Case` instrukcji. Definicje wyrażenia lambda zwrócić funkcje i wyrażenie testu `Select Case` instrukcja musi być typem podstawowym danych.  
  
 Poniższy kod przyczyny tego błędu:  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **Identyfikator błędu:** BC36635  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź swój kod, aby określić, czy inny konstrukcji warunkowego, takich jak `If...Then...Else` instrukcji, będzie działać dla Ciebie.  
  
-   Może mieć zamierzonym do wywołania tej funkcji, jak pokazano w poniższym kodzie:  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [If...Then...Else, instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Select...Case, instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md)
