---
title: 'Przykłady składni zapytania oparte na metodzie: Partycjonowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 42c562e7665a53053f125c17d073eb437574939f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250124"
---
# <a name="method-based-query-syntax-examples-partitioning"></a>Przykłady składni zapytania oparte na metodzie: Partycjonowanie
W przykładach w tym temacie pokazano <xref:System.Linq.Enumerable.Skip%2A>, jak użyć metod, i <xref:System.Linq.Enumerable.Take%2A> zbadać [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytań. Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a>Skip  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Skip%2A> metodę, aby pobrać wszystkie pierwsze kontakty z tabeli kontaktowej.  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Skip%2A> metodę, aby pobrać wszystkie pierwsze dwa adresy z Seattle.  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a>Take  
  
### <a name="example"></a>Przykład  
 Poniższy przykład używa metody, <xref:System.Linq.Enumerable.Take%2A> Aby uzyskać tylko pięć pierwszych kontaktów z tabeli kontaktów.  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Take%2A> metodę, aby pobrać pierwsze trzy adresy w Seattle.  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
