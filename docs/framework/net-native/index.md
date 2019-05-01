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
ms.openlocfilehash: 6900bca2bd94f52ea5603c752681163cde52ce19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867033"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="6dc3c-102">Kompilowanie aplikacji z architekturą .NET Native</span><span class="sxs-lookup"><span data-stu-id="6dc3c-102">Compiling Apps with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)] <span data-ttu-id="6dc3c-103">jest technologia kompilacji wstępnej do kompilowania i wdrażania aplikacji Windows, który jest dołączony do programu Visual Studio 2015 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-103">is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="6dc3c-104">Automatycznie skompiluje wersji aplikacji, które są zapisywane w kodzie zarządzanym (C# lub Visual Basic) i przeznaczone na platformę .NET Framework i Windows 10 do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>  
  
 <span data-ttu-id="6dc3c-105">Zazwyczaj aplikacje, które obsługują program .NET Framework są kompilowane do języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="6dc3c-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="6dc3c-106">W czasie wykonywania kompilator just-in-time (JIT) tłumaczy IL do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="6dc3c-107">Z kolei [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilować aplikacje Windows bezpośrednio do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-107">In contrast, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiles Windows apps directly to native code.</span></span> <span data-ttu-id="6dc3c-108">Dla deweloperów oznacza to:</span><span class="sxs-lookup"><span data-stu-id="6dc3c-108">For developers, this means:</span></span>  
  
- <span data-ttu-id="6dc3c-109">Twoje aplikacje są wyposażone w wydajności kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="6dc3c-110">Zwykle wydajność będzie nadrzędne w stosunku do kodu, który jest najpierw skompilowane do IL, a następnie kompilowane do kodu macierzystego przy użyciu kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span> 
  
- <span data-ttu-id="6dc3c-111">Można kontynuować programu C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-111">You can continue to program in C# or Visual Basic.</span></span>  
  
- <span data-ttu-id="6dc3c-112">Można nadal korzystać z zasobów udostępnianych przez .NET Framework, w tym jego biblioteki klas, pamięcią automatyczną zarządzania i wyrzucania elementów kolekcji i obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>  
  
 <span data-ttu-id="6dc3c-113">Dla użytkowników aplikacji [!INCLUDE[net_native](../../../includes/net-native-md.md)] oferuje następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="6dc3c-113">For users of your apps, [!INCLUDE[net_native](../../../includes/net-native-md.md)] offers these advantages:</span></span>  
  
- <span data-ttu-id="6dc3c-114">Krótszy czas wykonywania dla większości scenariuszy i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-114">Faster execution times for the majority of apps and scenarios.</span></span>
  
- <span data-ttu-id="6dc3c-115">Krótszy czas uruchamiania dla większości scenariuszy i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-115">Faster startup times for the majority of apps and scenarios.</span></span> 
  
- <span data-ttu-id="6dc3c-116">Niskie koszty wdrożenia i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-116">Low deployment and update costs.</span></span>  
  
- <span data-ttu-id="6dc3c-117">Zoptymalizowane pod kątem użycia pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-117">Optimized app memory usage.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="6dc3c-118">Większość aplikacji i scenariuszy .NET Native oferuje znacznie krótszy czas uruchamiania i doskonałą wydajność w porównaniu do aplikacji skompilowanych IL lub obrazów NGEN.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="6dc3c-119">Jednak wyniki mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-119">However, your results may vary.</span></span> <span data-ttu-id="6dc3c-120">Aby upewnić się, że aplikacja skorzystał z ulepszenia wydajności programu .NET Native, należy porównać jego wydajność, korzystając z niego bez — .NET Native wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="6dc3c-121">Aby uzyskać więcej informacji, zobacz [sesja wydajności — omówienie](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="6dc3c-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>
 
<span data-ttu-id="6dc3c-122">Ale [!INCLUDE[net_native](../../../includes/net-native-md.md)] obejmuje więcej niż kompilacji do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-122">But [!INCLUDE[net_native](../../../includes/net-native-md.md)] involves more than a compilation to native code.</span></span> <span data-ttu-id="6dc3c-123">Jego zmienia sposób skompilowane i wykonywane aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="6dc3c-124">W szczególności:</span><span class="sxs-lookup"><span data-stu-id="6dc3c-124">In particular:</span></span>  
  
- <span data-ttu-id="6dc3c-125">Podczas wstępnej kompilacji wymagane części programu .NET Framework są łączone statycznie z Twoją aplikacją.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="6dc3c-126">Umożliwia to aplikacji do uruchamiania z bibliotekami lokalnego dla aplikacji programu .NET Framework i kompilator do przeprowadzenia analizy globalnego dostarczać wydajności usługi wins.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="6dc3c-127">W rezultacie aplikacje będą uruchamiać zawsze szybciej nawet po zakończeniu aktualizacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>  
  
- <span data-ttu-id="6dc3c-128">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Środowiska uruchomieniowego jest zoptymalizowany pod kątem statyczne wstępnej kompilacji i w zdecydowanej większości przypadków zapewnia najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-128">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="6dc3c-129">W tym samym czasie zachowuje podstawowe funkcje odbicia, które więc produktywności deweloperów.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>  
  
- [!INCLUDE[net_native](../../../includes/net-native-md.md)] <span data-ttu-id="6dc3c-130">wykorzystuje takie same ponownie zakończyć jako C++ kompilatora, który jest zoptymalizowany pod kątem statyczne scenariuszy wstępnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-130">uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] <span data-ttu-id="6dc3c-131">może przynieść korzyści wydajności C++ do zarządzanego kodu deweloperów, ponieważ używa ona narzędzi takie same lub podobne jak C++ kulisy, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-131">is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|<span data-ttu-id="6dc3c-132">C++</span><span class="sxs-lookup"><span data-stu-id="6dc3c-132">C++</span></span>|  
|-|----------------------------------------------------------------|-----------|  
|<span data-ttu-id="6dc3c-133">Biblioteki</span><span class="sxs-lookup"><span data-stu-id="6dc3c-133">Libraries</span></span>|<span data-ttu-id="6dc3c-134">.NET Framework i środowiska wykonawczego Windows</span><span class="sxs-lookup"><span data-stu-id="6dc3c-134">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="6dc3c-135">Win32 i środowiska wykonawczego Windows</span><span class="sxs-lookup"><span data-stu-id="6dc3c-135">Win32 + Windows Runtime</span></span>|  
|<span data-ttu-id="6dc3c-136">Kompilator</span><span class="sxs-lookup"><span data-stu-id="6dc3c-136">Compiler</span></span>|<span data-ttu-id="6dc3c-137">Optymalizacja kompilatora UTC</span><span class="sxs-lookup"><span data-stu-id="6dc3c-137">UTC optimizing compiler</span></span>|<span data-ttu-id="6dc3c-138">Optymalizacja kompilatora UTC</span><span class="sxs-lookup"><span data-stu-id="6dc3c-138">UTC optimizing compiler</span></span>|  
|<span data-ttu-id="6dc3c-139">wdrożony</span><span class="sxs-lookup"><span data-stu-id="6dc3c-139">Deployed</span></span>|<span data-ttu-id="6dc3c-140">Pliki binarne gotowe do uruchomienia</span><span class="sxs-lookup"><span data-stu-id="6dc3c-140">Ready-to-run binaries</span></span>|<span data-ttu-id="6dc3c-141">Gotowe do uruchomienia pliki binarne (ASM)</span><span class="sxs-lookup"><span data-stu-id="6dc3c-141">Ready-to-run binaries (ASM)</span></span>|  
|<span data-ttu-id="6dc3c-142">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6dc3c-142">Runtime</span></span>|<span data-ttu-id="6dc3c-143">MRT.dll (środowisko uruchomieniowe CLR minimalny)</span><span class="sxs-lookup"><span data-stu-id="6dc3c-143">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="6dc3c-144">CRT.dll (środowiska wykonawczego języka C)</span><span class="sxs-lookup"><span data-stu-id="6dc3c-144">CRT.dll (C Runtime)</span></span>|  
  
 <span data-ttu-id="6dc3c-145">W przypadku aplikacji Windows dla systemu Windows 10 możesz przekazać pliki binarne natywnej kompilacji kodu .NET, w pakiety aplikacji (pliki .appx) Store Windows.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-145">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6dc3c-146">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6dc3c-146">In This Section</span></span>  
 <span data-ttu-id="6dc3c-147">Aby uzyskać więcej informacji na temat tworzenia aplikacji za pomocą natywnej kompilacji kodu .NET zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="6dc3c-147">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>  
  
- [<span data-ttu-id="6dc3c-148">Wprowadzenie do kodu natywnej kompilacji .NET: Przewodnik doświadczenia dewelopera</span><span class="sxs-lookup"><span data-stu-id="6dc3c-148">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
- <span data-ttu-id="6dc3c-149">[Architektura .NET native i kompilacja:](../../../docs/framework/net-native/net-native-and-compilation.md) Jak .NET Native kompiluje projekt do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="6dc3c-149">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>  
  
- [<span data-ttu-id="6dc3c-150">Odbicie i architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="6dc3c-150">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    - [<span data-ttu-id="6dc3c-151">Interfejsy API, które działają na podstawie odbicia</span><span class="sxs-lookup"><span data-stu-id="6dc3c-151">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    - [<span data-ttu-id="6dc3c-152">Dokumentacja interfejsu API odbicia</span><span class="sxs-lookup"><span data-stu-id="6dc3c-152">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    - [<span data-ttu-id="6dc3c-153">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="6dc3c-153">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
- [<span data-ttu-id="6dc3c-154">Serializacja i metadane</span><span class="sxs-lookup"><span data-stu-id="6dc3c-154">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
- [<span data-ttu-id="6dc3c-155">Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native</span><span class="sxs-lookup"><span data-stu-id="6dc3c-155">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
- [<span data-ttu-id="6dc3c-156">Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native</span><span class="sxs-lookup"><span data-stu-id="6dc3c-156">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
