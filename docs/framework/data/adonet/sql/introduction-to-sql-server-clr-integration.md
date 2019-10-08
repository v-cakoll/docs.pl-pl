---
title: Wprowadzenie do integracji środowiska CLR programu SQL Server
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 76c6fb4cb37807f286f1f1f2aeedbdea6c74fe38
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002143"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="b6f30-102">Wprowadzenie do integracji środowiska CLR programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="b6f30-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="b6f30-103">Środowisko uruchomieniowe języka wspólnego (CLR) jest sercem struktury Microsoft .NET i udostępnia środowisko wykonywania dla całego kodu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6f30-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="b6f30-104">Kod, który jest uruchamiany w środowisku CLR, jest nazywany kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="b6f30-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="b6f30-105">Środowisko CLR udostępnia różne funkcje i usługi wymagane do wykonania programu, w tym kompilację just-in-Time (JIT), przydzielanie i zarządzanie pamięcią, wymuszanie bezpieczeństwa typów, obsługę wyjątków, zarządzanie wątkami i zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="b6f30-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="b6f30-106">Za pomocą środowiska CLR hostowanego w Microsoft SQL Server (nazywanej integracją środowiska CLR) można tworzyć procedury składowane, wyzwalacze, funkcje zdefiniowane przez użytkownika, typy zdefiniowane przez użytkownika i agregacje zdefiniowane przez użytkownika w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="b6f30-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="b6f30-107">Ponieważ kod zarządzany kompiluje się do kodu natywnego przed wykonaniem, można osiągnąć znaczący wzrost wydajności w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="b6f30-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="b6f30-108">Kod zarządzany używa zabezpieczeń dostępu kodu (CAS), linków do kodu i domen aplikacji, aby zapobiec wykonywaniu przez nie niektórych operacji.</span><span class="sxs-lookup"><span data-stu-id="b6f30-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="b6f30-109">SQL Server używa urzędów certyfikacji do zabezpieczania kodu zarządzanego i zapobiegania naruszeniu systemu operacyjnego lub serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b6f30-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="b6f30-110">Ta sekcja ma na celu dostarczenie tylko wystarczającej ilości informacji, aby rozpocząć programowanie przy użyciu integracji środowiska CLR SQL Server i nie jest to wszechstronne.</span><span class="sxs-lookup"><span data-stu-id="b6f30-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="b6f30-111">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6f30-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="b6f30-112">**Książka SQL Server online**</span><span class="sxs-lookup"><span data-stu-id="b6f30-112">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="b6f30-113">Omówienie integracji środowiska uruchomieniowego języka wspólnego (CLR)</span><span class="sxs-lookup"><span data-stu-id="b6f30-113">Common Language Runtime (CLR) Integration Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="b6f30-114">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b6f30-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="b6f30-115">Funkcja integracji środowiska uruchomieniowego języka wspólnego (CLR) jest domyślnie wyłączona w Microsoft SQL Server i musi być włączona, aby można było używać obiektów wdrożonych przy użyciu integracji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b6f30-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="b6f30-116">Aby włączyć integrację środowiska CLR przy użyciu języka Transact-SQL, użyj opcji `clr enabled` procedury składowanej `sp_configure`, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="b6f30-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="b6f30-117">Integrację środowiska CLR można wyłączyć, ustawiając opcję `clr enabled` na 0.</span><span class="sxs-lookup"><span data-stu-id="b6f30-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="b6f30-118">Po wyłączeniu integracji środowiska CLR SQL Server przestaje wykonywać wszystkie procedury CLR i zwalnia wszystkie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6f30-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="b6f30-119">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6f30-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="b6f30-120">**Książka SQL Server online**</span><span class="sxs-lookup"><span data-stu-id="b6f30-120">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="b6f30-121">Włączanie integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b6f30-121">Enabling CLR Integration</span></span>](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="b6f30-122">Wdrażanie zestawu CLR</span><span class="sxs-lookup"><span data-stu-id="b6f30-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="b6f30-123">Po przetestowaniu i zweryfikowaniu metod CLR na serwerze testowym mogą one być dystrybuowane do serwerów produkcyjnych przy użyciu skryptu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="b6f30-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="b6f30-124">Skrypt wdrażania można wygenerować ręcznie lub za pomocą SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="b6f30-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="b6f30-125">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6f30-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="b6f30-126">**Książka SQL Server online**</span><span class="sxs-lookup"><span data-stu-id="b6f30-126">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="b6f30-127">Wdrażanie obiektów bazy danych CLR</span><span class="sxs-lookup"><span data-stu-id="b6f30-127">Deploying CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="b6f30-128">Zabezpieczenia integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b6f30-128">CLR Integration Security</span></span>  
 <span data-ttu-id="b6f30-129">Model zabezpieczeń Microsoft SQL Server integracji ze środowiskiem uruchomieniowym języka wspólnego (CLR) w programie Microsoft .NET Framework umożliwia zarządzanie dostępem między różnymi typami obiektów CLR i innych niż środowiska CLR uruchomionych w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6f30-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="b6f30-130">Te obiekty mogą być wywoływane przez instrukcję języka Transact-SQL lub inny obiekt CLR uruchomiony na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b6f30-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="b6f30-131">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6f30-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="b6f30-132">**Książka SQL Server online**</span><span class="sxs-lookup"><span data-stu-id="b6f30-132">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="b6f30-133">Zabezpieczenia integracji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="b6f30-133">CLR Integration Security</span></span>](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="b6f30-134">Debugowanie zestawu CLR</span><span class="sxs-lookup"><span data-stu-id="b6f30-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="b6f30-135">Microsoft SQL Server zapewnia obsługę debugowania obiektów Transact-SQL i środowiska uruchomieniowego języka wspólnego (CLR) w bazie danych programu.</span><span class="sxs-lookup"><span data-stu-id="b6f30-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="b6f30-136">Debugowanie działa między językami: użytkownicy mogą bezproblemowo przechodzenie do obiektów CLR z języka Transact-SQL i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="b6f30-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="b6f30-137">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6f30-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="b6f30-138">**Książka SQL Server online**</span><span class="sxs-lookup"><span data-stu-id="b6f30-138">**SQL Server Books Online**</span></span>  
  
- [<span data-ttu-id="b6f30-139">Debugowanie obiektów bazy danych CLR</span><span class="sxs-lookup"><span data-stu-id="b6f30-139">Debugging CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="b6f30-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6f30-140">See also</span></span>

- [<span data-ttu-id="b6f30-141">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6f30-141">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="b6f30-142">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6f30-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
