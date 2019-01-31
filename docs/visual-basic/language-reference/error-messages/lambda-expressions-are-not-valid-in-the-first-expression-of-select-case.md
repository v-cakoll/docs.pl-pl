---
title: Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu instrukcji „Select Case"
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: d56515093020a4c987d132491957ce6db9e21683
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287797"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="7fc8b-102">Wyrażenia lambda nie są prawidłowe w pierwszym wyrażeniu instrukcji „Select Case"</span><span class="sxs-lookup"><span data-stu-id="7fc8b-102">Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>
<span data-ttu-id="7fc8b-103">Nie można użyć wyrażenia lambda wyrażenia testu w `Select Case` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7fc8b-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="7fc8b-104">Definicje Wyrażenie lambda zwraca funkcje i wyrażenia testu `Select Case` instrukcja musi być typem danych podstawowych.</span><span class="sxs-lookup"><span data-stu-id="7fc8b-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="7fc8b-105">Poniższy kod powoduje błąd:</span><span class="sxs-lookup"><span data-stu-id="7fc8b-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="7fc8b-106">**Identyfikator błędu:** BC36635</span><span class="sxs-lookup"><span data-stu-id="7fc8b-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7fc8b-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="7fc8b-107">To correct this error</span></span>  
  
-   <span data-ttu-id="7fc8b-108">Sprawdź swój kod, aby określić, czy innej konstrukcji warunkowych, takich jak `If...Then...Else` instrukcji, będzie działać dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="7fc8b-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="7fc8b-109">Może być przeznaczone do wywołania funkcji, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="7fc8b-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fc8b-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fc8b-110">See also</span></span>
- [<span data-ttu-id="7fc8b-111">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="7fc8b-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="7fc8b-112">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="7fc8b-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="7fc8b-113">Instrukcja Select...Case</span><span class="sxs-lookup"><span data-stu-id="7fc8b-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
