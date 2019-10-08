---
title: Continue — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 9ee5fb19db6eafeb7e4bed12935d0b950d6368d6
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005106"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="ad551-102">Continue — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad551-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="ad551-103">Natychmiast przenosi kontrolę do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="ad551-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad551-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad551-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="ad551-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad551-105">Remarks</span></span>  
 <span data-ttu-id="ad551-106">Można dokonać transferu z wewnątrz pętli `Do`, `For` lub `While` do następnej iteracji tej pętli.</span><span class="sxs-lookup"><span data-stu-id="ad551-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="ad551-107">Kontrolka natychmiast przechodzi do testu warunku pętli, który jest równoważny do przenoszenia do instrukcji `For` lub `While` lub do instrukcji `Do` lub `Loop`, która zawiera klauzulę `Until` lub `While`.</span><span class="sxs-lookup"><span data-stu-id="ad551-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="ad551-108">Można użyć `Continue` w dowolnej lokalizacji w pętli, która umożliwia transfery.</span><span class="sxs-lookup"><span data-stu-id="ad551-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="ad551-109">Reguły zezwalające na transfer kontroli są takie same jak w przypadku [instrukcji goto](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ad551-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="ad551-110">Na przykład jeśli pętla jest całkowicie zawarta w bloku `Try`, blok `Catch` lub blok `Finally`, można użyć `Continue` do przetransferowania z pętli.</span><span class="sxs-lookup"><span data-stu-id="ad551-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="ad551-111">Jeśli z drugiej strony, struktura `Try`... `End Try` jest zawarta w pętli, nie można użyć `Continue` do transferowania kontroli z bloku `Finally` i można jej użyć do przetransferowania z `Try` lub `Catch` bloków tylko wtedy, gdy transfer jest całkowicie z @no_ Struktura _T-6... `End Try`.</span><span class="sxs-lookup"><span data-stu-id="ad551-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="ad551-112">Jeśli istnieją zagnieżdżone pętle tego samego typu, na przykład pętla `Do` w innej pętli `Do`, instrukcja `Continue Do` przeskakuje do następnej iteracji wewnętrznej pętli `Do`, która ją zawiera.</span><span class="sxs-lookup"><span data-stu-id="ad551-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="ad551-113">Nie można użyć `Continue`, aby przejść do następnej iteracji zawierającej pętlę tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="ad551-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="ad551-114">Jeśli istnieją zagnieżdżone pętle różnych typów, na przykład pętla `Do` w pętli `For`, można przejść do następnej iteracji każdej pętli, używając `Continue Do` lub `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="ad551-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad551-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad551-115">Example</span></span>  
 <span data-ttu-id="ad551-116">Poniższy przykład kodu używa instrukcji `Continue While`, aby przejść do następnej kolumny tablicy, Jeśli dzielnik jest równy zero.</span><span class="sxs-lookup"><span data-stu-id="ad551-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="ad551-117">@No__t-0 jest wewnątrz pętli `For`.</span><span class="sxs-lookup"><span data-stu-id="ad551-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="ad551-118">Przesyła do `While col < lastcol` instrukcji, która jest następną iteracją wewnętrznej pętli `While`, która zawiera pętlę `For`.</span><span class="sxs-lookup"><span data-stu-id="ad551-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="ad551-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad551-119">See also</span></span>

- [<span data-ttu-id="ad551-120">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ad551-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="ad551-121">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ad551-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="ad551-122">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ad551-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="ad551-123">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ad551-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
