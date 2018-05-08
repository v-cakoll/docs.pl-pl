---
title: Właściwości SqlTypes i zestawie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: 14c341a014de5d0b3ede4d11841b34c1426d95fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sqltypes-and-the-dataset"></a>Właściwości SqlTypes i zestawie danych
ADO.NET 2.0 wprowadzono rozszerzoną obsługę typu `DataSet` za pośrednictwem <xref:System.Data.SqlTypes> przestrzeni nazw. Typy w <xref:System.Data.SqlTypes> zaprojektowano typów danych o tej samej semantyki i dokładność jako typy danych w bazie danych programu SQL Server. Każdy typ danych w <xref:System.Data.SqlTypes> ma typ danych odpowiednik w programie SQL Server z tego samego podstawowego reprezentację danych.  
  
 Przy użyciu <xref:System.Data.SqlTypes> bezpośrednio w <xref:System.Data.DataSet> przyznaje wiele zalet, podczas pracy z typów danych programu SQL Server. <xref:System.Data.SqlTypes> obsługuje tej samej semantyki jako typów danych natywnych programu SQL Server. Określenie jednego z <xref:System.Data.SqlTypes> w definicji <xref:System.Data.DataColumn> eliminuje zmniejszenie precyzji, które mogą wystąpić podczas konwertowania typu dziesiętnego lub liczbowego danych do jednej z standardowe typy danych języka wspólnego (CLR).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataTable> obiekt, jawnie definiujący <xref:System.Data.DataColumn> typy danych przy użyciu <xref:System.Data.SqlTypes> zamiast typów CLR. Wstawia kod <xref:System.Data.DataTable> przy użyciu danych z tabeli Sales.SalesOrderDetail w bazie danych AdventureWorks programu SQL Server. Wyświetlane w oknie konsoli wyświetlany jest typem danych kolumn i pobrać wartości z programu SQL Server.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
