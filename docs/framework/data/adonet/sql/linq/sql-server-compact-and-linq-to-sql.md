---
title: SQL Server Compact i LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792536"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="e1ee7-102">SQL Server Compact i LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e1ee7-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="e1ee7-103">SQL Server Compact jest domyślną bazą danych zainstalowaną z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="e1ee7-104">Aby uzyskać więcej informacji, zobacz [używanie SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="e1ee7-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="e1ee7-105">W tym temacie omówiono kluczowe różnice w zakresie użycia, konfiguracji, zestawów funkcji i zakresu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="e1ee7-106">Charakterystyka SQL Server Compact w odniesieniu do LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e1ee7-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="e1ee7-107">Domyślnie program SQL Server Compact jest instalowany dla wszystkich wersji programu Visual Studio i dlatego jest dostępny na komputerze deweloperskim do użytku z programem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e1ee7-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="e1ee7-108">Ale wdrożenie aplikacji, która używa SQL Server Compact i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] różni się od tej dla aplikacji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="e1ee7-109">SQL Server Compact nie jest częścią .NET Framework i dlatego musi być spakowana z aplikacją lub pobierana oddzielnie z witryny firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="e1ee7-110">Należy pamiętać o następujących cechach:</span><span class="sxs-lookup"><span data-stu-id="e1ee7-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="e1ee7-111">SQL Server Compact jest spakowany jako biblioteka DLL, która może być używana bezpośrednio dla plików bazy danych (rozszerzenie SDF).</span><span class="sxs-lookup"><span data-stu-id="e1ee7-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="e1ee7-112">SQL Server Compact uruchamiane w tym samym procesie co aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="e1ee7-113">W związku z tym wydajność komunikacji z SQL Server Compactami może być znacznie wyższa niż komunikacja z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="e1ee7-114">Z drugiej strony, SQL Server Compact wymaga współdziałania między kodem zarządzanym i niezarządzanym z kosztami towarzyszącymi.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="e1ee7-115">Rozmiar biblioteki DLL SQL Server Compact jest mały.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="e1ee7-116">Ta funkcja zmniejsza całkowity rozmiar aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="e1ee7-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Środowisko uruchomieniowe i narzędzie wiersza polecenia SQLMetal SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="e1ee7-118">Object Relational Designer nie obsługuje SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-118">The Object Relational Designer does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="e1ee7-119">Zestaw funkcji</span><span class="sxs-lookup"><span data-stu-id="e1ee7-119">Feature Set</span></span>  
 <span data-ttu-id="e1ee7-120">Zestaw funkcji SQL Server Compact jest znacznie prostszy niż zestaw funkcji SQL Server w następujących sposobach, które mogą mieć wpływ na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacje:</span><span class="sxs-lookup"><span data-stu-id="e1ee7-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="e1ee7-121">SQL Server Compact nie obsługuje procedur ani widoków składowanych.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="e1ee7-122">SQL Server Compact obsługuje tylko podzbiór typów danych i funkcji SQL.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="e1ee7-123">SQL Server Compact obsługuje tylko podzestaw konstrukcji SQL.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="e1ee7-124">SQL Server Compact zapewnia tylko minimalny optymalizator.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="e1ee7-125">Istnieje możliwość, że niektóre zapytania mogą przekroczyć limit czasu.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="e1ee7-126">SQL Server Compact nie obsługuje częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="e1ee7-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ee7-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1ee7-127">See also</span></span>

- [<span data-ttu-id="e1ee7-128">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="e1ee7-128">Reference</span></span>](reference.md)
