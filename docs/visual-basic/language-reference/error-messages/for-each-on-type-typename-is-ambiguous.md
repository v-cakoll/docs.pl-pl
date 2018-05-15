---
title: '&#39;Dla każdego&#39; typu &#39; &lt;typename&gt; &#39; jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu &#39;System.Collections.Generic.IEnumerable (Of T)&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 8c48a7134eb8da83fb418b9aa91d55dcbe8e8bcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39for-each39-on-type-39lttypenamegt39-is-ambiguous-because-the-type-implements-multiple-instantiations-of-39systemcollectionsgenericienumerableof-t39"></a><span data-ttu-id="89a3c-102">&#39;Dla każdego&#39; typu &#39; &lt;typename&gt; &#39; jest niejednoznaczny, ponieważ typ implementuje wiele wystąpień elementu &#39;System.Collections.Generic.IEnumerable (Of T)&#39;</span><span class="sxs-lookup"><span data-stu-id="89a3c-102">&#39;For Each&#39; on type &#39;&lt;typename&gt;&#39; is ambiguous because the type implements multiple instantiations of &#39;System.Collections.Generic.IEnumerable(Of T)&#39;</span></span>
<span data-ttu-id="89a3c-103">A `For Each` instrukcji określa zmiennej iteracyjnej, która ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="89a3c-103">A `For Each` statement specifies an iterator variable that has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span>  
  
 <span data-ttu-id="89a3c-104">Zmienna sterująca musi być typu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu w jednym z `Collections` przestrzeni nazw [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89a3c-104">The iterator variable must be of a type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface in one of the `Collections` namespaces of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="89a3c-105">Istnieje możliwość dla klasy do zaimplementowania więcej niż jeden skonstruowane interfejs ogólny, przy użyciu argumentu innego typu, dla każdego konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="89a3c-105">It is possible for a class to implement more than one constructed generic interface, using a different type argument for each construction.</span></span> <span data-ttu-id="89a3c-106">Klasa, która wykonuje to użycie zmiennej iteracyjnej tej zmiennej ma więcej niż jedną <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="89a3c-106">If a class that does this is used for the iterator variable, that variable has more than one <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="89a3c-107">W takim przypadku Visual Basic nie można wybrać którego metoda do wywołania.</span><span class="sxs-lookup"><span data-stu-id="89a3c-107">In such a case, Visual Basic cannot choose which method to call.</span></span>  
  
 <span data-ttu-id="89a3c-108">**Identyfikator błędu:** BC32096</span><span class="sxs-lookup"><span data-stu-id="89a3c-108">**Error ID:** BC32096</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="89a3c-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="89a3c-109">To correct this error</span></span>  
  
-   <span data-ttu-id="89a3c-110">Użyj [operatora DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) lub [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) można rzutować typu zmiennej iteracyjnej do definiowania interfejsu <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="89a3c-110">Use [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) to cast the iterator variable type to the interface defining the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a3c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89a3c-111">See Also</span></span>  
 [<span data-ttu-id="89a3c-112">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="89a3c-112">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="89a3c-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="89a3c-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
