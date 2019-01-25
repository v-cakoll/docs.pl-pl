---
title: Łączenie dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 831905ca5a712bcb80d5bab1aef61a81d2ade1b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734287"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="4b78b-102">Łączenie dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="4b78b-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="4b78b-103">Użyj <xref:System.Linq.Queryable.Concat%2A> operatora łączenie dwóch sekwencji.</span><span class="sxs-lookup"><span data-stu-id="4b78b-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="4b78b-104"><xref:System.Linq.Queryable.Concat%2A> Operator jest zdefiniowany dla uporządkowane multisets, gdzie zamówienia odbiornika i argument są takie same.</span><span class="sxs-lookup"><span data-stu-id="4b78b-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="4b78b-105">Kolejność w języku SQL jest to ostatni krok, zanim wyniki są tworzone.</span><span class="sxs-lookup"><span data-stu-id="4b78b-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="4b78b-106">Z tego powodu <xref:System.Linq.Queryable.Concat%2A> operator jest implementowany przy użyciu `UNION ALL` i nie pozwala zachować kolejność argumentów.</span><span class="sxs-lookup"><span data-stu-id="4b78b-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="4b78b-107">Aby upewnić się, że szeregowania jest poprawny w wynikach, upewnij się, że jawne kolejność wyników.</span><span class="sxs-lookup"><span data-stu-id="4b78b-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b78b-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b78b-108">Example</span></span>  
 <span data-ttu-id="4b78b-109">W tym przykładzie użyto <xref:System.Linq.Queryable.Concat%2A> celu zwrócenia sekwencji wszystkich `Customer` i `Employee` numery telefonu i faksu.</span><span class="sxs-lookup"><span data-stu-id="4b78b-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="4b78b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b78b-110">Example</span></span>  
 <span data-ttu-id="4b78b-111">W tym przykładzie użyto <xref:System.Linq.Queryable.Concat%2A> celu zwrócenia sekwencji wszystkich `Customer` i `Employee` nazwy i mapowania numeru telefonu.</span><span class="sxs-lookup"><span data-stu-id="4b78b-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="4b78b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b78b-112">See also</span></span>
- [<span data-ttu-id="4b78b-113">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="4b78b-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="4b78b-114">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="4b78b-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
