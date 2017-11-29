---
title: "Debugowanie, śledzenie i profilowanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
caps.latest.revision: "28"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 21032358c9edb1b79d9e170e477502670f781fc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="bd017-102">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="bd017-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="bd017-103">Do debugowania aplikacji .NET Framework, kompilatora i środowiska uruchomieniowego musi być skonfigurowane do włączenia debugera dołączyć do aplikacji i zarówno symbole i linii mapy, jeśli to możliwe, aplikacji i jej odpowiednie Microsoft pośredni język (MSIL).</span><span class="sxs-lookup"><span data-stu-id="bd017-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="bd017-104">Po zarządzanej aplikacji został debugowania, mogą być profilowane zwiększania wydajności.</span><span class="sxs-lookup"><span data-stu-id="bd017-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="bd017-105">Profilowanie ocenia i opisuje wierszy kodu źródłowego z generowaniem kodu najczęściej wykonywane, i ile czasu potrzebnego na ich wykonanie.</span><span class="sxs-lookup"><span data-stu-id="bd017-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="bd017-106">Aplikacji programu .NET framework są łatwo debugować przy użyciu programu Visual Studio, która obsługuje wiele informacji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bd017-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="bd017-107">Jeśli nie zainstalowano programu Visual Studio, możesz sprawdzić i zwiększanie wydajności aplikacji .NET Framework za pomocą klasy debugowania w programie .NET Framework <xref:System.Diagnostics> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bd017-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="bd017-108">Ta przestrzeń nazw zawiera <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, i <xref:System.Diagnostics.TraceSource> klasy śledzenia przepływu wykonywania i <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, i <xref:System.Diagnostics.PerformanceCounter> klasy dla profilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="bd017-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd017-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bd017-109">In This Section</span></span>  
 [<span data-ttu-id="bd017-110">Włączanie debugowanie dołączania JIT</span><span class="sxs-lookup"><span data-stu-id="bd017-110">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 <span data-ttu-id="bd017-111">Pokazuje, jak skonfigurować rejestr w celu dołączania JIT to aparat debugowania aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bd017-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="bd017-112">Ułatwianie debugowania obrazu</span><span class="sxs-lookup"><span data-stu-id="bd017-112">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 <span data-ttu-id="bd017-113">Pokazuje, jak wyłączyć śledzenia JIT na i optymalizacji ułatwiające debugowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="bd017-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="bd017-114">Śledzenie i Instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="bd017-114">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="bd017-115">Opisuje sposób monitorowania wykonywanie aplikacji, gdy jest on uruchomiony i jak możliwość agregowania go, aby wyświetlić jak wykonuje czy też coś niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="bd017-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="bd017-116">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="bd017-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="bd017-117">W tym artykule opisano Asystenci zarządzanego debugowania (mda), które pomocy, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR), aby podać informacje dotyczące stanu środowiska uruchomieniowego debugowania.</span><span class="sxs-lookup"><span data-stu-id="bd017-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="bd017-118">Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera</span><span class="sxs-lookup"><span data-stu-id="bd017-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="bd017-119">W tym artykule opisano, jak developer typu można określić co typu będą wyglądać po wyświetleniu go w debugerze.</span><span class="sxs-lookup"><span data-stu-id="bd017-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="bd017-120">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="bd017-120">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 <span data-ttu-id="bd017-121">W tym artykule opisano liczniki, które można śledzić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd017-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bd017-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bd017-122">Related Sections</span></span>  
 [<span data-ttu-id="bd017-123">Debugowanie aplikacji ASP.NET i AJAX</span><span class="sxs-lookup"><span data-stu-id="bd017-123">Debugging ASP.NET and AJAX Applications</span></span>](http://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 <span data-ttu-id="bd017-124">Zawiera wymagania wstępne i instrukcje dotyczące debugowania aplikacji ASP.NET, podczas tworzenia lub po wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="bd017-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="bd017-125">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="bd017-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="bd017-126">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="bd017-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
