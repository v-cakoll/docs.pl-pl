---
title: Struktury decyzji (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b89d6f9b27e086b657c29f3353b63cdd855ae19
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="ffa73-102">Struktury decyzji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffa73-102">Decision Structures (Visual Basic)</span></span>
<span data-ttu-id="ffa73-103">Visual Basic umożliwia warunkach testowych i wykonywać różne operacje, w zależności od wyniki tego testu.</span><span class="sxs-lookup"><span data-stu-id="ffa73-103">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="ffa73-104">Można sprawdzić warunku jest PRAWDA lub FAŁSZ, różnych wartości wyrażenia lub różne wyjątki generowane, gdy wykonanie serię instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ffa73-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="ffa73-105">Na poniższej ilustracji przedstawiono strukturę decyzji, sprawdza, czy warunek jest spełniony, który wykonuje różne akcje w zależności od tego, czy ma wartość PRAWDA lub FAŁSZ.</span><span class="sxs-lookup"><span data-stu-id="ffa73-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 <span data-ttu-id="ffa73-106">![Schemat blokowy If... Następnie... Else budowa](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "ifthenelse —")</span><span class="sxs-lookup"><span data-stu-id="ffa73-106">![Flow chart of an If...Then...Else construction](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span></span>  
<span data-ttu-id="ffa73-107">Wykonywania różnych akcji, gdy warunek ma wartość PRAWDA, a gdy ma wartość false</span><span class="sxs-lookup"><span data-stu-id="ffa73-107">Taking different actions when a condition is true and when it is false</span></span>  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="ffa73-108">IF... Następnie... Else budowa</span><span class="sxs-lookup"><span data-stu-id="ffa73-108">If...Then...Else Construction</span></span>  
 <span data-ttu-id="ffa73-109">`If...Then...Else` konstrukcje umożliwiają testu dla co najmniej jednego warunku i uruchom jedną lub więcej instrukcji w zależności od każdego warunku.</span><span class="sxs-lookup"><span data-stu-id="ffa73-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="ffa73-110">Można przetestować warunków, a następnie podjąć działania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ffa73-110">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="ffa73-111">Uruchom jednego lub więcej instrukcji, gdy jest warunek `True`</span><span class="sxs-lookup"><span data-stu-id="ffa73-111">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="ffa73-112">Uruchom jednego lub więcej instrukcji, gdy jest warunek `False`</span><span class="sxs-lookup"><span data-stu-id="ffa73-112">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="ffa73-113">Uruchamianie niektórych instrukcji, gdy jest warunek `True` oraz innym osobom, jeśli jest `False`</span><span class="sxs-lookup"><span data-stu-id="ffa73-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="ffa73-114">Test dodatkowy warunek, w przypadku warunku wstępnego `False`</span><span class="sxs-lookup"><span data-stu-id="ffa73-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="ffa73-115">Struktura kontroli, która oferuje wszystkie te możliwości to [Jeśli... Następnie... Else — instrukcja](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ffa73-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="ffa73-116">Można użyć wersji jeden wiersz, jeśli masz tylko jeden test i jednej instrukcji do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="ffa73-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="ffa73-117">Jeśli masz bardziej złożonego zestawu elementów warunków i akcji, można użyć wersji wielu linii.</span><span class="sxs-lookup"><span data-stu-id="ffa73-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="ffa73-118">Wybierz... Wielkość konstrukcji</span><span class="sxs-lookup"><span data-stu-id="ffa73-118">Select...Case Construction</span></span>  
 <span data-ttu-id="ffa73-119">`Select...Case` Konstrukcji pozwala obliczyć wyrażenia, jeden raz, a następnie uruchom różne zestawy instrukcji w oparciu o różne możliwe wartości.</span><span class="sxs-lookup"><span data-stu-id="ffa73-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="ffa73-120">Aby uzyskać więcej informacji, zobacz [wybierz... Case — instrukcja](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ffa73-120">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="ffa73-121">Try... CATCH... Na koniec konstrukcji</span><span class="sxs-lookup"><span data-stu-id="ffa73-121">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="ffa73-122">`Try...Catch...Finally` konstrukcje umożliwiają uruchamianie zestaw instrukcji w środowisku, który zachowuje formantu, jeśli dowolny z instrukcji powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ffa73-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="ffa73-123">Można wykonać różne akcje dla różnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ffa73-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="ffa73-124">Opcjonalnie można określić blok kodu uruchamianego przed zakończeniem pracy całego `Try...Catch...Finally` konstrukcji, niezależnie od tego, jakie występuje.</span><span class="sxs-lookup"><span data-stu-id="ffa73-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="ffa73-125">Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ffa73-125">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffa73-126">Dla wielu struktur kontroli po kliknięciu słowem kluczowym wszystkich słów kluczowych w strukturze wyróżniono.</span><span class="sxs-lookup"><span data-stu-id="ffa73-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="ffa73-127">Na przykład po kliknięciu `If` w `If...Then...Else` konstrukcji, wszystkie wystąpienia `If`, `Then`, `ElseIf`, `Else`, i `End If` są wyróżniane w konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="ffa73-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="ffa73-128">Aby przejść do następnej lub poprzedniej wyróżnione słowa kluczowego, naciśnij kombinację klawiszy CTRL + SHIFT + Strzałka w dół strzałkę lub CTRL + SHIFT + Strzałka w górę, strzałki.</span><span class="sxs-lookup"><span data-stu-id="ffa73-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa73-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ffa73-129">See Also</span></span>  
 [<span data-ttu-id="ffa73-130">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="ffa73-130">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="ffa73-131">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="ffa73-131">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="ffa73-132">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="ffa73-132">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="ffa73-133">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="ffa73-133">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="ffa73-134">If, operator</span><span class="sxs-lookup"><span data-stu-id="ffa73-134">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)
