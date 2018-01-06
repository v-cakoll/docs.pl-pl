---
title: "Kompilowanie aplikacji z architekturą .NET Native"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dec4d465b53f939f8fa711950ba6a000bd304e13
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="dbcd0-102">Kompilowanie aplikacji z architekturą .NET Native</span><span class="sxs-lookup"><span data-stu-id="dbcd0-102">Compiling Apps with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="dbcd0-103">jest to technologia wstępnej kompilacji umożliwiające tworzenie i wdrażanie aplikacji systemu Windows, która jest dołączana do programu Visual Studio 2015 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-103"> is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="dbcd0-104">Kompiluje automatycznie wersji aplikacji, które są zapisywane w kodu zarządzanego (C# lub Visual Basic), że docelowej platformy .NET Framework i Windows 10 do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>  
  
 <span data-ttu-id="dbcd0-105">Zwykle aplikacje, które odnoszą się do programu .NET Framework są kompilowane do języku pośrednim (IL).</span><span class="sxs-lookup"><span data-stu-id="dbcd0-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="dbcd0-106">W czasie wykonywania przy użyciu kompilatora just in time (JIT) tłumaczy IL do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="dbcd0-107">Z kolei [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompiluje aplikacji systemu Windows bezpośrednio do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-107">In contrast, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiles Windows apps directly to native code.</span></span> <span data-ttu-id="dbcd0-108">Dla deweloperów oznacza to:</span><span class="sxs-lookup"><span data-stu-id="dbcd0-108">For developers, this means:</span></span>  
  
-   <span data-ttu-id="dbcd0-109">Aplikacje funkcji wydajność kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="dbcd0-110">Zwykle wydajność będzie nadrzędne w stosunku do kodu, który jest najpierw skompilować do IL i następnie skompilowanych do natywnego kodu przy użyciu kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span> 
  
-   <span data-ttu-id="dbcd0-111">Można kontynuować do programowania w języku C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-111">You can continue to program in C# or Visual Basic.</span></span>  
  
-   <span data-ttu-id="dbcd0-112">Można nadal korzystać z zasobów udostępnianych przez program .NET Framework, w tym biblioteki klas, pamięci automatycznego zarządzania i odzyskiwanie pamięci i obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>  
  
 <span data-ttu-id="dbcd0-113">Dla użytkowników w aplikacjach [!INCLUDE[net_native](../../../includes/net-native-md.md)] ma następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="dbcd0-113">For users of your apps, [!INCLUDE[net_native](../../../includes/net-native-md.md)] offers these advantages:</span></span>  
  
-   <span data-ttu-id="dbcd0-114">Szybsze wykonywanie w większości scenariuszy i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-114">Faster execution times for the majority of apps and scenarios.</span></span>
  
-   <span data-ttu-id="dbcd0-115">Szybsze uruchamianie w większości scenariuszy i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-115">Faster startup times for the majority of apps and scenarios.</span></span> 
  
-   <span data-ttu-id="dbcd0-116">Niskie koszty wdrożenia i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-116">Low deployment and update costs.</span></span>  
  
-   <span data-ttu-id="dbcd0-117">Zoptymalizowanych pod kątem użycia pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-117">Optimized app memory usage.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="dbcd0-118">Większość aplikacji i scenariusze platformy .NET Native oferuje znacznie szybsze uruchamianie i lepszą wydajność w porównaniu do aplikacji kompilowane IL lub obrazów NGEN.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="dbcd0-119">Jednak wyniki mogą być różne.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-119">However, your results may vary.</span></span> <span data-ttu-id="dbcd0-120">W celu zapewnienia aplikacji uzyskał ulepszenia wydajności programu .NET Native, należy porównać jego wydajność, z tym nie - platformy .NET Native wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="dbcd0-121">Aby uzyskać więcej informacji, zobacz [sesja wydajności — omówienie](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="dbcd0-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>
 
<span data-ttu-id="dbcd0-122">Ale [!INCLUDE[net_native](../../../includes/net-native-md.md)] obejmuje więcej niż kompilacji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-122">But [!INCLUDE[net_native](../../../includes/net-native-md.md)] involves more than a compilation to native code.</span></span> <span data-ttu-id="dbcd0-123">Przekształca ją sposób, że aplikacje .NET Framework są wbudowane i wykonywane.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="dbcd0-124">W szczególności:</span><span class="sxs-lookup"><span data-stu-id="dbcd0-124">In particular:</span></span>  
  
-   <span data-ttu-id="dbcd0-125">Podczas wstępnej kompilacji wymagane części programu .NET Framework są statycznie połączone w swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="dbcd0-126">Umożliwia to aplikacji do uruchamiania z bibliotekami lokalnej dla aplikacji programu .NET Framework i kompilator przeprowadzić analizę globalną dostarczać wydajności usługi wins.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="dbcd0-127">W związku z tym aplikacje będą uruchamiać zawsze szybciej nawet po aktualizacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>  
  
-   <span data-ttu-id="dbcd0-128">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Środowiska uruchomieniowego jest zoptymalizowana pod kątem statycznych wstępnej kompilacji i w większość przypadków oferuje lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-128">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="dbcd0-129">W tym samym czasie zachowuje podstawowe funkcje odbicia, które tak produktywności deweloperów.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="dbcd0-130">używa takie same wstecz końcowy jako kompilatora języka C++, która jest zoptymalizowana pod kątem scenariuszy wstępnej kompilacji statycznych.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-130"> uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="dbcd0-131">jest w stanie można wyświetlić zwiększenia wydajności C++ deweloperom kodu zarządzanego, ponieważ używa narzędzia takie same lub podobne jako C++ pod maską, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-131"> is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|<span data-ttu-id="dbcd0-132">C++</span><span class="sxs-lookup"><span data-stu-id="dbcd0-132">C++</span></span>|  
|-|----------------------------------------------------------------|-----------|  
|<span data-ttu-id="dbcd0-133">Biblioteki</span><span class="sxs-lookup"><span data-stu-id="dbcd0-133">Libraries</span></span>|<span data-ttu-id="dbcd0-134">.NET Framework i środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dbcd0-134">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="dbcd0-135">Win32 + środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dbcd0-135">Win32 + Windows Runtime</span></span>|  
|<span data-ttu-id="dbcd0-136">Kompilatora</span><span class="sxs-lookup"><span data-stu-id="dbcd0-136">Compiler</span></span>|<span data-ttu-id="dbcd0-137">Optymalizacja kompilatora UTC</span><span class="sxs-lookup"><span data-stu-id="dbcd0-137">UTC optimizing compiler</span></span>|<span data-ttu-id="dbcd0-138">Optymalizacja kompilatora UTC</span><span class="sxs-lookup"><span data-stu-id="dbcd0-138">UTC optimizing compiler</span></span>|  
|<span data-ttu-id="dbcd0-139">Wdrożony</span><span class="sxs-lookup"><span data-stu-id="dbcd0-139">Deployed</span></span>|<span data-ttu-id="dbcd0-140">Pliki binarne gotowy do uruchomienia</span><span class="sxs-lookup"><span data-stu-id="dbcd0-140">Ready-to-run binaries</span></span>|<span data-ttu-id="dbcd0-141">Pliki binarne gotowy do uruchomienia (ASM)</span><span class="sxs-lookup"><span data-stu-id="dbcd0-141">Ready-to-run binaries (ASM)</span></span>|  
|<span data-ttu-id="dbcd0-142">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="dbcd0-142">Runtime</span></span>|<span data-ttu-id="dbcd0-143">MRT.dll (środowisko uruchomieniowe CLR minimalnego)</span><span class="sxs-lookup"><span data-stu-id="dbcd0-143">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="dbcd0-144">CRT.dll (C Runtime)</span><span class="sxs-lookup"><span data-stu-id="dbcd0-144">CRT.dll (C Runtime)</span></span>|  
  
 <span data-ttu-id="dbcd0-145">Dla aplikacji systemu Windows dla systemu Windows 10 możesz przekazać dane binarne kompilacja kodu natywnego platformy .NET w pakiety aplikacji (pliki .appx) do Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-145">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dbcd0-146">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dbcd0-146">In This Section</span></span>  
 <span data-ttu-id="dbcd0-147">Aby uzyskać więcej informacji na temat tworzenia aplikacji za pomocą natywnej kompilacji kodu .NET zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="dbcd0-147">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>  
  
-   [<span data-ttu-id="dbcd0-148">Wprowadzenie do korzystania z natywnej kompilacji kodu .NET: wskazówki środowisko dewelopera</span><span class="sxs-lookup"><span data-stu-id="dbcd0-148">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   <span data-ttu-id="dbcd0-149">[Platforma .NET native i kompilacja:](../../../docs/framework/net-native/net-native-and-compilation.md) jak platforma .NET Native kompiluje projektu do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="dbcd0-149">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>  
  
-   [<span data-ttu-id="dbcd0-150">Odbicie i architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="dbcd0-150">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [<span data-ttu-id="dbcd0-151">Interfejsy API, które działają na podstawie odbicia</span><span class="sxs-lookup"><span data-stu-id="dbcd0-151">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [<span data-ttu-id="dbcd0-152">Dokumentacja interfejsu API odbicia</span><span class="sxs-lookup"><span data-stu-id="dbcd0-152">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [<span data-ttu-id="dbcd0-153">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="dbcd0-153">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [<span data-ttu-id="dbcd0-154">Serializacja i metadane</span><span class="sxs-lookup"><span data-stu-id="dbcd0-154">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [<span data-ttu-id="dbcd0-155">Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native</span><span class="sxs-lookup"><span data-stu-id="dbcd0-155">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [<span data-ttu-id="dbcd0-156">Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native</span><span class="sxs-lookup"><span data-stu-id="dbcd0-156">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## <a name="see-also"></a><span data-ttu-id="dbcd0-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbcd0-157">See Also</span></span>  
 [<span data-ttu-id="dbcd0-158">.NET natywnego — często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="dbcd0-158">.NET Native FAQ</span></span>](http://msdn.microsoft.com/vstudio/dn642499.aspx)
