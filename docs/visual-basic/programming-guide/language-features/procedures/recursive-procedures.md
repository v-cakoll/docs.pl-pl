---
title: Procedury rekurencyjne (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 444eeaf043cf3710c5154fd7e8577590e3ce7d1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="cca00-102">Procedury rekurencyjne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cca00-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="cca00-103">A *cykliczne* procedura jest taki, który wywołuje sam siebie.</span><span class="sxs-lookup"><span data-stu-id="cca00-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="cca00-104">Ogólnie rzecz biorąc, nie jest to najbardziej efektywny sposób zapisu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="cca00-104">In general, this is not the most effective way to write [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
 <span data-ttu-id="cca00-105">W poniższej procedurze użyto rekursji do obliczania silni oryginalnego argumentu.</span><span class="sxs-lookup"><span data-stu-id="cca00-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="cca00-106">Zagadnienia dotyczące z procedury cykliczne</span><span class="sxs-lookup"><span data-stu-id="cca00-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="cca00-107">**Warunki ograniczające**.</span><span class="sxs-lookup"><span data-stu-id="cca00-107">**Limiting Conditions**.</span></span> <span data-ttu-id="cca00-108">Należy projektować procedury cykliczne do testowania dla co najmniej jeden warunek, który może obsłużyć rekursji i również musi obsługiwać case, gdzie nie taki warunek jest spełniony w rozsądnym liczbę wywołań cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="cca00-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="cca00-109">Bez co najmniej jeden warunek, który może zostać spełniony bez błędów procedura jest uruchamiana wysokiego ryzyka wykonywanych w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="cca00-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="cca00-110">**Użycie pamięci**.</span><span class="sxs-lookup"><span data-stu-id="cca00-110">**Memory Usage**.</span></span> <span data-ttu-id="cca00-111">Aplikacja ma ograniczoną ilość miejsca dla zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="cca00-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="cca00-112">Zawsze wywołania procedur, używa więcej miejsca dla dodatkowych kopii jego zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="cca00-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="cca00-113">Jeśli ten proces jest kontynuowany przez nieokreślony czas, po pewnym czasie powoduje <xref:System.StackOverflowException> błędu.</span><span class="sxs-lookup"><span data-stu-id="cca00-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="cca00-114">**Wydajność**.</span><span class="sxs-lookup"><span data-stu-id="cca00-114">**Efficiency**.</span></span> <span data-ttu-id="cca00-115">Prawie zawsze można zastąpić pętli rekursji.</span><span class="sxs-lookup"><span data-stu-id="cca00-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="cca00-116">Pętla nie ma obciążenie przekazywanie argumentów, inicjowanie dodatkowego miejsca do magazynowania i zwracanie wartości.</span><span class="sxs-lookup"><span data-stu-id="cca00-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="cca00-117">Wydajność może być znacznie poprawia bez wywołania cykliczne.</span><span class="sxs-lookup"><span data-stu-id="cca00-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="cca00-118">**Rekursja wzajemna**.</span><span class="sxs-lookup"><span data-stu-id="cca00-118">**Mutual Recursion**.</span></span> <span data-ttu-id="cca00-119">Widoczny bardzo niską wydajnością, lub nawet nieskończoną pętlę, jeśli dwie procedury wywołać siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="cca00-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="cca00-120">Taki projekt przedstawia informacje o tej samej problemów jako procedura pojedynczego cykliczne, ale może być trudniejsza do wykrywania i debugowania.</span><span class="sxs-lookup"><span data-stu-id="cca00-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="cca00-121">**Wywoływanie z nawiasów**.</span><span class="sxs-lookup"><span data-stu-id="cca00-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="cca00-122">Gdy `Function` procedury wywołuje cyklicznie, należy wykonać nazwę procedury w nawiasach, nawet jeśli nie są znane argumentu.</span><span class="sxs-lookup"><span data-stu-id="cca00-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="cca00-123">W przeciwnym razie nazwa funkcji jest pobierana jako zwracana wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="cca00-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="cca00-124">**Testowanie**.</span><span class="sxs-lookup"><span data-stu-id="cca00-124">**Testing**.</span></span> <span data-ttu-id="cca00-125">Procedury cykliczne podczas pisania, należy przetestować go dokładnie aby upewnić się, że spełnia on zawsze spełnienia określonego warunku ograniczającego.</span><span class="sxs-lookup"><span data-stu-id="cca00-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="cca00-126">Ponadto upewnij się, że nie można uruchomić za mało pamięci z powodu konieczności zbyt wiele wywołań cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="cca00-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cca00-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cca00-127">See Also</span></span>  
 <xref:System.StackOverflowException>  
 [<span data-ttu-id="cca00-128">Procedury</span><span class="sxs-lookup"><span data-stu-id="cca00-128">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="cca00-129">Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="cca00-129">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="cca00-130">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="cca00-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="cca00-131">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="cca00-131">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="cca00-132">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="cca00-132">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="cca00-133">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="cca00-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="cca00-134">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="cca00-134">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="cca00-135">Procedury rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="cca00-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="cca00-136">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="cca00-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="cca00-137">Rozwiązywanie problemów z wyjątkami: System.StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="cca00-137">Troubleshooting Exceptions: System.StackOverflowException</span></span>](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
