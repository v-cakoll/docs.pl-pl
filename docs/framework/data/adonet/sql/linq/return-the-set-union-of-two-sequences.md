---
title: "Zwraca złożenie dwóch sekwencji zestawu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a9f1ba281c1c7bd6a6a0d96746caa512c6c208b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="d9263-102">Zwraca złożenie dwóch sekwencji zestawu</span><span class="sxs-lookup"><span data-stu-id="d9263-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="d9263-103">Użyj <xref:System.Linq.Queryable.Union%2A> operatora, aby zwrócić zestaw złożenie dwóch sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d9263-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9263-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9263-104">Example</span></span>  
 <span data-ttu-id="d9263-105">W tym przykładzie użyto <xref:System.Linq.Queryable.Union%2A> do zwrócenia wszystkich krajów, w którym są albo sekwencji `Customers` lub `Employees`.</span><span class="sxs-lookup"><span data-stu-id="d9263-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="d9263-106">W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Union%2A> operator jest zdefiniowany dla multisets jako nieuporządkowaną złączeniem multisets (efektywnie wynik `UNION ALL` klauzuli SQL).</span><span class="sxs-lookup"><span data-stu-id="d9263-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the `UNION ALL` clause in SQL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9263-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9263-107">See Also</span></span>  
 [<span data-ttu-id="d9263-108">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="d9263-108">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="d9263-109">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="d9263-109">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
