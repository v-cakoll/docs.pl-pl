---
title: Grupowanie elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: bc490b579e841a0e9b3724fe0e8789cc9411683d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782194"
---
# <a name="group-elements-in-a-sequence"></a>Grupowanie elementów w sekwencji
<xref:System.Linq.Enumerable.GroupBy%2A> Operator Grupuje elementy sekwencji. W poniższych przykładach użyto bazy danych Northwind.  
  
> [!NOTE]
> Wartości pustej kolumny <xref:System.Linq.Enumerable.GroupBy%2A> w zapytaniach mogą <xref:System.InvalidOperationException>czasami zgłosić. Aby uzyskać więcej informacji, zobacz sekcję "GroupBy InvalidOperationException" w temacie [Rozwiązywanie problemów](troubleshooting.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład partycjonowania `Products` przez `CategoryID`.  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Linq.Enumerable.Max%2A> , aby znaleźć maksymalną cenę jednostkową dla każdej `CategoryID`z nich.  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano średnią, aby `UnitPrice` znaleźć średnią dla każdej z nich. `CategoryID`  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Linq.Queryable.Sum%2A> , aby znaleźć sumę `UnitPrice` dla każdej z `CategoryID`nich.  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Linq.Queryable.Count%2A> , aby znaleźć liczbę `Products` wycofanych w każdym z nich `CategoryID`.  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano następującą `where` klauzulę, aby znaleźć wszystkie kategorie, które mają co najmniej 10 produktów.  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład grupuje produkty według `CategoryID` i `SupplierID`.  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca dwie sekwencje produktów. Pierwsza sekwencja zawiera produkty z ceną jednostkową mniejszą lub równą 10. Druga sekwencja zawiera produkty z ceną jednostkową większą niż 10.  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a>Przykład  
 <xref:System.Linq.Queryable.GroupBy%2A> Operator może przyjmować tylko jeden argument klucza. Jeśli zachodzi potrzeba pogrupowania przez więcej niż jeden klucz, należy utworzyć typ anonimowy, jak w poniższym przykładzie:  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
