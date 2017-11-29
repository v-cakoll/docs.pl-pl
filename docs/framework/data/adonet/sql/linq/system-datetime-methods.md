---
title: Metody System.DateTime
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e4923be2b9e083129c58d042b1ad3e21897c0346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="2afc8-102">Metody System.DateTime</span><span class="sxs-lookup"><span data-stu-id="2afc8-102">System.DateTime Methods</span></span>
<span data-ttu-id="2afc8-103">Następujące LINQ do operatorów, właściwości i metod obsługiwanych przez program SQL są dostępne do użycia w składniku LINQ do SQL zapytań.</span><span class="sxs-lookup"><span data-stu-id="2afc8-103">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="2afc8-104">Gdy metoda, operator lub właściwość nie jest obsługiwany, LINQ do SQL nie może dokonywać translacji elementu członkowskiego do wykonania na serwerze SQL.</span><span class="sxs-lookup"><span data-stu-id="2afc8-104">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="2afc8-105">Możesz użyć tych elementów członkowskich w kodzie, jednak ich musi przyjąć przed zapytania jest translacja języka Transact-SQL lub po wyniki zostały pobrane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2afc8-105">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="2afc8-106">Elementy członkowskie System.DateTime obsługiwane</span><span class="sxs-lookup"><span data-stu-id="2afc8-106">Supported System.DateTime Members</span></span>  
 <span data-ttu-id="2afc8-107">Zmapowaniu w modelu obiektu lub plik mapowania zewnętrznych LINQ do SQL pozwala wywoływać następujące <xref:System.DateTime?displayProperty=nameWithType> członków wewnątrz LINQ do zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="2afc8-107">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="2afc8-108">Obsługiwane <xref:System.DateTime> metody</span><span class="sxs-lookup"><span data-stu-id="2afc8-108">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="2afc8-109">Obsługiwane <xref:System.DateTime> operatory</span><span class="sxs-lookup"><span data-stu-id="2afc8-109">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="2afc8-110">Obsługiwane <xref:System.DateTime> właściwości</span><span class="sxs-lookup"><span data-stu-id="2afc8-110">Supported <xref:System.DateTime> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="2afc8-111">Elementy członkowskie nie jest obsługiwana w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2afc8-111">Members Not Supported by LINQ to SQL</span></span>  
 <span data-ttu-id="2afc8-112">Następujące elementy członkowskie nie są obsługiwane wewnątrz LINQ do zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="2afc8-112">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a><span data-ttu-id="2afc8-113">Przykład translatora — metoda</span><span class="sxs-lookup"><span data-stu-id="2afc8-113">Method Translation Example</span></span>  
 <span data-ttu-id="2afc8-114">Wszystkie metody obsługiwania w składniku LINQ to SQL są tłumaczone na języka Transact-SQL, przed ich wysłaniem do serwera SQL.</span><span class="sxs-lookup"><span data-stu-id="2afc8-114">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="2afc8-115">Rozważmy na przykład następującego wzorca.</span><span class="sxs-lookup"><span data-stu-id="2afc8-115">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="2afc8-116">Gdy uznaje się jest przetłumaczyć bezpośrednie połączenie z programem SQL Server `DATEDIFF` działają w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2afc8-116">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="2afc8-117">SQLMethods Data i godzina metody</span><span class="sxs-lookup"><span data-stu-id="2afc8-117">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="2afc8-118">Oprócz metod oferowane przez <xref:System.DateTime> struktury LINQ do SQL oferuje metody wymienione w poniższej tabeli z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> klasy do pracy z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="2afc8-118">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="2afc8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2afc8-119">See Also</span></span>  
 [<span data-ttu-id="2afc8-120">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="2afc8-120">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="2afc8-121">Tworzenie modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="2afc8-121">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="2afc8-122">Mapowanie typu środowiska CLR SQL</span><span class="sxs-lookup"><span data-stu-id="2afc8-122">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="2afc8-123">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="2afc8-123">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
