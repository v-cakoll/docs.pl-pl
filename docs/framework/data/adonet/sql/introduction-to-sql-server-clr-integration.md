---
title: Wprowadzenie do integracji środowiska CLR programu SQL Server
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: dd0ef041db13aa842554c70533770bf99c369941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="dd272-102">Wprowadzenie do integracji środowiska CLR programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="dd272-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="dd272-103">Środowisko uruchomieniowe języka wspólnego (CLR) jest bardzo ważne dla programu Microsoft .NET Framework i zapewnia środowiska wykonawczego dla całego kodu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd272-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="dd272-104">Kod uruchamiany w ramach środowiska CLR jest określana jako kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="dd272-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="dd272-105">Środowisko CLR zapewnia różnych funkcji i usług wymaganych do wykonania programu, w tym just in time (JIT) kompilację, przydzielanie i zarządzanie pamięcią, wymuszanie zabezpieczeń, obsługa wyjątków wątku zarządzania i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="dd272-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="dd272-106">Z CLR hostowanej w programie Microsoft SQL Server (nazywane integrację środowiska CLR) można tworzyć procedury składowane, wyzwalacze, funkcje zdefiniowane przez użytkownika, typy danych zdefiniowane przez użytkownika i agregacje zdefiniowane przez użytkownika, w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="dd272-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="dd272-107">Ponieważ kompiluje kodu zarządzanego do kodu natywnego przed wykonaniem, można osiągnąć wzrośnie znaczne wydajności w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="dd272-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="dd272-108">Zarządzany kod używa zabezpieczeń dostępu kodu (CAS), linków do kodu i domen aplikacji, aby zapobiec zestawy z wykonywania pewnych operacji.</span><span class="sxs-lookup"><span data-stu-id="dd272-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="dd272-109">SQL Server używa urzędów certyfikacji, aby ułatwić Zabezpieczanie kodu zarządzanego i zapobiec naruszeniu zabezpieczeń systemu operacyjnego lub serwer bazy danych.</span><span class="sxs-lookup"><span data-stu-id="dd272-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="dd272-110">Ta sekcja ma zapewnić tylko za mało informacji, aby rozpocząć programowanie z integrację środowiska CLR programu SQL Server i nie jest przeznaczona pełne.</span><span class="sxs-lookup"><span data-stu-id="dd272-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="dd272-111">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="dd272-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="dd272-112">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="dd272-112">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="dd272-113">Omówienie integracji środowiska uruchomieniowego (języka wspólnego CLR) w usłudze wspólnego języka</span><span class="sxs-lookup"><span data-stu-id="dd272-113">Common Language Runtime (CLR) Integration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="dd272-114">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dd272-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="dd272-115">Z typowych funkcji Integracja z języka wspólnego (CLR) jest wyłączona, domyślnie w programie Microsoft SQL Server, a musi być włączona, aby można było używać obiektów, które są implementowane za pomocą integracji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="dd272-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="dd272-116">Aby włączyć integrację środowiska CLR przy użyciu języka Transact-SQL, należy użyć `clr enabled` opcji `sp_configure` procedury składowanej, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="dd272-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="dd272-117">Integrację środowiska CLR można wyłączyć, ustawiając `clr enabled` opcję na wartość 0.</span><span class="sxs-lookup"><span data-stu-id="dd272-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="dd272-118">Po wyłączeniu integrację środowiska CLR programu SQL Server zatrzymuje wykonywanie wszystkich procedur CLR i zwalnia wszystkie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd272-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="dd272-119">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="dd272-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="dd272-120">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="dd272-120">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="dd272-121">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dd272-121">Enabling CLR Integration</span></span>](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="dd272-122">Wdrażanie Zestaw CLR</span><span class="sxs-lookup"><span data-stu-id="dd272-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="dd272-123">Po metodach CLR zostały przetestowane i zweryfikowane na serwerze testowym, mogą być dystrybuowane do produkcyjnego serwerami przy użyciu skryptu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="dd272-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="dd272-124">Skrypt wdrożenia można wygenerować ręcznie lub za pomocą programu SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="dd272-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="dd272-125">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="dd272-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="dd272-126">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="dd272-126">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="dd272-127">Wdrażanie obiektów bazy danych CLR</span><span class="sxs-lookup"><span data-stu-id="dd272-127">Deploying CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="dd272-128">Zabezpieczenia integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dd272-128">CLR Integration Security</span></span>  
 <span data-ttu-id="dd272-129">Model zabezpieczeń integracji programu Microsoft SQL Server z systemu Microsoft .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) zarządza i zabezpiecza dostęp między różnymi typami obiektów CLR i -CLR uruchomiony w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dd272-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="dd272-130">Te obiekty może zostać wywołana przez instrukcję Transact-SQL lub innego obiektu CLR uruchomionej na serwerze.</span><span class="sxs-lookup"><span data-stu-id="dd272-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="dd272-131">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="dd272-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="dd272-132">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="dd272-132">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="dd272-133">Zabezpieczenia integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dd272-133">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="dd272-134">Debugowanie zestawu CLR</span><span class="sxs-lookup"><span data-stu-id="dd272-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="dd272-135">Microsoft SQL Server zapewnia obsługę debugowania Transact-SQL i wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="dd272-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="dd272-136">Debugowanie działa w językach: użytkownicy mogą Wkrocz bezproblemowo obiektów CLR z Transact-SQL i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="dd272-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="dd272-137">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="dd272-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="dd272-138">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="dd272-138">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="dd272-139">Debugowanie CLR obiektów bazy danych</span><span class="sxs-lookup"><span data-stu-id="dd272-139">Debugging CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="dd272-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd272-140">See Also</span></span>  
 [<span data-ttu-id="dd272-141">Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="dd272-141">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="dd272-142">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd272-142">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="dd272-143">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="dd272-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
