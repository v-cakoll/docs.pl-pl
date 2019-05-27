---
title: Kompilowanie aplikacji z architekturą .NET Native
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28b09bf07d831747be0006ffe1f1d8c5ac5171ce
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052643"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="cc169-102">Kompilowanie aplikacji z architekturą .NET Native</span><span class="sxs-lookup"><span data-stu-id="cc169-102">Compiling Apps with .NET Native</span></span>
<span data-ttu-id="cc169-103">.NET native jest technologia kompilacji wstępnej do kompilowania i wdrażania aplikacji Windows, który jest dołączony do programu Visual Studio 2015 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="cc169-103">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="cc169-104">Automatycznie skompiluje wersji aplikacji, które są zapisywane w kodzie zarządzanym (C# lub Visual Basic) i przeznaczone na platformę .NET Framework i Windows 10 do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="cc169-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>  
  
 <span data-ttu-id="cc169-105">Zazwyczaj aplikacje, które obsługują program .NET Framework są kompilowane do języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="cc169-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="cc169-106">W czasie wykonywania kompilator just-in-time (JIT) tłumaczy IL do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="cc169-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="cc169-107">Z kolei .NET Native kompiluje aplikacje Windows bezpośrednio do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="cc169-107">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="cc169-108">Dla deweloperów oznacza to:</span><span class="sxs-lookup"><span data-stu-id="cc169-108">For developers, this means:</span></span>  
  
- <span data-ttu-id="cc169-109">Twoje aplikacje są wyposażone w wydajności kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="cc169-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="cc169-110">Zwykle wydajność będzie nadrzędne w stosunku do kodu, który jest najpierw skompilowane do IL, a następnie kompilowane do kodu macierzystego przy użyciu kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="cc169-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span> 
  
- <span data-ttu-id="cc169-111">Można kontynuować programu C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cc169-111">You can continue to program in C# or Visual Basic.</span></span>  
  
- <span data-ttu-id="cc169-112">Można nadal korzystać z zasobów udostępnianych przez .NET Framework, w tym jego biblioteki klas, pamięcią automatyczną zarządzania i wyrzucania elementów kolekcji i obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cc169-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>  
  
 <span data-ttu-id="cc169-113">W przypadku użytkowników aplikacji .NET Native oferuje następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="cc169-113">For users of your apps, .NET Native offers these advantages:</span></span>  
  
- <span data-ttu-id="cc169-114">Krótszy czas wykonywania dla większości scenariuszy i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc169-114">Faster execution times for the majority of apps and scenarios.</span></span>
  
- <span data-ttu-id="cc169-115">Krótszy czas uruchamiania dla większości scenariuszy i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc169-115">Faster startup times for the majority of apps and scenarios.</span></span> 
  
- <span data-ttu-id="cc169-116">Niskie koszty wdrożenia i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="cc169-116">Low deployment and update costs.</span></span>  
  
- <span data-ttu-id="cc169-117">Zoptymalizowane pod kątem użycia pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc169-117">Optimized app memory usage.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="cc169-118">Większość aplikacji i scenariuszy .NET Native oferuje znacznie krótszy czas uruchamiania i doskonałą wydajność w porównaniu do aplikacji skompilowanych IL lub obrazów NGEN.</span><span class="sxs-lookup"><span data-stu-id="cc169-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="cc169-119">Jednak wyniki mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="cc169-119">However, your results may vary.</span></span> <span data-ttu-id="cc169-120">Aby upewnić się, że aplikacja skorzystał z ulepszenia wydajności programu .NET Native, należy porównać jego wydajność, korzystając z niego bez — .NET Native wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc169-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="cc169-121">Aby uzyskać więcej informacji, zobacz [sesja wydajności — omówienie](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="cc169-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>
 
<span data-ttu-id="cc169-122">Jednak .NET Native obejmuje więcej niż kompilacji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="cc169-122">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="cc169-123">Jego zmienia sposób skompilowane i wykonywane aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc169-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="cc169-124">W szczególności:</span><span class="sxs-lookup"><span data-stu-id="cc169-124">In particular:</span></span>  
  
- <span data-ttu-id="cc169-125">Podczas wstępnej kompilacji wymagane części programu .NET Framework są łączone statycznie z Twoją aplikacją.</span><span class="sxs-lookup"><span data-stu-id="cc169-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="cc169-126">Umożliwia to aplikacji do uruchamiania z bibliotekami lokalnego dla aplikacji programu .NET Framework i kompilator do przeprowadzenia analizy globalnego dostarczać wydajności usługi wins.</span><span class="sxs-lookup"><span data-stu-id="cc169-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="cc169-127">W rezultacie aplikacje będą uruchamiać zawsze szybciej nawet po zakończeniu aktualizacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cc169-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>  
  
- <span data-ttu-id="cc169-128">Środowisko uruchomieniowe platformy .NET Native została zoptymalizowana pod kątem statyczne wstępnej kompilacji i w zdecydowanej większości przypadków zapewnia najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="cc169-128">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="cc169-129">W tym samym czasie zachowuje podstawowe funkcje odbicia, które więc produktywności deweloperów.</span><span class="sxs-lookup"><span data-stu-id="cc169-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>  
  
- <span data-ttu-id="cc169-130">.NET native używa tego samego zaplecza co C++ kompilatora, który jest zoptymalizowany pod kątem statyczne scenariuszy wstępnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cc169-130">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>  
  
 <span data-ttu-id="cc169-131">.NET native może przynieść korzyści wydajności C++ do zarządzanego kodu deweloperów, ponieważ używa ona narzędzi takie same lub podobne jak C++ kulisy, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="cc169-131">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>  
  
||<span data-ttu-id="cc169-132">Architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="cc169-132">.NET Native</span></span>|<span data-ttu-id="cc169-133">C++</span><span class="sxs-lookup"><span data-stu-id="cc169-133">C++</span></span>|  
|-|----------------------------------------------------------------|-----------|  
|<span data-ttu-id="cc169-134">Biblioteki</span><span class="sxs-lookup"><span data-stu-id="cc169-134">Libraries</span></span>|<span data-ttu-id="cc169-135">.NET Framework i środowiska wykonawczego Windows</span><span class="sxs-lookup"><span data-stu-id="cc169-135">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="cc169-136">Win32 i środowiska wykonawczego Windows</span><span class="sxs-lookup"><span data-stu-id="cc169-136">Win32 + Windows Runtime</span></span>|  
|<span data-ttu-id="cc169-137">Kompilator</span><span class="sxs-lookup"><span data-stu-id="cc169-137">Compiler</span></span>|<span data-ttu-id="cc169-138">Optymalizacja kompilatora UTC</span><span class="sxs-lookup"><span data-stu-id="cc169-138">UTC optimizing compiler</span></span>|<span data-ttu-id="cc169-139">Optymalizacja kompilatora UTC</span><span class="sxs-lookup"><span data-stu-id="cc169-139">UTC optimizing compiler</span></span>|  
|<span data-ttu-id="cc169-140">wdrożony</span><span class="sxs-lookup"><span data-stu-id="cc169-140">Deployed</span></span>|<span data-ttu-id="cc169-141">Pliki binarne gotowe do uruchomienia</span><span class="sxs-lookup"><span data-stu-id="cc169-141">Ready-to-run binaries</span></span>|<span data-ttu-id="cc169-142">Gotowe do uruchomienia pliki binarne (ASM)</span><span class="sxs-lookup"><span data-stu-id="cc169-142">Ready-to-run binaries (ASM)</span></span>|  
|<span data-ttu-id="cc169-143">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="cc169-143">Runtime</span></span>|<span data-ttu-id="cc169-144">MRT.dll (środowisko uruchomieniowe CLR minimalny)</span><span class="sxs-lookup"><span data-stu-id="cc169-144">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="cc169-145">CRT.dll (środowiska wykonawczego języka C)</span><span class="sxs-lookup"><span data-stu-id="cc169-145">CRT.dll (C Runtime)</span></span>|  
  
 <span data-ttu-id="cc169-146">W przypadku aplikacji Windows dla systemu Windows 10 możesz przekazać pliki binarne natywnej kompilacji kodu .NET, w pakiety aplikacji (pliki .appx) Store Windows.</span><span class="sxs-lookup"><span data-stu-id="cc169-146">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc169-147">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cc169-147">In This Section</span></span>  
 <span data-ttu-id="cc169-148">Aby uzyskać więcej informacji na temat tworzenia aplikacji za pomocą natywnej kompilacji kodu .NET zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="cc169-148">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>  
  
- [<span data-ttu-id="cc169-149">Wprowadzenie do kodu natywnej kompilacji .NET: Przewodnik doświadczenia dewelopera</span><span class="sxs-lookup"><span data-stu-id="cc169-149">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
- <span data-ttu-id="cc169-150">[Architektura .NET native i kompilacja:](../../../docs/framework/net-native/net-native-and-compilation.md) Jak .NET Native kompiluje projekt do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="cc169-150">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>  
  
- [<span data-ttu-id="cc169-151">Odbicie i architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="cc169-151">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    - [<span data-ttu-id="cc169-152">Interfejsy API, które działają na podstawie odbicia</span><span class="sxs-lookup"><span data-stu-id="cc169-152">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    - [<span data-ttu-id="cc169-153">Dokumentacja interfejsu API odbicia</span><span class="sxs-lookup"><span data-stu-id="cc169-153">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    - [<span data-ttu-id="cc169-154">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="cc169-154">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
- [<span data-ttu-id="cc169-155">Serializacja i metadane</span><span class="sxs-lookup"><span data-stu-id="cc169-155">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
- [<span data-ttu-id="cc169-156">Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native</span><span class="sxs-lookup"><span data-stu-id="cc169-156">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
- [<span data-ttu-id="cc169-157">Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native</span><span class="sxs-lookup"><span data-stu-id="cc169-157">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
