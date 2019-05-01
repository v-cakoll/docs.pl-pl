---
title: Zwracanie zestawu różnic między dwoma sekwencjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 7edc60c7ab8510aadd9ac273529a88adeb41352a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037534"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="103d9-102">Zwracanie zestawu różnic między dwoma sekwencjami</span><span class="sxs-lookup"><span data-stu-id="103d9-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="103d9-103">Użyj <xref:System.Linq.Queryable.Except%2A> operator ma być zwracanie zestawu różnic między dwoma sekwencjami.</span><span class="sxs-lookup"><span data-stu-id="103d9-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="103d9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="103d9-104">Example</span></span>  
 <span data-ttu-id="103d9-105">W tym przykładzie użyto <xref:System.Linq.Queryable.Except%2A> w celu zwrócenia sekwencji wszystkie kraje, w którym `Customers` aktywna, ale w przypadku którego nie `Employees` na żywo.</span><span class="sxs-lookup"><span data-stu-id="103d9-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="103d9-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> działa dobrze zdefiniowane tylko na zestawach.</span><span class="sxs-lookup"><span data-stu-id="103d9-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="103d9-107">Semantyka dla multisets jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="103d9-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="103d9-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="103d9-108">See also</span></span>

- [<span data-ttu-id="103d9-109">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="103d9-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="103d9-110">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="103d9-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
