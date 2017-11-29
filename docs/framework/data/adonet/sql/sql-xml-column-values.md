---
title: "Wartości w kolumnie SQL XML"
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
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c974749ee84bf64d1912ed71ea0817227b1ea514
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sql-xml-column-values"></a>Wartości w kolumnie SQL XML
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]obsługuje `xml` typu danych i deweloperzy mogą pobrać zestawów wyników w tym tego typu przy użyciu standardowego zachowania <xref:System.Data.SqlClient.SqlCommand> klasy. `xml` Kolumny można pobrać tak samo, jak wszystkie kolumny są pobierane (w <xref:System.Data.SqlClient.SqlDataReader>, na przykład), ale jeśli chcesz pracować z zawartością kolumny w formacie XML, należy użyć <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Przykład  
 Dwa wiersze, każdy z nich zawiera wybiera następującej aplikacji konsoli `xml` kolumny, od **Sales.Store** tabeli w **AdventureWorks** bazy danych do <xref:System.Data.SqlClient.SqlDataReader> wystąpienia. Dla każdego wiersza wartości `xml` przy użyciu kolumny jest do odczytu <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> metody <xref:System.Data.SqlClient.SqlDataReader>. Wartość jest przechowywana w <xref:System.Xml.XmlReader>. Należy pamiętać, że należy użyć <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> zamiast <xref:System.Data.IDataRecord.GetValue%2A> metody, jeśli chcesz ustawić zawartość <xref:System.Data.SqlTypes.SqlXml> zmiennej; <xref:System.Data.IDataRecord.GetValue%2A> zwraca wartość `xml` kolumny jako ciąg.  
  
> [!NOTE]
>  **AdventureWorks** przykładowej bazy danych nie jest instalowany domyślnie podczas instalowania [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Można ją zainstalować, uruchamiając [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Instalatora.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.SqlTypes.SqlXml>  
 [Dane XML w programie SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
