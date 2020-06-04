---
title: Struktury pętli
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
ms.openlocfilehash: 3f60e9dc83dc7174e765903be13f2870ea40ce4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403524"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="0e660-102">Struktury pętli (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e660-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="0e660-103">Struktury pętli Visual Basic umożliwiają powtarzanie jednego lub kilku wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="0e660-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="0e660-104">Można powtarzać instrukcje w strukturze pętli do momentu, aż do `True` osiągnięcia warunku `False` , określonej liczby razy lub jeden raz dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0e660-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="0e660-105">Poniższa ilustracja przedstawia strukturę pętli, która uruchamia zestaw instrukcji do momentu, gdy zostanie spełniony warunek:</span><span class="sxs-lookup"><span data-stu-id="0e660-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![Wykres przepływu, który zawiera element do... Do pętli.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="0e660-107">While — pętle</span><span class="sxs-lookup"><span data-stu-id="0e660-107">While Loops</span></span>  
 <span data-ttu-id="0e660-108">W `While` konstrukcji... `End While` konstrukcja działa zestaw instrukcji, o ile warunek określony w `While` instrukcji to `True` .</span><span class="sxs-lookup"><span data-stu-id="0e660-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="0e660-109">Aby uzyskać więcej informacji, zobacz [while... Instrukcja End while](../../../language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0e660-109">For more information, see [While...End While Statement](../../../language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="0e660-110">Pętle do</span><span class="sxs-lookup"><span data-stu-id="0e660-110">Do Loops</span></span>  
 <span data-ttu-id="0e660-111">`Do`Obiekt... `Loop` konstrukcja umożliwia przetestowanie warunku na początku lub na końcu struktury pętli.</span><span class="sxs-lookup"><span data-stu-id="0e660-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="0e660-112">Można również określić, czy pętla ma być powtarzana, gdy warunek pozostanie, `True` lub dopóki się nie stanie `True` .</span><span class="sxs-lookup"><span data-stu-id="0e660-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="0e660-113">Aby uzyskać więcej informacji, zobacz [... Loop — instrukcja](../../../language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0e660-113">For more information, see [Do...Loop Statement](../../../language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="0e660-114">Pętle for</span><span class="sxs-lookup"><span data-stu-id="0e660-114">For Loops</span></span>  
 <span data-ttu-id="0e660-115">`For`... `Next` Konstrukcja wykonuje pętlę określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="0e660-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="0e660-116">Używa zmiennej sterującej pętli, zwanej również *licznikiem*, do śledzenia powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="0e660-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="0e660-117">Należy określić wartości początkową i końcową dla tego licznika. Opcjonalnie możesz określić ilość, o którą wzrośnie od jednego powtórzenia do następnego.</span><span class="sxs-lookup"><span data-stu-id="0e660-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="0e660-118">Aby uzyskać więcej informacji, zobacz [dla... Next — instrukcja](../../../language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0e660-118">For more information, see [For...Next Statement](../../../language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="0e660-119">Dla każdej pętli</span><span class="sxs-lookup"><span data-stu-id="0e660-119">For Each Loops</span></span>  
 <span data-ttu-id="0e660-120">W `For Each` konstrukcji... `Next` konstrukcja uruchamia zestaw instrukcji jeden raz dla każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0e660-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="0e660-121">Należy określić zmienną sterującą pętli, ale nie trzeba określać jej wartości początkowej ani końcowej.</span><span class="sxs-lookup"><span data-stu-id="0e660-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="0e660-122">Aby uzyskać więcej informacji, zobacz [dla każdej z nich... Next — instrukcja](../../../language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0e660-122">For more information, see [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e660-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e660-123">See also</span></span>

- [<span data-ttu-id="0e660-124">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="0e660-124">Control Flow</span></span>](index.md)
- [<span data-ttu-id="0e660-125">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="0e660-125">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="0e660-126">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="0e660-126">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="0e660-127">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="0e660-127">Nested Control Structures</span></span>](nested-control-structures.md)
