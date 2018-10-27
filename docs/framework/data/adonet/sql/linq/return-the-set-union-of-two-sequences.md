---
title: Zwracanie sumy zbiorów dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: ffdc1dc0f9b5c2ed3b9898d0c71c9b384723fe05
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047894"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="cd7d8-102">Zwracanie sumy zbiorów dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="cd7d8-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="cd7d8-103">Użyj <xref:System.Linq.Queryable.Union%2A> operator ma być zwracanie sumy zbiorów dwóch sekwencji.</span><span class="sxs-lookup"><span data-stu-id="cd7d8-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd7d8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd7d8-104">Example</span></span>  
 <span data-ttu-id="cd7d8-105">W tym przykładzie użyto <xref:System.Linq.Queryable.Union%2A> celu zwrócenia sekwencji wszystkich krajów, w którym istnieją albo `Customers` lub `Employees`.</span><span class="sxs-lookup"><span data-stu-id="cd7d8-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="cd7d8-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Union%2A> operator jest zdefiniowany dla multisets jako Nieuporządkowana łączenie multisets (skutecznie wynik [ `UNION ALL` ](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) klauzuli w języku SQL).</span><span class="sxs-lookup"><span data-stu-id="cd7d8-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause in SQL).</span></span>

<span data-ttu-id="cd7d8-107">Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd7d8-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cd7d8-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd7d8-108">See Also</span></span>  
 [<span data-ttu-id="cd7d8-109">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="cd7d8-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="cd7d8-110">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="cd7d8-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
