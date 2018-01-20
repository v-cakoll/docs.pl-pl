---
title: "Przykłady składni zapytania oparte na metodzie: konwersja"
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
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aafc059b5560af1fef54c20a3718d3f405ce7ba9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="method-based-query-syntax-examples-conversion"></a>Przykłady składni zapytania oparte na metodzie: konwersja
Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> i <xref:System.Linq.Enumerable.ToList%2A> metod do badania [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) przy użyciu składni zapytania oparte na metodzie. Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a>toArray  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Enumerable.ToArray%2A> metodę, aby natychmiast ocenić sekwencji do tablicy.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a>ToDictionary  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Enumerable.ToDictionary%2A> metodę, aby natychmiast ocenę sekwencji i powiązane wyrażenia klucza do słownika.  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a>tolist —  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Enumerable.ToList%2A> metodę, aby natychmiast ocenić sekwencji do <xref:System.Collections.Generic.List%601>, gdzie `T` jest typu <xref:System.Data.DataRow>.  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
