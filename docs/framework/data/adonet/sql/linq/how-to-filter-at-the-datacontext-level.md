---
title: 'Instrukcje: Filtrowanie na poziomie elementu DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: 0ef5ba8e975cb1c59720c96b214ae2696cc6356e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781939"
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="f9b28-102">Instrukcje: Filtrowanie na poziomie elementu DataContext</span><span class="sxs-lookup"><span data-stu-id="f9b28-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="f9b28-103">Można filtrować `EntitySets` `DataContext` na poziomie.</span><span class="sxs-lookup"><span data-stu-id="f9b28-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="f9b28-104">Filtry takie mają zastosowanie do wszystkich zapytań wykonanych <xref:System.Data.Linq.DataContext> z tym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="f9b28-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9b28-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9b28-105">Example</span></span>  
 <span data-ttu-id="f9b28-106">W poniższym przykładzie <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> jest używany do filtrowania wstępnie załadowanych zamówień dla klientów przez `ShippedDate`program.</span><span class="sxs-lookup"><span data-stu-id="f9b28-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="f9b28-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9b28-107">See also</span></span>

- [<span data-ttu-id="f9b28-108">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="f9b28-108">Query Concepts</span></span>](query-concepts.md)
