---
title: 'Przykłady składni zapytania oparte na metodzie: Operatory elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 9a057cd80b3dc110626d1a9a850ee7c9704b33b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250259"
---
# <a name="method-based-query-syntax-examples-element-operators"></a>Przykłady składni zapytania oparte na metodzie: Operatory elementu
W przykładach w tym temacie pokazano, <xref:System.Linq.Enumerable.First%2A> jak używać metody do wykonywania zapytań względem [modelu sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni zapytania opartego na metodzie. Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.  
  
 W przykładzie w tym temacie są stosowane następujące `using` / `Imports` instrukcje:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a>Pierwszego  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.First%2A> metodę w celu znalezienia pierwszego adresu e-mail, który rozpoczyna się od "Caroline".  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
