---
title: System.TimeSpan Methods
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: baec7609ce1d2f04b1c24165c53bc7cce425f06d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="systemtimespan-methods"></a><span data-ttu-id="fd265-102">System.TimeSpan Methods</span><span class="sxs-lookup"><span data-stu-id="fd265-102">System.TimeSpan Methods</span></span>
<span data-ttu-id="fd265-103">Obsługa elementu członkowskiego <xref:System.TimeSpan?displayProperty=nameWithType> zależy od wersji programu .NET Framework i program Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fd265-103">Member support for <xref:System.TimeSpan?displayProperty=nameWithType> greatly depends on the versions of the .NET Framework and Microsoft SQL Server that you are using.</span></span>  
  
 <span data-ttu-id="fd265-104">Gdy metoda, operator lub właściwość nie jest obsługiwany; oznacza to, że LINQ do SQL nie może dokonywać translacji elementu członkowskiego do wykonania na serwerze SQL.</span><span class="sxs-lookup"><span data-stu-id="fd265-104">When a method, operator, or property is unsupported; it means that LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="fd265-105">Można nadal używać tych elementów członkowskich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fd265-105">You may still be able to use these members in your code.</span></span> <span data-ttu-id="fd265-106">Jednak ich musi przyjąć przed zapytania jest translacja języka Transact-SQL lub po wyniki zostały pobrane z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fd265-106">However, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="previous-limitations"></a><span data-ttu-id="fd265-107">Ograniczenia poprzedniej</span><span class="sxs-lookup"><span data-stu-id="fd265-107">Previous Limitations</span></span>  
 <span data-ttu-id="fd265-108">Podczas korzystania z LINQ do SQL z wersji programu .NET Framework, przed programu .NET Framework 3.5 z dodatkiem SP1, nie możesz mapować pola bazy danych programu SQL Server do <xref:System.TimeSpan?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd265-108">When using LINQ to SQL with versions of the .NET Framework prior to .NET Framework 3.5 SP1, you cannot map SQL Server database fields to <xref:System.TimeSpan?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fd265-109">Jednak operacje na <xref:System.TimeSpan> są obsługiwane, ponieważ <xref:System.TimeSpan> może zwracać wartości <xref:System.DateTime> odejmowania lub wprowadzane jako zmienną literału lub powiązane wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fd265-109">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
## <a name="supported-systemtimespan-method-support"></a><span data-ttu-id="fd265-110">Obsługiwana metoda System.TimeSpan pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="fd265-110">Supported System.TimeSpan Method Support</span></span>  
 <span data-ttu-id="fd265-111">Następujące LINQ do operatorów, właściwości i metod obsługiwanych przez program SQL są dostępne do użycia w Twojej LINQ do zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="fd265-111">The following LINQ to SQL-supported methods, operators, and properties are available for you to use in your LINQ to SQL queries.</span></span> <span data-ttu-id="fd265-112">Zmapowaniu w modelu obiektu lub plik mapowania zewnętrznych LINQ do SQL pozwala wywoływać wiele <xref:System.TimeSpan?displayProperty=nameWithType> członków wewnątrz programu LINQ do zapytania SQL.</span><span class="sxs-lookup"><span data-stu-id="fd265-112">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call many of the <xref:System.TimeSpan?displayProperty=nameWithType> members inside your LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="fd265-113">Obsługiwane <xref:System.TimeSpan> metody</span><span class="sxs-lookup"><span data-stu-id="fd265-113">Supported <xref:System.TimeSpan> Methods</span></span>|<span data-ttu-id="fd265-114">Obsługiwane <xref:System.TimeSpan> operatory</span><span class="sxs-lookup"><span data-stu-id="fd265-114">Supported <xref:System.TimeSpan> Operators</span></span>|<span data-ttu-id="fd265-115">Obsługiwane <xref:System.TimeSpan> właściwości</span><span class="sxs-lookup"><span data-stu-id="fd265-115">Supported <xref:System.TimeSpan> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<!--zz <xref:System.TimeSpan.MinValue%2A>-->|  
  
> [!NOTE]
>  <span data-ttu-id="fd265-116">Możliwość mapowania <xref:System.TimeSpan?displayProperty=nameWithType> SQL `TIME` kolumny za pomocą LINQ do SQL wymaga platformy .NET Framework 3.5 SP1 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="fd265-116">The ability to map <xref:System.TimeSpan?displayProperty=nameWithType> to a SQL `TIME` column with LINQ to SQL requires the .NET Framework 3.5 SP1 and beyond.</span></span> <span data-ttu-id="fd265-117">SQL `TIME` — typ danych jest dostępna w programie Microsoft SQL Server 2008 i poza tylko.</span><span class="sxs-lookup"><span data-stu-id="fd265-117">The SQL `TIME` data type is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
### <a name="addition-and-subtraction"></a><span data-ttu-id="fd265-118">Dodawanie i odejmowanie</span><span class="sxs-lookup"><span data-stu-id="fd265-118">Addition and Subtraction</span></span>  
 <span data-ttu-id="fd265-119">Mimo że środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> typ obsługuje dodawanie i odejmowanie, SQL `TIME` nie ma typu.</span><span class="sxs-lookup"><span data-stu-id="fd265-119">Although the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type does support addition and subtraction, the SQL `TIME` type does not.</span></span> <span data-ttu-id="fd265-120">W związku z tym programu LINQ kwerendy SQL będzie generować błędy, jeśli próbują dodawania i odejmowania gdy są one mapowane na SQL `TIME` typu.</span><span class="sxs-lookup"><span data-stu-id="fd265-120">Because of this, your LINQ to SQL queries will generate errors if they attempt addition and subtraction when they are mapped to the SQL `TIME` type.</span></span> <span data-ttu-id="fd265-121">Inne uwagi dotyczące pracy z typami daty i godziny w SQL można znaleźć [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="fd265-121">You can find other considerations for working with SQL date and time types in [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd265-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd265-122">See Also</span></span>  
 [<span data-ttu-id="fd265-123">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="fd265-123">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="fd265-124">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="fd265-124">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="fd265-125">Mapowania typów środowiska SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="fd265-125">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="fd265-126">Typy danych i funkcje</span><span class="sxs-lookup"><span data-stu-id="fd265-126">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
