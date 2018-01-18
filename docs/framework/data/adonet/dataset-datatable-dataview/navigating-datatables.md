---
title: Nawigowanie po DataTables
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
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2233beeab5bc613966375f9a8ccf18c333e9f4c6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="navigating-datatables"></a>Nawigowanie po DataTables
<xref:System.Data.DataTableReader> Uzyskuje zawartość jednego lub więcej <xref:System.Data.DataTable> obiekty w postaci jednego lub więcej zestawów wyników tylko do odczytu, tylko do przodu.  
  
 A <xref:System.Data.DataTableReader> może zawierać wiele zestawów wyników, jeśli jest tworzona przy użyciu <xref:System.Data.DataSet.CreateDataReader%2A> metody. Jeśli istnieje więcej niż jeden zestaw wyników, <xref:System.Data.DataTableReader.NextResult%2A> metody przesuwa kursor do następnego zestawu wyników. Jest to proces tylko do przodu. Nie jest możliwe powrócić do poprzedniego zestawu wyników.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `TestConstructor` metoda tworzy dwa <xref:System.Data.DataTable> wystąpień. W celu zaprezentowania tego konstruktora dla <xref:System.Data.DataTableReader> klasy, tworzy nową próbkę **Element DataTableReader** na podstawie tablicy, która zawiera dwa **DataTables**i wykonuje operację proste Drukowanie zawartości z pierwszego kilka kolumn, w oknie konsoli.  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataTableReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
