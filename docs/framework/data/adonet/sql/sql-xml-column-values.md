---
title: Wartości kolumny SQL XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 803357f9ae97eee2cbbf5e777dbc1210ded26ab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149711"
---
# <a name="sql-xml-column-values"></a>Wartości kolumny SQL XML
SQL Server obsługuje `xml` typu danych i deweloperzy mogą pobrać zestawów wyników, w tym tego typu przy użyciu standardowego zachowania <xref:System.Data.SqlClient.SqlCommand> klasy. `xml` Kolumn mogą być pobierane, tak samo, jak wszystkie kolumny są pobierane (w <xref:System.Data.SqlClient.SqlDataReader>, na przykład), ale jeśli chcesz pracować nad otrzymaną zawartością kolumny w formacie XML, należy użyć <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji konsoli wybiera dwa wiersze, zawierających `xml` kolumny z **Sales.Store** tabelę **AdventureWorks** bazy danych do <xref:System.Data.SqlClient.SqlDataReader> wystąpienia. Dla każdego wiersza wartości `xml` kolumny są odczytywane przy użyciu <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> metody <xref:System.Data.SqlClient.SqlDataReader>. Wartość jest przechowywana w <xref:System.Xml.XmlReader>. Należy zauważyć, że należy użyć <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> zamiast <xref:System.Data.IDataRecord.GetValue%2A> metody, jeśli chcesz ustawić zawartość <xref:System.Data.SqlTypes.SqlXml> zmiennej; <xref:System.Data.IDataRecord.GetValue%2A> zwraca wartość `xml` kolumny jako ciąg.  
  
> [!NOTE]
>  **AdventureWorks** przykładowej bazy danych nie jest instalowany domyślnie podczas instalowania programu SQL Server. Można go zainstalować, uruchamiając Instalatora programu SQL Server.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.SqlTypes.SqlXml>
- [Dane XML w programie SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
