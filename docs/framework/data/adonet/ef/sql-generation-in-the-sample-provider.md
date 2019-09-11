---
title: Generowanie kodu SQL w dostawcy próbki
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: a59f1fecf85d63208c3388204c962b5838902ba7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854317"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="2db8f-102">Generowanie kodu SQL w dostawcy próbki</span><span class="sxs-lookup"><span data-stu-id="2db8f-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="2db8f-103">[Przykładowy dostawca Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ilustruje nowe składniki dostawców danych ADO.NET, które obsługują Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2db8f-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the Entity Framework.</span></span>  <span data-ttu-id="2db8f-104">Działa ona z bazą danych SQL Server 2005 i jest zaimplementowana jako otoka dla Dostawca danych System. Data. SqlClient ADO.NET 2,0.</span><span class="sxs-lookup"><span data-stu-id="2db8f-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="2db8f-105">Moduł generowania kodu SQL dostawcy przykładowego (znajdującego się w folderze generacji SQL, z wyjątkiem pliku DmlSqlGenerator.cs) przyjmuje wejściowy DbQueryCommandTree i tworzy pojedynczą instrukcję SELECT języka SQL.</span><span class="sxs-lookup"><span data-stu-id="2db8f-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2db8f-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2db8f-106">In This Section</span></span>  
 <span data-ttu-id="2db8f-107">Ta sekcja zawiera następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="2db8f-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="2db8f-108">Architektura i projekt</span><span class="sxs-lookup"><span data-stu-id="2db8f-108">Architecture and Design</span></span>](architecture-and-design.md)  
  
 [<span data-ttu-id="2db8f-109">Przewodnik: Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="2db8f-109">Walkthrough: SQL Generation</span></span>](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="2db8f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2db8f-110">See also</span></span>

- [<span data-ttu-id="2db8f-111">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="2db8f-111">SQL Generation</span></span>](sql-generation.md)
