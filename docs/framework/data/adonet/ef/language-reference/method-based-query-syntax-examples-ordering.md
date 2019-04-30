---
title: 'Przykłady składni zapytania oparte na metodzie: Szeregowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: e213046955c2c4e720c56adb96da29078ea3c48d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760574"
---
# <a name="method-based-query-syntax-examples-ordering"></a>Przykłady składni zapytania oparte na metodzie: Szeregowanie
Przykłady w tym temacie prezentują sposób użycia <xref:System.Linq.Enumerable.ThenBy%2A> metody zapytania [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) za pomocą składni zapytania oparte na metodzie. Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przy użyciu składni zapytania oparte na metodzie <xref:System.Linq.Queryable.OrderBy%2A> i <xref:System.Linq.Queryable.ThenBy%2A> aby powrócić do listy kontaktów, uporządkowane według nazwiska, a następnie według imienia.  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a>ThenByDescending  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Queryable.OrderBy%2A> i <xref:System.Linq.Queryable.ThenByDescending%2A> metody uprzedniego sortować według ceny, a następnie wykonaj, malejąco swoistego nazw produktów.  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
