---
title: Nawigowanie w elementach DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: f00e2171c1adf4ff99a669085131ebc8d38f7006
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080058"
---
# <a name="navigating-datatables"></a>Nawigowanie w elementach DataTable
<xref:System.Data.DataTableReader> Uzyskuje zawartość jednego lub więcej <xref:System.Data.DataTable> obiektów w postaci jednego lub więcej zestawów wyników tylko do odczytu, tylko do przodu.  
  
 A <xref:System.Data.DataTableReader> może zawierać wiele zestawów wyników, jeśli jest tworzona przy użyciu <xref:System.Data.DataSet.CreateDataReader%2A> metody. Jeśli istnieje więcej niż jeden zestaw wyników, <xref:System.Data.DataTableReader.NextResult%2A> metoda przesuwa kursor do następnego zestawu wyników. Jest to proces tylko do przodu. Nie jest możliwe powrócić do poprzedniego zestawu wyników.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `TestConstructor` metoda tworzy dwa <xref:System.Data.DataTable> wystąpień. W celu przedstawienia tej Konstruktor <xref:System.Data.DataTableReader> klasy Przykładowa aplikacja tworzy nową **elementu DataTableReader** na podstawie tablicy, która zawiera dwa **DataTables**i wykonuje prostą operacją Drukowanie zawartości z pierwszego mało kolumn w oknie konsoli.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataTableReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
