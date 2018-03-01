---
title: "Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu &#39; Wybierz przypadek &#39; — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="016fe-102">Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu &#39; Wybierz przypadek &#39; — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="016fe-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="016fe-103">Nie można użyć wyrażenia lambda wyrażenia testu w `Select Case` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="016fe-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="016fe-104">Definicje wyrażenia lambda zwrócić funkcje i wyrażenie testu `Select Case` instrukcja musi być typem podstawowym danych.</span><span class="sxs-lookup"><span data-stu-id="016fe-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="016fe-105">Poniższy kod przyczyny tego błędu:</span><span class="sxs-lookup"><span data-stu-id="016fe-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="016fe-106">**Identyfikator błędu:** BC36635</span><span class="sxs-lookup"><span data-stu-id="016fe-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="016fe-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="016fe-107">To correct this error</span></span>  
  
-   <span data-ttu-id="016fe-108">Sprawdź swój kod, aby określić, czy inny konstrukcji warunkowego, takich jak `If...Then...Else` instrukcji, będzie działać dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="016fe-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="016fe-109">Może mieć zamierzonym do wywołania tej funkcji, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="016fe-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="016fe-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="016fe-110">See Also</span></span>  
 [<span data-ttu-id="016fe-111">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="016fe-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="016fe-112">IF... Następnie... Else — instrukcja</span><span class="sxs-lookup"><span data-stu-id="016fe-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="016fe-113">Wybierz... Case-instrukcja</span><span class="sxs-lookup"><span data-stu-id="016fe-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
