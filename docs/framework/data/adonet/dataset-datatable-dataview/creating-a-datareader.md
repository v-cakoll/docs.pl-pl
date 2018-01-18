---
title: Tworzenie elementu DataReader
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
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b603e4fad628d0bb338213420059ffa411acd432
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-datareader"></a>Tworzenie elementu DataReader
<xref:System.Data.DataTable> i <xref:System.Data.DataSet> klasy mają <xref:System.Data.DataTable.CreateDataReader%2A> metodę, która zwraca zawartość <xref:System.Data.DataTable> lub zawartość <xref:System.Data.DataSet> obiektu <xref:System.Data.DataSet.Tables%2A> kolekcji jako jeden lub więcej zestawów wyników tylko do odczytu, tylko do przodu.  
  
## <a name="example"></a>Przykład  
 Tworzy następującej aplikacji konsoli <xref:System.Data.DataTable> wystąpienia. Przykład następnie przekazuje wypełniony <xref:System.Data.DataTable> do procedury, która wywołuje <xref:System.Data.DataTable.CreateDataReader%2A> metodę, która iterację w wynikach zawartych w <xref:System.Data.DataTableReader>.  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 W przykładzie przedstawiono następujące wyniki w oknie konsoli:  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [Elementy DataTableReader](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
