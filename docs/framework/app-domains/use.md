---
title: "Używanie domeny aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53180d5d3d9314c3f078ddca8f5c155b01981f4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-application-domains"></a><span data-ttu-id="55e3b-102">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55e3b-102">Using Application Domains</span></span>
<span data-ttu-id="55e3b-103">Domeny aplikacji Podaj jednostkę izolacji dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="55e3b-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="55e3b-104">Są one tworzone i uruchamiane wewnątrz procesu.</span><span class="sxs-lookup"><span data-stu-id="55e3b-104">They are created and run inside a process.</span></span> <span data-ttu-id="55e3b-105">Domeny aplikacji są zwykle tworzone przez host czasu wykonywania, który jest odpowiedzialny za ładowanie środowiska uruchomieniowego do procesu i wykonywanie kodu użytkownika w domenie aplikacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55e3b-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="55e3b-106">Host czasu wykonywania tworzy proces i domyślnej domeny aplikacji i uruchamia kod zarządzany wewnątrz niej.</span><span class="sxs-lookup"><span data-stu-id="55e3b-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="55e3b-107">Hosty środowiska uruchomieniowego obejmują ASP.NET, programu Microsoft Internet Explorer i powłoki systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="55e3b-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="55e3b-108">Dla większości aplikacji nie trzeba tworzyć własne domenę aplikacji. host czasu wykonywania utworzy wszystkie domeny aplikacji to konieczne.</span><span class="sxs-lookup"><span data-stu-id="55e3b-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="55e3b-109">Można jednak utworzyć i skonfigurować domeny dodatkowych aplikacji, jeśli aplikacja musi izolowanie kodu lub użycia i zwolnić biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="55e3b-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55e3b-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="55e3b-110">In This Section</span></span>  
 [<span data-ttu-id="55e3b-111">Porady: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55e3b-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="55e3b-112">Opisuje sposób programowego tworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55e3b-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="55e3b-113">Porady: zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55e3b-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="55e3b-114">Opisuje sposób programowego wyładować domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55e3b-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="55e3b-115">Porady: Konfigurowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55e3b-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="55e3b-116">Wprowadzenie do konfigurowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55e3b-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="55e3b-117">Pobieranie informacji o Instalatorze z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55e3b-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="55e3b-118">Opisuje sposób pobrać informacji o instalacji z domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55e3b-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="55e3b-119">Porady: ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55e3b-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="55e3b-120">Opisuje sposób załadować zestawu do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55e3b-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="55e3b-121">Porady: uzyskać informacje dotyczące elementu członkowskiego typu i z zestawu</span><span class="sxs-lookup"><span data-stu-id="55e3b-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="55e3b-122">Zawiera opis sposobu pobierania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="55e3b-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="55e3b-123">Kopiowanie zestawów w tle</span><span class="sxs-lookup"><span data-stu-id="55e3b-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="55e3b-124">W tym artykule opisano, jak kopiowanie w tle umożliwia aktualizacji do zestawów, gdy są one używane i sposobie konfigurowania kopiowanie w tle.</span><span class="sxs-lookup"><span data-stu-id="55e3b-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="55e3b-125">Porady: otrzymywać powiadomienia o wyjątkach pierwszej szansy</span><span class="sxs-lookup"><span data-stu-id="55e3b-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="55e3b-126">W tym artykule wyjaśniono, jak możesz otrzymywać powiadomienia, który zgłosił wyjątek, zanim środowisko uruchomieniowe języka wspólnego rozpoczął wyszukiwanie programy obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="55e3b-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="55e3b-127">Rozwiązywanie Załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="55e3b-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="55e3b-128">Ten artykuł zawiera wskazówki dotyczące używania <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby naprawić błędy ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="55e3b-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="55e3b-129">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="55e3b-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="55e3b-130">Reprezentuje domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55e3b-130">Represents an application domain.</span></span> <span data-ttu-id="55e3b-131">Udostępnia metody tworzenia i kontrolowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55e3b-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="55e3b-132">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="55e3b-132">Related Sections</span></span>  
 [<span data-ttu-id="55e3b-133">Zestawy w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="55e3b-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="55e3b-134">Zawiera omówienie funkcji wykonywane przez zestawy.</span><span class="sxs-lookup"><span data-stu-id="55e3b-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="55e3b-135">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="55e3b-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="55e3b-136">Opisuje sposób tworzenia, zaloguj się i ustawić atrybuty zestawów.</span><span class="sxs-lookup"><span data-stu-id="55e3b-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="55e3b-137">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="55e3b-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="55e3b-138">Opisuje sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="55e3b-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="55e3b-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55e3b-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="55e3b-140">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55e3b-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="55e3b-141">Odbicie — omówienie</span><span class="sxs-lookup"><span data-stu-id="55e3b-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="55e3b-142">Informacje dotyczące używania **odbicia** klasę, aby uzyskać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="55e3b-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
