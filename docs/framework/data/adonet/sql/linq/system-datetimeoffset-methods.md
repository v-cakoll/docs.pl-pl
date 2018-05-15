---
title: System.DateTimeOffset Methods
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 7fc6502f899e953637d23c0d54cc5fe615c38eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="185a7-102">System.DateTimeOffset Methods</span><span class="sxs-lookup"><span data-stu-id="185a7-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="185a7-103">Zmapowaniu w modelu obiektu lub plik mapowania zewnętrznych LINQ do SQL pozwala wywoływać większość <xref:System.DateTimeOffset?displayProperty=nameWithType> metody, Operatorzy i właściwości z Twojej LINQ do zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="185a7-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="185a7-104">Tylko metody nie jest obsługiwane są te dziedziczone z <xref:System.Object?displayProperty=nameWithType> które nie mają sensu w kontekście LINQ do zapytania SQL, takich jak: `Finalize`, `GetHashCode`, `GetType`, i `MemberwiseClone`.</span><span class="sxs-lookup"><span data-stu-id="185a7-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="185a7-105">Te metody nie są obsługiwane, ponieważ LINQ do SQL nie może tłumaczyć je do wykonania na serwerze SQL.</span><span class="sxs-lookup"><span data-stu-id="185a7-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="185a7-106">Środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> struktury i możliwość mapowanie go SQL `DATETIMEOFFSET` kolumny za pomocą LINQ do SQL, wymaga platformy .NET Framework 3.5 z dodatkiem SP1 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="185a7-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="185a7-107">SQL `DATETIMEOFFSET` kolumny jest dostępna w programie Microsoft SQL Server 2008 i poza tylko.</span><span class="sxs-lookup"><span data-stu-id="185a7-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="185a7-108">SQLMethods Data i godzina metody</span><span class="sxs-lookup"><span data-stu-id="185a7-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="185a7-109">Oprócz metod oferowane przez <xref:System.DateTimeOffset> struktury LINQ do SQL oferuje metody wymienione w poniższej tabeli z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> klasy do pracy z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="185a7-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="185a7-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="185a7-110">See Also</span></span>  
 [<span data-ttu-id="185a7-111">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="185a7-111">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="185a7-112">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="185a7-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="185a7-113">Mapowania typów środowiska SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="185a7-113">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
