---
title: Debugowanie, śledzenie i profilowanie
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e9438ed2c1cd82bb4d89ff082545021b2d543e
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195343"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="708da-102">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="708da-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="708da-103">Aby debugować aplikację .NET Framework, środowisko kompilatora i środowiska uruchomieniowego musi być skonfigurowane tak, aby umożliwić debugerowi dołączenie do aplikacji i tworzenie zarówno symboli, jak i map wierszy, jeśli jest to możliwe, dla aplikacji i jej odpowiadającego pośredniego firmy Microsoft język (MSIL).</span><span class="sxs-lookup"><span data-stu-id="708da-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="708da-104">Po debugowaniu aplikacji zarządzanej można ją profilować w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="708da-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="708da-105">Profilowanie szacuje i opisuje wiersze kodu źródłowego, które generują najczęściej wykonywany kod, oraz czas ich wykonania.</span><span class="sxs-lookup"><span data-stu-id="708da-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="708da-106">Aplikacje .NET Framework są łatwo debugowane przy użyciu programu Visual Studio, który obsługuje wiele szczegółów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="708da-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="708da-107">Jeśli program Visual Studio nie jest zainstalowany, można przeanalizować i poprawić wydajność aplikacji .NET Framework przy użyciu klas debugowania w przestrzeni nazw .NET Framework <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="708da-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="708da-108">Ta przestrzeń nazw zawiera klasy <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>i <xref:System.Diagnostics.TraceSource> dla przepływu wykonywania śledzenia, a także klasy <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>i <xref:System.Diagnostics.PerformanceCounter> na potrzeby profilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="708da-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="708da-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="708da-109">In This Section</span></span>  
 [<span data-ttu-id="708da-110">Włączanie debugowania dołączania JIT</span><span class="sxs-lookup"><span data-stu-id="708da-110">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="708da-111">Pokazuje, jak skonfigurować rejestr do JIT — Dołącz aparat debugowania do aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="708da-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="708da-112">Ułatwianie debugowania obrazu</span><span class="sxs-lookup"><span data-stu-id="708da-112">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="708da-113">Pokazuje, jak włączyć i zoptymalizować śledzenie JIT, aby ułatwić debugowanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="708da-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="708da-114">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="708da-114">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="708da-115">Opisuje, jak monitorować wykonywanie aplikacji w trakcie jej działania oraz jak można przyłączyć ją do wyświetlania, jak to działa, lub czy problem został usunięty.</span><span class="sxs-lookup"><span data-stu-id="708da-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="708da-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="708da-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="708da-117">Opisuje zarządzane asystentów debugowania (MDA), które są ułatwieniami debugowania, które działają w połączeniu z środowiskiem uruchomieniowym języka wspólnego (CLR) w celu zapewnienia informacji o stanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="708da-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="708da-118">Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera</span><span class="sxs-lookup"><span data-stu-id="708da-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="708da-119">Opisuje, w jaki sposób deweloper typu może określić, jaki typ ma wyglądać, gdy zostanie wyświetlony w debugerze.</span><span class="sxs-lookup"><span data-stu-id="708da-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="708da-120">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="708da-120">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="708da-121">Opisuje liczniki, których można użyć do śledzenia wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="708da-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="708da-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="708da-122">Related Sections</span></span>  
 [<span data-ttu-id="708da-123">Debuguj ASP.NET lub ASP.NET Core aplikacje w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="708da-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="708da-124">Zawiera wymagania wstępne i instrukcje dotyczące debugowania aplikacji ASP.NET podczas tworzenia lub po wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="708da-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="708da-125">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="708da-125">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="708da-126">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="708da-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
