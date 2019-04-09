---
title: Nawigowanie w elementach DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 91db42acb0e09b8fc99b0ee710a60800d40938ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112856"
---
# <a name="navigating-datatables"></a>Nawigowanie w elementach DataTable
<xref:System.Data.DataTableReader> Uzyskuje zawartość jednego lub więcej <xref:System.Data.DataTable> obiektów w postaci jednego lub więcej zestawów wyników tylko do odczytu, tylko do przodu.  
  
 A <xref:System.Data.DataTableReader> może zawierać wiele zestawów wyników, jeśli jest tworzona przy użyciu <xref:System.Data.DataSet.CreateDataReader%2A> metody. Jeśli istnieje więcej niż jeden zestaw wyników, <xref:System.Data.DataTableReader.NextResult%2A> metoda przesuwa kursor do następnego zestawu wyników. Jest to proces tylko do przodu. Nie jest możliwe powrócić do poprzedniego zestawu wyników.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `TestConstructor` metoda tworzy dwa <xref:System.Data.DataTable> wystąpień. W celu przedstawienia tej Konstruktor <xref:System.Data.DataTableReader> klasy Przykładowa aplikacja tworzy nową **elementu DataTableReader** na podstawie tablicy, która zawiera dwa **DataTables**i wykonuje prostą operacją Drukowanie zawartości z pierwszego mało kolumn w oknie konsoli.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataTableReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
