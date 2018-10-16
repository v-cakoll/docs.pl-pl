---
title: Zwracanie sumy zbiorów dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: c7d7a267df13cfa54d682ab9b65953f2c0a85a27
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347549"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="f3510-102">Zwracanie sumy zbiorów dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="f3510-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="f3510-103">Użyj <xref:System.Linq.Queryable.Union%2A> operator ma być zwracanie sumy zbiorów dwóch sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f3510-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3510-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3510-104">Example</span></span>  
 <span data-ttu-id="f3510-105">W tym przykładzie użyto <xref:System.Linq.Queryable.Union%2A> celu zwrócenia sekwencji wszystkich krajów, w którym istnieją albo `Customers` lub `Employees`.</span><span class="sxs-lookup"><span data-stu-id="f3510-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="f3510-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Union%2A> operator jest zdefiniowany dla multisets jako Nieuporządkowana łączenie multisets (skutecznie wynik [ `UNION ALL` ](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) klauzuli w języku SQL).</span><span class="sxs-lookup"><span data-stu-id="f3510-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause in SQL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3510-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3510-107">See Also</span></span>  
 [<span data-ttu-id="f3510-108">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="f3510-108">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="f3510-109">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="f3510-109">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
