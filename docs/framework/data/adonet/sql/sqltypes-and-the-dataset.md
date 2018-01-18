---
title: "Właściwości SqlTypes i zestawie danych"
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
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 61308d6c2c66e1c163431ced8d9c66980705b9c7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="0c39f-102">Właściwości SqlTypes i zestawie danych</span><span class="sxs-lookup"><span data-stu-id="0c39f-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="0c39f-103">ADO.NET 2.0 wprowadzono rozszerzoną obsługę typu `DataSet` za pośrednictwem <xref:System.Data.SqlTypes> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0c39f-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="0c39f-104">Typy w <xref:System.Data.SqlTypes> zaprojektowano typów danych o tej samej semantyki i dokładność jako typy danych w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c39f-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="0c39f-105">Każdy typ danych w <xref:System.Data.SqlTypes> ma typ danych odpowiednik w programie SQL Server z tego samego podstawowego reprezentację danych.</span><span class="sxs-lookup"><span data-stu-id="0c39f-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="0c39f-106">Przy użyciu <xref:System.Data.SqlTypes> bezpośrednio w <xref:System.Data.DataSet> przyznaje wiele zalet, podczas pracy z typów danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c39f-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="0c39f-107"><xref:System.Data.SqlTypes>obsługuje tej samej semantyki jako typów danych natywnych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c39f-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="0c39f-108">Określenie jednego z <xref:System.Data.SqlTypes> w definicji <xref:System.Data.DataColumn> eliminuje zmniejszenie precyzji, które mogą wystąpić podczas konwertowania typu dziesiętnego lub liczbowego danych do jednej z standardowe typy danych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="0c39f-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c39f-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c39f-109">Example</span></span>  
 <span data-ttu-id="0c39f-110">Poniższy przykład tworzy <xref:System.Data.DataTable> obiekt, jawnie definiujący <xref:System.Data.DataColumn> typy danych przy użyciu <xref:System.Data.SqlTypes> zamiast typów CLR.</span><span class="sxs-lookup"><span data-stu-id="0c39f-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="0c39f-111">Wstawia kod <xref:System.Data.DataTable> przy użyciu danych z tabeli Sales.SalesOrderDetail w bazie danych AdventureWorks programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c39f-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="0c39f-112">Wyświetlane w oknie konsoli wyświetlany jest typem danych kolumn i pobrać wartości z programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0c39f-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0c39f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c39f-113">See Also</span></span>  
 [<span data-ttu-id="0c39f-114">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="0c39f-114">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="0c39f-115">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="0c39f-115">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="0c39f-116">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="0c39f-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
