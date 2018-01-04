---
title: "Porównanie wierszy danych (LINQ do DataSet)"
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
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5634a20c51dd86bd383286735ee094d8746615d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-datarows-linq-to-dataset"></a>Porównanie wierszy danych (LINQ do DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]definiuje różne operatory zestawów do porównania elementy źródłowe, aby zobaczyć, czy są równe. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]udostępnia następujące operatory zestawów:  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 Te operatory porównania elementy źródłowe wywołując <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> i <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> metody dla każdej kolekcji elementów. W przypadku liczby <xref:System.Data.DataRow>, tych operatorów wykonać porównanie odwołań, które zwykle nie jest idealne zachowanie operacje na zestawie za pośrednictwem danych tabelarycznych. Dla operacji set zwykle chcesz określić, czy są równe wartości elementów i nie odwołania do elementu. W związku z tym <xref:System.Data.DataRowComparer> klasy został dodany do [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Ta klasa umożliwia porównanie wartości wiersza.  
  
 <xref:System.Data.DataRowComparer> Klasa zawiera implementację porównania wartości <xref:System.Data.DataRow>, więc ta klasa może być używana dla operacje na zestawie takich jak <xref:System.Linq.Enumerable.Distinct%2A>. Ta klasa nie może występować bezpośrednio; Zamiast tego <xref:System.Data.DataRowComparer.Default%2A> właściwość musi być używana do zwrócenia wystąpienia klasy <xref:System.Data.DataRowComparer%601>. <xref:System.Data.DataRowComparer%601.Equals%2A> Następnie wywoływana jest metoda i dwa <xref:System.Data.DataRow> obiektów, które ma zostać porównane, są przekazywane w jako parametry wejściowe. <xref:System.Data.DataRowComparer%601.Equals%2A> Metoda zwraca `true` w przypadku uporządkowanej zestaw kolumn wartości w obu <xref:System.Data.DataRow> obiekty są równe; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Intersect` do zwrócenia kontaktów wyświetlane w obu tabel.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Przykład  
 Porównuje dwa wiersze, pobiera ich skrótu w następującym przykładzie.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataRowComparer>  
 [Ładowanie danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
