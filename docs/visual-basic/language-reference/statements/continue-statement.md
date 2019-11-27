---
title: Continue, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354108"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="c5530-102">Continue — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5530-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="c5530-103">Natychmiast przenosi kontrolę do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="c5530-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5530-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5530-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="c5530-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5530-105">Remarks</span></span>  
 <span data-ttu-id="c5530-106">Można dokonać transferu z wewnątrz pętli `Do`, `For`lub `While` do następnej iteracji tej pętli.</span><span class="sxs-lookup"><span data-stu-id="c5530-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="c5530-107">Kontrolka natychmiast przechodzi do testu warunku pętli, który jest równoznaczny z transferem do instrukcji `For` lub `While` lub do instrukcji `Do` lub `Loop`, która zawiera klauzulę `Until` lub `While`.</span><span class="sxs-lookup"><span data-stu-id="c5530-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="c5530-108">`Continue` można użyć w dowolnej lokalizacji w pętli, która umożliwia transfery.</span><span class="sxs-lookup"><span data-stu-id="c5530-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="c5530-109">Reguły zezwalające na transfer kontroli są takie same jak w przypadku [instrukcji goto](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c5530-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="c5530-110">Na przykład jeśli pętla znajduje się w całości w bloku `Try`, blok `Catch` lub blok `Finally`, można użyć `Continue` do przetransferowania z pętli.</span><span class="sxs-lookup"><span data-stu-id="c5530-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="c5530-111">Jeśli z drugiej strony, struktura `Try`...`End Try` jest zawarta w pętli, nie można użyć `Continue` do transferu kontroli z bloku `Finally` i można jej użyć do transferowania z `Try` lub `Catch` bloku tylko wtedy, gdy przeniesiesz całkowicie z `Try`...`End Try` Structure.</span><span class="sxs-lookup"><span data-stu-id="c5530-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="c5530-112">Jeśli istnieją zagnieżdżone pętle tego samego typu, na przykład pętla `Do` w innej pętli `Do`, instrukcja `Continue Do` pomija następną iterację wewnętrznej pętli `Do`, która ją zawiera.</span><span class="sxs-lookup"><span data-stu-id="c5530-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="c5530-113">Nie można użyć `Continue`, aby przejść do następnej iteracji zawierającej pętlę tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="c5530-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="c5530-114">Jeśli istnieją zagnieżdżone pętle różnych typów, na przykład pętla `Do` w pętli `For`, można przejść do następnej iteracji każdej pętli, używając `Continue Do` lub `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="c5530-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5530-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5530-115">Example</span></span>  
 <span data-ttu-id="c5530-116">Poniższy przykład kodu używa instrukcji `Continue While`, aby przejść do następnej kolumny tablicy, Jeśli dzielnik ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="c5530-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="c5530-117">`Continue While` znajduje się wewnątrz pętli `For`.</span><span class="sxs-lookup"><span data-stu-id="c5530-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="c5530-118">Przesyła do instrukcji `While col < lastcol`, która jest następną iteracją wewnętrznej pętli `While`, która zawiera pętlę `For`.</span><span class="sxs-lookup"><span data-stu-id="c5530-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="c5530-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5530-119">See also</span></span>

- [<span data-ttu-id="c5530-120">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c5530-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="c5530-121">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c5530-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="c5530-122">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c5530-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="c5530-123">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c5530-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
