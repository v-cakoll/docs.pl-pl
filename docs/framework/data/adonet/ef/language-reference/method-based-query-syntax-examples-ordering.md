---
title: "Przykłady składni zapytania oparte na metodzie: porządkowanie"
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
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0ba6dc4127a3240adb686fe8c0753a1c93afef12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="method-based-query-syntax-examples-ordering"></a>Przykłady składni zapytania oparte na metodzie: porządkowanie
Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.ThenBy%2A> metody query [AdventureWorks sprzedaży modelu](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni zapytania oparte na metodzie. Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie w składni zapytania oparte na metodzie <xref:System.Linq.Queryable.OrderBy%2A> i <xref:System.Linq.Queryable.ThenBy%2A> aby powrócić do listy kontaktów uporządkowanych według nazwisko, a następnie według imienia.  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a>ThenByDescending  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Queryable.OrderBy%2A> i <xref:System.Linq.Queryable.ThenByDescending%2A> metody pierwszy sortować cennika, a następnie wykonaj, malejąco sortowania nazwy produktu.  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
