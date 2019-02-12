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
ms.openlocfilehash: 855a1329c9804e4b40d796c639bbe8768156dcc2
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092504"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="b3e37-102">Debugowanie, śledzenie i profilowanie</span><span class="sxs-lookup"><span data-stu-id="b3e37-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="b3e37-103">Do debugowania aplikacji .NET Framework, kompilatora i środowiska uruchomieniowego musi być skonfigurowana do włączenia debuger, który chcesz dołączyć do aplikacji i aby wygenerować symbole i linii mapy, jeśli to możliwe, dla aplikacji i jej odpowiednie Microsoft intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="b3e37-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="b3e37-104">Po zarządzanych aplikacji został debugowany, mogą być profilowane do poprawienia wydajności.</span><span class="sxs-lookup"><span data-stu-id="b3e37-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="b3e37-105">Profilowanie oblicza i opisuje linie kodu źródłowego, które generują kod najczęściej wykonywaną i ile czas potrzebny do ich wykonania.</span><span class="sxs-lookup"><span data-stu-id="b3e37-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="b3e37-106">Aplikacje programu .NET framework są łatwo debugować za pomocą programu Visual Studio, która obsługuje wiele szczegółów konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b3e37-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="b3e37-107">Jeśli nie zainstalowano programu Visual Studio, możesz sprawdzić i zwiększyć wydajność aplikacji .NET Framework przy użyciu klas debugowania w programie .NET Framework <xref:System.Diagnostics> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b3e37-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="b3e37-108">Ta przestrzeń nazw zawiera <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, i <xref:System.Diagnostics.TraceSource> klasy w celu śledzenia wykonywania przepływu, a <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, i <xref:System.Diagnostics.PerformanceCounter> klas na potrzeby profilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="b3e37-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3e37-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b3e37-109">In This Section</span></span>  
 [<span data-ttu-id="b3e37-110">Włączanie debugowania dołączania JIT</span><span class="sxs-lookup"><span data-stu-id="b3e37-110">Enabling JIT-Attach Debugging</span></span>](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 <span data-ttu-id="b3e37-111">Pokazuje, jak skonfigurować rejestr w celu dołączania JIT aparatu debugowania aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3e37-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="b3e37-112">Ułatwianie debugowania obrazu</span><span class="sxs-lookup"><span data-stu-id="b3e37-112">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 <span data-ttu-id="b3e37-113">Pokazuje, jak wyłączyć śledzenia JIT na i optymalizacji ułatwiają zestaw do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b3e37-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="b3e37-114">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="b3e37-114">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="b3e37-115">W tym artykule opisano, jak monitorować wykonywanie aplikacji, gdy jest uruchomiona i w jaki sposób do Instrumentacji go, aby wyświetlić jak dobrze działa, czy Niestety, wystąpił problem.</span><span class="sxs-lookup"><span data-stu-id="b3e37-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="b3e37-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="b3e37-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="b3e37-117">W tym artykule opisano asystentów zarządzanego debugowania (mda), które są Debugowanie — pomoce, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR) zawiera informacje na temat stanu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b3e37-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="b3e37-118">Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera</span><span class="sxs-lookup"><span data-stu-id="b3e37-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="b3e37-119">W tym artykule opisano, jak Deweloper typ można określić, co typ będzie wyglądać po wyświetleniu go w debugerze.</span><span class="sxs-lookup"><span data-stu-id="b3e37-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="b3e37-120">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="b3e37-120">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 <span data-ttu-id="b3e37-121">W tym artykule opisano liczniki, które służą do śledzenia wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3e37-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b3e37-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b3e37-122">Related Sections</span></span>  
 [<span data-ttu-id="b3e37-123">Debugowanie aplikacji ASP.NET lub ASP.NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b3e37-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/debugging-aspnet-and-ajax-applications)  
 <span data-ttu-id="b3e37-124">Zawiera wymagania wstępne i instrukcje dotyczące sposobu debugowania aplikacji ASP.NET, podczas tworzenia lub po wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="b3e37-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="b3e37-125">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="b3e37-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="b3e37-126">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="b3e37-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
