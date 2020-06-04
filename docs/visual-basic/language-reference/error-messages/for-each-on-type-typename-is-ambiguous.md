---
title: Element „For Each” w typie „<typename>” jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu „System.Collections.Generic.IEnumerable(Of T)”.
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 153a2640d66f48660f21339aaf0ecc8eaa10f51f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402969"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="cadde-102">Element „For Each” w typie „\<typename>” jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu „System.Collections.Generic.IEnumerable(Of T)”.</span><span class="sxs-lookup"><span data-stu-id="cadde-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>
<span data-ttu-id="cadde-103">`For Each`Instrukcja określa zmienną iteratora, która ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="cadde-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="cadde-104">Zmienna iteratora musi być typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejs lub w jednej z `Collections` przestrzeni nazw .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cadde-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the .NET Framework.</span></span> <span data-ttu-id="cadde-105">Klasa może zaimplementować więcej niż jeden skonstruowany interfejs ogólny przy użyciu innego argumentu typu dla każdej konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="cadde-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="cadde-106">Jeśli klasa, która jest używana jako zmienna iteratora, ta zmienna ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="cadde-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="cadde-107">W takim przypadku Visual Basic nie może wybrać metody do wywołania.</span><span class="sxs-lookup"><span data-stu-id="cadde-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="cadde-108">**Identyfikator błędu:** BC32096</span><span class="sxs-lookup"><span data-stu-id="cadde-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cadde-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cadde-109">To correct this error</span></span>  
  
- <span data-ttu-id="cadde-110">Użyj [operatora DirectCast](../operators/directcast-operator.md) lub [operatora TryCast](../operators/trycast-operator.md) do rzutowania typu zmiennej iteratora na interfejs definiujący <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="cadde-110">Use [DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadde-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cadde-111">See also</span></span>

- [<span data-ttu-id="cadde-112">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cadde-112">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="cadde-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cadde-113">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
