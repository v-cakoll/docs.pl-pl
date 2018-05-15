---
title: Throw — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="1f6ae-102">Throw — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f6ae-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="1f6ae-103">Zgłasza wyjątek w obrębie procedury.</span><span class="sxs-lookup"><span data-stu-id="1f6ae-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f6ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f6ae-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="1f6ae-105">Część</span><span class="sxs-lookup"><span data-stu-id="1f6ae-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="1f6ae-106">Zawiera informacje o wyjątku, który zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="1f6ae-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="1f6ae-107">Opcjonalny, gdy znajdującej się w `Catch` instrukcji, w przeciwnym razie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="1f6ae-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f6ae-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f6ae-108">Remarks</span></span>  
 <span data-ttu-id="1f6ae-109">`Throw` Instrukcji zgłasza wyjątek, który może obsługiwać kodem obsługi wyjątków strukturalnych (`Try`... `Catch`... `Finally`) lub bez struktury kod obsługi wyjątków (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="1f6ae-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="1f6ae-110">Można użyć `Throw` instrukcji pułapki błędów w kodzie, ponieważ Visual Basic umożliwia przeniesienie w górę stosu wywołań, aż do znalezienia odpowiedni kod obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="1f6ae-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="1f6ae-111">A `Throw` instrukcji za pomocą wyrażenia nie można użyć tylko w `Catch` instrukcji, w którym instrukcji case ponownie zgłasza wyjątek, w obecnie obsługiwane przez `Catch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1f6ae-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="1f6ae-112">`Throw` Instrukcji resetuje stosie wywołań `expression` wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1f6ae-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="1f6ae-113">Jeśli `expression` nie zostanie podany, stos wywołań pozostanie niezmieniona.</span><span class="sxs-lookup"><span data-stu-id="1f6ae-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="1f6ae-114">Dostęp można uzyskać stos wywołań dla wyjątku za pomocą <xref:System.Exception.StackTrace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1f6ae-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f6ae-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f6ae-115">Example</span></span>  
 <span data-ttu-id="1f6ae-116">Poniższy kod używa `Throw` instrukcji, aby zgłosić wyjątek:</span><span class="sxs-lookup"><span data-stu-id="1f6ae-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="1f6ae-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f6ae-117">Requirements</span></span>  
 <span data-ttu-id="1f6ae-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="1f6ae-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="1f6ae-119">**Moduł:** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="1f6ae-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="1f6ae-120">**Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="1f6ae-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6ae-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f6ae-121">See Also</span></span>  
 [<span data-ttu-id="1f6ae-122">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1f6ae-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="1f6ae-123">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1f6ae-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
