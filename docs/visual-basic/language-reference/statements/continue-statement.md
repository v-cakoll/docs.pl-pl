---
title: Continue, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382097"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="5a3b2-102">Continue — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a3b2-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="5a3b2-103">Natychmiast przenosi kontrolę do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a3b2-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a3b2-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a3b2-105">Remarks</span></span>  
 <span data-ttu-id="5a3b2-106">Można przenieść z wewnątrz `Do` , `For` lub `While` do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="5a3b2-107">Kontrolka natychmiast przechodzi do testu warunku pętli, który jest równoznaczny z transferem do `For` instrukcji or lub `While` do `Do` instrukcji or, `Loop` która zawiera `Until` `While` klauzulę OR.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="5a3b2-108">Można użyć `Continue` w dowolnej lokalizacji w pętli, która umożliwia transfery.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="5a3b2-109">Reguły zezwalające na transfer kontroli są takie same jak w przypadku [instrukcji goto](goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5a3b2-109">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="5a3b2-110">Na przykład jeśli pętla znajduje się w całości w `Try` bloku, `Catch` bloku lub `Finally` bloku, można użyć `Continue` do przetransferowania z pętli.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="5a3b2-111">Jeśli z drugiej strony, `Try` Struktura... `End Try` jest zawarta w pętli, nie można użyć `Continue` programu do przeniesienia kontroli z `Finally` bloku i można użyć jej do przesłania poza `Try` lub tylko wtedy, `Catch` gdy przeniesiesz całkowicie poza `Try` strukturę... `End Try` .</span><span class="sxs-lookup"><span data-stu-id="5a3b2-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="5a3b2-112">Jeśli istnieją zagnieżdżone pętle tego samego typu, na przykład `Do` Pętla w innej `Do` pętli, `Continue Do` instrukcja przeskoczy do następnej iteracji wewnętrznej `Do` pętli, która ją zawiera.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="5a3b2-113">Nie można użyć, `Continue` Aby przejść do następnej iteracji zawierającej pętlę tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="5a3b2-114">Jeśli istnieją zagnieżdżone pętle różnych typów, na przykład `Do` Pętla w `For` pętli, można przejść do następnej iteracji jednej pętli, używając `Continue Do` lub `Continue For` .</span><span class="sxs-lookup"><span data-stu-id="5a3b2-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a3b2-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a3b2-115">Example</span></span>  
 <span data-ttu-id="5a3b2-116">Poniższy przykład kodu używa instrukcji, `Continue While` Aby przejść do następnej kolumny tablicy, Jeśli dzielnik ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="5a3b2-117">`Continue While`Znajduje się wewnątrz `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="5a3b2-118">Przesyła do `While col < lastcol` instrukcji, która jest następną iteracją wewnętrznej `While` pętli, która zawiera `For` pętlę.</span><span class="sxs-lookup"><span data-stu-id="5a3b2-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="5a3b2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a3b2-119">See also</span></span>

- [<span data-ttu-id="5a3b2-120">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a3b2-120">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="5a3b2-121">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a3b2-121">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="5a3b2-122">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a3b2-122">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="5a3b2-123">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5a3b2-123">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
