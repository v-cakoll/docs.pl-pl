---
title: Resume — instrukcja (Visual Basic)
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
ms.openlocfilehash: fcb50a9c7e36bab046be25d7f82f91cfe0f9be8e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966921"
---
# <a name="resume-statement"></a><span data-ttu-id="79eed-102">Resume — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="79eed-102">Resume Statement</span></span>
<span data-ttu-id="79eed-103">Wznawia działanie po zakończeniu procedury obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="79eed-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="79eed-104">Sugerujemy, że używasz strukturalna Obsługa wyjątków w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez określonej struktury i `On Error` i `Resume` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="79eed-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="79eed-105">Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="79eed-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79eed-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="79eed-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="79eed-107">Części</span><span class="sxs-lookup"><span data-stu-id="79eed-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="79eed-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="79eed-108">Required.</span></span> <span data-ttu-id="79eed-109">Jeśli błąd wystąpił w tej samej procedury obsługi błędów, wykonanie zostanie wznowione za pomocą instrukcji, które spowodowały błąd.</span><span class="sxs-lookup"><span data-stu-id="79eed-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="79eed-110">Jeśli błąd wystąpił w wywołanej procedurze, wykonanie wznawia działanie w instrukcji, która ostatnio wywołana poza procedura zawierająca procedurę obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="79eed-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="79eed-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="79eed-111">Optional.</span></span> <span data-ttu-id="79eed-112">Jeśli błąd wystąpił w tej samej procedury obsługi błędów, wykonanie zostanie wznowione za pomocą instrukcji natychmiast następującej instrukcji, które spowodowały błąd.</span><span class="sxs-lookup"><span data-stu-id="79eed-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="79eed-113">Jeśli błąd wystąpił w wywołanej procedurze, wykonanie zostanie wznowione instrukcji od razu następującej instrukcji, które ostatnio wywołana poza procedura zawierająca procedurę obsługi błędów (lub `On Error Resume Next` instrukcji).</span><span class="sxs-lookup"><span data-stu-id="79eed-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="79eed-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="79eed-114">Optional.</span></span> <span data-ttu-id="79eed-115">Wykonanie zostanie wznowione w wierszu określonym w wymaganym `line` argumentu.</span><span class="sxs-lookup"><span data-stu-id="79eed-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="79eed-116">`line` Argument jest etykieta wiersza lub numer wiersza i musi znajdować się w tej samej procedury obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="79eed-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79eed-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79eed-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79eed-118">Zalecane jest użycie strukturalna Obsługa wyjątków w kodzie, jeśli to możliwe, zamiast korzystać z obsługi wyjątków bez określonej struktury i `On Error` i `Resume` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="79eed-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="79eed-119">Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="79eed-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="79eed-120">Jeśli używasz `Resume` wystąpi błąd instrukcji dowolnym innym niż w procedurze obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="79eed-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="79eed-121">`Resume` Instrukcji nie można używać w dowolnej procedury, która zawiera `Try...Catch...Finally` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="79eed-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79eed-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="79eed-122">Example</span></span>  
 <span data-ttu-id="79eed-123">W tym przykładzie użyto `Resume` instrukcję, aby zakończyć obsługi błędów w procedurze, a następnie wznowić wykonywania za pomocą instrukcji, które spowodowały błąd.</span><span class="sxs-lookup"><span data-stu-id="79eed-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="79eed-124">Numer błędu 55 jest generowany w celu zilustrowania użytkowania `Resume` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="79eed-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="79eed-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="79eed-125">Requirements</span></span>  
 <span data-ttu-id="79eed-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="79eed-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="79eed-127">**Zestaw:** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="79eed-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79eed-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79eed-128">See also</span></span>
- [<span data-ttu-id="79eed-129">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="79eed-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="79eed-130">Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="79eed-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="79eed-131">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="79eed-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
