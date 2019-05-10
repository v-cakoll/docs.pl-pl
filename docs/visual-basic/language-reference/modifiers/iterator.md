---
title: Iterator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 4f42cf864e836c53cff5e7d620f4bdfa43c4c7ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661284"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="95728-102">Iterator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95728-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="95728-103">Określa, że funkcja lub `Get` metody dostępu jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="95728-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95728-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95728-104">Remarks</span></span>  
 <span data-ttu-id="95728-105">*Iteratora* wykonywania niestandardowych iteracji przez kolekcję.</span><span class="sxs-lookup"><span data-stu-id="95728-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="95728-106">Używa iteratora [uzyskanie](../../../visual-basic/language-reference/statements/yield-statement.md) instrukcja zwraca każdy element w jednej kolekcji w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="95728-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="95728-107">Gdy `Yield` osiągnięta zostanie instrukcja, bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="95728-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="95728-108">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="95728-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="95728-109">Iterator można zaimplementować jako funkcję lub `Get` akcesor definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="95728-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="95728-110">`Iterator` Modyfikator pojawia się w deklaracji funkcji iteratora lub `Get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="95728-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="95728-111">Wywołujesz iterację z poziomu kodu klienta przy użyciu [For Each... Następna instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="95728-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="95728-112">Zwracany typ funkcji iteratora lub `Get` dostępu mogą być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="95728-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="95728-113">Iterator nie może zawierać żadnych `ByRef` parametrów.</span><span class="sxs-lookup"><span data-stu-id="95728-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="95728-114">Iterator nie może wystąpić w zdarzeń, konstruktora wystąpienia, statyczny Konstruktor lub destruktor statyczne.</span><span class="sxs-lookup"><span data-stu-id="95728-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="95728-115">Iteracją może być funkcją anonimową.</span><span class="sxs-lookup"><span data-stu-id="95728-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="95728-116">Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="95728-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="95728-117">Użycie</span><span class="sxs-lookup"><span data-stu-id="95728-117">Usage</span></span>  
 <span data-ttu-id="95728-118">`Iterator` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="95728-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="95728-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="95728-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="95728-120">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="95728-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="95728-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="95728-121">Example</span></span>  
 <span data-ttu-id="95728-122">W poniższym przykładzie pokazano funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="95728-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="95728-123">Funkcja iteratora ma `Yield` instrukcji, która znajduje się wewnątrz [dla... Następny](../../../visual-basic/language-reference/statements/for-next-statement.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="95728-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="95728-124">Każda iteracja [dla każdego](../../../visual-basic/language-reference/statements/for-each-next-statement.md) treść instrukcji w `Main` tworzy wywołanie `Power` funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="95728-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="95728-125">Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `Yield` instrukcję, która występuje w ciągu następnej iteracji `For…Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="95728-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="95728-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="95728-126">Example</span></span>  
 <span data-ttu-id="95728-127">W poniższym przykładzie pokazano `Get` metodę dostępu, która jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="95728-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="95728-128">`Iterator` Modyfikator znajduje się w deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="95728-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="95728-129">Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="95728-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95728-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95728-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="95728-131">Iteratory</span><span class="sxs-lookup"><span data-stu-id="95728-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="95728-132">Yield, instrukcja</span><span class="sxs-lookup"><span data-stu-id="95728-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
