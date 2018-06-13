---
title: Używanie domeny aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ebd1de46eb2757098a369b58dd9a6c0009e5b95
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742474"
---
# <a name="using-application-domains"></a><span data-ttu-id="bf98e-102">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bf98e-102">Using Application Domains</span></span>
<span data-ttu-id="bf98e-103">Domeny aplikacji Podaj jednostkę izolacji dla środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="bf98e-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="bf98e-104">Są one tworzone i uruchamiane wewnątrz procesu.</span><span class="sxs-lookup"><span data-stu-id="bf98e-104">They are created and run inside a process.</span></span> <span data-ttu-id="bf98e-105">Domeny aplikacji są zwykle tworzone przez host czasu wykonywania, który jest odpowiedzialny za ładowanie środowiska uruchomieniowego do procesu i wykonywanie kodu użytkownika w domenie aplikacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf98e-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="bf98e-106">Host czasu wykonywania tworzy proces i domyślnej domeny aplikacji i uruchamia kod zarządzany wewnątrz niej.</span><span class="sxs-lookup"><span data-stu-id="bf98e-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="bf98e-107">Hosty środowiska uruchomieniowego obejmują ASP.NET, programu Microsoft Internet Explorer i powłoki systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bf98e-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="bf98e-108">Dla większości aplikacji nie trzeba tworzyć własne domenę aplikacji. host czasu wykonywania utworzy wszystkie domeny aplikacji to konieczne.</span><span class="sxs-lookup"><span data-stu-id="bf98e-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="bf98e-109">Można jednak utworzyć i skonfigurować domeny dodatkowych aplikacji, jeśli aplikacja musi izolowanie kodu lub użycia i zwolnić biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="bf98e-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf98e-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bf98e-110">In This Section</span></span>  
 [<span data-ttu-id="bf98e-111">Instrukcje: tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bf98e-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="bf98e-112">Opisuje sposób programowego tworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf98e-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="bf98e-113">Instrukcje: zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bf98e-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="bf98e-114">Opisuje sposób programowego wyładować domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf98e-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="bf98e-115">Instrukcje: konfigurowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bf98e-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="bf98e-116">Wprowadzenie do konfigurowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf98e-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="bf98e-117">Pobieranie informacji o instalacji z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bf98e-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="bf98e-118">Opisuje sposób pobrać informacji o instalacji z domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf98e-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="bf98e-119">Instrukcje: ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bf98e-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="bf98e-120">Opisuje sposób załadować zestawu do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf98e-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="bf98e-121">Instrukcje: uzyskiwanie informacji dotyczących typów i elementów członkowskich z zestawu</span><span class="sxs-lookup"><span data-stu-id="bf98e-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="bf98e-122">Zawiera opis sposobu pobierania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="bf98e-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="bf98e-123">Kopiowanie zestawów w tle</span><span class="sxs-lookup"><span data-stu-id="bf98e-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="bf98e-124">W tym artykule opisano, jak kopiowanie w tle umożliwia aktualizacji do zestawów, gdy są one używane i sposobie konfigurowania kopiowanie w tle.</span><span class="sxs-lookup"><span data-stu-id="bf98e-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="bf98e-125">Instrukcje: odbieranie powiadomień o wyjątkach pierwszej szansy</span><span class="sxs-lookup"><span data-stu-id="bf98e-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="bf98e-126">W tym artykule wyjaśniono, jak możesz otrzymywać powiadomienia, który zgłosił wyjątek, zanim środowisko uruchomieniowe języka wspólnego rozpoczął wyszukiwanie programy obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="bf98e-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="bf98e-127">Rozwiązywanie załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="bf98e-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="bf98e-128">Ten artykuł zawiera wskazówki dotyczące używania <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby naprawić błędy ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="bf98e-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bf98e-129">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="bf98e-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="bf98e-130">Reprezentuje domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf98e-130">Represents an application domain.</span></span> <span data-ttu-id="bf98e-131">Udostępnia metody tworzenia i kontrolowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf98e-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bf98e-132">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bf98e-132">Related Sections</span></span>  
 [<span data-ttu-id="bf98e-133">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="bf98e-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="bf98e-134">Zawiera omówienie funkcji wykonywane przez zestawy.</span><span class="sxs-lookup"><span data-stu-id="bf98e-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="bf98e-135">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="bf98e-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="bf98e-136">Opisuje sposób tworzenia, zaloguj się i ustawić atrybuty zestawów.</span><span class="sxs-lookup"><span data-stu-id="bf98e-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="bf98e-137">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="bf98e-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="bf98e-138">Opisuje sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="bf98e-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="bf98e-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bf98e-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="bf98e-140">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf98e-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="bf98e-141">Odbicie — omówienie</span><span class="sxs-lookup"><span data-stu-id="bf98e-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="bf98e-142">Informacje dotyczące używania **odbicia** klasę, aby uzyskać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="bf98e-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
