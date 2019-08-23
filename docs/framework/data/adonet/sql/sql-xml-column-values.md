---
title: Wartości kolumny SQL XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 29e9ac5b95b62ef2a4467bf41484c3740d550abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964946"
---
# <a name="sql-xml-column-values"></a>Wartości kolumny SQL XML
SQL Server obsługuje `xml` typ danych, a deweloperzy mogą pobierać zestawy wyników, w tym typ, przy użyciu standardowego zachowania <xref:System.Data.SqlClient.SqlCommand> klasy. Kolumnę można pobrać tylko w przypadku pobrania dowolnej kolumny ( <xref:System.Data.SqlClient.SqlDataReader>na przykład), ale jeśli chcesz korzystać z zawartości kolumny jako XML <xref:System.Xml.XmlReader>, musisz użyć. `xml`  
  
## <a name="example"></a>Przykład  
 Poniższa Aplikacja konsolowa wybiera dwa wiersze, z których `xml` każda zawiera kolumnę, z tabeli **Sales. Store** w bazie danych **AdventureWorks** do <xref:System.Data.SqlClient.SqlDataReader> wystąpienia. Dla każdego wiersza wartość `xml` kolumny jest odczytywana <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> przy użyciu metody <xref:System.Data.SqlClient.SqlDataReader>. Wartość jest przechowywana w <xref:System.Xml.XmlReader>. Należy pamiętać, że należy <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> użyć zamiast <xref:System.Data.IDataRecord.GetValue%2A> metody, jeśli chcesz <xref:System.Data.SqlTypes.SqlXml> ustawić zawartość na zmienną; <xref:System.Data.IDataRecord.GetValue%2A> zwraca wartość`xml` kolumny jako ciąg.  
  
> [!NOTE]
> Przykładowa baza danych **AdventureWorks** nie jest instalowana domyślnie podczas instalowania SQL Server. Można go zainstalować, uruchamiając Instalatora SQL Server.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.SqlTypes.SqlXml>
- [Dane XML w programie SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
