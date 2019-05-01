---
title: Właściwość SqlTypes i zestaw danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: a218a8e0fe3d2c17a0f09a40645c7b3ad26fb5ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780175"
---
# <a name="sqltypes-and-the-dataset"></a>Właściwość SqlTypes i zestaw danych
ADO.NET w wersji 2.0 wprowadzono rozszerzoną obsługę typu `DataSet` za pośrednictwem <xref:System.Data.SqlTypes> przestrzeni nazw. Typy w <xref:System.Data.SqlTypes> zaprojektowano w celu zapewnienia typów danych o tej samej semantyki i dokładność jako typy danych w bazie danych programu SQL Server. Każdy typ danych w <xref:System.Data.SqlTypes> ma typ danych równoważne w programie SQL Server przy użyciu tej samej podstawowej reprezentacji danych.  
  
 Za pomocą <xref:System.Data.SqlTypes> bezpośrednio w <xref:System.Data.DataSet> daje kilka korzyści, podczas pracy z typami danych programu SQL Server. <xref:System.Data.SqlTypes> obsługuje tą samą semantyką jako typy danych natywnych programu SQL Server. Określając jeden z <xref:System.Data.SqlTypes> w definicji <xref:System.Data.DataColumn> eliminuje utratę dokładności, który może wystąpić, gdy Konwersja typów danych typu dziesiętnego lub liczbowego na jeden z najczęściej popełnianymi typami danych języka wspólnego (CLR).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataTable> obiektu jawne określenie <xref:System.Data.DataColumn> typy danych przy użyciu <xref:System.Data.SqlTypes> zamiast typów CLR. Wypełnia kod <xref:System.Data.DataTable> przy użyciu danych z tabeli Sales.SalesOrderDetail w bazie AdventureWorks programu SQL Server. Dane wyjściowe wyświetlane w oknie konsoli przedstawia typ danych w każdej kolumnie i wartości pobierane z programu SQL Server.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie typu danych serwera SQL](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Konfigurowanie parametrów i typów danych parametrów](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
