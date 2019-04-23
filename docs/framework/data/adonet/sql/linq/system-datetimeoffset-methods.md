---
title: System.DateTimeOffset Methods
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 288a0d99feecdeccc0d215ec3c14ec31bb3ccb54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149724"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="195f8-102">System.DateTimeOffset, metody</span><span class="sxs-lookup"><span data-stu-id="195f8-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="195f8-103">Gdy mapowane w modelu obiektu lub pliku mapowania zewnętrznych, LINQ to SQL pozwala wywoływać większość <xref:System.DateTimeOffset?displayProperty=nameWithType> metody, operatorów i właściwości z LINQ do zapytań SQL.</span><span class="sxs-lookup"><span data-stu-id="195f8-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="195f8-104">Jedyne metody, które nie są obsługiwane są te odziedziczone z <xref:System.Object?displayProperty=nameWithType> , nie mają sensu w kontekście LINQ do zapytań SQL, takich jak: `Finalize`, `GetHashCode`, `GetType`, i `MemberwiseClone`.</span><span class="sxs-lookup"><span data-stu-id="195f8-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="195f8-105">Te metody nie są obsługiwane, ponieważ LINQ to SQL nie może ich tłumaczyć do wykonania w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="195f8-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="195f8-106">Środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> struktury i możliwości w celu zamapowania go do bazy danych SQL `DATETIMEOFFSET` kolumny za pomocą LINQ to SQL, wymaga platformy .NET Framework 3.5 z dodatkiem SP1 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="195f8-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="195f8-107">SQL `DATETIMEOFFSET` kolumny dostępną tylko w programie Microsoft SQL Server 2008 i nie tylko.</span><span class="sxs-lookup"><span data-stu-id="195f8-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="195f8-108">SQLMethods daty i godziny metody</span><span class="sxs-lookup"><span data-stu-id="195f8-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="195f8-109">Oprócz metod oferowane przez <xref:System.DateTimeOffset> struktury, LINQ to SQL oferuje metody wymienione w poniższej tabeli z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> klasy do pracy z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="195f8-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="195f8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="195f8-110">See also</span></span>

- [<span data-ttu-id="195f8-111">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="195f8-111">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="195f8-112">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="195f8-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="195f8-113">Mapowania typów środowiska SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="195f8-113">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
