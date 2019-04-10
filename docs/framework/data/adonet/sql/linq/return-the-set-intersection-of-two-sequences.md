---
title: Zwracanie zestawu części wspólnych dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 07f48ab7ef1095ba80b1a955a4bd1ea602a75aa8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205915"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="76cf2-102">Zwracanie zestawu części wspólnych dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="76cf2-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="76cf2-103">Użyj <xref:System.Linq.Queryable.Intersect%2A> operator, aby zwrócić zestawu części wspólnych dwóch sekwencji.</span><span class="sxs-lookup"><span data-stu-id="76cf2-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76cf2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="76cf2-104">Example</span></span>  
 <span data-ttu-id="76cf2-105">W tym przykładzie użyto <xref:System.Linq.Queryable.Intersect%2A> w celu zwrócenia sekwencji wszystkie kraje, w których obie `Customers` i `Employees` na żywo.</span><span class="sxs-lookup"><span data-stu-id="76cf2-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="76cf2-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> działa dobrze zdefiniowane tylko na zestawach.</span><span class="sxs-lookup"><span data-stu-id="76cf2-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="76cf2-107">Semantyka dla multisets jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="76cf2-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76cf2-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76cf2-108">See also</span></span>

- [<span data-ttu-id="76cf2-109">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="76cf2-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="76cf2-110">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="76cf2-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
