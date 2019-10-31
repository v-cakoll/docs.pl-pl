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
ms.openlocfilehash: 1f176e81905fe68c6d740a13240fe814659a7a59
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128375"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="4111d-102">Kompilowanie aplikacji z architekturą .NET Native</span><span class="sxs-lookup"><span data-stu-id="4111d-102">Compiling Apps with .NET Native</span></span>

<span data-ttu-id="4111d-103">.NET Native jest technologią prekompilacji do kompilowania i wdrażania aplikacji systemu Windows, które są dołączone do programu Visual Studio 2015 i jego nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="4111d-103">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="4111d-104">Automatycznie kompiluje wydaną wersję aplikacji, które są zapisywane w kodzie zarządzanym (C# lub Visual Basic), które są przeznaczone dla .NET Framework i systemu Windows 10 do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="4111d-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>

<span data-ttu-id="4111d-105">Zazwyczaj aplikacje przeznaczone dla .NET Framework są kompilowane do języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="4111d-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="4111d-106">W czasie wykonywania kompilator just-in-Time (JIT) tłumaczy kod IL na natywny.</span><span class="sxs-lookup"><span data-stu-id="4111d-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="4111d-107">Z kolei .NET Native kompiluje aplikacje systemu Windows bezpośrednio do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="4111d-107">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="4111d-108">Dla deweloperów oznacza to:</span><span class="sxs-lookup"><span data-stu-id="4111d-108">For developers, this means:</span></span>

- <span data-ttu-id="4111d-109">Twoje aplikacje mają wydajność kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="4111d-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="4111d-110">Zwykle wydajność zostanie przewyższana do kodu, który jest najpierw kompilowany do IL, a następnie skompilowany do kodu natywnego przez kompilator JIT.</span><span class="sxs-lookup"><span data-stu-id="4111d-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span>

- <span data-ttu-id="4111d-111">Możesz kontynuować program w C# programie lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4111d-111">You can continue to program in C# or Visual Basic.</span></span>

- <span data-ttu-id="4111d-112">Można nadal korzystać z zasobów udostępnianych przez .NET Framework, w tym biblioteki klas, automatycznego zarządzania pamięcią i wyrzucania elementów bezużytecznych oraz obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="4111d-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>

<span data-ttu-id="4111d-113">W przypadku użytkowników aplikacji .NET Native oferuje następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="4111d-113">For users of your apps, .NET Native offers these advantages:</span></span>

- <span data-ttu-id="4111d-114">Krótsze czasy wykonywania większości aplikacji i scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="4111d-114">Faster execution times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="4111d-115">Krótszy czas uruchamiania dla większości aplikacji i scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="4111d-115">Faster startup times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="4111d-116">Niskie koszty wdrożenia i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="4111d-116">Low deployment and update costs.</span></span>

- <span data-ttu-id="4111d-117">Zoptymalizowano użycie pamięci przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4111d-117">Optimized app memory usage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4111d-118">W przypadku większości aplikacji i scenariuszy .NET Native oferuje znacznie krótszy czas uruchamiania i wyższą wydajność w porównaniu z aplikacją skompilowaną do IL lub obrazu NGEN.</span><span class="sxs-lookup"><span data-stu-id="4111d-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="4111d-119">Jednak wyniki mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="4111d-119">However, your results may vary.</span></span> <span data-ttu-id="4111d-120">Aby upewnić się, że aplikacja korzystała z ulepszeń .NET Native, należy porównać jej wydajność z wersją natywną aplikacji non-.NET.</span><span class="sxs-lookup"><span data-stu-id="4111d-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="4111d-121">Aby uzyskać więcej informacji, zobacz [Omówienie sesji wydajności](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="4111d-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>

<span data-ttu-id="4111d-122">Ale .NET Native zawiera więcej niż Kompilacja kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="4111d-122">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="4111d-123">Przekształca on sposób kompilowania i wykonywania .NET Framework aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4111d-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="4111d-124">W szczególności:</span><span class="sxs-lookup"><span data-stu-id="4111d-124">In particular:</span></span>

- <span data-ttu-id="4111d-125">Podczas wstępnej kompilacji wymagane fragmenty .NET Framework są statycznie połączone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="4111d-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="4111d-126">Dzięki temu aplikacja może działać z bibliotekami lokalnymi aplikacji .NET Framework i kompilatorem do wykonywania analizy globalnej w celu zapewnienia wydajności usługi WINS.</span><span class="sxs-lookup"><span data-stu-id="4111d-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="4111d-127">W efekcie aplikacje są uruchamiane w sposób ciągły nawet po aktualizacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4111d-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>

- <span data-ttu-id="4111d-128">Środowisko uruchomieniowe .NET Native jest zoptymalizowane pod kątem statycznej kompilacji wstępnej, a w większości przypadków oferuje najwyższą wydajność.</span><span class="sxs-lookup"><span data-stu-id="4111d-128">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="4111d-129">W tym samym czasie zachowuje podstawowe funkcje odbicia, które deweloperzy mogą znaleźć.</span><span class="sxs-lookup"><span data-stu-id="4111d-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>

- <span data-ttu-id="4111d-130">.NET Native używa tego samego zaplecza, co C++ kompilator, który jest zoptymalizowany pod kątem statycznych scenariuszy prekompilacji.</span><span class="sxs-lookup"><span data-stu-id="4111d-130">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>

<span data-ttu-id="4111d-131">.NET Native jest w stanie obsłużyć zalety wydajności C++ programu dla deweloperów kodu zarządzanego, ponieważ używa tych samych lub podobnych narzędzi C++ , co w obszarze okapu, jak pokazano w tej tabeli.</span><span class="sxs-lookup"><span data-stu-id="4111d-131">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>

||<span data-ttu-id="4111d-132">Architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="4111d-132">.NET Native</span></span>|<span data-ttu-id="4111d-133">C++</span><span class="sxs-lookup"><span data-stu-id="4111d-133">C++</span></span>|
|-|----------------------------------------------------------------|-----------|
|<span data-ttu-id="4111d-134">Biblioteki</span><span class="sxs-lookup"><span data-stu-id="4111d-134">Libraries</span></span>|<span data-ttu-id="4111d-135">.NET Framework + środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4111d-135">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="4111d-136">Win32 + środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4111d-136">Win32 + Windows Runtime</span></span>|
|<span data-ttu-id="4111d-137">Compiler</span><span class="sxs-lookup"><span data-stu-id="4111d-137">Compiler</span></span>|<span data-ttu-id="4111d-138">Kompilator optymalizacji UTC</span><span class="sxs-lookup"><span data-stu-id="4111d-138">UTC optimizing compiler</span></span>|<span data-ttu-id="4111d-139">Kompilator optymalizacji UTC</span><span class="sxs-lookup"><span data-stu-id="4111d-139">UTC optimizing compiler</span></span>|
|<span data-ttu-id="4111d-140">szczebl</span><span class="sxs-lookup"><span data-stu-id="4111d-140">Deployed</span></span>|<span data-ttu-id="4111d-141">Gotowe do uruchomienia pliki binarne</span><span class="sxs-lookup"><span data-stu-id="4111d-141">Ready-to-run binaries</span></span>|<span data-ttu-id="4111d-142">Gotowe do uruchomienia pliki binarne (ASM)</span><span class="sxs-lookup"><span data-stu-id="4111d-142">Ready-to-run binaries (ASM)</span></span>|
|<span data-ttu-id="4111d-143">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4111d-143">Runtime</span></span>|<span data-ttu-id="4111d-144">MRT. dll (minimalne środowisko uruchomieniowe CLR)</span><span class="sxs-lookup"><span data-stu-id="4111d-144">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="4111d-145">CRT. dll (środowisko uruchomieniowe języka C)</span><span class="sxs-lookup"><span data-stu-id="4111d-145">CRT.dll (C Runtime)</span></span>|

<span data-ttu-id="4111d-146">W przypadku aplikacji systemu Windows dla systemu Windows 10 przekazywanie plików binarnych kompilacji kodu .NET Native w pakietach aplikacji (pliki. appx) do sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="4111d-146">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4111d-147">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4111d-147">In This Section</span></span>

<span data-ttu-id="4111d-148">Aby uzyskać więcej informacji na temat opracowywania aplikacji za pomocą kompilacji kodu .NET Native, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="4111d-148">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>

- [<span data-ttu-id="4111d-149">Wprowadzenie z kompilacją .NET Native kodu: Przewodnik po samouczku dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="4111d-149">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](getting-started-with-net-native.md)

- <span data-ttu-id="4111d-150">[.NET Native i kompilacja:](net-native-and-compilation.md) Jak .NET Native kompiluje projekt na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="4111d-150">[.NET Native and Compilation:](net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>

- [<span data-ttu-id="4111d-151">Odbicie i architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="4111d-151">Reflection and .NET Native</span></span>](reflection-and-net-native.md)

  - [<span data-ttu-id="4111d-152">Interfejsy API, które działają na podstawie odbicia</span><span class="sxs-lookup"><span data-stu-id="4111d-152">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)

  - [<span data-ttu-id="4111d-153">Dokumentacja interfejsu API odbicia</span><span class="sxs-lookup"><span data-stu-id="4111d-153">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)

  - [<span data-ttu-id="4111d-154">Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="4111d-154">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)

- [<span data-ttu-id="4111d-155">Serializacja i metadane</span><span class="sxs-lookup"><span data-stu-id="4111d-155">Serialization and Metadata</span></span>](serialization-and-metadata.md)

- [<span data-ttu-id="4111d-156">Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native</span><span class="sxs-lookup"><span data-stu-id="4111d-156">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)

- [<span data-ttu-id="4111d-157">Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native</span><span class="sxs-lookup"><span data-stu-id="4111d-157">.NET Native General Troubleshooting</span></span>](net-native-general-troubleshooting.md)
