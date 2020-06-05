---
title: Iterator
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: bb19289c69f4c523363e88e91a58f37d232b07df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396236"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="17048-102">Iterator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17048-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="17048-103">Określa, że funkcja lub `Get` metoda dostępu jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="17048-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17048-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17048-104">Remarks</span></span>  
 <span data-ttu-id="17048-105">*Iterator* wykonuje niestandardową iterację w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="17048-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="17048-106">Iterator używa instrukcji [Yield](../statements/yield-statement.md) do zwrócenia każdego elementu w kolekcji po jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="17048-106">An iterator uses the [Yield](../statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="17048-107">Po `Yield` osiągnięciu instrukcji bieżąca lokalizacja w kodzie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="17048-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="17048-108">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="17048-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="17048-109">Iterator można zaimplementować jako funkcję lub jako `Get` metodę dostępu do definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="17048-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="17048-110">`Iterator`Modyfikator pojawia się w deklaracji funkcji iteratora lub `Get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="17048-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="17048-111">Należy wywołać iterator z kodu klienta przy użyciu [for each... Next — instrukcja](../statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="17048-111">You call an iterator from client code by using a [For Each...Next Statement](../statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="17048-112">Zwracanym typem funkcji iteratora lub `Get` metody dostępu może być <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> , lub <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="17048-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="17048-113">Iterator nie może mieć żadnych `ByRef` parametrów.</span><span class="sxs-lookup"><span data-stu-id="17048-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="17048-114">Iterator nie może wystąpić w zdarzeniu, konstruktorze wystąpień, konstruktorze statycznym lub destruktorze statycznym.</span><span class="sxs-lookup"><span data-stu-id="17048-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="17048-115">Iterator może być funkcją anonimową.</span><span class="sxs-lookup"><span data-stu-id="17048-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="17048-116">Aby uzyskać więcej informacji, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="17048-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="17048-117">Użycie</span><span class="sxs-lookup"><span data-stu-id="17048-117">Usage</span></span>  
 <span data-ttu-id="17048-118">`Iterator`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="17048-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="17048-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="17048-119">Function Statement</span></span>](../statements/function-statement.md)  
  
- [<span data-ttu-id="17048-120">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="17048-120">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="17048-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="17048-121">Example</span></span>  
 <span data-ttu-id="17048-122">Poniższy przykład ilustruje funkcję iteratora.</span><span class="sxs-lookup"><span data-stu-id="17048-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="17048-123">Funkcja iteratora zawiera `Yield` instrukcję, która znajduje się wewnątrz elementu [... Następna](../statements/for-next-statement.md) pętla.</span><span class="sxs-lookup"><span data-stu-id="17048-123">The iterator function has a `Yield` statement that is inside a [For…Next](../statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="17048-124">Każda iteracja [dla każdej](../statements/for-each-next-statement.md) treści instrukcji w programie `Main` tworzy wywołanie `Power` funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="17048-124">Each iteration of the [For Each](../statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="17048-125">Każde wywołanie funkcji iteratora przechodzi do następnego wykonania `Yield` instrukcji, która występuje w następnej iteracji `For…Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="17048-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="17048-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="17048-126">Example</span></span>  
 <span data-ttu-id="17048-127">Poniższy przykład ilustruje `Get` metodę dostępu, która jest iteratorem.</span><span class="sxs-lookup"><span data-stu-id="17048-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="17048-128">`Iterator`Modyfikator znajduje się w deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="17048-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="17048-129">Aby uzyskać więcej przykładów, zobacz [Iteratory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="17048-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17048-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17048-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="17048-131">Iteratory</span><span class="sxs-lookup"><span data-stu-id="17048-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="17048-132">Yield, instrukcja</span><span class="sxs-lookup"><span data-stu-id="17048-132">Yield Statement</span></span>](../statements/yield-statement.md)
