---
title: Zwraca różnicy pomiędzy dwoma sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 80348961d2848e9664e6978789ceb2441ea2f89a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356221"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="365b7-102">Zwraca różnicy pomiędzy dwoma sekwencji</span><span class="sxs-lookup"><span data-stu-id="365b7-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="365b7-103">Użyj <xref:System.Linq.Queryable.Except%2A> operatora, aby zwrócić różnicy pomiędzy dwoma sekwencji.</span><span class="sxs-lookup"><span data-stu-id="365b7-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="365b7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="365b7-104">Example</span></span>  
 <span data-ttu-id="365b7-105">W tym przykładzie użyto <xref:System.Linq.Queryable.Except%2A> do zwrócenia sekwencji wszystkich krajów, w którym `Customers` ale na żywo, w których nie `Employees` na żywo.</span><span class="sxs-lookup"><span data-stu-id="365b7-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="365b7-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> operacja jest także zdefiniowana tylko dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="365b7-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="365b7-107">Semantyka dla multisets jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="365b7-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365b7-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="365b7-108">See Also</span></span>  
 [<span data-ttu-id="365b7-109">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="365b7-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="365b7-110">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="365b7-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
