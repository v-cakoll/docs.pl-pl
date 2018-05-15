---
title: Generowanie kodu SQL w dostawcy próbki
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 7275a67927d7692dc943e2555d65d1f7d6e4ba5a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="70aff-102">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="70aff-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="70aff-103">[Entity Framework próbki dostawcy](http://go.microsoft.com/fwlink/?LinkId=180616) pokazuje nowe składniki dostawcy danych ADO.NET, która obsługuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70aff-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="70aff-104">Z bazy danych programu SQL Server 2005 i lepiej jest zaimplementowany jako otoka dla dostawcy System.Data.SqlClient ADO.NET 2.0 danych.</span><span class="sxs-lookup"><span data-stu-id="70aff-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="70aff-105">Generowanie kodu SQL modułu dostawcy próbki (znajdujący się w folderze generowanie kodu SQL, z wyjątkiem pliku DmlSqlGenerator.cs) przyjmuje wejściowych DbQueryCommandTree i tworzy jednej instrukcji SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="70aff-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70aff-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="70aff-106">In This Section</span></span>  
 <span data-ttu-id="70aff-107">Ta sekcja zawiera następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="70aff-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="70aff-108">Architektura i projekt</span><span class="sxs-lookup"><span data-stu-id="70aff-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="70aff-109">Przewodnik: Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="70aff-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="70aff-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70aff-110">See Also</span></span>  
 [<span data-ttu-id="70aff-111">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="70aff-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
