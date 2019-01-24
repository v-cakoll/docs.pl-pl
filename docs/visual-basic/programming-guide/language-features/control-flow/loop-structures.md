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
ms.openlocfilehash: b72eef632b4564abc69e6ebef43b940eb0950e9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523392"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="23058-102">Struktury pętli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23058-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="23058-103">Struktury pętli w języku Visual Basic pozwalają kilkukrotnie uruchomić jeden lub więcej wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="23058-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="23058-104">Możesz powtórzyć instrukcji w strukturze pętli, dopóki warunek jest `True`, dopóki nie zostanie warunek `False`, określona liczba razy lub jeden raz dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="23058-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="23058-105">Poniższa ilustracja przedstawia strukturę pętli, która uruchamia zestaw instrukcji, dopóki warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="23058-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="23058-106">![Schemat blokowy wykonuj... Pętlą UNTIL](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="23058-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="23058-107">Uruchamianie zbiór instrukcji, dopóki warunek jest spełniony</span><span class="sxs-lookup"><span data-stu-id="23058-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="23058-108">Pętli WHILE</span><span class="sxs-lookup"><span data-stu-id="23058-108">While Loops</span></span>  
 <span data-ttu-id="23058-109">`While`... `End While` konstrukcji uruchamia zestaw instrukcji tak długo, jak warunek określony w `While` instrukcja jest `True`.</span><span class="sxs-lookup"><span data-stu-id="23058-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="23058-110">Aby uzyskać więcej informacji, zobacz [podczas... Kończy While, instrukcja](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="23058-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="23058-111">Do loops-pętle</span><span class="sxs-lookup"><span data-stu-id="23058-111">Do Loops</span></span>  
 <span data-ttu-id="23058-112">`Do`... `Loop` konstrukcja umożliwia testowanie warunku na początku lub końcu struktury pętli.</span><span class="sxs-lookup"><span data-stu-id="23058-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="23058-113">Można również określić, czy powtórzeń pętli, gdy warunek pozostaje `True` lub aż przyjmie postać `True`.</span><span class="sxs-lookup"><span data-stu-id="23058-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="23058-114">Aby uzyskać więcej informacji, zobacz [zrobić... Instrukcja pętli](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="23058-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="23058-115">Dla pętli</span><span class="sxs-lookup"><span data-stu-id="23058-115">For Loops</span></span>  
 <span data-ttu-id="23058-116">`For`... `Next` konstrukcji wykonuje pętli określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="23058-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="23058-117">Używa zmienna sterująca pętli, nazywany również *licznika*, aby śledzić powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="23058-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="23058-118">Określ wartości początkowa i końcowa dla tego licznika, a opcjonalnie możesz określić ilość, za pomocą którego zwiększa z jednego powtórzenia do następnego.</span><span class="sxs-lookup"><span data-stu-id="23058-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="23058-119">Aby uzyskać więcej informacji, zobacz [dla... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="23058-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="23058-120">Pętle for Each</span><span class="sxs-lookup"><span data-stu-id="23058-120">For Each Loops</span></span>  
 <span data-ttu-id="23058-121">`For Each`... `Next` konstrukcji uruchamia zestaw instrukcji jeden raz dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="23058-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="23058-122">Określ zmienna sterująca pętli, ale nie trzeba określić rozpoczęcia lub zakończenia wartości dla niego.</span><span class="sxs-lookup"><span data-stu-id="23058-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="23058-123">Aby uzyskać więcej informacji, zobacz [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="23058-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23058-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23058-124">See also</span></span>
- [<span data-ttu-id="23058-125">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="23058-125">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="23058-126">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="23058-126">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="23058-127">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="23058-127">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="23058-128">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="23058-128">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
