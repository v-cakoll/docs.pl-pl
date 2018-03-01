---
title: ".NET Framework — podręcznik programowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d7950ae39ada3e1e0e070967f8d578fc3371126
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="net-framework-development-guide"></a><span data-ttu-id="ebde5-102">.NET Framework — podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="ebde5-102">.NET Framework Development Guide</span></span>
<span data-ttu-id="ebde5-103">W tej sekcji opisano sposób tworzenia, konfigurowanie debugowania, zabezpieczenia i wdrażanie aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebde5-103">This section explains how to create, configure, debug, secure, and deploy your .NET Framework apps.</span></span> <span data-ttu-id="ebde5-104">Sekcja ta zawiera też informacji na temat obszarów technologii, takich jak dynamiczne programowania, współdziałanie rozszerzalności, zarządzanie pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="ebde5-104">The section also provides information about technology areas such as dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ebde5-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ebde5-105">In This Section</span></span>  
 [<span data-ttu-id="ebde5-106">Podstawy aplikacji</span><span class="sxs-lookup"><span data-stu-id="ebde5-106">Application Essentials</span></span>](../../docs/standard/application-essentials.md)  
 <span data-ttu-id="ebde5-107">Zawiera informacje o aplikacji podstawowych zadań związanych z projektowaniem, takich jak programowania za pomocą zestawów i domen aplikacji, przy użyciu atrybutów, formatowanie i analizowania typów podstawowych, przy użyciu kolekcji, obsługi zdarzeń i wyjątków, przy użyciu plików i strumieni danych i przy użyciu typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="ebde5-107">Provides information about basic app development tasks, such as programming with app domains and assemblies, using attributes, formatting and parsing base types, using collections, handling events and exceptions, using files and data streams, and using generics.</span></span>  
  
 [<span data-ttu-id="ebde5-108">Dane i modelowanie</span><span class="sxs-lookup"><span data-stu-id="ebde5-108">Data and Modeling</span></span>](../../docs/framework/data/index.md)  
 <span data-ttu-id="ebde5-109">Zawiera informacje o tym, jak uzyskać dostęp do danych za pomocą ADO.NET, język kwerendy zintegrowanym (LINQ), usługi danych WCF i XML.</span><span class="sxs-lookup"><span data-stu-id="ebde5-109">Provides information about how to access data using ADO.NET, Language Integrated Query (LINQ), WCF Data Services, and XML.</span></span>  
  
 [<span data-ttu-id="ebde5-110">Aplikacje klienckie</span><span class="sxs-lookup"><span data-stu-id="ebde5-110">Client Applications</span></span>](../../docs/framework/develop-client-apps.md)  
 <span data-ttu-id="ebde5-111">Wyjaśnia sposób tworzenia aplikacji opartych na systemie Windows przy użyciu systemu Windows Presentation Foundation (WPF) lub program Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ebde5-111">Explains how to create Windows-based apps by using Windows Presentation Foundation (WPF) or Windows Forms.</span></span>  
  
 [<span data-ttu-id="ebde5-112">Aplikacje sieci Web wykorzystujące technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ebde5-112">Web Applications with ASP.NET</span></span>](../../docs/framework/develop-web-apps-with-aspnet.md)  
 <span data-ttu-id="ebde5-113">Zawiera linki do informacji o korzystaniu z programu ASP.NET do tworzenia aplikacji sieci web z co najmniej kodowania klasy korporacyjnej.</span><span class="sxs-lookup"><span data-stu-id="ebde5-113">Provides links to information about using ASP.NET to build enterprise-class web apps with a minimum of coding.</span></span>  
  
 [<span data-ttu-id="ebde5-114">Zorientowane na usługę aplikacje z usługą WCF</span><span class="sxs-lookup"><span data-stu-id="ebde5-114">Service-Oriented Applications with WCF</span></span>](../../docs/framework/wcf/index.md)  
 <span data-ttu-id="ebde5-115">Informacje dotyczące używania usług Windows Communication Foundation (WCF), aby tworzyć aplikacje zorientowane na usługę, które są bezpieczne i niezawodne.</span><span class="sxs-lookup"><span data-stu-id="ebde5-115">Describes how to use Windows Communication Foundation (WCF) to build service-oriented apps that are secure and reliable.</span></span>  
  
 <span data-ttu-id="ebde5-116">[Tworzenie przepływów z programu Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span><span class="sxs-lookup"><span data-stu-id="ebde5-116">[Building workflows with Windows Workflow Foundation](windows-workflow-foundation/index.md)   </span></span>  
 <span data-ttu-id="ebde5-117">Zawiera informacje o modelu programowania, przykłady i narzędzia dotyczące korzystania z usługi Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="ebde5-117">Provides information about the programming model, samples, and tools for using Windows Workflow Foundation (WF).</span></span>  

 [<span data-ttu-id="ebde5-118">Aplikacje usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ebde5-118">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
 <span data-ttu-id="ebde5-119">W tym artykule wyjaśniono, jak utworzyć aplikację, która jest zainstalowana jako usługę i uruchamiania, Zatrzymaj, a w przeciwnym razie kontrolowanie swojego zachowania można użyć programu Visual Studio i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebde5-119">Explains how you can use Visual Studio and the .NET Framework to create an app that is installed as a service, and start, stop, and otherwise control its behavior.</span></span>  
  
 [<span data-ttu-id="ebde5-120">Przetwarzanie równoległe i współbieżność</span><span class="sxs-lookup"><span data-stu-id="ebde5-120">Parallel Processing and Concurrency</span></span>](../../docs/standard/parallel-processing-and-concurrency.md)  
 <span data-ttu-id="ebde5-121">Zawiera informacje o zarządzanych wątków Programowanie równoległe i asynchroniczne wzorce projektowe programowania.</span><span class="sxs-lookup"><span data-stu-id="ebde5-121">Provides information about managed threading, parallel programming, and asynchronous programming design patterns.</span></span>  
  
 [<span data-ttu-id="ebde5-122">Programowanie dla sieci w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ebde5-122">Network Programming in the .NET Framework</span></span>](../../docs/framework/network-programming/index.md)  
 <span data-ttu-id="ebde5-123">W tym artykule opisano warstwowych, rozszerzalne i zarządzane wdrożenia usług internetowych, które można szybko i łatwo zintegrować z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebde5-123">Describes the layered, extensible, and managed implementation of Internet services that you can quickly and easily integrate into your apps.</span></span>  
  
 <span data-ttu-id="ebde5-124">[Konfigurowanie aplikacji programu .NET Framework](configure-apps/index.md)  </span><span class="sxs-lookup"><span data-stu-id="ebde5-124">[Configuring .NET Framework Apps](configure-apps/index.md)  </span></span>  
 <span data-ttu-id="ebde5-125">W tym artykule wyjaśniono, jak pliki konfiguracji można użyć do zmiany ustawień bez konieczności ponownego kompilowania aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebde5-125">Explains how you can use configuration files to change settings without having to recompile your .NET Framework apps.</span></span>  
  
 [<span data-ttu-id="ebde5-126">Kompilowanie aplikacji z architekturą .NET Native</span><span class="sxs-lookup"><span data-stu-id="ebde5-126">Compiling Apps with .NET Native</span></span>](../../docs/framework/net-native/index.md)  
 <span data-ttu-id="ebde5-127">Wyjaśniono, jak używasz [!INCLUDE[net_native](../../includes/net-native-md.md)] technologii wstępnej kompilacji do tworzenia i wdrażania aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="ebde5-127">Explains how you can use the [!INCLUDE[net_native](../../includes/net-native-md.md)] precompilation technology to build and deploy Windows Store apps.</span></span> [!INCLUDE[net_native](../../includes/net-native-md.md)]<span data-ttu-id="ebde5-128">kompiluje aplikacje, które są zapisywane w kodzie zarządzanym (C#) i które dla środowiska .NET Framework do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="ebde5-128"> compiles apps that are written in managed code (C#) and that target the .NET Framework to native code.</span></span>  
  
 [<span data-ttu-id="ebde5-129">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ebde5-129">Security</span></span>](../../docs/standard/security/index.md)  
 <span data-ttu-id="ebde5-130">Informacje na temat klas i usług w programie .NET Framework, które ułatwiają tworzenie aplikacji bezpiecznego.</span><span class="sxs-lookup"><span data-stu-id="ebde5-130">Provides information about the classes and services in the .NET Framework that facilitate secure app development.</span></span>  
  
 [<span data-ttu-id="ebde5-131">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="ebde5-131">Debugging, Tracing, and Profiling</span></span>](../../docs/framework/debug-trace-profile/index.md)  
 <span data-ttu-id="ebde5-132">Wyjaśniono, jak do testowania, optymalizacja i profilu aplikacji .NET Framework i środowiska aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebde5-132">Explains how to test, optimize, and profile .NET Framework apps and the app environment.</span></span> <span data-ttu-id="ebde5-133">Ta sekcja zawiera informacje dla administratorów, a także deweloperom.</span><span class="sxs-lookup"><span data-stu-id="ebde5-133">This section includes information for administrators as well as developers.</span></span>  
  
 [<span data-ttu-id="ebde5-134">Tworzenie aplikacji dla wielu platform</span><span class="sxs-lookup"><span data-stu-id="ebde5-134">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="ebde5-135">Zawiera informacje na temat wykorzystania programu .NET Framework do kompilacji zestawy, które mogą być współużytkowane przez wiele platform i wielu urządzeń, takich jak telefony, pulpitu i sieci web.</span><span class="sxs-lookup"><span data-stu-id="ebde5-135">Provides information about how you can use the .NET Framework to build assemblies that can be shared across multiple platforms and multiple devices such as phones, desktop, and web.</span></span>  
  
 [<span data-ttu-id="ebde5-136">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="ebde5-136">Deployment</span></span>](../../docs/framework/deployment/index.md)  
 <span data-ttu-id="ebde5-137">Wyjaśniono, jak pakietu i rozproszyć aplikacji .NET Framework i zawiera wskazówki dotyczące wdrażania dla administratorów i deweloperów.</span><span class="sxs-lookup"><span data-stu-id="ebde5-137">Explains how to package and distribute your .NET Framework app, and includes deployment guides for both developers and administrators.</span></span>  
  
 [<span data-ttu-id="ebde5-138">Wydajność</span><span class="sxs-lookup"><span data-stu-id="ebde5-138">Performance</span></span>](../../docs/framework/performance/index.md)  
 <span data-ttu-id="ebde5-139">Zawiera informacje o pamięci podręcznej, inicjowania z opóźnieniem, niezawodności i zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="ebde5-139">Provides information about caching, lazy initialization, reliability, and ETW events.</span></span>  
  
 <!--zz [Advanced Reading for the .NET Framework](http://msdn.microsoft.com/library/faae8083-fecb-4514-b133-b0a5a32a7c3c)  
 Provides information about advanced development tasks and techniques in the .NET Framework, including extensibility, interoperability, and reflection. Also includes the reference topics for unmanaged APIs that can be used by managed apps, such as runtime hosts, compilers, disassemblers, debuggers, and profilers.  --> 
  
## <a name="reference"></a><span data-ttu-id="ebde5-140">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ebde5-140">Reference</span></span>  
 [<span data-ttu-id="ebde5-141">Biblioteka klas programu .NET framework</span><span class="sxs-lookup"><span data-stu-id="ebde5-141">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.7)  
 <span data-ttu-id="ebde5-142">Dostarcza składni, przykłady kodu i informacje o użyciu dla każdej klasy, który jest zawarty w [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ebde5-142">Supplies syntax, code examples, and usage information for each class that is contained in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ebde5-143">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ebde5-143">Related Sections</span></span>  
 [<span data-ttu-id="ebde5-144">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="ebde5-144">Getting Started</span></span>](../../docs/framework/get-started/index.md)  
 <span data-ttu-id="ebde5-145">Wyczerpujące omówienie programu .NET Framework i łącza do dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="ebde5-145">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>  
  
 [<span data-ttu-id="ebde5-146">Co nowego</span><span class="sxs-lookup"><span data-stu-id="ebde5-146">What's New</span></span>](../../docs/framework/whats-new/index.md)  
 <span data-ttu-id="ebde5-147">Opisuje Najważniejsze nowe funkcje i zmiany w najnowszej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebde5-147">Describes key new features and changes in the latest version of the .NET Framework.</span></span> <span data-ttu-id="ebde5-148">Zawiera listę nowych i przestarzałe typy i składniki i udostępnia Przewodnik po migracji aplikacji z poprzedniej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebde5-148">Includes lists of new and obsolete types and members, and provides a guide for migrating your apps from the previous version of the .NET Framework.</span></span>  
  
 [<span data-ttu-id="ebde5-149">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="ebde5-149">Tools</span></span>](../../docs/framework/tools/index.md)  
 <span data-ttu-id="ebde5-150">W tym artykule opisano narzędzia, które ułatwiają tworzenie, konfigurować i wdrażać aplikacje przy użyciu technologii .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebde5-150">Describes the tools that help you develop, configure, and deploy apps by using .NET Framework technologies.</span></span>  
  
 [<span data-ttu-id="ebde5-151">.NET framework — przykłady</span><span class="sxs-lookup"><span data-stu-id="ebde5-151">.NET Framework Samples</span></span>](http://msdn.microsoft.com/library/177055f8-4a1f-43e7-aee6-995c196079b1)  
 <span data-ttu-id="ebde5-152">Zawiera łącza do galerii przykładów kodu MSDN przykładowych aplikacji, które przedstawiają technologii .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebde5-152">Provides links to the MSDN Code Samples Gallery for sample apps that demonstrate .NET Framework technologies.</span></span>
