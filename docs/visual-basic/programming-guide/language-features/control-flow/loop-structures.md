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
ms.openlocfilehash: 8138609f06d82b53ef5b5afb480e8609461ffc33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647894"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="36249-102">Struktury pętli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36249-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="36249-103">Struktury pętli Visual Basic zezwalają na uruchamianie kilkukrotnie jeden lub więcej wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="36249-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="36249-104">Instrukcje w struktury pętli można powtórzyć, dopóki nie zostanie warunek `True`, dopóki nie zostanie warunek `False`, określona liczba razy lub raz dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="36249-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="36249-105">Na poniższej ilustracji przedstawiono struktury pętli, który uruchamia zestaw instrukcji, dopóki nie zostanie spełniony warunek.</span><span class="sxs-lookup"><span data-stu-id="36249-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="36249-106">![Schemat blokowy czy... Do pętli](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="36249-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="36249-107">Uruchomiona zestaw instrukcji, dopóki nie zostanie spełniony warunek</span><span class="sxs-lookup"><span data-stu-id="36249-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="36249-108">Pętli WHILE</span><span class="sxs-lookup"><span data-stu-id="36249-108">While Loops</span></span>  
 <span data-ttu-id="36249-109">`While`... `End While` konstrukcji uruchamia zestaw instrukcji tak długo, jak warunek określony w `While` instrukcja jest `True`.</span><span class="sxs-lookup"><span data-stu-id="36249-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="36249-110">Aby uzyskać więcej informacji, zobacz [podczas... End While — instrukcja](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36249-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="36249-111">Do loops-pętle</span><span class="sxs-lookup"><span data-stu-id="36249-111">Do Loops</span></span>  
 <span data-ttu-id="36249-112">`Do`... `Loop` konstrukcji można testować warunek na początku lub końca struktury pętli.</span><span class="sxs-lookup"><span data-stu-id="36249-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="36249-113">Można również określić, czy powtórzeń pętli, gdy warunek jest `True` lub aż przyjmie postać `True`.</span><span class="sxs-lookup"><span data-stu-id="36249-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="36249-114">Aby uzyskać więcej informacji, zobacz [czy... Pętla instrukcji](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36249-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="36249-115">Dla pętli</span><span class="sxs-lookup"><span data-stu-id="36249-115">For Loops</span></span>  
 <span data-ttu-id="36249-116">`For`... `Next` konstrukcja wykonuje pętli określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="36249-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="36249-117">Ta zmienna sterująca pętli, nazywany również *licznika*, aby śledzić powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="36249-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="36249-118">Określ początkową i końcową dla tego licznika, a opcjonalnie możesz określić ilość za pomocą którego wykazuje wzrost wartości wraz z jednego powtarzania do następnego.</span><span class="sxs-lookup"><span data-stu-id="36249-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="36249-119">Aby uzyskać więcej informacji, zobacz [dla... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36249-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="36249-120">Dla każdej pętli</span><span class="sxs-lookup"><span data-stu-id="36249-120">For Each Loops</span></span>  
 <span data-ttu-id="36249-121">`For Each`... `Next` konstrukcji uruchamia zestaw instrukcji raz dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="36249-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="36249-122">Określ zmienna sterująca pętli, ale nie trzeba określić rozpoczęcia lub zakończenia dla niego wartości.</span><span class="sxs-lookup"><span data-stu-id="36249-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="36249-123">Aby uzyskać więcej informacji, zobacz [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36249-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36249-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36249-124">See Also</span></span>  
 [<span data-ttu-id="36249-125">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="36249-125">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="36249-126">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="36249-126">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="36249-127">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="36249-127">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="36249-128">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="36249-128">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
