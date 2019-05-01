---
title: Generowanie kodu SQL w dostawcy próbki
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 88223930b65ccec9d030104c62d8b4b2e77ddbe2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879297"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="7ab62-102">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="7ab62-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="7ab62-103">[Dostawcy programu Entity Framework przykładowe](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) pokazuje nowe składniki dostawcy danych ADO.NET, który obsługuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ab62-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="7ab62-104">Z bazą danych programu SQL Server 2005 i lepiej jest implementowany jako otoki dla dostawcy danych System.Data.SqlClient ADO.NET w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="7ab62-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="7ab62-105">Moduł generowanie kodu SQL w dostawcy próbki (znajdujący się w folderze generowanie kodu SQL, z wyjątkiem pliku DmlSqlGenerator.cs) zajmuje DbQueryCommandTree danych wejściowych i tworzy pojedynczą instrukcję SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="7ab62-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ab62-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7ab62-106">In This Section</span></span>  
 <span data-ttu-id="7ab62-107">Ta sekcja zawiera następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="7ab62-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="7ab62-108">Architektura i projekt</span><span class="sxs-lookup"><span data-stu-id="7ab62-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="7ab62-109">Przewodnik: Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="7ab62-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ab62-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ab62-110">See also</span></span>

- [<span data-ttu-id="7ab62-111">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="7ab62-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
