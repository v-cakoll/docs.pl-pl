---
title: Właściwość SqlTypes i zestaw danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: fe00e669449d40320a2038697976423db83ade5b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394210"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="5da88-102">Właściwość SqlTypes i zestaw danych</span><span class="sxs-lookup"><span data-stu-id="5da88-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="5da88-103">ADO.NET w wersji 2.0 wprowadzono rozszerzoną obsługę typu `DataSet` za pośrednictwem <xref:System.Data.SqlTypes> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5da88-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="5da88-104">Typy w <xref:System.Data.SqlTypes> zaprojektowano w celu zapewnienia typów danych o tej samej semantyki i dokładność jako typy danych w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5da88-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="5da88-105">Każdy typ danych w <xref:System.Data.SqlTypes> ma typ danych równoważne w programie SQL Server przy użyciu tej samej podstawowej reprezentacji danych.</span><span class="sxs-lookup"><span data-stu-id="5da88-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="5da88-106">Za pomocą <xref:System.Data.SqlTypes> bezpośrednio w <xref:System.Data.DataSet> daje kilka korzyści, podczas pracy z typami danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5da88-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="5da88-107"><xref:System.Data.SqlTypes> obsługuje tą samą semantyką jako typy danych natywnych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5da88-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="5da88-108">Określając jeden z <xref:System.Data.SqlTypes> w definicji <xref:System.Data.DataColumn> eliminuje utratę dokładności, który może wystąpić, gdy Konwersja typów danych typu dziesiętnego lub liczbowego na jeden z najczęściej popełnianymi typami danych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="5da88-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5da88-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5da88-109">Example</span></span>  
 <span data-ttu-id="5da88-110">Poniższy przykład tworzy <xref:System.Data.DataTable> obiektu jawne określenie <xref:System.Data.DataColumn> typy danych przy użyciu <xref:System.Data.SqlTypes> zamiast typów CLR.</span><span class="sxs-lookup"><span data-stu-id="5da88-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="5da88-111">Wypełnia kod <xref:System.Data.DataTable> przy użyciu danych z tabeli Sales.SalesOrderDetail w bazie AdventureWorks programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5da88-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="5da88-112">Dane wyjściowe wyświetlane w oknie konsoli przedstawia typ danych w każdej kolumnie i wartości pobierane z programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5da88-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5da88-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5da88-113">See Also</span></span>  
 [<span data-ttu-id="5da88-114">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="5da88-114">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="5da88-115">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="5da88-115">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="5da88-116">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5da88-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
