---
title: Używanie domeny aplikacji
description: Użyj domen aplikacji, które zapewniają jednostkę izolacji dla środowiska uruchomieniowego języka wspólnego (CLR). Domeny aplikacji są tworzone i uruchamiane w ramach procesu.
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: df2a63716904ebfc6ee163121a1f07e53aa07514
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105183"
---
# <a name="using-application-domains"></a><span data-ttu-id="8be70-104">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8be70-104">Using Application Domains</span></span>

<span data-ttu-id="8be70-105">Domeny aplikacji zapewniają jednostkę izolacji dla środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="8be70-105">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="8be70-106">Są one tworzone i uruchamiane w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8be70-106">They are created and run inside a process.</span></span> <span data-ttu-id="8be70-107">Domeny aplikacji są zwykle tworzone przez hosta środowiska uruchomieniowego, który jest aplikacją odpowiedzialną za ładowanie środowiska uruchomieniowego do procesu i wykonywanie kodu użytkownika w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-107">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="8be70-108">Host środowiska uruchomieniowego tworzy proces i domyślną domenę aplikacji, a następnie uruchamia zarządzany kod.</span><span class="sxs-lookup"><span data-stu-id="8be70-108">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="8be70-109">Hosty środowiska uruchomieniowego obejmują ASP.NET, program Microsoft Internet Explorer i powłokę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8be70-109">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="8be70-110">W przypadku większości aplikacji nie trzeba tworzyć własnej domeny aplikacji. Host środowiska uruchomieniowego tworzy wszystkie wymagane domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-110">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="8be70-111">Można jednak utworzyć i skonfigurować dodatkowe domeny aplikacji, jeśli aplikacja wymaga odizolowania kodu lub użycia i zwolnienia bibliotek DLL.</span><span class="sxs-lookup"><span data-stu-id="8be70-111">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8be70-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8be70-112">In This Section</span></span>  

[<span data-ttu-id="8be70-113">Instrukcje: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8be70-113">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="8be70-114">Opisuje sposób programowego tworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-114">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="8be70-115">Instrukcje: Zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8be70-115">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="8be70-116">Opisuje sposób programowego zwalniania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-116">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="8be70-117">Instrukcje: Konfigurowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8be70-117">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="8be70-118">Zawiera wprowadzenie do konfigurowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-118">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="8be70-119">Pobieranie informacji o instalacji z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8be70-119">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="8be70-120">Opisuje sposób pobierania informacji o instalacji z domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-120">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="8be70-121">Instrukcje: Ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8be70-121">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="8be70-122">Opisuje sposób ładowania zestawu do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-122">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="8be70-123">Porady: uzyskiwanie informacji dotyczących typów i członków z zestawu</span><span class="sxs-lookup"><span data-stu-id="8be70-123">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="8be70-124">Opisuje sposób pobierania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="8be70-124">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="8be70-125">Kopiowanie zestawów w tle</span><span class="sxs-lookup"><span data-stu-id="8be70-125">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="8be70-126">Opisuje, w jaki sposób kopiowanie w tle umożliwia aktualizowanie zestawów, gdy są używane, oraz sposób konfigurowania kopiowania w tle.</span><span class="sxs-lookup"><span data-stu-id="8be70-126">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="8be70-127">Instrukcje: Odbieranie powiadomień o wyjątkach pierwszej szansy</span><span class="sxs-lookup"><span data-stu-id="8be70-127">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="8be70-128">Wyjaśnia, jak można odebrać powiadomienie zgłoszone przez wyjątek, zanim środowisko uruchomieniowe języka wspólnego rozpoczęło wyszukiwanie obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="8be70-128">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="8be70-129">Rozwiązywanie załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="8be70-129">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="8be70-130">Zawiera wskazówki dotyczące używania <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia do rozwiązywania niepowodzeń ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="8be70-130">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8be70-131">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="8be70-131">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="8be70-132">Reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-132">Represents an application domain.</span></span> <span data-ttu-id="8be70-133">Zapewnia metody tworzenia i kontrolowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-133">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8be70-134">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="8be70-134">Related Sections</span></span>  
[<span data-ttu-id="8be70-135">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="8be70-135">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="8be70-136">Zawiera przegląd funkcji wykonywanych przez zestawy.</span><span class="sxs-lookup"><span data-stu-id="8be70-136">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="8be70-137">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="8be70-137">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="8be70-138">Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="8be70-138">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="8be70-139">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="8be70-139">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="8be70-140">Opisuje sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="8be70-140">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="8be70-141">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8be70-141">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="8be70-142">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8be70-142">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="8be70-143">Przegląd odbicia</span><span class="sxs-lookup"><span data-stu-id="8be70-143">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="8be70-144">Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="8be70-144">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
