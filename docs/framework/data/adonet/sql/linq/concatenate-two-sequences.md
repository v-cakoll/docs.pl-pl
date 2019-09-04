---
title: Łączenie dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: b802abae9fc2c1731a623209862f61ed5ee51f9c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247883"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="45275-102">Łączenie dwóch sekwencji</span><span class="sxs-lookup"><span data-stu-id="45275-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="45275-103">Użyj operatora <xref:System.Linq.Queryable.Concat%2A> , aby połączyć dwie sekwencje.</span><span class="sxs-lookup"><span data-stu-id="45275-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="45275-104"><xref:System.Linq.Queryable.Concat%2A> Operator jest zdefiniowany dla uporządkowanych zestawów wielozbiorowych, gdzie zamówienia odbiornika i argumentu są takie same.</span><span class="sxs-lookup"><span data-stu-id="45275-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="45275-105">Porządkowanie w języku SQL to ostatni krok przed wygenerowanymi wynikami.</span><span class="sxs-lookup"><span data-stu-id="45275-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="45275-106">Z <xref:System.Linq.Queryable.Concat%2A> tego powodu operator jest implementowany przy użyciu `UNION ALL` i nie zachowuje kolejności argumentów.</span><span class="sxs-lookup"><span data-stu-id="45275-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="45275-107">Aby upewnić się, że kolejność jest prawidłowa w wynikach, upewnij się, że zostały one jawnie uporządkowane.</span><span class="sxs-lookup"><span data-stu-id="45275-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45275-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="45275-108">Example</span></span>  
 <span data-ttu-id="45275-109">Ten przykład używa <xref:System.Linq.Queryable.Concat%2A> do zwracania sekwencji wszystkich `Customer` i `Employee` numerów telefonów i faksów.</span><span class="sxs-lookup"><span data-stu-id="45275-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="45275-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="45275-110">Example</span></span>  
 <span data-ttu-id="45275-111">Ten przykład używa <xref:System.Linq.Queryable.Concat%2A> do zwracania sekwencji wszystkich `Customer` i `Employee` nazwy i mapowania numerów telefonów.</span><span class="sxs-lookup"><span data-stu-id="45275-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="45275-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45275-112">See also</span></span>

- [<span data-ttu-id="45275-113">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="45275-113">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="45275-114">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="45275-114">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
