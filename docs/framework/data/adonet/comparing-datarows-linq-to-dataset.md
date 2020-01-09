---
title: Porównywanie wierszy DataRows (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: fbd642fb3da6d664df9076b8d7576865d516727e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634901"
---
# <a name="comparing-datarows-linq-to-dataset"></a>Porównywanie wierszy DataRows (LINQ to DataSet)
Załączone w języku zapytanie (LINQ) definiuje różne operatory zestawów do porównywania elementów źródłowych, aby sprawdzić, czy są równe. LINQ udostępnia następujące operatory zestawu:  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 Te operatory porównują elementy źródłowe, wywołując <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> i <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> metody dla każdej kolekcji elementów. W przypadku <xref:System.Data.DataRow>te operatory wykonują porównanie odwołań, które zwykle nie jest idealnym zachowaniem dla operacji ustawiania w danych tabelarycznych. W przypadku operacji ustawiania zazwyczaj należy określić, czy wartości elementów są równe, a nie odwołania do elementów. W związku z tym Klasa <xref:System.Data.DataRowComparer> została dodana do LINQ to DataSet. Ta klasa może służyć do porównywania wartości wierszy.  
  
 Klasa <xref:System.Data.DataRowComparer> zawiera implementację porównania wartości dla <xref:System.Data.DataRow>, więc ta klasa może być używana do ustawiania operacji, takich jak <xref:System.Linq.Enumerable.Distinct%2A>. Nie można bezpośrednio utworzyć wystąpienia tej klasy; Zamiast tego Właściwość <xref:System.Data.DataRowComparer.Default%2A> musi być używana do zwracania wystąpienia <xref:System.Data.DataRowComparer%601>. Metoda <xref:System.Data.DataRowComparer%601.Equals%2A> jest następnie wywoływana, a dwa <xref:System.Data.DataRow> obiekty, które mają być porównane, są przenoszone jako parametry wejściowe. Metoda <xref:System.Data.DataRowComparer%601.Equals%2A> zwraca `true`, jeśli uporządkowany zestaw wartości kolumn w obu <xref:System.Data.DataRow> obiektów jest równy; w przeciwnym razie `false`.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa `Intersect`, aby zwrócić kontakty, które są wyświetlane w obu tabelach.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład porównuje dwa wiersze i pobiera ich kody skrótów.  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRowComparer>
- [Ładowanie danych do zestawu danych](loading-data-into-a-dataset.md)
- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
