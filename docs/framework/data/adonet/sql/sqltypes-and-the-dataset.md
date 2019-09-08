---
title: Właściwość SqlTypes i zestaw danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791500"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="d7fe0-102">Właściwość SqlTypes i zestaw danych</span><span class="sxs-lookup"><span data-stu-id="d7fe0-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="d7fe0-103">`DataSet` W<xref:System.Data.SqlTypes> systemie ADO.NET 2,0 wprowadzono rozszerzoną obsługę typów w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d7fe0-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="d7fe0-104">Typy w programie <xref:System.Data.SqlTypes> zaprojektowano w celu zapewnienia typów danych z tą samą semantyką i dokładnością jako typami danych w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d7fe0-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="d7fe0-105">Każdy typ danych w <xref:System.Data.SqlTypes> ma odpowiedni typ danych w SQL Server, z tą samą reprezentacją danych.</span><span class="sxs-lookup"><span data-stu-id="d7fe0-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="d7fe0-106">Użycie <xref:System.Data.SqlTypes> bezpośrednio<xref:System.Data.DataSet> w przystawce przydaje kilka korzyści podczas pracy z SQL Server typami danych.</span><span class="sxs-lookup"><span data-stu-id="d7fe0-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="d7fe0-107"><xref:System.Data.SqlTypes>obsługuje te same semantykę co SQL Server natywne typy danych.</span><span class="sxs-lookup"><span data-stu-id="d7fe0-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="d7fe0-108">Określanie jednej z <xref:System.Data.SqlTypes> w definicji a <xref:System.Data.DataColumn> eliminuje utratę dokładności, która może wystąpić podczas konwertowania dziesiętnych lub liczbowych typów danych na jeden z typów danych środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d7fe0-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7fe0-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7fe0-109">Example</span></span>  
 <span data-ttu-id="d7fe0-110">Poniższy przykład tworzy <xref:System.Data.DataTable> obiekt, jawnie <xref:System.Data.DataColumn> definiując typy danych przy użyciu <xref:System.Data.SqlTypes> zamiast typów CLR.</span><span class="sxs-lookup"><span data-stu-id="d7fe0-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="d7fe0-111">Kod wypełnia <xref:System.Data.DataTable> dane z tabeli Sales. SalesOrderDetail w bazie danych AdventureWorks w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d7fe0-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="d7fe0-112">Dane wyjściowe wyświetlane w oknie konsoli programu pokazują typ danych każdej kolumny i wartości pobrane z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d7fe0-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d7fe0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7fe0-113">See also</span></span>

- [<span data-ttu-id="d7fe0-114">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="d7fe0-114">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="d7fe0-115">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="d7fe0-115">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="d7fe0-116">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d7fe0-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
