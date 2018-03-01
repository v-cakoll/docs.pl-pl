---
title: Iterator (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd6c0b1fa422dc4ab659d8c59472e5c098c729bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="554a5-102">Iterator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="554a5-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="554a5-103">Określa, że funkcja lub `Get` akcesor jest iteratora.</span><span class="sxs-lookup"><span data-stu-id="554a5-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="554a5-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="554a5-104">Remarks</span></span>  
 <span data-ttu-id="554a5-105">*Iterator* wykonuje niestandardowych iteracji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="554a5-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="554a5-106">Używa iteratora [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcji, aby zwracany był każdy element w kolekcji jednego naraz.</span><span class="sxs-lookup"><span data-stu-id="554a5-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="554a5-107">Gdy `Yield` osiągnięciu instrukcji, są przechowywane w bieżącej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="554a5-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="554a5-108">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="554a5-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="554a5-109">Iteratora można zaimplementować jako funkcję lub `Get` akcesor definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="554a5-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="554a5-110">`Iterator` Modyfikator pojawia się w deklaracji funkcji iteracyjnej lub `Get` dostępu.</span><span class="sxs-lookup"><span data-stu-id="554a5-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="554a5-111">Wywołaj iteratora z kodu klienta przy użyciu [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="554a5-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="554a5-112">Zwracany typ funkcji iteracyjnej lub `Get` dostępu może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="554a5-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="554a5-113">Iterator nie mogą zawierać `ByRef` parametrów.</span><span class="sxs-lookup"><span data-stu-id="554a5-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="554a5-114">Iterator nie może wystąpić w zdarzenia, konstruktora wystąpienia, statycznego konstruktora lub destruktora statycznych.</span><span class="sxs-lookup"><span data-stu-id="554a5-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="554a5-115">Iteratora można funkcji anonimowej.</span><span class="sxs-lookup"><span data-stu-id="554a5-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="554a5-116">Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="554a5-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="554a5-117">Użycie</span><span class="sxs-lookup"><span data-stu-id="554a5-117">Usage</span></span>  
 <span data-ttu-id="554a5-118">`Iterator` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="554a5-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="554a5-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="554a5-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="554a5-120">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="554a5-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="554a5-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="554a5-121">Example</span></span>  
 <span data-ttu-id="554a5-122">W poniższym przykładzie pokazano funkcji iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="554a5-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="554a5-123">Funkcja iteratora ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="554a5-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="554a5-124">Każdej iteracji [dla każdego](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treść instrukcji w `Main` tworzy wywołanie `Power` funkcji iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="554a5-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="554a5-125">Każde wywołanie funkcji iteracyjnej przechodzi do następnego wykonywanie `Yield` instrukcja, która występuje w ciągu następnej iteracji `For…Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="554a5-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="554a5-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="554a5-126">Example</span></span>  
 <span data-ttu-id="554a5-127">W poniższym przykładzie pokazano `Get` dostępu, który jest iteratora.</span><span class="sxs-lookup"><span data-stu-id="554a5-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="554a5-128">`Iterator` Jest modyfikatora w deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="554a5-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="554a5-129">Aby uzyskać dodatkowe przykłady, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="554a5-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554a5-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="554a5-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="554a5-131">Iteratory</span><span class="sxs-lookup"><span data-stu-id="554a5-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)  
 [<span data-ttu-id="554a5-132">Yield, instrukcja</span><span class="sxs-lookup"><span data-stu-id="554a5-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
