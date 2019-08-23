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
# <a name="sql-xml-column-values"></a><span data-ttu-id="2c88e-102">Wartości kolumny SQL XML</span><span class="sxs-lookup"><span data-stu-id="2c88e-102">SQL XML Column Values</span></span>
<span data-ttu-id="2c88e-103">SQL Server obsługuje `xml` typ danych, a deweloperzy mogą pobierać zestawy wyników, w tym typ, przy użyciu standardowego zachowania <xref:System.Data.SqlClient.SqlCommand> klasy.</span><span class="sxs-lookup"><span data-stu-id="2c88e-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="2c88e-104">Kolumnę można pobrać tylko w przypadku pobrania dowolnej kolumny ( <xref:System.Data.SqlClient.SqlDataReader>na przykład), ale jeśli chcesz korzystać z zawartości kolumny jako XML <xref:System.Xml.XmlReader>, musisz użyć. `xml`</span><span class="sxs-lookup"><span data-stu-id="2c88e-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c88e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c88e-105">Example</span></span>  
 <span data-ttu-id="2c88e-106">Poniższa Aplikacja konsolowa wybiera dwa wiersze, z których `xml` każda zawiera kolumnę, z tabeli **Sales. Store** w bazie danych **AdventureWorks** do <xref:System.Data.SqlClient.SqlDataReader> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2c88e-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="2c88e-107">Dla każdego wiersza wartość `xml` kolumny jest odczytywana <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> przy użyciu metody <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="2c88e-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="2c88e-108">Wartość jest przechowywana w <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="2c88e-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="2c88e-109">Należy pamiętać, że należy <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> użyć zamiast <xref:System.Data.IDataRecord.GetValue%2A> metody, jeśli chcesz <xref:System.Data.SqlTypes.SqlXml> ustawić zawartość na zmienną; <xref:System.Data.IDataRecord.GetValue%2A> zwraca wartość`xml` kolumny jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="2c88e-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c88e-110">Przykładowa baza danych **AdventureWorks** nie jest instalowana domyślnie podczas instalowania SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2c88e-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="2c88e-111">Można go zainstalować, uruchamiając Instalatora SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2c88e-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2c88e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c88e-112">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="2c88e-113">Dane XML w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="2c88e-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [<span data-ttu-id="2c88e-114">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2c88e-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
