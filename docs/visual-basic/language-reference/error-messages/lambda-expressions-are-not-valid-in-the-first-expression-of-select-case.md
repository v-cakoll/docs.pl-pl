---
title: Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu &#39;Select Case&#39; — instrukcja
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: afefa821f9695dbbfe2a96aee5afd3171ae5b1db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700224"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu &#39;Select Case&#39; — instrukcja
Nie można użyć wyrażenia lambda wyrażenia testu w `Select Case` instrukcji. Definicje Wyrażenie lambda zwraca funkcje i wyrażenia testu `Select Case` instrukcja musi być typem danych podstawowych.  
  
 Poniższy kod powoduje błąd:  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **Identyfikator błędu:** BC36635  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź swój kod, aby określić, czy innej konstrukcji warunkowych, takich jak `If...Then...Else` instrukcji, będzie działać dla Ciebie.  
  
-   Może być przeznaczone do wywołania funkcji, jak pokazano w poniższym kodzie:  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>Zobacz także
- [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Instrukcja Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
