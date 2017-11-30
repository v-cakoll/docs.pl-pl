---
title: "Generowanie kodu SQL w dostawcy próbki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58a49f7bf5d385466810a3c59bda748ef66d5840
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="516e9-102">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="516e9-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="516e9-103">[Entity Framework próbki dostawcy](http://go.microsoft.com/fwlink/?LinkId=180616) pokazuje nowe składniki dostawcy danych ADO.NET, która obsługuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="516e9-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="516e9-104">Z bazy danych programu SQL Server 2005 i lepiej jest zaimplementowany jako otoka dla dostawcy System.Data.SqlClient ADO.NET 2.0 danych.</span><span class="sxs-lookup"><span data-stu-id="516e9-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="516e9-105">Generowanie kodu SQL modułu dostawcy próbki (znajdujący się w folderze generowanie kodu SQL, z wyjątkiem pliku DmlSqlGenerator.cs) przyjmuje wejściowych DbQueryCommandTree i tworzy jednej instrukcji SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="516e9-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="516e9-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="516e9-106">In This Section</span></span>  
 <span data-ttu-id="516e9-107">Ta sekcja zawiera następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="516e9-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="516e9-108">Architektury i projektu</span><span class="sxs-lookup"><span data-stu-id="516e9-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="516e9-109">Wskazówki: Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="516e9-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="516e9-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="516e9-110">See Also</span></span>  
 [<span data-ttu-id="516e9-111">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="516e9-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
