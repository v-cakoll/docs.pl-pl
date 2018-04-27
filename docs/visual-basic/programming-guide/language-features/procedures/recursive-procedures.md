---
title: Procedury rekurencyjne (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 471746f4412b61c9782e8019aa8a9ec6221afb04
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="9f1db-102">Procedury rekurencyjne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f1db-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="9f1db-103">A *cykliczne* procedura jest taki, który wywołuje sam siebie.</span><span class="sxs-lookup"><span data-stu-id="9f1db-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="9f1db-104">Ogólnie rzecz biorąc to nie jest najbardziej efektywny sposób pisania kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9f1db-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="9f1db-105">W poniższej procedurze użyto rekursji do obliczania silni oryginalnego argumentu.</span><span class="sxs-lookup"><span data-stu-id="9f1db-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="9f1db-106">Zagadnienia dotyczące z procedury cykliczne</span><span class="sxs-lookup"><span data-stu-id="9f1db-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="9f1db-107">**Warunki ograniczające**.</span><span class="sxs-lookup"><span data-stu-id="9f1db-107">**Limiting Conditions**.</span></span> <span data-ttu-id="9f1db-108">Należy projektować procedury cykliczne do testowania dla co najmniej jeden warunek, który może obsłużyć rekursji i również musi obsługiwać case, gdzie nie taki warunek jest spełniony w rozsądnym liczbę wywołań cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="9f1db-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="9f1db-109">Bez co najmniej jeden warunek, który może zostać spełniony bez błędów procedura jest uruchamiana wysokiego ryzyka wykonywanych w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="9f1db-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="9f1db-110">**Użycie pamięci**.</span><span class="sxs-lookup"><span data-stu-id="9f1db-110">**Memory Usage**.</span></span> <span data-ttu-id="9f1db-111">Aplikacja ma ograniczoną ilość miejsca dla zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="9f1db-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="9f1db-112">Zawsze wywołania procedur, używa więcej miejsca dla dodatkowych kopii jego zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="9f1db-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="9f1db-113">Jeśli ten proces jest kontynuowany przez nieokreślony czas, po pewnym czasie powoduje <xref:System.StackOverflowException> błędu.</span><span class="sxs-lookup"><span data-stu-id="9f1db-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="9f1db-114">**Wydajność**.</span><span class="sxs-lookup"><span data-stu-id="9f1db-114">**Efficiency**.</span></span> <span data-ttu-id="9f1db-115">Prawie zawsze można zastąpić pętli rekursji.</span><span class="sxs-lookup"><span data-stu-id="9f1db-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="9f1db-116">Pętla nie ma obciążenie przekazywanie argumentów, inicjowanie dodatkowego miejsca do magazynowania i zwracanie wartości.</span><span class="sxs-lookup"><span data-stu-id="9f1db-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="9f1db-117">Wydajność może być znacznie poprawia bez wywołania cykliczne.</span><span class="sxs-lookup"><span data-stu-id="9f1db-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="9f1db-118">**Rekursja wzajemna**.</span><span class="sxs-lookup"><span data-stu-id="9f1db-118">**Mutual Recursion**.</span></span> <span data-ttu-id="9f1db-119">Widoczny bardzo niską wydajnością, lub nawet nieskończoną pętlę, jeśli dwie procedury wywołać siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="9f1db-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="9f1db-120">Taki projekt przedstawia informacje o tej samej problemów jako procedura pojedynczego cykliczne, ale może być trudniejsza do wykrywania i debugowania.</span><span class="sxs-lookup"><span data-stu-id="9f1db-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="9f1db-121">**Wywoływanie z nawiasów**.</span><span class="sxs-lookup"><span data-stu-id="9f1db-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="9f1db-122">Gdy `Function` procedury wywołuje cyklicznie, należy wykonać nazwę procedury w nawiasach, nawet jeśli nie są znane argumentu.</span><span class="sxs-lookup"><span data-stu-id="9f1db-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="9f1db-123">W przeciwnym razie nazwa funkcji jest pobierana jako zwracana wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="9f1db-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="9f1db-124">**Testowanie**.</span><span class="sxs-lookup"><span data-stu-id="9f1db-124">**Testing**.</span></span> <span data-ttu-id="9f1db-125">Procedury cykliczne podczas pisania, należy przetestować go dokładnie aby upewnić się, że spełnia on zawsze spełnienia określonego warunku ograniczającego.</span><span class="sxs-lookup"><span data-stu-id="9f1db-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="9f1db-126">Ponadto upewnij się, że nie można uruchomić za mało pamięci z powodu konieczności zbyt wiele wywołań cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="9f1db-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f1db-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f1db-127">See Also</span></span>  
 <xref:System.StackOverflowException>  
 [<span data-ttu-id="9f1db-128">Procedury</span><span class="sxs-lookup"><span data-stu-id="9f1db-128">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="9f1db-129">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="9f1db-129">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="9f1db-130">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="9f1db-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="9f1db-131">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="9f1db-131">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="9f1db-132">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="9f1db-132">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="9f1db-133">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="9f1db-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="9f1db-134">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="9f1db-134">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="9f1db-135">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="9f1db-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="9f1db-136">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="9f1db-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="9f1db-137">Rozwiązywanie problemów z wyjątkami: System.StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="9f1db-137">Troubleshooting Exceptions: System.StackOverflowException</span></span>](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
