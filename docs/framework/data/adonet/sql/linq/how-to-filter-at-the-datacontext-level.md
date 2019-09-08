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
# <a name="how-to-filter-at-the-datacontext-level"></a>Instrukcje: Filtrowanie na poziomie elementu DataContext
Można filtrować `EntitySets` `DataContext` na poziomie. Filtry takie mają zastosowanie do wszystkich zapytań wykonanych <xref:System.Data.Linq.DataContext> z tym wystąpieniem.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> jest używany do filtrowania wstępnie załadowanych zamówień dla klientów przez `ShippedDate`program.  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](query-concepts.md)
