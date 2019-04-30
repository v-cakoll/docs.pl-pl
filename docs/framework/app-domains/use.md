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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674896"
---
# <a name="using-application-domains"></a><span data-ttu-id="c0e68-102">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0e68-102">Using Application Domains</span></span>
<span data-ttu-id="c0e68-103">Domen aplikacji zapewniają jednostkę izolacji dla środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="c0e68-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="c0e68-104">Są one tworzone i uruchamiane wewnątrz procesu.</span><span class="sxs-lookup"><span data-stu-id="c0e68-104">They are created and run inside a process.</span></span> <span data-ttu-id="c0e68-105">Domeny aplikacji są zwykle tworzone przez hosta środowiska uruchomieniowego, czyli aplikacji, które są odpowiedzialne za ładowanie środowiska uruchomieniowego do procesu i wykonywanie kodu użytkownika w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0e68-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="c0e68-106">Host środowiska uruchomieniowego tworzy proces i domyślnej domeny aplikacji i uruchamia kodu zarządzanego wewnątrz niego.</span><span class="sxs-lookup"><span data-stu-id="c0e68-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="c0e68-107">Hosty środowiska uruchomieniowego obejmują usługę ASP.NET, Microsoft Internet Explorer oraz powłoki Windows.</span><span class="sxs-lookup"><span data-stu-id="c0e68-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="c0e68-108">W przypadku większości aplikacji nie trzeba tworzyć własną domenę aplikacji. host środowiska uruchomieniowego tworzy wszystkie domeny aplikacji konieczne.</span><span class="sxs-lookup"><span data-stu-id="c0e68-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="c0e68-109">Można jednak utworzyć i skonfigurować domeny dodatkowych aplikacji, jeśli Twoja aplikacja potrzebuje do izolowania kodu lub do użycia i zwalnianie bibliotek DLL.</span><span class="sxs-lookup"><span data-stu-id="c0e68-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0e68-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c0e68-110">In This Section</span></span>  
 [<span data-ttu-id="c0e68-111">Instrukcje: Tworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0e68-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="c0e68-112">W tym artykule opisano, jak programowo utworzyć domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0e68-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="c0e68-113">Instrukcje: Zwolnienie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0e68-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="c0e68-114">W tym artykule opisano, jak programowo zwolnienie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0e68-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="c0e68-115">Instrukcje: Konfigurowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0e68-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="c0e68-116">Wprowadzenie do konfigurowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0e68-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="c0e68-117">Pobieranie informacji o instalacji z domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0e68-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="c0e68-118">W tym artykule opisano sposób pobierania informacji o instalacji z domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0e68-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="c0e68-119">Instrukcje: Ładowanie zestawów do domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0e68-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="c0e68-120">W tym artykule opisano sposób ładowania zestawu do domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0e68-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="c0e68-121">Instrukcje: Uzyskiwanie informacji dotyczących elementu członkowskiego typów i z zestawu</span><span class="sxs-lookup"><span data-stu-id="c0e68-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="c0e68-122">W tym artykule opisano, jak pobrać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="c0e68-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="c0e68-123">Kopiowanie zestawów w tle</span><span class="sxs-lookup"><span data-stu-id="c0e68-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="c0e68-124">Opisuje sposób kopiowania w tle zezwala na aktualizacje do zestawów, gdy są one używane oraz skonfigurować kopiowania w tle.</span><span class="sxs-lookup"><span data-stu-id="c0e68-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="c0e68-125">Instrukcje: Odbieranie powiadomień o wyjątkach pierwszej szansy</span><span class="sxs-lookup"><span data-stu-id="c0e68-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="c0e68-126">W tym artykule wyjaśniono, jak otrzymasz powiadomienie, że wygenerowany został wyjątek, zanim środowiska uruchomieniowego języka wspólnego została rozpoczęta, wyszukując obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="c0e68-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="c0e68-127">Rozwiązywanie załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="c0e68-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="c0e68-128">Ten artykuł zawiera wskazówki na temat korzystania z <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie, aby rozwiązać błędy ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="c0e68-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c0e68-129">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c0e68-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="c0e68-130">Reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0e68-130">Represents an application domain.</span></span> <span data-ttu-id="c0e68-131">Zawiera metody służące do tworzenia i kontrolowania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0e68-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0e68-132">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c0e68-132">Related Sections</span></span>  
 [<span data-ttu-id="c0e68-133">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="c0e68-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="c0e68-134">Zawiera omówienie funkcji, wykonywane przez zestawy.</span><span class="sxs-lookup"><span data-stu-id="c0e68-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="c0e68-135">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="c0e68-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="c0e68-136">W tym artykule opisano sposób tworzenia, zaloguj się i ustawianie atrybutów zestawów.</span><span class="sxs-lookup"><span data-stu-id="c0e68-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="c0e68-137">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="c0e68-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="c0e68-138">W tym artykule opisano sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="c0e68-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="c0e68-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0e68-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="c0e68-140">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0e68-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="c0e68-141">Omówienie odbicia</span><span class="sxs-lookup"><span data-stu-id="c0e68-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="c0e68-142">Opisuje sposób używania **odbicia** klasy, aby uzyskać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="c0e68-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
