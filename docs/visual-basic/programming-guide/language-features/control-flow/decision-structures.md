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
ms.openlocfilehash: 4a76b2565c343e69ac3c11441035a7682a8f08ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318939"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="dd8a3-102">Struktury decyzji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd8a3-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="dd8a3-103">Visual Basic umożliwia warunki badania i wykonywać różne operacje, w zależności od wyników tego testu.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="dd8a3-104">Możesz sprawdzić warunku jest wartość true lub false dla różnych wartości wyrażenia lub różne wyjątki generowane, gdy wykonać serię instrukcji.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="dd8a3-105">Poniższa ilustracja przedstawia strukturę decyzji, które sprawdza, czy warunek jest spełniony i wykonują różne akcje zależnie od tego, czy jest wartość PRAWDA lub FAŁSZ.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Schemat blokowy If... Następnie... Budowa else.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="dd8a3-107">If...Then...Else Construction</span><span class="sxs-lookup"><span data-stu-id="dd8a3-107">If...Then...Else Construction</span></span>  
 <span data-ttu-id="dd8a3-108">`If...Then...Else` konstrukcje umożliwiają testowanie dla co najmniej jeden warunek i uruchomić jedną lub więcej instrukcji w zależności od każdego warunku.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-108">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="dd8a3-109">Można przetestować warunki i akcje w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dd8a3-109">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="dd8a3-110">Uruchomić jedną lub więcej instrukcji, jeśli warunek jest `True`</span><span class="sxs-lookup"><span data-stu-id="dd8a3-110">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="dd8a3-111">Uruchomić jedną lub więcej instrukcji, jeśli warunek jest `False`</span><span class="sxs-lookup"><span data-stu-id="dd8a3-111">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="dd8a3-112">Uruchamianie niektórych instrukcji, jeśli warunek jest `True` i innym osobom, gdy jest `False`</span><span class="sxs-lookup"><span data-stu-id="dd8a3-112">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="dd8a3-113">Dodatkowe warunki badania, w przypadku warunku wstępnego `False`</span><span class="sxs-lookup"><span data-stu-id="dd8a3-113">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="dd8a3-114">Struktura kontrolki, która oferuje wszystkie powyższe możliwości jest [Jeśli... Następnie... Else — instrukcja](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dd8a3-114">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="dd8a3-115">Można użyć wersji jednowierszowego, jeśli masz tylko jeden test i jednej instrukcji do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-115">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="dd8a3-116">W przypadku bardziej złożonego zestawu warunków i akcji można użyć wersji wielu linii.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-116">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="dd8a3-117">Wybierz... Konstrukcja wielkości liter</span><span class="sxs-lookup"><span data-stu-id="dd8a3-117">Select...Case Construction</span></span>  
 <span data-ttu-id="dd8a3-118">`Select...Case` Konstrukcja umożliwia ocena wyrażenia jeden raz i uruchomić różne zestawy instrukcji, w oparciu o różne możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-118">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="dd8a3-119">Aby uzyskać więcej informacji, zobacz [wybierz... Case — instrukcja](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dd8a3-119">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="dd8a3-120">Try... CATCH... Na koniec konstrukcji</span><span class="sxs-lookup"><span data-stu-id="dd8a3-120">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="dd8a3-121">`Try...Catch...Finally` konstrukcje umożliwiają uruchamianie zbiór instrukcji w środowisku, w którym zachowuje kontrolki, jeśli dowolny z zestawienia powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-121">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="dd8a3-122">Możesz wykonywać różne akcje dla różnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-122">You can take different actions for different exceptions.</span></span> <span data-ttu-id="dd8a3-123">Opcjonalnie można określić bloku kodu, który jest uruchamiany przed zakończeniem pracy całego `Try...Catch...Finally` konstrukcji, niezależnie od tego, co występuje.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-123">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="dd8a3-124">Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dd8a3-124">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd8a3-125">Dla wielu struktur sterowania po kliknięciu słowem kluczowym wszystkich słów kluczowych w strukturze, zostały wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-125">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="dd8a3-126">Na przykład po kliknięciu `If` w `If...Then...Else` budowy, wszystkie wystąpienia elementu `If`, `Then`, `ElseIf`, `Else`, i `End If` w konstrukcji są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-126">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="dd8a3-127">Aby przejść do następnego lub poprzedniego wyróżnionego słów kluczowych, naciśnij klawisz Strzałka CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę Strzałka.</span><span class="sxs-lookup"><span data-stu-id="dd8a3-127">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8a3-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd8a3-128">See also</span></span>

- [<span data-ttu-id="dd8a3-129">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="dd8a3-129">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="dd8a3-130">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="dd8a3-130">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="dd8a3-131">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="dd8a3-131">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="dd8a3-132">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="dd8a3-132">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="dd8a3-133">If, operator</span><span class="sxs-lookup"><span data-stu-id="dd8a3-133">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
