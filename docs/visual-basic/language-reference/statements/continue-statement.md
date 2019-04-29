---
title: Continue — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 5523be69f2901851c86f6c0263548e3577507ff9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638249"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="363e6-102">Continue — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="363e6-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="363e6-103">Kontrolka transferu bezpośrednio do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="363e6-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="363e6-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="363e6-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="363e6-105">Remarks</span></span>  
 <span data-ttu-id="363e6-106">Można przenieść z wewnątrz `Do`, `For`, lub `While` pętli do następnej iteracji pętli tego.</span><span class="sxs-lookup"><span data-stu-id="363e6-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="363e6-107">Kontrola przechodzi bezpośrednio do testu warunek pętli, który jest odpowiednikiem przesyłania do `For` lub `While` instrukcji lub `Do` lub `Loop` instrukcji, która zawiera `Until` lub `While` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="363e6-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="363e6-108">Możesz użyć `Continue` w dowolnym miejscu w pętli, która umożliwia transfer.</span><span class="sxs-lookup"><span data-stu-id="363e6-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="363e6-109">Zasady umożliwiające przekazywanie sterowania są takie same jak za pomocą [instrukcji GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="363e6-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="363e6-110">Na przykład, jeśli pętla jest całkowicie zawarte w ramach `Try` bloku, `Catch` bloku lub `Finally` bloku, możesz użyć `Continue` na przesyłanie wyjścia z pętli.</span><span class="sxs-lookup"><span data-stu-id="363e6-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="363e6-111">Jeśli z drugiej strony, `Try`... `End Try` struktury jest zawarty w pętli, nie można użyć `Continue` Aby przekazać sterowanie z `Finally` bloku i służy do przeniesienia poza `Try` lub `Catch` zablokować tylko wtedy, gdy przeniesiesz całkowicie z `Try`... `End Try` struktury.</span><span class="sxs-lookup"><span data-stu-id="363e6-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="363e6-112">Jeśli na przykład masz zagnieżdżonej pętli tego samego typu `Do` pętli w innym `Do` pętli, `Continue Do` instrukcji przejdzie do następnej iteracji najbardziej wewnętrzną funkcją `Do` pętli, która go zawiera.</span><span class="sxs-lookup"><span data-stu-id="363e6-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="363e6-113">Nie można użyć `Continue` aby przejść do następnej iteracji pętli zawierającego tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="363e6-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="363e6-114">Jeśli na przykład masz zagnieżdżonej pętli różnych typów, `Do` pętli w ramach `For` pętli, możesz przejść do następnej iteracji pętli albo przy użyciu `Continue Do` lub `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="363e6-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="363e6-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="363e6-115">Example</span></span>  
 <span data-ttu-id="363e6-116">Poniższy przykład kodu wykorzystuje `Continue While` instrukcję, aby przejść do następnej kolumny tablicy, jeśli dzielnik jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="363e6-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="363e6-117">`Continue While` Znajduje się wewnątrz `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="363e6-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="363e6-118">Przesyłania do `While col < lastcol` instrukcji, co jest kolejną iterację najbardziej wewnętrzną funkcją `While` pętli, która zawiera `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="363e6-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="363e6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="363e6-119">See also</span></span>

- [<span data-ttu-id="363e6-120">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="363e6-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="363e6-121">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="363e6-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="363e6-122">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="363e6-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="363e6-123">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="363e6-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
