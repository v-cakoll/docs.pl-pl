---
title: Wartości kolumny SQL XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: b46c763e7cddfc7617c9a6a23428f83a54955ba0
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244701"
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="ab15a-102">Wartości kolumny SQL XML</span><span class="sxs-lookup"><span data-stu-id="ab15a-102">SQL XML Column Values</span></span>
<span data-ttu-id="ab15a-103">SQL Server obsługuje `xml` typu danych i deweloperzy mogą pobrać zestawów wyników, w tym tego typu przy użyciu standardowego zachowania <xref:System.Data.SqlClient.SqlCommand> klasy.</span><span class="sxs-lookup"><span data-stu-id="ab15a-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="ab15a-104">`xml` Kolumn mogą być pobierane, tak samo, jak wszystkie kolumny są pobierane (w <xref:System.Data.SqlClient.SqlDataReader>, na przykład), ale jeśli chcesz pracować nad otrzymaną zawartością kolumny w formacie XML, należy użyć <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="ab15a-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab15a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab15a-105">Example</span></span>  
 <span data-ttu-id="ab15a-106">Następującej aplikacji konsoli wybiera dwa wiersze, zawierających `xml` kolumny z **Sales.Store** tabelę **AdventureWorks** bazy danych do <xref:System.Data.SqlClient.SqlDataReader> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ab15a-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="ab15a-107">Dla każdego wiersza wartości `xml` kolumny są odczytywane przy użyciu <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> metody <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="ab15a-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="ab15a-108">Wartość jest przechowywana w <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="ab15a-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="ab15a-109">Należy zauważyć, że należy użyć <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> zamiast <xref:System.Data.IDataRecord.GetValue%2A> metody, jeśli chcesz ustawić zawartość <xref:System.Data.SqlTypes.SqlXml> zmiennej; <xref:System.Data.IDataRecord.GetValue%2A> zwraca wartość `xml` kolumny jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="ab15a-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab15a-110">**AdventureWorks** przykładowej bazy danych nie jest instalowany domyślnie podczas instalowania programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab15a-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="ab15a-111">Można go zainstalować, uruchamiając Instalatora programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ab15a-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ab15a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab15a-112">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="ab15a-113">Dane XML w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="ab15a-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="ab15a-114">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ab15a-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
