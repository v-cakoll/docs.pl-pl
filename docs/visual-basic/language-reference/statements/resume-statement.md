---
title: Resume — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 1d03f631893be51529f29af824de0d684bf43804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resume-statement"></a><span data-ttu-id="477d2-102">Resume — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="477d2-102">Resume Statement</span></span>
<span data-ttu-id="477d2-103">Wznawia wykonywanie po zakończeniu procedury obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="477d2-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="477d2-104">Zaleca się, że używasz, obsługa wyjątków strukturalnych w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez struktury i `On Error` i `Resume` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="477d2-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="477d2-105">Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="477d2-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="477d2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="477d2-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="477d2-107">Części</span><span class="sxs-lookup"><span data-stu-id="477d2-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="477d2-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="477d2-108">Required.</span></span> <span data-ttu-id="477d2-109">Jeśli błąd wystąpił w tej samej procedury co program obsługi błędów, zostanie wznowione instrukcja, która spowodowała błąd wykonywania.</span><span class="sxs-lookup"><span data-stu-id="477d2-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="477d2-110">Jeśli błąd wystąpił w wywoływana procedura, wykonanie wznawia działanie w instrukcji, która ostatnio została wywołana poza procedury zawierające procedury obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="477d2-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="477d2-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="477d2-111">Optional.</span></span> <span data-ttu-id="477d2-112">Jeśli w tę samą procedurę obsługi błędu wystąpił błąd, wykonanie wznawia z instrukcją natychmiast po instrukcji, który spowodował błąd.</span><span class="sxs-lookup"><span data-stu-id="477d2-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="477d2-113">Jeśli błąd wystąpił w wywoływana procedura, wykonanie wznawia z instrukcją natychmiast po instrukcji, które ostatnio została wywołana poza procedury zawierająca procedurę obsługi błędu (lub `On Error Resume Next` instrukcji).</span><span class="sxs-lookup"><span data-stu-id="477d2-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="477d2-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="477d2-114">Optional.</span></span> <span data-ttu-id="477d2-115">Wznawia wykonywanie w wierszu określonym w wymaganym `line` argumentu.</span><span class="sxs-lookup"><span data-stu-id="477d2-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="477d2-116">`line` Argument wiersza etykiety lub numeru wiersza i musi być w tej samej procedury co program obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="477d2-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="477d2-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="477d2-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="477d2-118">Zalecane jest użycie Obsługa wyjątków strukturalnych w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez struktury i `On Error` i `Resume` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="477d2-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="477d2-119">Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="477d2-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="477d2-120">Jeśli używasz `Resume` instrukcji dowolnym innym niż w procedurze obsługi błędów, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="477d2-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="477d2-121">`Resume` Instrukcji nie można użyć w dowolnej procedury, która zawiera `Try...Catch...Finally` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="477d2-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="477d2-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="477d2-122">Example</span></span>  
 <span data-ttu-id="477d2-123">W tym przykładzie użyto `Resume` instrukcji, aby zakończyć obsługi błędów w procedurze, a następnie Wznów wykonywanie instrukcji, który spowodował błąd.</span><span class="sxs-lookup"><span data-stu-id="477d2-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="477d2-124">Błąd 55 jest generowane w celu zilustrowania użycie `Resume` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="477d2-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="477d2-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="477d2-125">Requirements</span></span>  
 <span data-ttu-id="477d2-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="477d2-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="477d2-127">**Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="477d2-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="477d2-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="477d2-128">See Also</span></span>  
 [<span data-ttu-id="477d2-129">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="477d2-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="477d2-130">Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="477d2-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)  
 [<span data-ttu-id="477d2-131">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="477d2-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
