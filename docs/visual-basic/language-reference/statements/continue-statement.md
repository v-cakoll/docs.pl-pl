---
title: "Continue — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="93ec1-102">Continue — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93ec1-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="93ec1-103">Formant transferów bezpośrednio do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="93ec1-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93ec1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93ec1-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="93ec1-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93ec1-105">Remarks</span></span>  
 <span data-ttu-id="93ec1-106">Można przenieść z wewnątrz `Do`, `For`, lub `While` pętli do następnej iteracji pętli tego.</span><span class="sxs-lookup"><span data-stu-id="93ec1-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="93ec1-107">Kontrola przechodzi natychmiast w teście warunek pętli, który jest odpowiednikiem transferu do `For` lub `While` instrukcji lub `Do` lub `Loop` instrukcji, która zawiera `Until` lub `While` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="93ec1-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="93ec1-108">Można użyć `Continue` w dowolnym miejscu w pętli, które umożliwia transferów.</span><span class="sxs-lookup"><span data-stu-id="93ec1-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="93ec1-109">Zasady umożliwiające przekazanie sterowania są takie same jak z [instrukcji GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="93ec1-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="93ec1-110">Na przykład, jeśli jest całkowicie zawarte w pętli `Try` bloku, `Catch` bloku, lub `Finally` bloku, można użyć `Continue` do przeniesienia poza pętli.</span><span class="sxs-lookup"><span data-stu-id="93ec1-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="93ec1-111">Jeśli z drugiej strony, `Try`... `End Try` struktury znajduje się w pętli, nie można użyć `Continue` do przekazywania kontroli z `Finally` blok i służy do przeniesienia poza `Try` lub `Catch` zablokować tylko wtedy, gdy transfer całkowicie poza `Try`... `End Try` struktury.</span><span class="sxs-lookup"><span data-stu-id="93ec1-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="93ec1-112">Jeśli na przykład masz pętle zagnieżdżone tego samego typu `Do` pętli w innym `Do` pętli, `Continue Do` instrukcji przejdzie do następnej iteracji najbardziej wewnętrzną funkcją `Do` pętli, która go zawiera.</span><span class="sxs-lookup"><span data-stu-id="93ec1-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="93ec1-113">Nie można użyć `Continue` aby przejść do następnej iteracji pętli zawierającego tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="93ec1-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="93ec1-114">Jeśli na przykład masz pętle zagnieżdżone o różnych typach `Do` pętli w ramach `For` pętli, możesz przejść do następnej iteracji pętli albo za pomocą `Continue Do` lub `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="93ec1-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93ec1-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="93ec1-115">Example</span></span>  
 <span data-ttu-id="93ec1-116">Poniższy przykład kodu wykorzystuje `Continue While` instrukcji, aby przejść do następnej kolumnie tablicy, jeśli dzielnik jest równy zero.</span><span class="sxs-lookup"><span data-stu-id="93ec1-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="93ec1-117">`Continue While` Znajduje się wewnątrz `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="93ec1-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="93ec1-118">Przekazuje do `While col < lastcol` instrukcja, która jest najbardziej wewnętrzną funkcją następnej iteracji `While` pętli, które zawiera `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="93ec1-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="93ec1-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93ec1-119">See Also</span></span>  
 [<span data-ttu-id="93ec1-120">Czy... Loop — instrukcja</span><span class="sxs-lookup"><span data-stu-id="93ec1-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="93ec1-121">Dla... Next — instrukcja</span><span class="sxs-lookup"><span data-stu-id="93ec1-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="93ec1-122">While... End While — instrukcja</span><span class="sxs-lookup"><span data-stu-id="93ec1-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="93ec1-123">Try... CATCH... Finally — instrukcja</span><span class="sxs-lookup"><span data-stu-id="93ec1-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
