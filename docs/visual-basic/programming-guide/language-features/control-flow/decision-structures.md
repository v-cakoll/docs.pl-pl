---
title: Struktury decyzji (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: f0df649c4be50e9cadd51258c89137b68b4ffe22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963198"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="5ebe4-102">Struktury decyzji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ebe4-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="5ebe4-103">Visual Basic umożliwia testowanie warunków i wykonywanie różnych operacji w zależności od wyników tego testu.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="5ebe4-104">Możesz sprawdzić, czy dla warunku określono wartość PRAWDA lub FAŁSZ, dla różnych wartości wyrażenia lub dla różnych wyjątków generowanych podczas wykonywania serii instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="5ebe4-105">Na poniższej ilustracji przedstawiono strukturę decyzyjną, która sprawdza, czy jest spełniony warunek, i wykonuje różne akcje w zależności od tego, czy jest to prawda czy fałsz.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Wykres przepływu dla elementu If...Then...Else.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="5ebe4-107">If...Then...Else — konstrukcja</span><span class="sxs-lookup"><span data-stu-id="5ebe4-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="5ebe4-108">`If...Then...Else`Konstrukcje umożliwiają przetestowanie pod kątem jednego lub kilku warunków i uruchomienie jednej lub kilku instrukcji w zależności od poszczególnych warunków.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="5ebe4-109">Można testować warunki i podejmować działania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5ebe4-109">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="5ebe4-110">Uruchom jedną lub więcej instrukcji, jeśli warunek jest`True`</span><span class="sxs-lookup"><span data-stu-id="5ebe4-110">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="5ebe4-111">Uruchom jedną lub więcej instrukcji, jeśli warunek jest`False`</span><span class="sxs-lookup"><span data-stu-id="5ebe4-111">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="5ebe4-112">Uruchom niektóre instrukcje, jeśli warunek jest `True` i inne, jeśli jest`False`</span><span class="sxs-lookup"><span data-stu-id="5ebe4-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="5ebe4-113">Przetestuj dodatkowy warunek, jeśli poprzedni warunek jest`False`</span><span class="sxs-lookup"><span data-stu-id="5ebe4-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="5ebe4-114">Struktura formantów, która oferuje wszystkie te możliwości, to [If...Then...Else — instrukcja](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5ebe4-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="5ebe4-115">Możesz użyć pojedynczej wersji, jeśli masz tylko jeden test i jedną instrukcję do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="5ebe4-116">Jeśli masz bardziej skomplikowany zestaw warunków i akcji, możesz użyć wersji wielowierszowej.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="5ebe4-117">Select...Case konstrukcja</span><span class="sxs-lookup"><span data-stu-id="5ebe4-117">Select...Case Construction</span></span>  
 <span data-ttu-id="5ebe4-118">`Select...Case` Konstrukcja pozwala oszacować wyrażenie jeden raz i uruchamiać różne zestawy instrukcji na podstawie różnych możliwych wartości.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="5ebe4-119">Aby uzyskać więcej informacji, zobacz [Select...Case — instrukcja](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5ebe4-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="5ebe4-120">Try...Catch...Finally konstrukcja</span><span class="sxs-lookup"><span data-stu-id="5ebe4-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="5ebe4-121">`Try...Catch...Finally`Konstrukcje umożliwiają uruchomienie zestawu instrukcji w środowisku, które zachowuje kontrolę, jeśli którykolwiek z instrukcji powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="5ebe4-122">Dla różnych wyjątków można wykonać różne działania.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="5ebe4-123">Opcjonalnie można określić blok kodu, który jest uruchamiany przed wyjściem z całego `Try...Catch...Finally` konstruowania, niezależnie od tego, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="5ebe4-124">Aby uzyskać więcej informacji, zobacz [Try...Catch...Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5ebe4-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ebe4-125">W przypadku wielu struktur kontroli po kliknięciu słowa kluczowego, zostaną wyróżnione wszystkie słowa kluczowe w strukturze.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="5ebe4-126">`If` Na przykład po kliknięciu `If...Then...Else` w konstrukcji `Then` `End If` wszystkie wystąpienia elementów `If`, ,,iwkonstrukcjisąwyróżnione.`Else` `ElseIf`</span><span class="sxs-lookup"><span data-stu-id="5ebe4-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="5ebe4-127">Aby przejść do następnego lub poprzedniego wyróżnionego słowa kluczowego, naciśnij klawisze CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę.</span><span class="sxs-lookup"><span data-stu-id="5ebe4-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebe4-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ebe4-128">See also</span></span>

- [<span data-ttu-id="5ebe4-129">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="5ebe4-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="5ebe4-130">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="5ebe4-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="5ebe4-131">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="5ebe4-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="5ebe4-132">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="5ebe4-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="5ebe4-133">If, operator</span><span class="sxs-lookup"><span data-stu-id="5ebe4-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
