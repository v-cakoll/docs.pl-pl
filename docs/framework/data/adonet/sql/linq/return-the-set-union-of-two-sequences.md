---
title: Zwracanie sumy zbiorów dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 058856243b2a8daaecd653a9b5999013de5407a8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182524"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="cd293-102">Zwracanie sumy zbiorów dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="cd293-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="cd293-103"><xref:System.Linq.Queryable.Union%2A> Użyj operatora, aby zwrócić zestaw zbiorów dwóch sekwencji.</span><span class="sxs-lookup"><span data-stu-id="cd293-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd293-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd293-104">Example</span></span>  
 <span data-ttu-id="cd293-105">Ten przykład używa <xref:System.Linq.Queryable.Union%2A> do zwracania sekwencji wszystkich krajów/regionów, w których `Customers` jest albo lub `Employees`.</span><span class="sxs-lookup"><span data-stu-id="cd293-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="cd293-106">W programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]operatorjestzdefiniowany dla wielozbiorów jako nieuporządkowane łączenie wielozestawów (w efekcie w wyniku [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) klauzuli w języku SQL). <xref:System.Linq.Queryable.Union%2A></span><span class="sxs-lookup"><span data-stu-id="cd293-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="cd293-107">Aby uzyskać więcej informacji i przykładów, <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>Zobacz.</span><span class="sxs-lookup"><span data-stu-id="cd293-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cd293-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd293-108">See also</span></span>

- [<span data-ttu-id="cd293-109">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="cd293-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="cd293-110">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="cd293-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
