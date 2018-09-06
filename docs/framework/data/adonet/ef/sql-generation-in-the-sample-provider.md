---
title: Generowanie kodu SQL w dostawcy próbki
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: cba1cec6d7ef0fdf8d4d4cf6c8e44fb325cf6447
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041301"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="b7721-102">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="b7721-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="b7721-103">[Dostawcy programu Entity Framework przykładowe](https://go.microsoft.com/fwlink/?LinkId=180616) pokazuje nowe składniki dostawcy danych ADO.NET, który obsługuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7721-103">The [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="b7721-104">Z bazą danych programu SQL Server 2005 i lepiej jest implementowany jako otoki dla dostawcy danych System.Data.SqlClient ADO.NET w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="b7721-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="b7721-105">Moduł generowanie kodu SQL w dostawcy próbki (znajdujący się w folderze generowanie kodu SQL, z wyjątkiem pliku DmlSqlGenerator.cs) zajmuje DbQueryCommandTree danych wejściowych i tworzy pojedynczą instrukcję SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="b7721-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b7721-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b7721-106">In This Section</span></span>  
 <span data-ttu-id="b7721-107">Ta sekcja zawiera następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="b7721-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="b7721-108">Architektura i projekt</span><span class="sxs-lookup"><span data-stu-id="b7721-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="b7721-109">Przewodnik: Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="b7721-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="b7721-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7721-110">See Also</span></span>  
 [<span data-ttu-id="b7721-111">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="b7721-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
