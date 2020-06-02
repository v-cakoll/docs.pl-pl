---
title: Wprowadzenie do integracji środowiska CLR programu SQL Server
description: Integracja środowiska CLR z SQL Server obsługuje procedury składowane, wyzwalacze, funkcje zdefiniowane przez użytkownika, typy zdefiniowane przez użytkownika i agregacje zdefiniowane przez użytkownika w kodzie zarządzanym.
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: fa2ef68792d09cf94b3e0680a14bd79f9b593999
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286433"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="96af1-103">Wprowadzenie do integracji środowiska CLR programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="96af1-103">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="96af1-104">Środowisko uruchomieniowe języka wspólnego (CLR) jest sercem struktury Microsoft .NET i udostępnia środowisko wykonywania dla całego kodu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96af1-104">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="96af1-105">Kod, który jest uruchamiany w środowisku CLR, jest nazywany kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="96af1-105">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="96af1-106">Środowisko CLR udostępnia różne funkcje i usługi wymagane do wykonania programu, w tym kompilację just-in-Time (JIT), przydzielanie i zarządzanie pamięcią, wymuszanie bezpieczeństwa typów, obsługę wyjątków, zarządzanie wątkami i zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="96af1-106">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="96af1-107">Za pomocą środowiska CLR hostowanego w Microsoft SQL Server (nazywanej integracją środowiska CLR) można tworzyć procedury składowane, wyzwalacze, funkcje zdefiniowane przez użytkownika, typy zdefiniowane przez użytkownika i agregacje zdefiniowane przez użytkownika w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="96af1-107">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="96af1-108">Ponieważ kod zarządzany kompiluje się do kodu natywnego przed wykonaniem, można osiągnąć znaczący wzrost wydajności w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="96af1-108">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="96af1-109">Kod zarządzany używa zabezpieczeń dostępu kodu (CAS), linków do kodu i domen aplikacji, aby zapobiec wykonywaniu przez nie niektórych operacji.</span><span class="sxs-lookup"><span data-stu-id="96af1-109">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="96af1-110">SQL Server używa urzędów certyfikacji do zabezpieczania kodu zarządzanego i zapobiegania naruszeniu systemu operacyjnego lub serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="96af1-110">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="96af1-111">Ta sekcja ma na celu dostarczenie tylko wystarczającej ilości informacji, aby rozpocząć programowanie przy użyciu integracji środowiska CLR SQL Server i nie jest to wszechstronne.</span><span class="sxs-lookup"><span data-stu-id="96af1-111">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="96af1-112">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96af1-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="96af1-113">**SQL Server documentation (Dokumentacja programu SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="96af1-113">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="96af1-114">Omówienie integracji środowiska uruchomieniowego języka wspólnego (CLR)</span><span class="sxs-lookup"><span data-stu-id="96af1-114">Common Language Runtime (CLR) Integration Overview</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-integration-overview)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="96af1-115">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="96af1-115">Enabling CLR Integration</span></span>  
 <span data-ttu-id="96af1-116">Funkcja integracji środowiska uruchomieniowego języka wspólnego (CLR) jest domyślnie wyłączona w Microsoft SQL Server i musi być włączona, aby można było używać obiektów wdrożonych przy użyciu integracji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="96af1-116">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="96af1-117">Aby włączyć integrację środowiska CLR przy użyciu języka Transact-SQL, użyj `clr enabled` opcji `sp_configure` procedury składowanej, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="96af1-117">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="96af1-118">Integrację środowiska CLR można wyłączyć, ustawiając `clr enabled` opcję na 0.</span><span class="sxs-lookup"><span data-stu-id="96af1-118">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="96af1-119">Po wyłączeniu integracji środowiska CLR SQL Server przestaje wykonywać wszystkie procedury CLR i zwalnia wszystkie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="96af1-119">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="96af1-120">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96af1-120">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="96af1-121">**SQL Server documentation (Dokumentacja programu SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="96af1-121">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="96af1-122">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="96af1-122">Enabling CLR Integration</span></span>](/sql/relational-databases/clr-integration/clr-integration-enabling)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="96af1-123">Wdrażanie zestawu CLR</span><span class="sxs-lookup"><span data-stu-id="96af1-123">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="96af1-124">Po przetestowaniu i zweryfikowaniu metod CLR na serwerze testowym mogą one być dystrybuowane do serwerów produkcyjnych przy użyciu skryptu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="96af1-124">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="96af1-125">Skrypt wdrażania można wygenerować ręcznie lub za pomocą SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="96af1-125">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="96af1-126">Aby uzyskać szczegółowe informacje, zobacz wersję dokumentacji SQL Server dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96af1-126">For more detailed information, see the version of SQL Server documentation for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="96af1-127">**SQL Server documentation (Dokumentacja programu SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="96af1-127">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="96af1-128">Wdrażanie obiektów bazy danych CLR</span><span class="sxs-lookup"><span data-stu-id="96af1-128">Deploying CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/deploying-clr-database-objects)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="96af1-129">Zabezpieczenia integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="96af1-129">CLR Integration Security</span></span>  
 <span data-ttu-id="96af1-130">Model zabezpieczeń Microsoft SQL Server integracji ze środowiskiem uruchomieniowym języka wspólnego (CLR) w programie Microsoft .NET Framework umożliwia zarządzanie dostępem między różnymi typami obiektów CLR i innych niż środowiska CLR uruchomionych w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96af1-130">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="96af1-131">Te obiekty mogą być wywoływane przez instrukcję języka Transact-SQL lub inny obiekt CLR uruchomiony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="96af1-131">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="96af1-132">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96af1-132">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="96af1-133">**SQL Server documentation (Dokumentacja programu SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="96af1-133">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="96af1-134">Zabezpieczenia integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="96af1-134">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="96af1-135">Debugowanie zestawu CLR</span><span class="sxs-lookup"><span data-stu-id="96af1-135">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="96af1-136">Microsoft SQL Server zapewnia obsługę debugowania obiektów Transact-SQL i środowiska uruchomieniowego języka wspólnego (CLR) w bazie danych programu.</span><span class="sxs-lookup"><span data-stu-id="96af1-136">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="96af1-137">Debugowanie działa między językami: użytkownicy mogą bezproblemowo przechodzenie do obiektów CLR z języka Transact-SQL i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="96af1-137">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="96af1-138">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96af1-138">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="96af1-139">**SQL Server documentation (Dokumentacja programu SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="96af1-139">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="96af1-140">Debugowanie obiektów bazy danych CLR</span><span class="sxs-lookup"><span data-stu-id="96af1-140">Debugging CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/debugging-clr-database-objects)  
  
## <a name="see-also"></a><span data-ttu-id="96af1-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96af1-141">See also</span></span>

- [<span data-ttu-id="96af1-142">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96af1-142">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="96af1-143">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96af1-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
