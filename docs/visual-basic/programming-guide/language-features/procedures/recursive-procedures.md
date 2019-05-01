---
title: Procedury rekurencyjne (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: de9a2af9fc3cd78879b6525245727a6f52d51c63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791849"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="546d3-102">Procedury rekurencyjne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="546d3-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="546d3-103">A *cyklicznego* procedura jest taki, który wywołuje sam siebie.</span><span class="sxs-lookup"><span data-stu-id="546d3-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="546d3-104">Ogólnie rzecz biorąc to nie jest najbardziej skutecznym sposobem pisania kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="546d3-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="546d3-105">W poniższej procedurze użyto rekursji, aby obliczyć silnię, oryginalnym argumentu.</span><span class="sxs-lookup"><span data-stu-id="546d3-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="546d3-106">Zagadnienia dotyczące z procedury rekurencyjne</span><span class="sxs-lookup"><span data-stu-id="546d3-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="546d3-107">**Ograniczanie warunki**.</span><span class="sxs-lookup"><span data-stu-id="546d3-107">**Limiting Conditions**.</span></span> <span data-ttu-id="546d3-108">Należy projektować procedury cykliczne do testowania dla co najmniej jeden warunek, który może obsłużyć rekursji, a także musi obsłużyć przypadek, gdzie żaden taki warunek jest spełniony w ramach uzasadnioną liczbę wywołań rekurencyjnych.</span><span class="sxs-lookup"><span data-stu-id="546d3-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="546d3-109">Bez co najmniej jeden warunek, które mogą zostać spełnione bez błędów procedura jest uruchamiana wysokiego ryzyka wykonywania w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="546d3-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="546d3-110">**Użycie pamięci**.</span><span class="sxs-lookup"><span data-stu-id="546d3-110">**Memory Usage**.</span></span> <span data-ttu-id="546d3-111">Twoja aplikacja ma ograniczoną ilość miejsca dla zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="546d3-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="546d3-112">Każdorazowo procedury wywołuje sam siebie, używa więcej miejsca dla dodatkowych kopii jego zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="546d3-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="546d3-113">Jeśli ten proces jest kontynuowany przez czas nieokreślony, ostatecznie powoduje <xref:System.StackOverflowException> błędu.</span><span class="sxs-lookup"><span data-stu-id="546d3-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="546d3-114">**Wydajność**.</span><span class="sxs-lookup"><span data-stu-id="546d3-114">**Efficiency**.</span></span> <span data-ttu-id="546d3-115">Prawie zawsze można zastąpić pętli rekursji.</span><span class="sxs-lookup"><span data-stu-id="546d3-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="546d3-116">Pętli nie ma konieczności przekazywanie argumentów, inicjowanie dodatkowego miejsca do magazynowania i zwracanie wartości.</span><span class="sxs-lookup"><span data-stu-id="546d3-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="546d3-117">Wydajność może być znacznie lepsze bez wywołania cykliczne.</span><span class="sxs-lookup"><span data-stu-id="546d3-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="546d3-118">**Rekursja wzajemna**.</span><span class="sxs-lookup"><span data-stu-id="546d3-118">**Mutual Recursion**.</span></span> <span data-ttu-id="546d3-119">Bardzo niska wydajność lub nawet wejścia w nieskończoną pętlę, może obserwować, jeśli dwie procedury wywołują się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="546d3-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="546d3-120">Taki projekt przedstawia informacje o tych samych problemów jako procedura pojedynczego cyklicznego, ale może być trudniejsze wykrycie i zdebugowanie.</span><span class="sxs-lookup"><span data-stu-id="546d3-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="546d3-121">**Wywoływanie za pomocą nawiasów**.</span><span class="sxs-lookup"><span data-stu-id="546d3-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="546d3-122">Gdy `Function` procedury wywołuje cyklicznie, należy wykonać Nazwa procedury za pomocą nawiasów, nawet jeśli dostępny jest nie listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="546d3-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="546d3-123">W przeciwnym razie nazwa funkcji jest pobierana jako wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="546d3-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="546d3-124">**Testowanie**.</span><span class="sxs-lookup"><span data-stu-id="546d3-124">**Testing**.</span></span> <span data-ttu-id="546d3-125">Jeśli piszesz procedury cykliczne, należy go przetestować dokładnie aby upewnić się, że spełnia on zawsze jakiegoś warunku ograniczającego.</span><span class="sxs-lookup"><span data-stu-id="546d3-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="546d3-126">Należy upewnić się, że nie można uruchomić za mało pamięci z powodu konieczności zbyt wiele wywołań rekurencyjnych.</span><span class="sxs-lookup"><span data-stu-id="546d3-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546d3-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="546d3-127">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="546d3-128">Procedury</span><span class="sxs-lookup"><span data-stu-id="546d3-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="546d3-129">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="546d3-129">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="546d3-130">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="546d3-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="546d3-131">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="546d3-131">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="546d3-132">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="546d3-132">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="546d3-133">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="546d3-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="546d3-134">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="546d3-134">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="546d3-135">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="546d3-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="546d3-136">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="546d3-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
