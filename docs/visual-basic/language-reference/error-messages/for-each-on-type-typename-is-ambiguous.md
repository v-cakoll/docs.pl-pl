---
title: Element „For Each” w typie „<typename>” jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu „System.Collections.Generic.IEnumerable(Of T)”.
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: af2340e8e514391503d5f9b706d13ba93336698e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662121"
---
# <a name="for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a><span data-ttu-id="b537f-102">"For Each" w typie "\<typename >" jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu "System.Collections.Generic.IEnumerable (Of T)"</span><span class="sxs-lookup"><span data-stu-id="b537f-102">'For Each' on type '\<typename>' is ambiguous because the type implements multiple instantiations of 'System.Collections.Generic.IEnumerable(Of T)'</span></span>
<span data-ttu-id="b537f-103">A `For Each` Instrukcja określa zmienna iteratora, który ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b537f-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="b537f-104">Zmienna iteratora musi być typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu w jednym z `Collections` przestrzeni nazw [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b537f-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="b537f-105">Istnieje możliwość dla klasy zaimplementować więcej niż jeden skonstruowanego interfejsu ogólnego, przy użyciu argumentu innego typu, dla każdego konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="b537f-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="b537f-106">Jeśli klasa, która wykonuje to jest używany dla zmiennej iteratora, zmienna ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b537f-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="b537f-107">W takim przypadku języka Visual Basic nie można wybrać jakiej metody do wywołania.</span><span class="sxs-lookup"><span data-stu-id="b537f-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="b537f-108">**Identyfikator błędu:** BC32096</span><span class="sxs-lookup"><span data-stu-id="b537f-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b537f-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b537f-109">To correct this error</span></span>  
  
- <span data-ttu-id="b537f-110">Użyj [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) lub [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) rzutowanie typu zmiennej iteratora Definiowanie interfejsu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metodę, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="b537f-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b537f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b537f-111">See also</span></span>

- [<span data-ttu-id="b537f-112">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b537f-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="b537f-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b537f-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
