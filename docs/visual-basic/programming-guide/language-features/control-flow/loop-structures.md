---
title: Struktury pętli (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 56165eecce5e73c4e06235dac1691774fb39b794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906867"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="57488-102">Struktury pętli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57488-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="57488-103">Struktury pętli w języku Visual Basic pozwalają kilkukrotnie uruchomić jeden lub więcej wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="57488-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="57488-104">Możesz powtórzyć instrukcji w strukturze pętli, dopóki warunek jest `True`, dopóki nie zostanie warunek `False`, określona liczba razy lub jeden raz dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="57488-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="57488-105">Poniższa ilustracja przedstawia strukturę pętli, która uruchamia zestaw instrukcji, dopóki warunek jest spełniony:</span><span class="sxs-lookup"><span data-stu-id="57488-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Schemat blokowy pokazujący wykonuj... Do momentu pętli.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="57488-107">Pętli WHILE</span><span class="sxs-lookup"><span data-stu-id="57488-107">While Loops</span></span>  
 <span data-ttu-id="57488-108">`While`... `End While` konstrukcji uruchamia zestaw instrukcji tak długo, jak warunek określony w `While` instrukcja jest `True`.</span><span class="sxs-lookup"><span data-stu-id="57488-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="57488-109">Aby uzyskać więcej informacji, zobacz [podczas... Kończy While, instrukcja](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="57488-109">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="57488-110">Do loops-pętle</span><span class="sxs-lookup"><span data-stu-id="57488-110">Do Loops</span></span>  
 <span data-ttu-id="57488-111">`Do`... `Loop` konstrukcja umożliwia testowanie warunku na początku lub końcu struktury pętli.</span><span class="sxs-lookup"><span data-stu-id="57488-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="57488-112">Można również określić, czy powtórzeń pętli, gdy warunek pozostaje `True` lub aż przyjmie postać `True`.</span><span class="sxs-lookup"><span data-stu-id="57488-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="57488-113">Aby uzyskać więcej informacji, zobacz [zrobić... Instrukcja pętli](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="57488-113">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="57488-114">Dla pętli</span><span class="sxs-lookup"><span data-stu-id="57488-114">For Loops</span></span>  
 <span data-ttu-id="57488-115">`For`... `Next` konstrukcji wykonuje pętli określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="57488-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="57488-116">Używa zmienna sterująca pętli, nazywany również *licznika*, aby śledzić powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="57488-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="57488-117">Określ wartości początkowa i końcowa dla tego licznika, a opcjonalnie możesz określić ilość, za pomocą którego zwiększa z jednego powtórzenia do następnego.</span><span class="sxs-lookup"><span data-stu-id="57488-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="57488-118">Aby uzyskać więcej informacji, zobacz [dla... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="57488-118">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="57488-119">Pętle for Each</span><span class="sxs-lookup"><span data-stu-id="57488-119">For Each Loops</span></span>  
 <span data-ttu-id="57488-120">`For Each`... `Next` konstrukcji uruchamia zestaw instrukcji jeden raz dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="57488-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="57488-121">Określ zmienna sterująca pętli, ale nie trzeba określić rozpoczęcia lub zakończenia wartości dla niego.</span><span class="sxs-lookup"><span data-stu-id="57488-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="57488-122">Aby uzyskać więcej informacji, zobacz [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="57488-122">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57488-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57488-123">See also</span></span>

- [<span data-ttu-id="57488-124">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="57488-124">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="57488-125">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="57488-125">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="57488-126">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="57488-126">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="57488-127">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="57488-127">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
