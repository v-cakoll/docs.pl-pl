---
title: Debugowanie, śledzenie i profilowanie
description: Przeczytaj informacje o debugowaniu, śledzeniu i profilowania w programie .NET. Zobacz artykuły dotyczące debugowania (just-in-Time), śledzenia i Instrumentacji aplikacji oraz nie tylko.
ms.date: 03/30/2017
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
ms.openlocfilehash: 745f16652c02e3409e7fa7a48beacbf7e777e924
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415982"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="34be2-104">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="34be2-104">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="34be2-105">Aby debugować aplikację .NET Framework, środowisko kompilatora i środowiska uruchomieniowego musi być skonfigurowane tak, aby umożliwić debugerowi dołączenie do aplikacji i tworzenie zarówno symboli, jak i map wierszy, jeśli to możliwe, dla aplikacji i odpowiedniego języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="34be2-105">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="34be2-106">Po debugowaniu aplikacji zarządzanej można ją profilować w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="34be2-106">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="34be2-107">Profilowanie szacuje i opisuje wiersze kodu źródłowego, które generują najczęściej wykonywany kod, oraz czas ich wykonania.</span><span class="sxs-lookup"><span data-stu-id="34be2-107">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="34be2-108">Aplikacje .NET Framework są łatwo debugowane przy użyciu programu Visual Studio, który obsługuje wiele szczegółów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="34be2-108">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="34be2-109">Jeśli program Visual Studio nie jest zainstalowany, można przeanalizować i poprawić wydajność aplikacji .NET Framework przy użyciu klas debugowania w <xref:System.Diagnostics> przestrzeni nazw .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34be2-109">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="34be2-110">Ta przestrzeń nazw zawiera <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug> klasy,, i <xref:System.Diagnostics.TraceSource> dla przepływu wykonywania śledzenia oraz <xref:System.Diagnostics.Process> klasy, <xref:System.Diagnostics.EventLog> i <xref:System.Diagnostics.PerformanceCounter> dla profilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="34be2-110">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34be2-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="34be2-111">In This Section</span></span>  
 [<span data-ttu-id="34be2-112">Włączanie debugowania dołączania JIT</span><span class="sxs-lookup"><span data-stu-id="34be2-112">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="34be2-113">Pokazuje, jak skonfigurować rejestr do JIT — Dołącz aparat debugowania do aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34be2-113">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="34be2-114">Ułatwianie debugowania obrazu</span><span class="sxs-lookup"><span data-stu-id="34be2-114">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="34be2-115">Pokazuje, jak włączyć i zoptymalizować śledzenie JIT, aby ułatwić debugowanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="34be2-115">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="34be2-116">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="34be2-116">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="34be2-117">Opisuje, jak monitorować wykonywanie aplikacji w trakcie jej działania oraz jak można przyłączyć ją do wyświetlania, jak to działa, lub czy problem został usunięty.</span><span class="sxs-lookup"><span data-stu-id="34be2-117">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="34be2-118">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="34be2-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="34be2-119">Opisuje zarządzane asystentów debugowania (MDA), które są ułatwieniami debugowania, które działają w połączeniu z środowiskiem uruchomieniowym języka wspólnego (CLR) w celu zapewnienia informacji o stanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="34be2-119">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="34be2-120">Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera</span><span class="sxs-lookup"><span data-stu-id="34be2-120">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="34be2-121">Opisuje, w jaki sposób deweloper typu może określić, jaki typ ma wyglądać, gdy zostanie wyświetlony w debugerze.</span><span class="sxs-lookup"><span data-stu-id="34be2-121">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="34be2-122">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="34be2-122">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="34be2-123">Opisuje liczniki, których można użyć do śledzenia wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34be2-123">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="34be2-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="34be2-124">Related Sections</span></span>  
 [<span data-ttu-id="34be2-125">Debugowanie aplikacji platformy ASP.NET lub ASP.NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="34be2-125">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="34be2-126">Zawiera wymagania wstępne i instrukcje dotyczące debugowania aplikacji ASP.NET podczas tworzenia lub po wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="34be2-126">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="34be2-127">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="34be2-127">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="34be2-128">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="34be2-128">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
