---
title: Wprowadzenie do integracji środowiska CLR programu SQL Server
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 380666ae9a3ebc18ef470e5ab719360f40510f41
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650605"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="32777-102">Wprowadzenie do integracji środowiska CLR programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="32777-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="32777-103">Środowisko uruchomieniowe języka wspólnego (CLR) to serce platformy Microsoft .NET Framework i oferuje środowisko wykonywania dla całego kodu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32777-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="32777-104">Kod, który jest uruchamiany w ramach środowiska CLR jest określany jako kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="32777-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="32777-105">Środowisko CLR oferuje różnych funkcji i usług wymaganych do wykonania programu, w tym just-in-time (JIT) kompilacja, przydzielanie i zarządzanie pamięcią, wymuszanie bezpieczeństwo typów, obsługa wyjątków, zarządzanie wątkami i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="32777-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="32777-106">Za pomocą środowiska CLR hostowanych w programie Microsoft SQL Server (nazywane integrację środowiska CLR) można tworzyć procedury składowane, wyzwalacze, funkcje zdefiniowane przez użytkownika, typy zdefiniowane przez użytkownika i agregacje zdefiniowane przez użytkownika w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="32777-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="32777-107">Ponieważ kompiluje kodu zarządzanego do kodu macierzystego przed wykonywania, można osiągnąć zwiększa istotnie poprawiającą wydajność w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="32777-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="32777-108">Zarządzany kod używa zabezpieczeń dostępu kodu (CAS), linków do kodu i domen aplikacji, aby zapobiec zestawów z wykonywania pewnych operacji.</span><span class="sxs-lookup"><span data-stu-id="32777-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="32777-109">Program SQL Server używa urzędów certyfikacji, aby ułatwić zabezpieczenie kodu zarządzanego i zapobiec naruszeniu zabezpieczeń systemu operacyjnego lub serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="32777-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="32777-110">Ta sekcja ma zapewnić tylko wystarczających informacji, aby rozpocząć programowanie z użyciem integracji środowiska CLR programu SQL Server i nie jest przeznaczona do wyczerpująca.</span><span class="sxs-lookup"><span data-stu-id="32777-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="32777-111">Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="32777-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="32777-112">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="32777-112">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="32777-113">Omówienie integracji środowiska uruchomieniowego (języka wspólnego CLR) w usłudze wspólnego języka</span><span class="sxs-lookup"><span data-stu-id="32777-113">Common Language Runtime (CLR) Integration Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="32777-114">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="32777-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="32777-115">Typowych funkcji integracji środowiska uruchomieniowego (języka wspólnego CLR) języka jest wyłączona, domyślnie w programie Microsoft SQL Server, a musi być włączona, aby można było używać obiektów, które są implementowane przy użyciu integrację środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="32777-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="32777-116">Aby włączyć integrację środowiska CLR przy użyciu języka Transact-SQL, użyj `clr enabled` opcji `sp_configure` procedurę składowaną, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="32777-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="32777-117">Wyłącz integrację środowiska CLR, ustawiając `clr enabled` opcję na wartość 0.</span><span class="sxs-lookup"><span data-stu-id="32777-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="32777-118">Po wyłączeniu integrację środowiska CLR programu SQL Server zatrzymuje wykonywanie wszystkich procedur CLR i zwalnia wszystkie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32777-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="32777-119">Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="32777-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="32777-120">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="32777-120">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="32777-121">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="32777-121">Enabling CLR Integration</span></span>](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="32777-122">Wdrażanie zestawu CLR</span><span class="sxs-lookup"><span data-stu-id="32777-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="32777-123">Po metodach CLR zostały przetestowane i zweryfikowane na serwerze testowym, mogą być rozproszone na serwerach produkcyjnych przy użyciu skryptu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="32777-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="32777-124">Ręcznie lub za pomocą programu SQL Server Management Studio można wygenerować skryptu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="32777-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="32777-125">Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="32777-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="32777-126">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="32777-126">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="32777-127">Wdrażanie obiekty bazy danych środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="32777-127">Deploying CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="32777-128">Zabezpieczenia integracji CLR</span><span class="sxs-lookup"><span data-stu-id="32777-128">CLR Integration Security</span></span>  
 <span data-ttu-id="32777-129">Model zabezpieczeń integracji programu Microsoft SQL Server za pomocą programu Microsoft .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) zarządza i zabezpiecza dostęp między różnymi typami obiektów CLR i / CLR, które są uruchomione w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="32777-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="32777-130">Te obiekty może zostać wywołana przez instrukcję Transact-SQL lub innego obiektu CLR uruchomiona na serwerze.</span><span class="sxs-lookup"><span data-stu-id="32777-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="32777-131">Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="32777-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="32777-132">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="32777-132">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="32777-133">Zabezpieczenia integracji CLR</span><span class="sxs-lookup"><span data-stu-id="32777-133">CLR Integration Security</span></span>](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="32777-134">Debugowanie zestawu CLR</span><span class="sxs-lookup"><span data-stu-id="32777-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="32777-135">Microsoft SQL Server zapewnia obsługę debugowania języka Transact-SQL i obiekty wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="32777-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="32777-136">Debugowanie działa w wielu językach: użytkownicy mogą Wkrocz bezproblemowo obiektów CLR z instrukcji Transact-SQL i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="32777-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="32777-137">Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="32777-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="32777-138">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="32777-138">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="32777-139">Debugowanie obiektów bazy danych środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="32777-139">Debugging CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="32777-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32777-140">See also</span></span>

- [<span data-ttu-id="32777-141">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="32777-141">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)
- [<span data-ttu-id="32777-142">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="32777-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
