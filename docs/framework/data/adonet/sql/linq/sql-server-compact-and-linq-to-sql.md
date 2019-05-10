---
title: SQL Server Compact i LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: a0cb45b31f7134264068297f54013f49b35f669d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651201"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="e018b-102">SQL Server Compact i LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e018b-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="e018b-103">SQL Server Compact to domyślna baza danych zainstalowana za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e018b-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="e018b-104">Aby uzyskać więcej informacji, zobacz [przy użyciu programu SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span><span class="sxs-lookup"><span data-stu-id="e018b-104">For more information, see [Using SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="e018b-105">W tym temacie opisano podstawowe różnice w użycia, konfiguracji, zestawy funkcji i zakres [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="e018b-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="e018b-106">Właściwości programu SQL Server Compact w odniesieniu do programu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e018b-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="e018b-107">Domyślnie programu SQL Server Compact są zainstalowane dla wszystkich wersji programu Visual Studio i w związku z tym jest dostępny na komputerze deweloperskim do użytku z programem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e018b-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="e018b-108">Ale wdrożenia aplikacji, która używa programu SQL Server Compact i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] różni się od tego dla aplikacji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e018b-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="e018b-109">SQL Server Compact nie jest częścią programu .NET Framework i w związku z tym musi być pakowane razem z aplikacją lub pobrane oddzielnie z witryny Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e018b-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="e018b-110">Należy zwrócić uwagę następujących właściwości:</span><span class="sxs-lookup"><span data-stu-id="e018b-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="e018b-111">SQL Server Compact jest spakowany jako bibliotekę DLL, która może zostać użyty dla plików bazy danych (z rozszerzeniem sdf) bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="e018b-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="e018b-112">SQL Server Compact działa w tym samym procesie co aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="e018b-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="e018b-113">Wydajność komunikacji przy użyciu programu SQL Server Compact, dlatego może być znacznie wyższa niż podczas komunikowania się z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e018b-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="e018b-114">Z drugiej strony SQL Server Compact wymagają współdziałanie między kodem zarządzanym i niezarządzanym jego towarzyszącej kosztów.</span><span class="sxs-lookup"><span data-stu-id="e018b-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="e018b-115">Rozmiar programu SQL Server Compact biblioteki DLL jest mały.</span><span class="sxs-lookup"><span data-stu-id="e018b-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="e018b-116">Ta funkcja zmniejsza rozmiar cała aplikacja.</span><span class="sxs-lookup"><span data-stu-id="e018b-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="e018b-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Środowiska uruchomieniowego i narzędzie wiersza polecenia SQLMetal obsługi programu SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="e018b-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="e018b-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nie obsługuje programu SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="e018b-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="e018b-119">Zestaw funkcji</span><span class="sxs-lookup"><span data-stu-id="e018b-119">Feature Set</span></span>  
 <span data-ttu-id="e018b-120">SQL Server Compact zestaw funkcji jest znacznie prostsze niż zestaw funkcji programu SQL Server w następujący sposób, który może mieć wpływ na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji:</span><span class="sxs-lookup"><span data-stu-id="e018b-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="e018b-121">SQL Server Compact nie obsługuje procedur przechowywanych lub widoków.</span><span class="sxs-lookup"><span data-stu-id="e018b-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="e018b-122">SQL Server Compact obsługuje tylko podzbiór typów danych i funkcji SQL.</span><span class="sxs-lookup"><span data-stu-id="e018b-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="e018b-123">SQL Server Compact obsługuje tylko podzbiór konstrukcji SQL.</span><span class="sxs-lookup"><span data-stu-id="e018b-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="e018b-124">SQL Server Compact zawiera tylko minimalne optymalizatora.</span><span class="sxs-lookup"><span data-stu-id="e018b-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="e018b-125">Istnieje możliwość, że niektóre zapytania może upłynąć limit czasu.</span><span class="sxs-lookup"><span data-stu-id="e018b-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="e018b-126">SQL Server Compact nie obsługuje częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="e018b-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e018b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e018b-127">See also</span></span>

- [<span data-ttu-id="e018b-128">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="e018b-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
