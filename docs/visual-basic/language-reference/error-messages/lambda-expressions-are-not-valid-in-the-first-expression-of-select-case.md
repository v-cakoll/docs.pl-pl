---
title: "Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu &#39; Wybierz przypadek &#39; — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords: BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu &#39; Wybierz przypadek &#39; — Instrukcja
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
 [IF... Następnie... Else — instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Wybierz... Case-instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md)
