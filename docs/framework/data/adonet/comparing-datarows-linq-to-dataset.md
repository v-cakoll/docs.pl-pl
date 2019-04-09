---
title: Porównywanie wierszy danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 2b45a4629474c394c8e49c41a7a98fc1181e124b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077176"
---
# <a name="comparing-datarows-linq-to-dataset"></a>Porównywanie wierszy danych (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] definiuje różne operatory zestawów do porównywania elementów źródła, aby zobaczyć, czy są równe. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] udostępnia następujące operatory zestawów:  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 Te operatory porównania elementy źródłowe, wywołując <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> i <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> metody dla każdej kolekcji elementów. W przypadku właściwości <xref:System.Data.DataRow>, te operatory wykonać porównanie odwołań, które zwykle nie jest idealnym rozwiązaniem zachowanie operacje na zestawie danych tabelarycznych. Dla operacji zestawu zazwyczaj chcesz określić, czy są równe wartości elementów i nie odwołania do elementu. W związku z tym <xref:System.Data.DataRowComparer> klasa została dodana do [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Tej klasy może służyć do porównywania wartości wierszy.  
  
 <xref:System.Data.DataRowComparer> Klasa zawiera implementację porównania wartości <xref:System.Data.DataRow>, więc ta klasa może służyć do zestawu operacji takich jak <xref:System.Linq.Enumerable.Distinct%2A>. To nie można bezpośrednio utworzyć wystąpienia klasy; Zamiast tego <xref:System.Data.DataRowComparer.Default%2A> właściwość musi być używana do zwrócenia wystąpienia <xref:System.Data.DataRowComparer%601>. <xref:System.Data.DataRowComparer%601.Equals%2A> Następnie wywoływana jest metoda i dwa <xref:System.Data.DataRow> obiekty, które mają być porównane, są przekazywane w jako parametry wejściowe. <xref:System.Data.DataRowComparer%601.Equals%2A> Metoda zwraca `true` Jeśli uporządkowany zestaw kolumn wartości w obu <xref:System.Data.DataRow> obiekty są równe; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Intersect` do zwrócenia kontakty, które pojawiają się w obu tabelach.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład porównuje dwa wiersze i pobiera ich kody skrótów.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRowComparer>
- [Ładowanie danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
