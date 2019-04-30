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
ms.openlocfilehash: 2494eac2f61f112f3ba6321ada7404f8cd618049
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766639"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="2600c-102">Throw — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2600c-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="2600c-103">Zgłasza wyjątek w obrębie procedury.</span><span class="sxs-lookup"><span data-stu-id="2600c-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2600c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2600c-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="2600c-105">Część</span><span class="sxs-lookup"><span data-stu-id="2600c-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="2600c-106">Zawiera informacje dotyczące zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2600c-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="2600c-107">Opcjonalny, gdy znajdują się w `Catch` instrukcji, w przeciwnym razie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="2600c-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2600c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2600c-108">Remarks</span></span>  
 <span data-ttu-id="2600c-109">`Throw` Instrukcji zgłasza wyjątek, który może obsłużyć kodem obsługi wyjątków strukturalnych (`Try`... `Catch`... `Finally`) lub bez struktury kodu obsługi wyjątków (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="2600c-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="2600c-110">Możesz użyć `Throw` instrukcję w celu przechwytywania błędów w kodzie, ponieważ Visual Basic przesunięte stos wywołań, aż znajdzie odpowiedni kod obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2600c-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="2600c-111">A `Throw` instrukcji za pomocą wyrażenia nie można używać tylko w `Catch` instrukcji, w którym instrukcji case ponownie zgłasza wyjątek, aktualnie obsługiwany przez `Catch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2600c-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="2600c-112">`Throw` Instrukcji przywraca stos wywołań dla `expression` wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2600c-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="2600c-113">Jeśli `expression` nie zostanie podany, stos wywołań pozostanie niezmieniona.</span><span class="sxs-lookup"><span data-stu-id="2600c-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="2600c-114">Możesz uzyskać dostęp stos wywołań dla wyjątku za pomocą <xref:System.Exception.StackTrace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2600c-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2600c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2600c-115">Example</span></span>  
 <span data-ttu-id="2600c-116">Poniższy kod używa `Throw` instrukcję, aby zgłosić wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2600c-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a><span data-ttu-id="2600c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2600c-117">Requirements</span></span>  
 <span data-ttu-id="2600c-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="2600c-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="2600c-119">**Moduł:** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="2600c-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="2600c-120">**Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="2600c-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2600c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2600c-121">See also</span></span>

- [<span data-ttu-id="2600c-122">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2600c-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="2600c-123">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2600c-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
