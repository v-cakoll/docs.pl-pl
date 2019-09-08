---
title: System.DateTimeOffset Methods
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 2e29cf02d4f7e8004782264bf940bb1faf393269
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781547"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="db321-102">System.DateTimeOffset, metody</span><span class="sxs-lookup"><span data-stu-id="db321-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="db321-103">Po zmapowaniu w modelu obiektów lub zewnętrznym pliku mapowania LINQ to SQL umożliwia wywoływanie większości <xref:System.DateTimeOffset?displayProperty=nameWithType> metod, operatorów i właściwości z zapytań LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="db321-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="db321-104"><xref:System.Object?displayProperty=nameWithType> Jedyne metody nie są obsługiwane przez te, które nie mają sensu w kontekście zapytań LINQ to SQL, takich jak: `Finalize`, `GetHashCode`, `GetType`i `MemberwiseClone`.</span><span class="sxs-lookup"><span data-stu-id="db321-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="db321-105">Te metody nie są obsługiwane, ponieważ LINQ to SQL nie można ich przetłumaczyć na SQL Server.</span><span class="sxs-lookup"><span data-stu-id="db321-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db321-106">Struktura środowiska uruchomieniowego języka wspólnego ( <xref:System.DateTimeOffset?displayProperty=nameWithType> CLR) i możliwość mapowania jej do kolumny SQL `DATETIMEOFFSET` z LINQ to SQL wymaga .NET Framework 3,5 z dodatkiem SP1 lub nowszych.</span><span class="sxs-lookup"><span data-stu-id="db321-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="db321-107">Kolumna SQL `DATETIMEOFFSET` jest dostępna tylko w Microsoft SQL Server 2008 i poza nią.</span><span class="sxs-lookup"><span data-stu-id="db321-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="db321-108">Metody SqlMethods i Time</span><span class="sxs-lookup"><span data-stu-id="db321-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="db321-109">Oprócz metod oferowanych przez <xref:System.DateTimeOffset> strukturę LINQ to SQL oferują metody wymienione w poniższej tabeli <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> z klasy do pracy z datą i godziną.</span><span class="sxs-lookup"><span data-stu-id="db321-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="db321-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db321-110">See also</span></span>

- [<span data-ttu-id="db321-111">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="db321-111">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="db321-112">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="db321-112">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="db321-113">Mapowania typów środowiska SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="db321-113">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
