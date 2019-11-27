---
title: Procedury rekurencyjne
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
ms.openlocfilehash: 646d4e29ed7a0b6367d4b35a7f8641bcf659e616
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352555"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="263ea-102">Procedury rekurencyjne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="263ea-102">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="263ea-103">Procedura *cykliczna* to taka, która wywołuje sam siebie.</span><span class="sxs-lookup"><span data-stu-id="263ea-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="263ea-104">Ogólnie rzecz biorąc, nie jest to najbardziej skuteczny sposób pisania kodu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="263ea-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="263ea-105">Poniższa procedura używa rekursji do obliczenia silni pierwotnego argumentu.</span><span class="sxs-lookup"><span data-stu-id="263ea-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="263ea-106">Zagadnienia dotyczące procedur cyklicznych</span><span class="sxs-lookup"><span data-stu-id="263ea-106">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="263ea-107">**Warunki ograniczające**.</span><span class="sxs-lookup"><span data-stu-id="263ea-107">**Limiting Conditions**.</span></span> <span data-ttu-id="263ea-108">Należy zaprojektować procedurę cykliczną w celu przetestowania dla co najmniej jednego warunku, który może zakończyć rekursję, a także obsłużyć przypadek, w którym taki warunek nie jest spełniony w ramach rozsądnej liczby wywołań cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="263ea-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="263ea-109">Bez co najmniej jednego warunku, który może zostać spełniony bez niepowodzenia, procedura wykonuje wysokie ryzyko wykonania w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="263ea-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="263ea-110">**Użycie pamięci**.</span><span class="sxs-lookup"><span data-stu-id="263ea-110">**Memory Usage**.</span></span> <span data-ttu-id="263ea-111">Twoja aplikacja ma ograniczoną ilość miejsca dla zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="263ea-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="263ea-112">Za każdym razem, gdy procedura wywołuje samą siebie, używa większej ilości miejsca, aby uzyskać dodatkowe kopie swoich zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="263ea-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="263ea-113">Jeśli ten proces będzie kontynuowany w nieskończoność, spowoduje to, że wystąpił błąd <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="263ea-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="263ea-114">**Wydajność**.</span><span class="sxs-lookup"><span data-stu-id="263ea-114">**Efficiency**.</span></span> <span data-ttu-id="263ea-115">Prawie zawsze można zastąpić pętlę do rekursji.</span><span class="sxs-lookup"><span data-stu-id="263ea-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="263ea-116">Pętla nie ma nakładu na przekazywanie argumentów, inicjowanie dodatkowego magazynu i zwracanie wartości.</span><span class="sxs-lookup"><span data-stu-id="263ea-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="263ea-117">Wydajność może być znacznie lepsza bez wywołań cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="263ea-117">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="263ea-118">**Wzajemna rekursja**.</span><span class="sxs-lookup"><span data-stu-id="263ea-118">**Mutual Recursion**.</span></span> <span data-ttu-id="263ea-119">Można zaobserwować bardzo niską wydajność lub nawet nieskończoną pętlę, jeśli dwie procedury wywołują siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="263ea-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="263ea-120">Taki projekt przedstawia te same problemy co pojedyncza procedura cykliczna, ale może być trudniejszy do wykrycia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="263ea-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="263ea-121">**Wywoływanie za pomocą nawiasów**.</span><span class="sxs-lookup"><span data-stu-id="263ea-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="263ea-122">Gdy procedura `Function` wywołuje się w sposób cykliczny, należy postępować zgodnie z nazwą procedury z nawiasami, nawet jeśli nie ma listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="263ea-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="263ea-123">W przeciwnym razie nazwa funkcji jest traktowana jak reprezentująca wartość zwracaną funkcji.</span><span class="sxs-lookup"><span data-stu-id="263ea-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="263ea-124">**Testowanie**.</span><span class="sxs-lookup"><span data-stu-id="263ea-124">**Testing**.</span></span> <span data-ttu-id="263ea-125">Jeśli napiszesz procedurę cykliczną, należy dokładnie ją przetestować, aby upewnić się, że zawsze spełnia pewne warunki ograniczające.</span><span class="sxs-lookup"><span data-stu-id="263ea-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="263ea-126">Należy również upewnić się, że nie można zalogować się za mało pamięci z powodu zbyt wielu wywołań cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="263ea-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="263ea-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="263ea-127">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="263ea-128">Procedury</span><span class="sxs-lookup"><span data-stu-id="263ea-128">Procedures</span></span>](index.md)
- [<span data-ttu-id="263ea-129">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="263ea-129">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="263ea-130">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="263ea-130">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="263ea-131">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="263ea-131">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="263ea-132">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="263ea-132">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="263ea-133">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="263ea-133">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="263ea-134">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="263ea-134">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="263ea-135">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="263ea-135">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="263ea-136">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="263ea-136">Loop Structures</span></span>](../control-flow/loop-structures.md)
