---
title: Daty i godziny
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2bd9fa595281f7dfda50ef22914ccce7bf814a36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="date-and-time-data"></a><span data-ttu-id="5ede0-102">Daty i godziny</span><span class="sxs-lookup"><span data-stu-id="5ede0-102">Date and Time Data</span></span>
<span data-ttu-id="5ede0-103">SQL Server 2008 wprowadzono nowe typy danych obsługi informacji o datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="5ede0-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="5ede0-104">Nowe typy danych obejmują osobne typy daty i godziny i typy danych rozszerzonych z większego zakresu, dokładność i świadomości strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="5ede0-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="5ede0-105">Począwszy od wersji .NET Framework 3.5 z dodatkiem Service Pack (SP1), .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) zapewnia pełną obsługę wszystkich nowych funkcji aparatu bazy danych programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="5ede0-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="5ede0-106">.NET Framework 3.5 z dodatkiem SP1 należy zainstalować (lub nowsza) do użycia z SqlClient te nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="5ede0-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="5ede0-107">Wersje programu SQL Server starszych niż SQL Server 2008 ma tylko dwa typy danych do pracy z wartości daty i godziny: `datetime` i `smalldatetime`.</span><span class="sxs-lookup"><span data-stu-id="5ede0-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="5ede0-108">Oba typy danych zawierają zarówno wartość daty i czasu wartości, która utrudnia współpracować tylko datę lub tylko wartości czasu.</span><span class="sxs-lookup"><span data-stu-id="5ede0-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="5ede0-109">Ponadto te typy danych obsługują tylko daty, które występują po wprowadzeniu kalendarza gregoriańskiego w Anglii w 1753.</span><span class="sxs-lookup"><span data-stu-id="5ede0-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="5ede0-110">Innym ograniczeniem jest to, że te starsze typy danych nie są strefy czasowej wiedzieć, co utrudnia do pracy z danymi, które pochodzą z wielu strefach czasowych.</span><span class="sxs-lookup"><span data-stu-id="5ede0-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="5ede0-111">Pełną dokumentację dla typów danych programu SQL Server jest dostępny w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="5ede0-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="5ede0-112">W poniższej tabeli wymieniono klasy podstawowej tematy dotyczące określonej wersji dla danych daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="5ede0-113">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="5ede0-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="5ede0-114">Przy użyciu daty i godziny</span><span class="sxs-lookup"><span data-stu-id="5ede0-114">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="5ede0-115">Typy danych wprowadzonych w programie SQL Server 2008 daty/godziny</span><span class="sxs-lookup"><span data-stu-id="5ede0-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="5ede0-116">W poniższej tabeli opisano nowe typy danych daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="5ede0-117">Typ danych programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="5ede0-117">SQL Server data type</span></span>|<span data-ttu-id="5ede0-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5ede0-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="5ede0-119">`date` — Typ danych ma zakres 1 stycznia 01 do 31 grudnia 9999, z dokładnością do 1 dzień.</span><span class="sxs-lookup"><span data-stu-id="5ede0-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="5ede0-120">Wartość domyślna to 1 stycznia 1900.</span><span class="sxs-lookup"><span data-stu-id="5ede0-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="5ede0-121">Rozmiar magazynu jest 3 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5ede0-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="5ede0-122">`time` — Typ danych przechowuje wartości czasu, oparte na zegarze 24-godzinnym.</span><span class="sxs-lookup"><span data-stu-id="5ede0-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="5ede0-123">`time` Zakres 00:00:00.0000000 za pośrednictwem 23:59:59.9999999 z dokładnością 100 nanosekundach ma typ danych.</span><span class="sxs-lookup"><span data-stu-id="5ede0-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="5ede0-124">Wartość domyślna to 00:00:00.0000000 (północ).</span><span class="sxs-lookup"><span data-stu-id="5ede0-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="5ede0-125">`time` — Typ danych obsługuje zdefiniowane przez użytkownika dokładność ułamkowych części sekundy, i rozmiar magazynu zależą od 3 do 6 bajtów, oparte na dokładność określona.</span><span class="sxs-lookup"><span data-stu-id="5ede0-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="5ede0-126">`datetime2` — Typ danych łączy zakresu i dokładność `date` i `time` typy danych do jednego typu danych.</span><span class="sxs-lookup"><span data-stu-id="5ede0-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="5ede0-127">Domyślne wartości i formaty literału ciągu, są takie same jak te zdefiniowane `date` i `time` typy danych.</span><span class="sxs-lookup"><span data-stu-id="5ede0-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="5ede0-128">`datetimeoffset` Typ danych ma wszystkich funkcji `datetime2` z przesunięciem dodatkową strefę czasową.</span><span class="sxs-lookup"><span data-stu-id="5ede0-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="5ede0-129">Przesunięcie strefy czasowej jest reprezentowany jako [+ &#124;-] hh: mm.</span><span class="sxs-lookup"><span data-stu-id="5ede0-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="5ede0-130">HH to 2 cyfry od 00 do 14 reprezentować liczbę godzin w przesunięcia strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="5ede0-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="5ede0-131">MM to 2 cyfry od 00 do 59 reprezentować liczbę dodatkowych minut w przesunięcia strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="5ede0-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="5ede0-132">Do 100 nanosekundach są obsługiwane formaty czasu.</span><span class="sxs-lookup"><span data-stu-id="5ede0-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="5ede0-133">Obowiązkowe + lub - znak wskazuje, czy przesunięcie strefy czasowej jest dodane lub usunięte od czasu UTC (uniwersalny czas koordynować lub czas uniwersalny Greenwich) można uzyskać czasu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="5ede0-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5ede0-134">Aby uzyskać więcej informacji o korzystaniu z `Type System Version` — słowo kluczowe, zobacz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ede0-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="5ede0-135">Format daty i kolejność daty</span><span class="sxs-lookup"><span data-stu-id="5ede0-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="5ede0-136">Jak program SQL Server, analizuje wartości daty i godziny zależy nie tylko od wersji systemu i wersji serwera, ale także z serwera do domyślnych ustawień języka i formatu.</span><span class="sxs-lookup"><span data-stu-id="5ede0-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="5ede0-137">Ciąg daty, która działa w przypadku formatów daty z jednym języku mogą być nierozpoznawalną, jeśli zapytanie jest wykonywane za pomocą połączenia używającej innego języka i formatu daty ustawienie.</span><span class="sxs-lookup"><span data-stu-id="5ede0-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="5ede0-138">Instrukcja SET LANGUAGE języka Transact-SQL niejawnie ustawia DATEFORMAT, który określa kolejność części daty.</span><span class="sxs-lookup"><span data-stu-id="5ede0-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="5ede0-139">Instrukcja USTAWIĆ DATEFORMAT języka Transact-SQL połączenia służy do odróżniania przez zamawiania części daty w kolejności MDY, DMY, YMD, YDM, MYD lub DYM wartości daty.</span><span class="sxs-lookup"><span data-stu-id="5ede0-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="5ede0-140">Jeśli nie określisz DATEFORMAT dowolnego połączenia, program SQL Server używa domyślny język skojarzone z połączeniem.</span><span class="sxs-lookup"><span data-stu-id="5ede0-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="5ede0-141">Na przykład ciąg daty 03-01 "-02" może zostać zinterpretowany jako MDY (2 stycznia 2003) na serwerze z ustawieniem języka z językiem angielskim i jako DMY (1 lutego 2003) na serwerze z ustawieniem języka angielskiego.</span><span class="sxs-lookup"><span data-stu-id="5ede0-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="5ede0-142">Rok jest określany przy użyciu reguły rok odcięcia programu SQL Server, która definiuje Data progowa przypisywania wartości wieku.</span><span class="sxs-lookup"><span data-stu-id="5ede0-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="5ede0-143">Aby uzyskać więcej informacji, zobacz [opcję cyfrę dwuletnie odcięcia](http://go.microsoft.com/fwlink/?LinkId=120473) w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="5ede0-143">For more information, see [two digit year cutoff Option](http://go.microsoft.com/fwlink/?LinkId=120473) in SQL Server Books Online.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ede0-144">Format daty YDM nie jest obsługiwana podczas konwersji z formatu ciągu do `date`, `time`, `datetime2`, lub `datetimeoffset`.</span><span class="sxs-lookup"><span data-stu-id="5ede0-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="5ede0-145">Aby uzyskać więcej informacji na temat interpretowanie danych daty i godziny w programie SQL Server, zobacz [przy użyciu daty i godziny](http://go.microsoft.com/fwlink/?LinkID=98361) w dokumentacji SQL Server 2008 — książki Online.</span><span class="sxs-lookup"><span data-stu-id="5ede0-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](http://go.microsoft.com/fwlink/?LinkID=98361) in SQL Server 2008 Books Online.</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="5ede0-146">Data/Godzina danych typów i parametry</span><span class="sxs-lookup"><span data-stu-id="5ede0-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="5ede0-147">Można określić typu danych <xref:System.Data.SqlClient.SqlParameter> przy użyciu jednej z <xref:System.Data.SqlDbType> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5ede0-147">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the <xref:System.Data.SqlDbType> enumerations.</span></span> <span data-ttu-id="5ede0-148">Dodano następujące wyliczenia <xref:System.Data.SqlDbType> do obsługi nowych typów danych daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-148">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  
  
 <span data-ttu-id="5ede0-149">Można również określić typ <xref:System.Data.SqlClient.SqlParameter> objęty przez ustawienie <xref:System.Data.SqlClient.SqlParameter.DbType%2A> właściwość `SqlParameter` obiektu do określonego <xref:System.Data.DbType> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5ede0-149">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="5ede0-150">Dodano następujące wartości wyliczenia <xref:System.Data.DbType> do obsługi `datetime2` i `datetimeoffset` typy danych:</span><span class="sxs-lookup"><span data-stu-id="5ede0-150">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
-   <span data-ttu-id="5ede0-151">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="5ede0-151">DbType.DateTime2</span></span>  
  
-   <span data-ttu-id="5ede0-152">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="5ede0-152">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="5ede0-153">Te nowe wyliczenia uzupełnić `Date`, `Time`, i `DateTime` wyliczenia, które istniały w starszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ede0-153">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="5ede0-154">Typ dostawcy danych .NET Framework parametr obiektu jest wywnioskowany na podstawie typu .NET Framework wartości obiektu parameter lub z `DbType` obiektu parameter.</span><span class="sxs-lookup"><span data-stu-id="5ede0-154">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="5ede0-155">Żadna nowa <xref:System.Data.SqlTypes> typy danych zostały wprowadzone do obsługi nowych typów danych daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-155">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="5ede0-156">W poniższej tabeli opisano mapowania między datą programu SQL Server 2008 i typów danych i typów CLR.</span><span class="sxs-lookup"><span data-stu-id="5ede0-156">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="5ede0-157">Typ danych programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="5ede0-157">SQL Server data type</span></span>|<span data-ttu-id="5ede0-158">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5ede0-158">.NET Framework type</span></span>|<span data-ttu-id="5ede0-159">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="5ede0-159">System.Data.SqlDbType</span></span>|<span data-ttu-id="5ede0-160">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="5ede0-160">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="5ede0-161">Data</span><span class="sxs-lookup"><span data-stu-id="5ede0-161">date</span></span>|<span data-ttu-id="5ede0-162">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="5ede0-162">System.DateTime</span></span>|<span data-ttu-id="5ede0-163">Data</span><span class="sxs-lookup"><span data-stu-id="5ede0-163">Date</span></span>|<span data-ttu-id="5ede0-164">Data</span><span class="sxs-lookup"><span data-stu-id="5ede0-164">Date</span></span>|  
|<span data-ttu-id="5ede0-165">czas</span><span class="sxs-lookup"><span data-stu-id="5ede0-165">time</span></span>|<span data-ttu-id="5ede0-166">Obiekt System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="5ede0-166">System.TimeSpan</span></span>|<span data-ttu-id="5ede0-167">Godzina</span><span class="sxs-lookup"><span data-stu-id="5ede0-167">Time</span></span>|<span data-ttu-id="5ede0-168">Godzina</span><span class="sxs-lookup"><span data-stu-id="5ede0-168">Time</span></span>|  
|<span data-ttu-id="5ede0-169">datetime2</span><span class="sxs-lookup"><span data-stu-id="5ede0-169">datetime2</span></span>|<span data-ttu-id="5ede0-170">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="5ede0-170">System.DateTime</span></span>|<span data-ttu-id="5ede0-171">DateTime2</span><span class="sxs-lookup"><span data-stu-id="5ede0-171">DateTime2</span></span>|<span data-ttu-id="5ede0-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="5ede0-172">DateTime2</span></span>|  
|<span data-ttu-id="5ede0-173">Datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="5ede0-173">datetimeoffset</span></span>|<span data-ttu-id="5ede0-174">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="5ede0-174">System.DateTimeOffset</span></span>|<span data-ttu-id="5ede0-175">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="5ede0-175">DateTimeOffset</span></span>|<span data-ttu-id="5ede0-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="5ede0-176">DateTimeOffset</span></span>|  
|<span data-ttu-id="5ede0-177">datetime</span><span class="sxs-lookup"><span data-stu-id="5ede0-177">datetime</span></span>|<span data-ttu-id="5ede0-178">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="5ede0-178">System.DateTime</span></span>|<span data-ttu-id="5ede0-179">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="5ede0-179">DateTime</span></span>|<span data-ttu-id="5ede0-180">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="5ede0-180">DateTime</span></span>|  
|<span data-ttu-id="5ede0-181">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="5ede0-181">smalldatetime</span></span>|<span data-ttu-id="5ede0-182">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="5ede0-182">System.DateTime</span></span>|<span data-ttu-id="5ede0-183">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="5ede0-183">DateTime</span></span>|<span data-ttu-id="5ede0-184">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="5ede0-184">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="5ede0-185">Właściwości SqlParameter</span><span class="sxs-lookup"><span data-stu-id="5ede0-185">SqlParameter Properties</span></span>  
 <span data-ttu-id="5ede0-186">W poniższej tabeli opisano `SqlParameter` właściwości, które mają zastosowanie do typów danych daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-186">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="5ede0-187">Właściwość</span><span class="sxs-lookup"><span data-stu-id="5ede0-187">Property</span></span>|<span data-ttu-id="5ede0-188">Opis</span><span class="sxs-lookup"><span data-stu-id="5ede0-188">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="5ede0-189">Pobiera lub ustawia, czy wartość jest wartością null.</span><span class="sxs-lookup"><span data-stu-id="5ede0-189">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="5ede0-190">Wartość null parametru są wysyłane do serwera, należy określić <xref:System.DBNull>, a nie `null` (`Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5ede0-190">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="5ede0-191">Aby uzyskać więcej informacji o wartości null bazy danych, zobacz [Obsługa wartości zerowych](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span><span class="sxs-lookup"><span data-stu-id="5ede0-191">For more information about database nulls, see [Handling Null Values](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="5ede0-192">Pobiera lub ustawia maksymalną liczbę cyfr używana do reprezentowania wartości.</span><span class="sxs-lookup"><span data-stu-id="5ede0-192">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="5ede0-193">To ustawienie jest ignorowane w przypadku typów danych daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-193">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="5ede0-194">Pobiera lub ustawia liczbę miejsc dziesiętnych, do których został rozwiązany dla części wartość `Time`, `DateTime2`, i `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="5ede0-194">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="5ede0-195">Wartość domyślna to 0, co oznacza, że rzeczywista skali jest wywnioskowany na podstawie wartości i wysłane do serwera.</span><span class="sxs-lookup"><span data-stu-id="5ede0-195">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="5ede0-196">Ignorowane dla typów danych daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-196">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="5ede0-197">Pobiera lub ustawia wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="5ede0-197">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="5ede0-198">Pobiera lub ustawia wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="5ede0-198">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5ede0-199">Wartości czasu jest większa niż zero lub większa niż 24 godziny zgłosi <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="5ede0-199">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="5ede0-200">Tworzenie parametrów</span><span class="sxs-lookup"><span data-stu-id="5ede0-200">Creating Parameters</span></span>  
 <span data-ttu-id="5ede0-201">Można utworzyć <xref:System.Data.SqlClient.SqlParameter> obiektu za pomocą jego konstruktora lub dodając go do <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji, wywołując `Add` metody <xref:System.Data.SqlClient.SqlParameterCollection>.</span><span class="sxs-lookup"><span data-stu-id="5ede0-201">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="5ede0-202">`Add` Metoda będzie przyjmować jako danych wejściowych w argumentach konstruktora lub istniejący obiekt parametru.</span><span class="sxs-lookup"><span data-stu-id="5ede0-202">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="5ede0-203">Następnej części tego tematu zawierają przykłady sposobu określania parametrów daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-203">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="5ede0-204">Dodatkowe przykłady pracy z parametrów, zobacz [konfigurowania parametrów i typ danych parametru](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) i [parametry element DataAdapter](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5ede0-204">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="5ede0-205">Przykład daty</span><span class="sxs-lookup"><span data-stu-id="5ede0-205">Date Example</span></span>  
 <span data-ttu-id="5ede0-206">Poniższy fragment kodu przedstawia sposób określić `date` parametru.</span><span class="sxs-lookup"><span data-stu-id="5ede0-206">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a><span data-ttu-id="5ede0-207">Przykład czasu</span><span class="sxs-lookup"><span data-stu-id="5ede0-207">Time Example</span></span>  
 <span data-ttu-id="5ede0-208">Poniższy fragment kodu przedstawia sposób określić `time` parametru.</span><span class="sxs-lookup"><span data-stu-id="5ede0-208">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a><span data-ttu-id="5ede0-209">Przykład Datetime2</span><span class="sxs-lookup"><span data-stu-id="5ede0-209">Datetime2 Example</span></span>  
 <span data-ttu-id="5ede0-210">Poniższy fragment kodu przedstawia sposób określić `datetime2` parametru z częściami datę i godzinę.</span><span class="sxs-lookup"><span data-stu-id="5ede0-210">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="5ede0-211">Przykład DateTimeOffSet</span><span class="sxs-lookup"><span data-stu-id="5ede0-211">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="5ede0-212">Poniższy fragment kodu przedstawia sposób określić `DateTimeOffSet` parametru datę, godzinę i przesunięcie strefy czasowej 0.</span><span class="sxs-lookup"><span data-stu-id="5ede0-212">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a><span data-ttu-id="5ede0-213">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="5ede0-213">AddWithValue</span></span>  
 <span data-ttu-id="5ede0-214">Może też podawać parametrów przy użyciu `AddWithValue` metody <xref:System.Data.SqlClient.SqlCommand>, jak pokazano w następującego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="5ede0-214">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="5ede0-215">Jednak `AddWithValue` — metoda nie umożliwiają określenie <xref:System.Data.SqlClient.SqlParameter.DbType%2A> lub <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> dla parametru.</span><span class="sxs-lookup"><span data-stu-id="5ede0-215">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="5ede0-216">`@date` Parametru może mapować na `date`, `datetime`, lub `datetime2` typu danych na serwerze.</span><span class="sxs-lookup"><span data-stu-id="5ede0-216">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="5ede0-217">Podczas pracy z nowym `datetime` typy danych, musisz jawnie ustawić parametr <xref:System.Data.SqlDbType> właściwości na typ danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5ede0-217">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="5ede0-218">Przy użyciu <xref:System.Data.SqlDbType.Variant> lub niejawnie podawania wartości parametrów może spowodować problemy z zgodności z poprzednimi wersjami `datetime` i `smalldatetime` typy danych.</span><span class="sxs-lookup"><span data-stu-id="5ede0-218">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="5ede0-219">W poniższej tabeli przedstawiono, które `SqlDbTypes` są wywnioskować na podstawie typy CLR:</span><span class="sxs-lookup"><span data-stu-id="5ede0-219">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="5ede0-220">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="5ede0-220">CLR type</span></span>|<span data-ttu-id="5ede0-221">Wywnioskowane SqlDbType</span><span class="sxs-lookup"><span data-stu-id="5ede0-221">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="5ede0-222">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="5ede0-222">DateTime</span></span>|<span data-ttu-id="5ede0-223">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="5ede0-223">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="5ede0-224">Zakres czasu</span><span class="sxs-lookup"><span data-stu-id="5ede0-224">TimeSpan</span></span>|<span data-ttu-id="5ede0-225">Elementu SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="5ede0-225">SqlDbType.Time</span></span>|  
|<span data-ttu-id="5ede0-226">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="5ede0-226">DateTimeOffset</span></span>|<span data-ttu-id="5ede0-227">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="5ede0-227">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="5ede0-228">Podczas pobierania daty i godziny</span><span class="sxs-lookup"><span data-stu-id="5ede0-228">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="5ede0-229">W poniższej tabeli opisano metody, które są używane do pobierania wartości daty i godziny programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="5ede0-229">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="5ede0-230">SqlClient — metoda</span><span class="sxs-lookup"><span data-stu-id="5ede0-230">SqlClient method</span></span>|<span data-ttu-id="5ede0-231">Opis</span><span class="sxs-lookup"><span data-stu-id="5ede0-231">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="5ede0-232">Pobiera wartość określonej kolumny jako <xref:System.DateTime> struktury.</span><span class="sxs-lookup"><span data-stu-id="5ede0-232">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="5ede0-233">Pobiera wartość określonej kolumny jako <xref:System.DateTimeOffset> struktury.</span><span class="sxs-lookup"><span data-stu-id="5ede0-233">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="5ede0-234">Zwraca typ, który jest typem podstawowym specyficznych dla dostawcy dla pola.</span><span class="sxs-lookup"><span data-stu-id="5ede0-234">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="5ede0-235">Zwraca te same typy jako `GetFieldType` dla nowych typów daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-235">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="5ede0-236">Pobiera wartość określonej kolumny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-236">Retrieves the value of the specified column.</span></span> <span data-ttu-id="5ede0-237">Zwraca te same typy jako `GetValue` dla nowych typów daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-237">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="5ede0-238">Pobiera wartości w określonej tablicy.</span><span class="sxs-lookup"><span data-stu-id="5ede0-238">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="5ede0-239">Pobiera wartość kolumny jako <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="5ede0-239">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="5ede0-240"><xref:System.InvalidCastException> Występuje, gdy dane nie może być wyrażona jako `SqlString`.</span><span class="sxs-lookup"><span data-stu-id="5ede0-240">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="5ede0-241">Pobiera dane w kolumnie jako jego domyślny `SqlDbType`.</span><span class="sxs-lookup"><span data-stu-id="5ede0-241">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="5ede0-242">Zwraca te same typy jako `GetValue` dla nowych typów daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-242">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="5ede0-243">Pobiera wartości w określonej tablicy.</span><span class="sxs-lookup"><span data-stu-id="5ede0-243">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="5ede0-244">Pobiera wartość kolumny jako ciąg, jeśli ustawiono typ wersji systemu do wersji SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="5ede0-244">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="5ede0-245"><xref:System.InvalidCastException> Występuje, gdy dane nie może być wyrażona jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="5ede0-245">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="5ede0-246">Pobiera wartość określonej kolumny jako <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="5ede0-246">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="5ede0-247">Pobiera wartość określonej kolumny jako jego podstawowy typ CLR.</span><span class="sxs-lookup"><span data-stu-id="5ede0-247">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="5ede0-248">Pobiera wartości w kolumnie w tablicy.</span><span class="sxs-lookup"><span data-stu-id="5ede0-248">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="5ede0-249">Zwraca <xref:System.Data.DataTable> opisujący metadanych zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="5ede0-249">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5ede0-250">Nowa data i godzina `SqlDbTypes` nie są obsługiwane dla kodu, który jest wykonywany w trakcie w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ede0-250">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="5ede0-251">Wystąpił wyjątek zostanie wygenerowany, jeśli jeden z tych typów są przekazywane do serwera.</span><span class="sxs-lookup"><span data-stu-id="5ede0-251">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="5ede0-252">Określanie wartości daty i godziny jako literały</span><span class="sxs-lookup"><span data-stu-id="5ede0-252">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="5ede0-253">Można określić typy danych daty i godziny przy użyciu różnych formatach inny ciąg literału, programem SQL Server, następnie oblicza w czasie wykonywania, ich konwersji do struktur wewnętrznych daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="5ede0-253">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="5ede0-254">SQL Server rozpoznaje danych daty i godziny, która jest ujęta w znaki apostrofu (').</span><span class="sxs-lookup"><span data-stu-id="5ede0-254">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="5ede0-255">W poniższych przykładach pokazano niektóre formaty:</span><span class="sxs-lookup"><span data-stu-id="5ede0-255">The following examples demonstrate some formats:</span></span>  
  
-   <span data-ttu-id="5ede0-256">Formatuje alfabetyczne Data, takich jak `'October 15, 2006'`.</span><span class="sxs-lookup"><span data-stu-id="5ede0-256">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
-   <span data-ttu-id="5ede0-257">Formatuje liczbowego Data, takich jak `'10/15/2006'`.</span><span class="sxs-lookup"><span data-stu-id="5ede0-257">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
-   <span data-ttu-id="5ede0-258">Nieoddzielone formaty ciągu, takich jak `'20061015'`, który zostanie zinterpretowany jako 15 października 2006 korzystania z formatu daty standardowe ISO.</span><span class="sxs-lookup"><span data-stu-id="5ede0-258">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ede0-259">Pełną dokumentację można znaleźć wszystkie formaty literału ciągu i inne funkcje typów danych daty i godziny w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="5ede0-259">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="5ede0-260">Wartości czasu jest większa niż zero lub większa niż 24 godziny zgłosi <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="5ede0-260">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-2008-books-online"></a><span data-ttu-id="5ede0-261">Zasoby programu SQL Server 2008 — książki Online</span><span class="sxs-lookup"><span data-stu-id="5ede0-261">Resources in SQL Server 2008 Books Online</span></span>  
 <span data-ttu-id="5ede0-262">Aby uzyskać więcej informacji na temat pracy z wartości daty i godziny w programie SQL Server 2008 zobacz następujące zasoby w programie SQL Server 2008 — książki Online.</span><span class="sxs-lookup"><span data-stu-id="5ede0-262">For more information about working with date and time values in SQL Server 2008, see the following resources in SQL Server 2008 Books Online.</span></span>  
  
|<span data-ttu-id="5ede0-263">Temat</span><span class="sxs-lookup"><span data-stu-id="5ede0-263">Topic</span></span>|<span data-ttu-id="5ede0-264">Opis</span><span class="sxs-lookup"><span data-stu-id="5ede0-264">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5ede0-265">Daty i godziny typy i funkcje (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5ede0-265">Date and Time Data Types and Functions (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98360)|<span data-ttu-id="5ede0-266">Zawiera omówienie Data języka Transact-SQL i typów danych i funkcji.</span><span class="sxs-lookup"><span data-stu-id="5ede0-266">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|[<span data-ttu-id="5ede0-267">Przy użyciu daty i godziny</span><span class="sxs-lookup"><span data-stu-id="5ede0-267">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkId=98361)|<span data-ttu-id="5ede0-268">Informacje na temat typów danych daty i godziny i funkcje i przykłady ich użycia.</span><span class="sxs-lookup"><span data-stu-id="5ede0-268">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="5ede0-269">Typy danych (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="5ede0-269">Data Types (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98362)|<span data-ttu-id="5ede0-270">Zawiera opis typów danych w programie SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="5ede0-270">Describes system data types in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ede0-271">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ede0-271">See Also</span></span>  
 [<span data-ttu-id="5ede0-272">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="5ede0-272">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="5ede0-273">Konfigurowanie parametrów i typów danych parametrów</span><span class="sxs-lookup"><span data-stu-id="5ede0-273">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="5ede0-274">Danych programu SQL Server typy i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5ede0-274">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="5ede0-275">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="5ede0-275">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
