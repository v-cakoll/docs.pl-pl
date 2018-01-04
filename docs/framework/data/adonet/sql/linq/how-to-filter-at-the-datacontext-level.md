---
title: 'Porady: filtru na poziomie elementu DataContext'
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
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b596a16a6bf11982ba6edd4a646b46fa22d3e3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="0925d-102">Porady: filtru na poziomie elementu DataContext</span><span class="sxs-lookup"><span data-stu-id="0925d-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="0925d-103">Można filtrować `EntitySets` na `DataContext` poziom.</span><span class="sxs-lookup"><span data-stu-id="0925d-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="0925d-104">Takie filtry mają zastosowanie do wszystkich zapytań odbywa się za pomocą którego <xref:System.Data.Linq.DataContext> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0925d-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0925d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0925d-105">Example</span></span>  
 <span data-ttu-id="0925d-106">W poniższym przykładzie <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> służy do filtrowania wstępnie załadowane zleceń dla klientów przez `ShippedDate`.</span><span class="sxs-lookup"><span data-stu-id="0925d-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="0925d-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0925d-107">See Also</span></span>  
 [<span data-ttu-id="0925d-108">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="0925d-108">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
