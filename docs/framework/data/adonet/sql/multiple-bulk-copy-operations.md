---
title: Wiele operacji kopiowania zbiorczego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 405a82c625853d242ca68088ffdf81b6bcd7c518
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209765"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="5aa4c-102">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="5aa4c-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="5aa4c-103">Można wykonać wiele operacji kopiowania zbiorczego przy użyciu pojedynczego wystąpienia <xref:System.Data.SqlClient.SqlBulkCopy> klasy.</span><span class="sxs-lookup"><span data-stu-id="5aa4c-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="5aa4c-104">Jeśli zmienisz parametry operacji między kopii (na przykład nazwa tabeli docelowej), należy zaktualizować je przed kolejnych wywołań do któregokolwiek elementu **WriteToServer** metody, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5aa4c-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="5aa4c-105">Chyba że jawnie zmieniona wartości wszystkich właściwości pozostają takie same, jakie były na poprzedniej operacji kopiowania zbiorczego dla danego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5aa4c-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5aa4c-106">Wykonując wiele operacji kopiowania zbiorczego przy użyciu tego samego wystąpienia <xref:System.Data.SqlClient.SqlBulkCopy> jest zazwyczaj bardziej efektywne niż przy użyciu oddzielnego wystąpienia dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="5aa4c-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="5aa4c-107">Należy wykonać kilka operacji kopiowania zbiorczego, korzystając z tych samych <xref:System.Data.SqlClient.SqlBulkCopy> obiektu, nie ma żadnych ograniczeń, czy informacje o źródłowej lub docelowej jest taki sam lub inne w przypadku każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="5aa4c-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="5aa4c-108">Jednak upewnij się, że informacji o skojarzeniu kolumny są ustawione właściwie każdorazowo, gdy zapisu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="5aa4c-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5aa4c-109">W tym przykładzie nie będzie działać, chyba że utworzonego tabelami pracy zgodnie z opisem w [Konfiguracja przykładu kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="5aa4c-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="5aa4c-110">Ten kod jest dostarczany do zademonstrowania składnia przy użyciu **SqlBulkCopy** tylko.</span><span class="sxs-lookup"><span data-stu-id="5aa4c-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="5aa4c-111">Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze użyj instrukcji Transact-SQL `INSERT … SELECT` instrukcję, aby skopiować dane.</span><span class="sxs-lookup"><span data-stu-id="5aa4c-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5aa4c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5aa4c-112">See also</span></span>

- [<span data-ttu-id="5aa4c-113">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="5aa4c-113">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="5aa4c-114">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="5aa4c-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
