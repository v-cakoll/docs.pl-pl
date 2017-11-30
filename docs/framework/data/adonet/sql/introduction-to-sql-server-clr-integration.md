---
title: "Wprowadzenie do integracji środowiska CLR programu SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ab9dad1031979169aee99a7bb6bc5fe409954e9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="d5d9d-102">Wprowadzenie do integracji środowiska CLR programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="d5d9d-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="d5d9d-103">Środowisko uruchomieniowe języka wspólnego (CLR) jest bardzo ważne dla programu Microsoft .NET Framework i zapewnia środowiska wykonawczego dla całego kodu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="d5d9d-104">Kod uruchamiany w ramach środowiska CLR jest określana jako kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="d5d9d-105">Środowisko CLR zapewnia różnych funkcji i usług wymaganych do wykonania programu, w tym just in time (JIT) kompilację, przydzielanie i zarządzanie pamięcią, wymuszanie zabezpieczeń, obsługa wyjątków wątku zarządzania i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="d5d9d-106">Z CLR hostowanej w programie Microsoft SQL Server (nazywane integrację środowiska CLR) można tworzyć procedury składowane, wyzwalacze, funkcje zdefiniowane przez użytkownika, typy danych zdefiniowane przez użytkownika i agregacje zdefiniowane przez użytkownika, w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="d5d9d-107">Ponieważ kompiluje kodu zarządzanego do kodu natywnego przed wykonaniem, można osiągnąć wzrośnie znaczne wydajności w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="d5d9d-108">Zarządzany kod używa zabezpieczeń dostępu kodu (CAS), linków do kodu i domen aplikacji, aby zapobiec zestawy z wykonywania pewnych operacji.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="d5d9d-109">SQL Server używa urzędów certyfikacji, aby ułatwić Zabezpieczanie kodu zarządzanego i zapobiec naruszeniu zabezpieczeń systemu operacyjnego lub serwer bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="d5d9d-110">Ta sekcja ma zapewnić tylko za mało informacji, aby rozpocząć programowanie z integrację środowiska CLR programu SQL Server i nie jest przeznaczona pełne.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="d5d9d-111">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="d5d9d-112">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="d5d9d-112">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="d5d9d-113">Omówienie integracji środowiska uruchomieniowego (języka wspólnego CLR) w usłudze wspólnego języka</span><span class="sxs-lookup"><span data-stu-id="d5d9d-113">Common Language Runtime (CLR) Integration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="d5d9d-114">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d5d9d-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="d5d9d-115">Z typowych funkcji Integracja z języka wspólnego (CLR) jest wyłączona, domyślnie w programie Microsoft SQL Server, a musi być włączona, aby można było używać obiektów, które są implementowane za pomocą integracji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="d5d9d-116">Aby włączyć integrację środowiska CLR przy użyciu języka Transact-SQL, należy użyć `clr enabled` opcji `sp_configure` procedury składowanej, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="d5d9d-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="d5d9d-117">Integrację środowiska CLR można wyłączyć, ustawiając `clr enabled` opcję na wartość 0.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="d5d9d-118">Po wyłączeniu integrację środowiska CLR programu SQL Server zatrzymuje wykonywanie wszystkich procedur CLR i zwalnia wszystkie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="d5d9d-119">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="d5d9d-120">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="d5d9d-120">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="d5d9d-121">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d5d9d-121">Enabling CLR Integration</span></span>](http://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="d5d9d-122">Wdrażanie Zestaw CLR</span><span class="sxs-lookup"><span data-stu-id="d5d9d-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="d5d9d-123">Po metodach CLR zostały przetestowane i zweryfikowane na serwerze testowym, mogą być dystrybuowane do produkcyjnego serwerami przy użyciu skryptu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="d5d9d-124">Skrypt wdrożenia można wygenerować ręcznie lub za pomocą programu SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="d5d9d-125">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="d5d9d-126">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="d5d9d-126">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="d5d9d-127">Wdrażanie obiektów bazy danych CLR</span><span class="sxs-lookup"><span data-stu-id="d5d9d-127">Deploying CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="d5d9d-128">Zabezpieczenia integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d5d9d-128">CLR Integration Security</span></span>  
 <span data-ttu-id="d5d9d-129">Model zabezpieczeń integracji programu Microsoft SQL Server z systemu Microsoft .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) zarządza i zabezpiecza dostęp między różnymi typami obiektów CLR i -CLR uruchomiony w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="d5d9d-130">Te obiekty może zostać wywołana przez instrukcję Transact-SQL lub innego obiektu CLR uruchomionej na serwerze.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="d5d9d-131">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="d5d9d-132">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="d5d9d-132">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="d5d9d-133">Zabezpieczenia integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d5d9d-133">CLR Integration Security</span></span>](http://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="d5d9d-134">Debugowanie zestawu CLR</span><span class="sxs-lookup"><span data-stu-id="d5d9d-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="d5d9d-135">Microsoft SQL Server zapewnia obsługę debugowania Transact-SQL i wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) obiektów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="d5d9d-136">Debugowanie działa w językach: użytkownicy mogą Wkrocz bezproblemowo obiektów CLR z Transact-SQL i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="d5d9d-137">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="d5d9d-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="d5d9d-138">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="d5d9d-138">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="d5d9d-139">Debugowanie CLR obiektów bazy danych</span><span class="sxs-lookup"><span data-stu-id="d5d9d-139">Debugging CLR Database Objects</span></span>](http://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="d5d9d-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5d9d-140">See Also</span></span>  
 [<span data-ttu-id="d5d9d-141">Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="d5d9d-141">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="d5d9d-142">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d5d9d-142">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="d5d9d-143">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="d5d9d-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
