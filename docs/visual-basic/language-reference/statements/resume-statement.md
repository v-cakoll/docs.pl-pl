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
ms.openlocfilehash: 884bdaa0c19508b5a6bf6377568a53acc6880518
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957690"
---
# <a name="resume-statement"></a><span data-ttu-id="ffbcf-102">Resume — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ffbcf-102">Resume Statement</span></span>
<span data-ttu-id="ffbcf-103">Wznawia wykonywanie po zakończeniu procedury obsługi błędu.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="ffbcf-104">Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie jest to możliwe, zamiast korzystania z `On Error` obsługi wyjątków bez struktury i instrukcji i. `Resume`</span><span class="sxs-lookup"><span data-stu-id="ffbcf-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="ffbcf-105">Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ffbcf-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffbcf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffbcf-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ffbcf-107">Części</span><span class="sxs-lookup"><span data-stu-id="ffbcf-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="ffbcf-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-108">Required.</span></span> <span data-ttu-id="ffbcf-109">Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="ffbcf-110">Jeśli wystąpił błąd w wywoływanej procedurze, wykonanie zostaje wznowione w instrukcji, która została ostatnio wywołana z procedury zawierającej procedurę obsługi błędu.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="ffbcf-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-111">Optional.</span></span> <span data-ttu-id="ffbcf-112">Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="ffbcf-113">Jeśli wystąpił błąd w wywoływanej procedurze, wykonywanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która została ostatnio wywołana z procedury zawierającej procedury obsługi błędu (lub `On Error Resume Next` instrukcji).</span><span class="sxs-lookup"><span data-stu-id="ffbcf-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="ffbcf-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-114">Optional.</span></span> <span data-ttu-id="ffbcf-115">Wykonanie wznowione w wierszu określonym w wymaganym `line` argumencie.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="ffbcf-116">`line` Argument jest etykietą wiersza lub numerem wiersza i musi znajdować się w tej samej procedurze jak program obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffbcf-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ffbcf-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ffbcf-118">Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie to możliwe, zamiast używania obsługi wyjątków niestrukturalnych i `On Error` instrukcji i. `Resume`</span><span class="sxs-lookup"><span data-stu-id="ffbcf-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="ffbcf-119">Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ffbcf-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="ffbcf-120">Jeśli używasz `Resume` instrukcji w innym miejscu niż w procedurze obsługi błędów, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="ffbcf-121">Instrukcji nie można używać w żadnej procedurze `Try...Catch...Finally` zawierającej instrukcję. `Resume`</span><span class="sxs-lookup"><span data-stu-id="ffbcf-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffbcf-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="ffbcf-122">Example</span></span>  
 <span data-ttu-id="ffbcf-123">W tym przykładzie używa `Resume` instrukcji, aby zakończyć obsługę błędów w procedurze, a następnie wznowić wykonywanie przy użyciu instrukcji, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="ffbcf-124">Numer błędu 55 został wygenerowany w celu zilustrowania użycia `Resume` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ffbcf-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="ffbcf-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffbcf-125">Requirements</span></span>  
 <span data-ttu-id="ffbcf-126">**Obszaru** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ffbcf-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ffbcf-127">**Hamulc** Visual Basic Runtime Library (w pliku Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="ffbcf-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffbcf-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffbcf-128">See also</span></span>

- [<span data-ttu-id="ffbcf-129">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ffbcf-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="ffbcf-130">Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ffbcf-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="ffbcf-131">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ffbcf-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
