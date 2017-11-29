---
title: Iterator (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Iterator
helpviewer_keywords: Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 503d586c0515b4cb53f8ec5656e5fe765cc094a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="6bde6-102">Iterator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bde6-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="6bde6-103">Określa, że funkcja lub `Get` akcesor jest iteratora.</span><span class="sxs-lookup"><span data-stu-id="6bde6-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bde6-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bde6-104">Remarks</span></span>  
 <span data-ttu-id="6bde6-105">*Iterator* wykonuje niestandardowych iteracji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6bde6-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="6bde6-106">Używa iteratora [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcji, aby zwracany był każdy element w kolekcji jednego naraz.</span><span class="sxs-lookup"><span data-stu-id="6bde6-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="6bde6-107">Gdy `Yield` osiągnięciu instrukcji, są przechowywane w bieżącej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6bde6-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="6bde6-108">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="6bde6-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="6bde6-109">Iteratora można zaimplementować jako funkcję lub `Get` akcesor definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="6bde6-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="6bde6-110">`Iterator` Modyfikator pojawia się w deklaracji funkcji iteracyjnej lub `Get` dostępu.</span><span class="sxs-lookup"><span data-stu-id="6bde6-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="6bde6-111">Wywołaj iteratora z kodu klienta przy użyciu [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6bde6-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="6bde6-112">Zwracany typ funkcji iteracyjnej lub `Get` dostępu może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="6bde6-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="6bde6-113">Iterator nie mogą zawierać `ByRef` parametrów.</span><span class="sxs-lookup"><span data-stu-id="6bde6-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="6bde6-114">Iterator nie może wystąpić w zdarzenia, konstruktora wystąpienia, statycznego konstruktora lub destruktora statycznych.</span><span class="sxs-lookup"><span data-stu-id="6bde6-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="6bde6-115">Iteratora można funkcji anonimowej.</span><span class="sxs-lookup"><span data-stu-id="6bde6-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="6bde6-116">Aby uzyskać więcej informacji, zobacz [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="6bde6-116">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="6bde6-117">Aby uzyskać więcej informacji na temat Iteratory, zobacz [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="6bde6-117">For more information about iterators, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="6bde6-118">Użycie</span><span class="sxs-lookup"><span data-stu-id="6bde6-118">Usage</span></span>  
 <span data-ttu-id="6bde6-119">`Iterator` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="6bde6-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="6bde6-120">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6bde6-120">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="6bde6-121">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6bde6-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="6bde6-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="6bde6-122">Example</span></span>  
 <span data-ttu-id="6bde6-123">W poniższym przykładzie pokazano funkcji iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="6bde6-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="6bde6-124">Funkcja iteratora ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="6bde6-124">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="6bde6-125">Każdej iteracji [dla każdego](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treść instrukcji w `Main` tworzy wywołanie `Power` funkcji iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="6bde6-125">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="6bde6-126">Każde wywołanie funkcji iteracyjnej przechodzi do następnego wykonywanie `Yield` instrukcja, która występuje w ciągu następnej iteracji `For…Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="6bde6-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="6bde6-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="6bde6-127">Example</span></span>  
 <span data-ttu-id="6bde6-128">W poniższym przykładzie pokazano `Get` dostępu, który jest iteratora.</span><span class="sxs-lookup"><span data-stu-id="6bde6-128">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="6bde6-129">`Iterator` Jest modyfikatora w deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="6bde6-129">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="6bde6-130">Aby uzyskać dodatkowe przykłady, zobacz [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="6bde6-130">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bde6-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bde6-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="6bde6-132">Iteratory</span><span class="sxs-lookup"><span data-stu-id="6bde6-132">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="6bde6-133">YIELD — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6bde6-133">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
