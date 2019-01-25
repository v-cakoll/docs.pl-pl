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
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="e1777-102">Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu &#39;Select Case&#39; — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e1777-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="e1777-103">Nie można użyć wyrażenia lambda wyrażenia testu w `Select Case` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e1777-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="e1777-104">Definicje Wyrażenie lambda zwraca funkcje i wyrażenia testu `Select Case` instrukcja musi być typem danych podstawowych.</span><span class="sxs-lookup"><span data-stu-id="e1777-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="e1777-105">Poniższy kod powoduje błąd:</span><span class="sxs-lookup"><span data-stu-id="e1777-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="e1777-106">**Identyfikator błędu:** BC36635</span><span class="sxs-lookup"><span data-stu-id="e1777-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e1777-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e1777-107">To correct this error</span></span>  
  
-   <span data-ttu-id="e1777-108">Sprawdź swój kod, aby określić, czy innej konstrukcji warunkowych, takich jak `If...Then...Else` instrukcji, będzie działać dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="e1777-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="e1777-109">Może być przeznaczone do wywołania funkcji, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e1777-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1777-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1777-110">See also</span></span>
- [<span data-ttu-id="e1777-111">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="e1777-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="e1777-112">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="e1777-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="e1777-113">Instrukcja Select...Case</span><span class="sxs-lookup"><span data-stu-id="e1777-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
