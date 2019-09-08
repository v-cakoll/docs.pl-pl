---
title: Wiele operacji kopiowania zbiorczego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 838f56311f165c99c71cc734576bbdb53a946b7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792066"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="00032-102">Wiele operacji kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="00032-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="00032-103">Można wykonywać wiele operacji kopiowania zbiorczego przy użyciu jednego wystąpienia <xref:System.Data.SqlClient.SqlBulkCopy> klasy.</span><span class="sxs-lookup"><span data-stu-id="00032-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="00032-104">Jeśli parametry operacji zmieniają się między kopiami (na przykład nazwę tabeli docelowej), należy je zaktualizować przed kolejnymi wywołaniami dowolnej metody **WriteToServer** , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="00032-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="00032-105">O ile nie zmieniono jawnie, wszystkie wartości właściwości pozostają takie same, jak w poprzedniej operacji kopiowania zbiorczego dla danego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="00032-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00032-106">Wykonywanie wielu operacji kopiowania zbiorczego przy użyciu tego samego <xref:System.Data.SqlClient.SqlBulkCopy> wystąpienia jest zwykle wydajniejsze niż używanie osobnego wystąpienia dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="00032-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="00032-107">Jeśli wykonujesz kilka operacji kopiowania zbiorczego przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> tego samego obiektu, nie ma żadnych ograniczeń dotyczących tego, czy informacje źródłowe i docelowe są równe lub różnią się w poszczególnych operacjach.</span><span class="sxs-lookup"><span data-stu-id="00032-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="00032-108">Należy jednak upewnić się, że informacje o skojarzeniach kolumn są prawidłowo ustawiane za każdym razem, gdy piszesz na serwerze.</span><span class="sxs-lookup"><span data-stu-id="00032-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="00032-109">Ten przykład nie zostanie uruchomiony, jeśli nie utworzono tabel roboczych, zgodnie z opisem w [przykładowej konfiguracji kopiowania zbiorczego](bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="00032-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="00032-110">Ten kod jest dostarczany w celu przedstawienia składni tylko za pomocą **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="00032-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="00032-111">Jeśli tabele źródłowe i docelowe znajdują się w tym samym wystąpieniu SQL Server, łatwiej i szybciej można używać instrukcji języka Transact-SQL `INSERT … SELECT` do kopiowania danych.</span><span class="sxs-lookup"><span data-stu-id="00032-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="00032-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00032-112">See also</span></span>

- [<span data-ttu-id="00032-113">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="00032-113">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="00032-114">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="00032-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
