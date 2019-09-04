---
title: 'Przykłady składni zapytania oparte na metodzie: Grupowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: c3a9bcef1944d0d018134383d3e556fe6ac24822
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250219"
---
# <a name="method-based-query-syntax-examples-grouping"></a>Przykłady składni zapytania oparte na metodzie: Grupowanie
W przykładach w tym temacie pokazano, jak używać `GroupBy` metody do wykonywania zapytań względem [modelu sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni zapytania opartego na metodzie. Model sprzedaży AdventureWorks używany w tych przykładach jest oparty na tabelach Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `GroupBy` metodę w celu `Address` zwrócenia obiektów, które są pogrupowane według kodu pocztowego. Wyniki są rzutowane na typ anonimowy.  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `GroupBy` metodę w celu `Contact` zwrócenia obiektów, które są pogrupowane według pierwszej litery nazwisko kontaktu. Wyniki są również sortowane według pierwszej litery ostatniej nazwy i są rzutowane na typ anonimowy.  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `GroupBy` metodę w celu `SalesOrderHeader` zwrócenia obiektów, które są pogrupowane według identyfikatora klienta. Zwracana jest również liczba sprzedaży dla każdego klienta.  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
