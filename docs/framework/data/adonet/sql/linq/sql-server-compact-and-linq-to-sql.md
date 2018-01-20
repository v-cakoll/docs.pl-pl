---
title: SQL Server Compact i LINQ do SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 24f620319cd469538cf4454be7caffececdf9213
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="1da96-102">SQL Server Compact i LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="1da96-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="1da96-103">SQL Server Compact to domyślna baza danych zainstalowana z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1da96-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="1da96-104">Aby uzyskać więcej informacji, zobacz [Pave – za pośrednictwem przy użyciu programu SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).</span><span class="sxs-lookup"><span data-stu-id="1da96-104">For more information, see [PAVE OVER Using SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).</span></span>  
  
 <span data-ttu-id="1da96-105">W tym temacie przedstawiono podstawowe różnice w użycia, konfiguracji, zestawy funkcji i zakres [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje.</span><span class="sxs-lookup"><span data-stu-id="1da96-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="1da96-106">Właściwości programu SQL Server Compact w odniesieniu do LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="1da96-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="1da96-107">Domyślnie program SQL Server Compact są instalowane dla wszystkich [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] wersje i w związku z tym jest dostępny na komputerze dewelopera do użycia z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1da96-107">By default, SQL Server Compact is installed for all [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="1da96-108">Wdrażanie aplikacji, która używa programu SQL Server Compact, ale i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] różni się od dla [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1da96-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] application.</span></span> <span data-ttu-id="1da96-109">SQL Server Compact nie jest częścią programu .NET Framework i w związku z tym musi być z aplikacji lub oddzielnie pobrane z witryny Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1da96-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="1da96-110">Należy uwzględnić następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="1da96-110">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="1da96-111">SQL Server Compact, jest dostarczana jako bibliotekę DLL, która może służyć do atakowania pliki bazy danych (z rozszerzeniem sdf) bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="1da96-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
-   <span data-ttu-id="1da96-112">SQL Server Compact działa w ten sam proces jako aplikacja klienta.</span><span class="sxs-lookup"><span data-stu-id="1da96-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="1da96-113">W związku z tym wydajność komunikacji z programu SQL Server Compact może być znacznie wyższa niż komunikowania się z [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1da96-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1da96-114">Z drugiej strony programu SQL Server Compact wymagają współdziałanie zarządzane i niezarządzane kodu przy użyciu jego koszty związane.</span><span class="sxs-lookup"><span data-stu-id="1da96-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
-   <span data-ttu-id="1da96-115">Rozmiar programu SQL Server Compact biblioteki DLL jest mała.</span><span class="sxs-lookup"><span data-stu-id="1da96-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="1da96-116">Ta funkcja pozwala zmniejszyć rozmiar ogólną aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1da96-116">This feature reduces the overall application size.</span></span>  
  
-   <span data-ttu-id="1da96-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Środowiska uruchomieniowego i narzędzie wiersza polecenia SQLMetal obsługuje program SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="1da96-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
-   <span data-ttu-id="1da96-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nie obsługuje programu SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="1da96-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="1da96-119">Zestaw funkcji</span><span class="sxs-lookup"><span data-stu-id="1da96-119">Feature Set</span></span>  
 <span data-ttu-id="1da96-120">SQL Server Compact zestaw funkcji jest znacznie prostsze niż zestaw funkcji [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] w następujący sposób, który może mieć wpływ na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji:</span><span class="sxs-lookup"><span data-stu-id="1da96-120">The SQL Server Compact feature set is much simpler than the feature set of [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
-   <span data-ttu-id="1da96-121">SQL Server Compact nie obsługuje procedur składowanych ani widoków.</span><span class="sxs-lookup"><span data-stu-id="1da96-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
-   <span data-ttu-id="1da96-122">SQL Server Compact obsługuje tylko typy danych i funkcji SQL.</span><span class="sxs-lookup"><span data-stu-id="1da96-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
-   <span data-ttu-id="1da96-123">SQL Server Compact obsługuje tylko podzestaw konstrukcji SQL.</span><span class="sxs-lookup"><span data-stu-id="1da96-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
-   <span data-ttu-id="1da96-124">SQL Server Compact zawiera tylko minimalne optymalizację.</span><span class="sxs-lookup"><span data-stu-id="1da96-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="1da96-125">Istnieje możliwość, że niektórych kwerend może upłynął limit czasu.</span><span class="sxs-lookup"><span data-stu-id="1da96-125">It is possible that some queries might time out.</span></span>  
  
-   <span data-ttu-id="1da96-126">SQL Server Compact nie obsługuje częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="1da96-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da96-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1da96-127">See Also</span></span>  
 [<span data-ttu-id="1da96-128">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="1da96-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
