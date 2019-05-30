---
title: Zwracanie zestawu różnic między dwoma sekwencjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 5bb7d797ad2adc4374f7a10c11d66be69feeb7a1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380046"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="ddf98-102">Zwracanie zestawu różnic między dwoma sekwencjami</span><span class="sxs-lookup"><span data-stu-id="ddf98-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="ddf98-103">Użyj <xref:System.Linq.Queryable.Except%2A> operator ma być zwracanie zestawu różnic między dwoma sekwencjami.</span><span class="sxs-lookup"><span data-stu-id="ddf98-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddf98-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddf98-104">Example</span></span>  
 <span data-ttu-id="ddf98-105">W tym przykładzie użyto <xref:System.Linq.Queryable.Except%2A> w celu zwrócenia sekwencji wszystkich krajach/regionach, w którym `Customers` aktywna, ale w przypadku którego nie `Employees` na żywo.</span><span class="sxs-lookup"><span data-stu-id="ddf98-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="ddf98-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> działa dobrze zdefiniowane tylko na zestawach.</span><span class="sxs-lookup"><span data-stu-id="ddf98-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="ddf98-107">Semantyka dla multisets jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="ddf98-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf98-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddf98-108">See also</span></span>

- [<span data-ttu-id="ddf98-109">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="ddf98-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="ddf98-110">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="ddf98-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
