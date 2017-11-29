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
ms.openlocfilehash: 69b711802d04e005095167db7df544e0f00d0b19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="aecca-102">Porady: filtru na poziomie elementu DataContext</span><span class="sxs-lookup"><span data-stu-id="aecca-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="aecca-103">Można filtrować `EntitySets` na `DataContext` poziom.</span><span class="sxs-lookup"><span data-stu-id="aecca-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="aecca-104">Takie filtry mają zastosowanie do wszystkich zapytań odbywa się za pomocą którego <xref:System.Data.Linq.DataContext> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="aecca-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aecca-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="aecca-105">Example</span></span>  
 <span data-ttu-id="aecca-106">W poniższym przykładzie <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> służy do filtrowania wstępnie załadowane zleceń dla klientów przez `ShippedDate`.</span><span class="sxs-lookup"><span data-stu-id="aecca-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="aecca-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aecca-107">See Also</span></span>  
 [<span data-ttu-id="aecca-108">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="aecca-108">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
