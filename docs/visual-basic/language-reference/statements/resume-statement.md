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
ms.openlocfilehash: 3f49f05f1deb2027b03bbf3443ca44f30c44344e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404216"
---
# <a name="resume-statement"></a><span data-ttu-id="80331-102">Resume — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="80331-102">Resume Statement</span></span>
<span data-ttu-id="80331-103">Wznawia wykonywanie po zakończeniu procedury obsługi błędu.</span><span class="sxs-lookup"><span data-stu-id="80331-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="80331-104">Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie jest to możliwe, zamiast korzystania z obsługi wyjątków bez struktury i `On Error` instrukcji i `Resume` .</span><span class="sxs-lookup"><span data-stu-id="80331-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="80331-105">Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="80331-105">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80331-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="80331-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="80331-107">Części</span><span class="sxs-lookup"><span data-stu-id="80331-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="80331-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="80331-108">Required.</span></span> <span data-ttu-id="80331-109">Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="80331-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="80331-110">Jeśli wystąpił błąd w wywoływanej procedurze, wykonanie zostaje wznowione w instrukcji, która została ostatnio wywołana z procedury zawierającej procedurę obsługi błędu.</span><span class="sxs-lookup"><span data-stu-id="80331-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="80331-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="80331-111">Optional.</span></span> <span data-ttu-id="80331-112">Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="80331-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="80331-113">Jeśli wystąpił błąd w wywoływanej procedurze, wykonywanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która została ostatnio wywołana z procedury zawierającej procedury obsługi błędu (lub `On Error Resume Next` instrukcji).</span><span class="sxs-lookup"><span data-stu-id="80331-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="80331-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="80331-114">Optional.</span></span> <span data-ttu-id="80331-115">Wykonanie wznowione w wierszu określonym w wymaganym `line` argumencie.</span><span class="sxs-lookup"><span data-stu-id="80331-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="80331-116">`line`Argument jest etykietą wiersza lub numerem wiersza i musi znajdować się w tej samej procedurze jak program obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="80331-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80331-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80331-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80331-118">Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie to możliwe, zamiast używania obsługi wyjątków niestrukturalnych i `On Error` `Resume` instrukcji i.</span><span class="sxs-lookup"><span data-stu-id="80331-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="80331-119">Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="80331-119">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="80331-120">Jeśli używasz `Resume` instrukcji w innym miejscu niż w procedurze obsługi błędów, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="80331-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="80331-121">`Resume`Instrukcji nie można używać w żadnej procedurze zawierającej `Try...Catch...Finally` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="80331-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80331-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="80331-122">Example</span></span>  
 <span data-ttu-id="80331-123">W tym przykładzie używa `Resume` instrukcji, aby zakończyć obsługę błędów w procedurze, a następnie wznowić wykonywanie przy użyciu instrukcji, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="80331-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="80331-124">Numer błędu 55 został wygenerowany w celu zilustrowania użycia `Resume` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="80331-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="80331-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80331-125">Requirements</span></span>  
 <span data-ttu-id="80331-126">**Przestrzeń nazw:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="80331-126">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="80331-127">**Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="80331-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80331-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80331-128">See also</span></span>

- [<span data-ttu-id="80331-129">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="80331-129">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="80331-130">Error — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="80331-130">Error Statement</span></span>](error-statement.md)
- [<span data-ttu-id="80331-131">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="80331-131">On Error Statement</span></span>](on-error-statement.md)
