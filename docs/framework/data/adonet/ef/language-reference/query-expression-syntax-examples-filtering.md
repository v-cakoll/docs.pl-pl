---
title: 'Przykłady składni wyrażeń zapytania: Filtrowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: b9e8cf238d35ec9a6fc9c6d013c4d92b00dced78
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955789"
---
# <a name="query-expression-syntax-examples-filtering"></a>Przykłady składni wyrażeń zapytania: Filtrowanie
W przykładach w tym temacie pokazano, `Where` jak za pomocą metod i `Where…Contains` zbadać [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytań. Uwaga, gdzie...`Contains` nie można użyć jako części [skompilowanego zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).  
  
 Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a>Gdzie  
  
### <a name="example"></a>Przykład  
 Poniższy przykład zwraca wszystkie zamówienia online.  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład zwraca zamówienia, w których ilość zamówienia jest większa niż 2 i mniejsza niż 6.  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład zwraca wszystkie kolorowe produkty.  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Where` metody, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2003, a następnie `order.SalesOrderDetail` użyć właściwości nawigacji, aby uzyskać szczegółowe informacje dotyczące poszczególnych zamówień.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a>Gdzie... Wyświetlana  
  
### <a name="example"></a>Przykład  
 Poniższy przykład używa tablicy jako części `Where…Contains` klauzuli, aby znaleźć wszystkie produkty, które `ProductModelID` są zgodne z wartością w tablicy.  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
> Jako część predykatu w `Where…Contains` klauzuli, można <xref:System.Array>użyć, a <xref:System.Collections.Generic.List%601>lub kolekcji dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs. Można również zadeklarować i zainicjować kolekcję w ramach zapytania LINQ to Entities. Aby uzyskać więcej informacji, zobacz następny przykład.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład deklaruje i inicjuje tablice w `Where…Contains` klauzuli, aby znaleźć wszystkie produkty, które `ProductModelID` mają lub `Size` które pasują do wartości w tablicach.  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
