---
title: Używanie domeny aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
ms.openlocfilehash: d6bbc2648608e9542158e0f281984174447633a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119724"
---
# <a name="using-application-domains"></a><span data-ttu-id="83c06-102">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="83c06-102">Using Application Domains</span></span>

<span data-ttu-id="83c06-103">Domeny aplikacji zapewniają jednostkę izolacji dla środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="83c06-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="83c06-104">Są one tworzone i uruchamiane w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="83c06-104">They are created and run inside a process.</span></span> <span data-ttu-id="83c06-105">Domeny aplikacji są zwykle tworzone przez hosta środowiska uruchomieniowego, który jest aplikacją odpowiedzialną za ładowanie środowiska uruchomieniowego do procesu i wykonywanie kodu użytkownika w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="83c06-106">Host środowiska uruchomieniowego tworzy proces i domyślną domenę aplikacji, a następnie uruchamia zarządzany kod.</span><span class="sxs-lookup"><span data-stu-id="83c06-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="83c06-107">Hosty środowiska uruchomieniowego obejmują ASP.NET, program Microsoft Internet Explorer i powłokę systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="83c06-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
<span data-ttu-id="83c06-108">W przypadku większości aplikacji nie trzeba tworzyć własnej domeny aplikacji. Host środowiska uruchomieniowego tworzy wszystkie wymagane domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="83c06-109">Można jednak utworzyć i skonfigurować dodatkowe domeny aplikacji, jeśli aplikacja wymaga odizolowania kodu lub użycia i zwolnienia bibliotek DLL.</span><span class="sxs-lookup"><span data-stu-id="83c06-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83c06-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="83c06-110">In This Section</span></span>  

[<span data-ttu-id="83c06-111">Instrukcje: tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="83c06-111">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)  
<span data-ttu-id="83c06-112">Opisuje sposób programowego tworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-112">Describes how to programmatically create an application domain.</span></span>  
  
[<span data-ttu-id="83c06-113">Instrukcje: zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="83c06-113">How to: Unload an Application Domain</span></span>](how-to-unload-an-application-domain.md)  
<span data-ttu-id="83c06-114">Opisuje sposób programowego zwalniania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-114">Describes how to programmatically unload an application domain.</span></span>  
  
[<span data-ttu-id="83c06-115">Instrukcje: konfigurowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="83c06-115">How to: Configure an Application Domain</span></span>](how-to-configure-an-application-domain.md)  
<span data-ttu-id="83c06-116">Zawiera wprowadzenie do konfigurowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-116">Provides an introduction to configuring an application domain.</span></span>  
  
[<span data-ttu-id="83c06-117">Pobieranie informacji o instalacji z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="83c06-117">Retrieving Setup Information from an Application Domain</span></span>](retrieve-setup-information.md)  
<span data-ttu-id="83c06-118">Opisuje sposób pobierania informacji o instalacji z domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
[<span data-ttu-id="83c06-119">Instrukcje: ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="83c06-119">How to: Load Assemblies into an Application Domain</span></span>](how-to-load-assemblies-into-an-application-domain.md)  
<span data-ttu-id="83c06-120">Opisuje sposób ładowania zestawu do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-120">Describes how to load an assembly into an application domain.</span></span>  
  
[<span data-ttu-id="83c06-121">Instrukcje: uzyskiwanie informacji dotyczących typów i elementów członkowskich z zestawu</span><span class="sxs-lookup"><span data-stu-id="83c06-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../reflection-and-codedom/get-type-member-information.md)  
<span data-ttu-id="83c06-122">Opisuje sposób pobierania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="83c06-122">Describes how to retrieve information about an assembly.</span></span>  
  
[<span data-ttu-id="83c06-123">Kopiowanie zestawów w tle</span><span class="sxs-lookup"><span data-stu-id="83c06-123">Shadow Copying Assemblies</span></span>](shadow-copy-assemblies.md)  
<span data-ttu-id="83c06-124">Opisuje, w jaki sposób kopiowanie w tle umożliwia aktualizowanie zestawów, gdy są używane, oraz sposób konfigurowania kopiowania w tle.</span><span class="sxs-lookup"><span data-stu-id="83c06-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
[<span data-ttu-id="83c06-125">Instrukcje: odbieranie powiadomień o wyjątkach pierwszej szansy</span><span class="sxs-lookup"><span data-stu-id="83c06-125">How to: Receive First-Chance Exception Notifications</span></span>](how-to-receive-first-chance-exception-notifications.md)  
<span data-ttu-id="83c06-126">Wyjaśnia, jak można odebrać powiadomienie zgłoszone przez wyjątek, zanim środowisko uruchomieniowe języka wspólnego rozpoczęło wyszukiwanie obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="83c06-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
[<span data-ttu-id="83c06-127">Rozwiązywanie załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="83c06-127">Resolving Assembly Loads</span></span>](../../standard/assembly/resolve-loads.md)  
<span data-ttu-id="83c06-128">Zawiera wskazówki dotyczące używania zdarzenia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> do rozwiązywania niepowodzeń ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="83c06-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="83c06-129">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="83c06-129">Reference</span></span>  

<xref:System.AppDomain>  
<span data-ttu-id="83c06-130">Reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-130">Represents an application domain.</span></span> <span data-ttu-id="83c06-131">Zapewnia metody tworzenia i kontrolowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="83c06-132">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="83c06-132">Related Sections</span></span>  
[<span data-ttu-id="83c06-133">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="83c06-133">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="83c06-134">Zawiera przegląd funkcji wykonywanych przez zestawy.</span><span class="sxs-lookup"><span data-stu-id="83c06-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
[<span data-ttu-id="83c06-135">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="83c06-135">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="83c06-136">Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="83c06-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
[<span data-ttu-id="83c06-137">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="83c06-137">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="83c06-138">Opisuje sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="83c06-138">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="83c06-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="83c06-139">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="83c06-140">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83c06-140">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="83c06-141">Przegląd odbicia</span><span class="sxs-lookup"><span data-stu-id="83c06-141">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="83c06-142">Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="83c06-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
