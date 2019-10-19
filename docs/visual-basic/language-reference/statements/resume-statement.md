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
ms.openlocfilehash: 7b8c2e123c04ff9720d690507ee41a6b52f40c3f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583277"
---
# <a name="resume-statement"></a><span data-ttu-id="39ee1-102">Resume — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="39ee1-102">Resume Statement</span></span>
<span data-ttu-id="39ee1-103">Wznawia wykonywanie po zakończeniu procedury obsługi błędu.</span><span class="sxs-lookup"><span data-stu-id="39ee1-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="39ee1-104">Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie jest to możliwe, zamiast korzystania z obsługi wyjątków niestrukturalnych oraz instrukcji `On Error` i `Resume`.</span><span class="sxs-lookup"><span data-stu-id="39ee1-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="39ee1-105">Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="39ee1-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39ee1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="39ee1-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="39ee1-107">Części</span><span class="sxs-lookup"><span data-stu-id="39ee1-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="39ee1-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="39ee1-108">Required.</span></span> <span data-ttu-id="39ee1-109">Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="39ee1-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="39ee1-110">Jeśli wystąpił błąd w wywoływanej procedurze, wykonanie zostaje wznowione w instrukcji, która została ostatnio wywołana z procedury zawierającej procedurę obsługi błędu.</span><span class="sxs-lookup"><span data-stu-id="39ee1-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="39ee1-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="39ee1-111">Optional.</span></span> <span data-ttu-id="39ee1-112">Jeśli błąd wystąpił w tej samej procedurze co program obsługi błędów, wykonanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="39ee1-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="39ee1-113">Jeśli wystąpił błąd w wywoływanej procedurze, wykonywanie jest wznawiane za pomocą instrukcji bezpośrednio po instrukcji, która została ostatnio wywołana z procedury zawierającej procedury obsługi błędu (lub instrukcji `On Error Resume Next`).</span><span class="sxs-lookup"><span data-stu-id="39ee1-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="39ee1-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="39ee1-114">Optional.</span></span> <span data-ttu-id="39ee1-115">Wykonanie wznowione w wierszu określonym w wymaganym argumencie `line`.</span><span class="sxs-lookup"><span data-stu-id="39ee1-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="39ee1-116">Argument `line` jest etykietą wiersza lub numerem wiersza i musi znajdować się w tej samej procedurze jak program obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="39ee1-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39ee1-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39ee1-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39ee1-118">Zalecamy używanie obsługi wyjątków strukturalnych w kodzie wszędzie tam, gdzie jest to możliwe, zamiast korzystania z obsługi wyjątków niestrukturalnych oraz instrukcji `On Error` i `Resume`.</span><span class="sxs-lookup"><span data-stu-id="39ee1-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="39ee1-119">Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="39ee1-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="39ee1-120">Jeśli używasz instrukcji `Resume` w innym miejscu niż w procedurze obsługi błędów, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="39ee1-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="39ee1-121">Instrukcji `Resume` nie można użyć w żadnej procedurze, która zawiera instrukcję `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="39ee1-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39ee1-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="39ee1-122">Example</span></span>  
 <span data-ttu-id="39ee1-123">W tym przykładzie używa instrukcji `Resume`, aby zakończyć obsługę błędów w procedurze, a następnie wznowić wykonywanie przy użyciu instrukcji, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="39ee1-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="39ee1-124">Numer błędu 55 został wygenerowany w celu zilustrowania użycia instrukcji `Resume`.</span><span class="sxs-lookup"><span data-stu-id="39ee1-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="39ee1-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39ee1-125">Requirements</span></span>  
 <span data-ttu-id="39ee1-126">**Przestrzeń nazw:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="39ee1-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="39ee1-127">**Zestaw:** Biblioteka środowiska uruchomieniowego Visual Basic (w pliku Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="39ee1-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39ee1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39ee1-128">See also</span></span>

- [<span data-ttu-id="39ee1-129">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="39ee1-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="39ee1-130">Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="39ee1-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="39ee1-131">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="39ee1-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
