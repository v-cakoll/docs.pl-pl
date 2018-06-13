---
title: SQL Server Compact i LINQ do SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 74b8a7a6dfc9a4050dbba9a8c2f6969dba42656c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355789"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="edf09-102">SQL Server Compact i LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="edf09-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="edf09-103">SQL Server Compact to domyślna baza danych zainstalowana z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="edf09-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="edf09-104">Aby uzyskać więcej informacji, zobacz [Pave – za pośrednictwem przy użyciu programu SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).</span><span class="sxs-lookup"><span data-stu-id="edf09-104">For more information, see [PAVE OVER Using SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).</span></span>  
  
 <span data-ttu-id="edf09-105">W tym temacie przedstawiono podstawowe różnice w użycia, konfiguracji, zestawy funkcji i zakres [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje.</span><span class="sxs-lookup"><span data-stu-id="edf09-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="edf09-106">Właściwości programu SQL Server Compact w odniesieniu do LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="edf09-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="edf09-107">Domyślnie program SQL Server Compact są zainstalowane dla wszystkich wersji programu Visual Studio i w związku z tym jest dostępny na komputerze dewelopera do użycia z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edf09-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="edf09-108">Wdrażanie aplikacji, która używa programu SQL Server Compact, ale i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] różni się od aplikacji serwera SQL.</span><span class="sxs-lookup"><span data-stu-id="edf09-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="edf09-109">SQL Server Compact nie jest częścią programu .NET Framework i w związku z tym musi być z aplikacji lub oddzielnie pobrane z witryny Microsoft.</span><span class="sxs-lookup"><span data-stu-id="edf09-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="edf09-110">Należy uwzględnić następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="edf09-110">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="edf09-111">SQL Server Compact, jest dostarczana jako bibliotekę DLL, która może służyć do atakowania pliki bazy danych (z rozszerzeniem sdf) bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="edf09-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
-   <span data-ttu-id="edf09-112">SQL Server Compact działa w ten sam proces jako aplikacja klienta.</span><span class="sxs-lookup"><span data-stu-id="edf09-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="edf09-113">Wydajność programu SQL Server Compact komunikacji w związku z tym może być znacznie wyższa niż komunikacji z serwerem SQL.</span><span class="sxs-lookup"><span data-stu-id="edf09-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="edf09-114">Z drugiej strony programu SQL Server Compact wymagają współdziałanie zarządzane i niezarządzane kodu przy użyciu jego koszty związane.</span><span class="sxs-lookup"><span data-stu-id="edf09-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
-   <span data-ttu-id="edf09-115">Rozmiar programu SQL Server Compact biblioteki DLL jest mała.</span><span class="sxs-lookup"><span data-stu-id="edf09-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="edf09-116">Ta funkcja pozwala zmniejszyć rozmiar ogólną aplikacji.</span><span class="sxs-lookup"><span data-stu-id="edf09-116">This feature reduces the overall application size.</span></span>  
  
-   <span data-ttu-id="edf09-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Środowiska uruchomieniowego i narzędzie wiersza polecenia SQLMetal obsługuje program SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="edf09-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
-   <span data-ttu-id="edf09-118">[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nie obsługuje programu SQL Server Compact.</span><span class="sxs-lookup"><span data-stu-id="edf09-118">The [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="edf09-119">Zestaw funkcji</span><span class="sxs-lookup"><span data-stu-id="edf09-119">Feature Set</span></span>  
 <span data-ttu-id="edf09-120">SQL Server Compact zestaw funkcji jest znacznie prostsze niż zestaw funkcji programu SQL Server w następujący sposób, który może mieć wpływ na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji:</span><span class="sxs-lookup"><span data-stu-id="edf09-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
-   <span data-ttu-id="edf09-121">SQL Server Compact nie obsługuje procedur składowanych ani widoków.</span><span class="sxs-lookup"><span data-stu-id="edf09-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
-   <span data-ttu-id="edf09-122">SQL Server Compact obsługuje tylko typy danych i funkcji SQL.</span><span class="sxs-lookup"><span data-stu-id="edf09-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
-   <span data-ttu-id="edf09-123">SQL Server Compact obsługuje tylko podzestaw konstrukcji SQL.</span><span class="sxs-lookup"><span data-stu-id="edf09-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
-   <span data-ttu-id="edf09-124">SQL Server Compact zawiera tylko minimalne optymalizację.</span><span class="sxs-lookup"><span data-stu-id="edf09-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="edf09-125">Istnieje możliwość, że niektórych kwerend może upłynął limit czasu.</span><span class="sxs-lookup"><span data-stu-id="edf09-125">It is possible that some queries might time out.</span></span>  
  
-   <span data-ttu-id="edf09-126">SQL Server Compact nie obsługuje częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="edf09-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf09-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edf09-127">See Also</span></span>  
 [<span data-ttu-id="edf09-128">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="edf09-128">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
