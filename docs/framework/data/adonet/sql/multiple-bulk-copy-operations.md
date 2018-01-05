---
title: Wiele operacji kopiowania zbiorczego
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
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 66d6aeffe813d6690a264cbe41eda83661ea1eec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="0463f-102">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="0463f-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="0463f-103">Można wykonywać wiele operacji kopiowania zbiorczego, za pomocą jednego wystąpienia <xref:System.Data.SqlClient.SqlBulkCopy> klasy.</span><span class="sxs-lookup"><span data-stu-id="0463f-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="0463f-104">Jeśli parametry operacji zmiany między kopiami (na przykład nazwa tabeli docelowej), należy zaktualizować je przed kolejnych wywołań dowolnej z **WriteToServer** metod, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0463f-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="0463f-105">Chyba że jawnie zmieniona wszystkich wartości właściwości pozostają takie same, jakie były na poprzedniej operacji kopiowania zbiorczego dla danego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0463f-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0463f-106">Wykonywanie wielu operacji kopiowania zbiorczego przy użyciu tego samego wystąpienia <xref:System.Data.SqlClient.SqlBulkCopy> jest zazwyczaj bardziej efektywne niż przy użyciu osobnego wystąpienia dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="0463f-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="0463f-107">Jeśli wykonano kilka operacji kopiowania zbiorczego korzystającej z tego samego <xref:System.Data.SqlClient.SqlBulkCopy> obiektu, nie ma żadnych ograniczeń czy informacji źródłowa lub docelowa jest taki sam lub inny w każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="0463f-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="0463f-108">Należy jednak upewnić się, czy informacje o skojarzeniu kolumny są ustawione właściwie zawsze, gdy zapisać na serwerze.</span><span class="sxs-lookup"><span data-stu-id="0463f-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0463f-109">W tym przykładzie nie będzie działać, jeśli nie utworzono tabel roboczych zgodnie z opisem w [Instalatora przykład kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="0463f-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="0463f-110">Ten kod jest dostarczany do zaprezentowania składnia przy użyciu **SqlBulkCopy** tylko.</span><span class="sxs-lookup"><span data-stu-id="0463f-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="0463f-111">Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze do używania języka Transact-SQL `INSERT … SELECT` instrukcji, aby skopiować dane.</span><span class="sxs-lookup"><span data-stu-id="0463f-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0463f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0463f-112">See Also</span></span>  
 [<span data-ttu-id="0463f-113">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="0463f-113">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="0463f-114">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="0463f-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
