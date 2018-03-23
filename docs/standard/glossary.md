---
title: .NET — słownik
description: Dowiedz się znaczenie wybranych terminów używanych w dokumentacji programu .NET.
keywords: .NET glossary, .NET dictionary, .NET terminology, .NET platform, .NET framework, .NET runtime
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 33123732514a53574036f6f8e948b2cf9acb9229
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="net-glossary"></a><span data-ttu-id="79980-104">.NET — słownik</span><span class="sxs-lookup"><span data-stu-id="79980-104">.NET Glossary</span></span>

<span data-ttu-id="79980-105">Podstawowym celem tego słownika jest wyjaśnienie znaczenia wybranego terminów i skrótów, które często pojawiają się w dokumentacji programu .NET, bez definicji.</span><span class="sxs-lookup"><span data-stu-id="79980-105">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="79980-106">AOT</span><span class="sxs-lookup"><span data-stu-id="79980-106">AOT</span></span>

<span data-ttu-id="79980-107">Kompilator z wyprzedzeniem o czasie.</span><span class="sxs-lookup"><span data-stu-id="79980-107">Ahead-of-time compiler.</span></span>

<span data-ttu-id="79980-108">Podobnie jak [JIT](#jit), tłumaczy także ten kompilator [IL](#il) do kodu maszyny.</span><span class="sxs-lookup"><span data-stu-id="79980-108">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="79980-109">W przeciwieństwie do kompilacji JIT kompilacji drzewa obiektów aplikacji odbywa się przed aplikacji jest wykonywane i jest zazwyczaj wykonywane na innym komputerze.</span><span class="sxs-lookup"><span data-stu-id="79980-109">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="79980-110">Ponieważ drzewa obiektów aplikacji narzędzia łańcuchów nie kompilacji w czasie wykonywania, nie będą musieli zminimalizować czas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="79980-110">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="79980-111">Oznacza to, że może poświęcić więcej czasu optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="79980-111">That means they can spend more time optimizing.</span></span> <span data-ttu-id="79980-112">Ponieważ kontekście drzewa obiektów aplikacji jest całej aplikacji, kompilator drzewa obiektów aplikacji wykonuje także łączenie między modułami i analizy całego programu, co oznacza, że wszystkie odwołania zostaną wykonane i pojedynczy plik wykonywalny jest generowany.</span><span class="sxs-lookup"><span data-stu-id="79980-112">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="79980-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79980-113">ASP.NET</span></span> 

<span data-ttu-id="79980-114">Oryginalny implementacja ASP.NET jest dostarczany z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79980-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="79980-115">Czasami ASP.NET jest ogólny termin odnoszący się do obu implementacje ASP.NET, w tym również platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="79980-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="79980-116">Co oznacza, że termin niesie w danym przypadku zależy od kontekstu.</span><span class="sxs-lookup"><span data-stu-id="79980-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="79980-117">Odwołuje się do platformy ASP.NET 4.x, aby wyjaśnić, że nie będziesz jej używać ASP.NET oznacza zarówno implementacji.</span><span class="sxs-lookup"><span data-stu-id="79980-117">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="79980-118">Zobacz [dokumentacji ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="79980-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="79980-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="79980-119">ASP.NET Core</span></span>

<span data-ttu-id="79980-120">Między platformami, implementacji wysokiej wydajności typu open source platformy ASP.NET w oparciu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="79980-120">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="79980-121">Zobacz [dokumentacji platformy ASP.NET Core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="79980-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="79980-122">zestaw</span><span class="sxs-lookup"><span data-stu-id="79980-122">assembly</span></span>

<span data-ttu-id="79980-123">A *.dll*/*.exe* pliku, który może zawierać kolekcję interfejsów API, które może być wywoływany przez aplikacje lub innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="79980-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="79980-124">Zestaw może zawierać typów, takie jak interfejsy, klasy, struktury, wyliczenia i delegaty.</span><span class="sxs-lookup"><span data-stu-id="79980-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="79980-125">Zestawy w projekcie *bin* folderu są czasami określane jako *plików binarnych*.</span><span class="sxs-lookup"><span data-stu-id="79980-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="79980-126">Zobacz też [biblioteki](#library).</span><span class="sxs-lookup"><span data-stu-id="79980-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="79980-127">CLR</span><span class="sxs-lookup"><span data-stu-id="79980-127">CLR</span></span>

<span data-ttu-id="79980-128">Środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="79980-128">Common Language Runtime.</span></span>

<span data-ttu-id="79980-129">Dokładne znaczenie zależy od kontekstu, ale zazwyczaj odnosi się do środowiska wykonawczego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="79980-129">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="79980-130">Środowisko CLR obsługuje alokacją pamięci i zarządzania.</span><span class="sxs-lookup"><span data-stu-id="79980-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="79980-131">Środowisko CLR jest również maszyny wirtualnej, który nie tylko wykonuje aplikacji, ale także generuje i kompiluje kodu na bieżąco przy użyciu kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="79980-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="79980-132">Bieżąca implementacja Microsoft CLR to tylko systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="79980-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="79980-133">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="79980-133">CoreCLR</span></span>

<span data-ttu-id="79980-134">.NET core środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="79980-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="79980-135">Ta CLR składa się z tego samego kodu podstawowej jako środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="79980-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="79980-136">Pierwotnie, środowisko CoreCLR został środowiska uruchomieniowego programu Silverlight i był przeznaczony do działania na wielu platformach, w szczególności systemu Windows i OS X. w środowisko CoreCLR jest obecnie częścią .NET Core i reprezentuje uproszczonej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="79980-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="79980-137">Jest ono nadal międzyplatformowego środowiska uruchomieniowego, teraz tym obsługę wielu dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="79980-137">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="79980-138">Środowisko CoreCLR jest również maszynę wirtualną z możliwości wykonywania JIT i kod.</span><span class="sxs-lookup"><span data-stu-id="79980-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="79980-139">CoreFX</span><span class="sxs-lookup"><span data-stu-id="79980-139">CoreFX</span></span>

<span data-ttu-id="79980-140">Biblioteka klasy podstawowej platformy .NET core (BCL)</span><span class="sxs-lookup"><span data-stu-id="79980-140">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="79980-141">Przestrzenie nazw bibliotek, które obejmują System.* (oraz w ograniczonym zakresie Microsoft.*).</span><span class="sxs-lookup"><span data-stu-id="79980-141">A set of libraries that comprise the System.* (and to a limited extent  Microsoft.*) namespaces.</span></span> <span data-ttu-id="79980-142">BCL jest ogólnego przeznaczenia, rozbudowywać wyższego poziomu struktur aplikacji, takich jak ASP.NET Core framework niższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="79980-142">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="79980-143">Kod źródłowy .NET Core BCL znajduje się w [repozytorium CoreFX](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="79980-143">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="79980-144">Jednak większość podstawowych interfejsów API .NET są również dostępne w programie .NET Framework, można traktować CoreFX jako rozwidlenia .NET Framework BCL.</span><span class="sxs-lookup"><span data-stu-id="79980-144">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="79980-145">CoreRT</span><span class="sxs-lookup"><span data-stu-id="79980-145">CoreRT</span></span>

<span data-ttu-id="79980-146">.NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="79980-146">.NET Core runtime.</span></span>

<span data-ttu-id="79980-147">W przeciwieństwie do środowiska CLR/na środowisko CoreCLR CoreRT nie jest maszyny wirtualnej, co oznacza, że nie ma wśród nich urządzeń do Generowanie i uruchamianie kodu na bieżąco, ponieważ nie ma wśród nich [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="79980-147">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="79980-148">Jednak zawierać [GC](#gc) z możliwością identyfikacji typu środowiska uruchomieniowego (RTTI) i odbicia.</span><span class="sxs-lookup"><span data-stu-id="79980-148">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="79980-149">Jednak system jego typ zaprojektowano tak, aby metadanych w celu odbicia nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="79980-149">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="79980-150">Dzięki temu o [drzewa obiektów aplikacji](#aot) narzędzia łańcucha, który umożliwia łączenie zadań zbędny metadanych (ważniejsze) identyfikację kodu, który nie korzysta z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="79980-150">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="79980-151">CoreRT trwa opracowywanie.</span><span class="sxs-lookup"><span data-stu-id="79980-151">CoreRT is in development.</span></span>

<span data-ttu-id="79980-152">Zobacz [wprowadzenie do architektury .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="79980-152">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="79980-153">ecosystem</span><span class="sxs-lookup"><span data-stu-id="79980-153">ecosystem</span></span>

<span data-ttu-id="79980-154">Wszystkie środowiska uruchomieniowego oprogramowania, narzędzia do programowania i zasoby społecznościowe, które są używane do tworzenia i uruchamiania aplikacji dla danej technologii.</span><span class="sxs-lookup"><span data-stu-id="79980-154">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="79980-155">Termin "Ekosystemu platformy .NET" różni się od podobnych warunkach, takich jak "Stosu .NET" w jej włączenia aplikacji innych firm i bibliotek.</span><span class="sxs-lookup"><span data-stu-id="79980-155">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="79980-156">Oto przykład w zdaniu na wyraz:</span><span class="sxs-lookup"><span data-stu-id="79980-156">Here's an example in a sentence:</span></span>

- <span data-ttu-id="79980-157">"Motywacją za [.NET Standard](#net-standard) jest ustanowienie większej jednolitości w ekosystemie .NET."</span><span class="sxs-lookup"><span data-stu-id="79980-157">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="79980-158">szablon</span><span class="sxs-lookup"><span data-stu-id="79980-158">framework</span></span>

<span data-ttu-id="79980-159">Ogólnie rzecz biorąc wszechstronny zbiór interfejsów API, które ułatwia opracowywania i wdrażania aplikacji, które są oparte na konkretnej technologii.</span><span class="sxs-lookup"><span data-stu-id="79980-159">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="79980-160">W tym sensie ogólne platformy ASP.NET Core i formularze systemu Windows to przykłady struktury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="79980-160">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="79980-161">Zobacz też [biblioteki](#library).</span><span class="sxs-lookup"><span data-stu-id="79980-161">See also [library](#library).</span></span>

<span data-ttu-id="79980-162">Wyraz "framework" ma więcej określone znaczenie techniczne w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="79980-162">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="79980-163">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="79980-163">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="79980-164">Platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="79980-164">target framework</span></span>](#target-framework)
* [<span data-ttu-id="79980-165">TFM (moniker platformy docelowej)</span><span class="sxs-lookup"><span data-stu-id="79980-165">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="79980-166">W dokumentacji istniejących "framework" czasami odwołuje się do [implementacji .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="79980-166">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="79980-167">Na przykład artykuł może wywołać .NET Core framework.</span><span class="sxs-lookup"><span data-stu-id="79980-167">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="79980-168">Firma Microsoft planuje wyeliminować mylące użycia w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="79980-168">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="79980-169">GC</span><span class="sxs-lookup"><span data-stu-id="79980-169">GC</span></span>

<span data-ttu-id="79980-170">Moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="79980-170">Garbage collector.</span></span>

<span data-ttu-id="79980-171">Moduł zbierający elementy bezużyteczne jest implementacją automatyczne zarządzanie pamięcią.</span><span class="sxs-lookup"><span data-stu-id="79980-171">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="79980-172">Wykaz Globalny zwalnia pamięć zajmowany przez obiekty, które nie są już w użyciu.</span><span class="sxs-lookup"><span data-stu-id="79980-172">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="79980-173">Zobacz [wyrzucanie elementów bezużytecznych](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="79980-173">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="79980-174">IL</span><span class="sxs-lookup"><span data-stu-id="79980-174">IL</span></span>

<span data-ttu-id="79980-175">Język pośredni.</span><span class="sxs-lookup"><span data-stu-id="79980-175">Intermediate language.</span></span>

<span data-ttu-id="79980-176">Kompiluj wyższego poziomu języków .NET, takich jak C#, dół zestaw instrukcji niezależny od sprzętu, który jest nazywany języku pośrednim (IL).</span><span class="sxs-lookup"><span data-stu-id="79980-176">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="79980-177">IL czasami nazywa się MSIL (Microsoft IL) lub CIL (język Common IL).</span><span class="sxs-lookup"><span data-stu-id="79980-177">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="79980-178">JIT</span><span class="sxs-lookup"><span data-stu-id="79980-178">JIT</span></span>

<span data-ttu-id="79980-179">Kompilatora just in time.</span><span class="sxs-lookup"><span data-stu-id="79980-179">Just-in-time compiler.</span></span>

<span data-ttu-id="79980-180">Podobnie jak [drzewa obiektów aplikacji](#aot), tłumaczy ten kompilator [IL](#il) do kodu maszyny, która obsługuje usługę procesora.</span><span class="sxs-lookup"><span data-stu-id="79980-180">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="79980-181">W przeciwieństwie do drzewa obiektów aplikacji kompilacja JIT wykonywany jest na żądanie i odbywa się na tym samym komputerze, który kod musi być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="79980-181">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="79980-182">Ponieważ kompilacja JIT odbywa się podczas wykonywania aplikacji, kompilowania wchodzi w skład w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="79980-182">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="79980-183">W związku z tym kompilatory JIT trzeba saldo czas optymalizacji kodu oszczędności, które mogą wytwarzać wynikowy kod.</span><span class="sxs-lookup"><span data-stu-id="79980-183">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="79980-184">Ale JIT zna rzeczywistego sprzętu i można zwolnić deweloperzy z konieczności wysłać różnych implementacji.</span><span class="sxs-lookup"><span data-stu-id="79980-184">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="79980-185">Implementacja programu .NET</span><span class="sxs-lookup"><span data-stu-id="79980-185">implementation of .NET</span></span>

<span data-ttu-id="79980-186">Implementacja .NET obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="79980-186">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="79980-187">Jeden lub więcej środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="79980-187">One or more runtimes.</span></span> <span data-ttu-id="79980-188">Przykłady: CLR, środowisko CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="79980-188">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="79980-189">Biblioteka klas, które implementuje w wersji programu .NET Standard i może zawierać dodatkowe interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="79980-189">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="79980-190">Przykłady: Klasa podstawowa Biblioteka programu .NET Framework, .NET Core klasy podstawowej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="79980-190">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="79980-191">Opcjonalnie co najmniej jeden struktury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="79980-191">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="79980-192">Przykłady: ASP.NET, formularzy systemu Windows i WPF znajdują się w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79980-192">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="79980-193">Opcjonalnie narzędzia do programowania.</span><span class="sxs-lookup"><span data-stu-id="79980-193">Optionally, development tools.</span></span> <span data-ttu-id="79980-194">Niektóre narzędzia do programowania są współużytkowane przez wiele implementacji.</span><span class="sxs-lookup"><span data-stu-id="79980-194">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="79980-195">Przykłady implementacji .NET:</span><span class="sxs-lookup"><span data-stu-id="79980-195">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="79980-196">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="79980-196">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="79980-197">.NET Core</span><span class="sxs-lookup"><span data-stu-id="79980-197">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="79980-198">Platforma uniwersalna systemu Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="79980-198">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="79980-199">biblioteka</span><span class="sxs-lookup"><span data-stu-id="79980-199">library</span></span>

<span data-ttu-id="79980-200">Kolekcja interfejsów API, które może być wywoływany przez aplikacje lub inne biblioteki.</span><span class="sxs-lookup"><span data-stu-id="79980-200">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="79980-201">Biblioteka .NET składa się z co najmniej jeden [zestawy](#assembly).</span><span class="sxs-lookup"><span data-stu-id="79980-201">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="79980-202">Biblioteka słów i [framework](#framework) są często używane jako synonim.</span><span class="sxs-lookup"><span data-stu-id="79980-202">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="79980-203">metapackage</span><span class="sxs-lookup"><span data-stu-id="79980-203">metapackage</span></span>

<span data-ttu-id="79980-204">Pakiet NuGet, który ma żadnej biblioteki oddzielnie, ale jest tylko listę zależności.</span><span class="sxs-lookup"><span data-stu-id="79980-204">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="79980-205">Dołączonych pakietów można opcjonalnie ustanowić interfejsu API dla struktury docelowej.</span><span class="sxs-lookup"><span data-stu-id="79980-205">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="79980-206">Zobacz [pakietów, Metapackages i platform](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="79980-206">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="79980-207">Mono</span><span class="sxs-lookup"><span data-stu-id="79980-207">Mono</span></span>

<span data-ttu-id="79980-208">Mono jest implementację .NET, która jest głównie używane, gdy wymagana jest mała środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="79980-208">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="79980-209">To środowisko uruchomieniowe, które uprawnienia aplikacji platformy Xamarin Android, Mac, iOS, systemu tvOS i watchOS i koncentruje się przede wszystkim na aplikacje, które wymagają niewielkie rozmiary.</span><span class="sxs-lookup"><span data-stu-id="79980-209">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="79980-210">Obsługuje wszystkie obecnie opublikowanej wersji platformy .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="79980-210">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="79980-211">W przeszłości Mono zaimplementowana większych interfejsu API programu .NET Framework i emulowane niektóre najpopularniejsze funkcje w systemie Unix.</span><span class="sxs-lookup"><span data-stu-id="79980-211">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="79980-212">Czasami służy do uruchamiania aplikacji .NET, które zależą od tych funkcji w systemie Unix.</span><span class="sxs-lookup"><span data-stu-id="79980-212">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="79980-213">Mono jest zwykle używana z kompilatora just in time, ale także kompilatora pełnej statyczne (kompilacja z wyprzedzeniem o czasie) używaną na platformach, np. z systemem iOS.</span><span class="sxs-lookup"><span data-stu-id="79980-213">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="79980-214">Aby dowiedzieć się więcej na temat Mono, zobacz [Mono dokumentacji](http://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="79980-214">To learn more about Mono, see the [Mono documentation](http://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="79980-215">.NET</span><span class="sxs-lookup"><span data-stu-id="79980-215">.NET</span></span>

<span data-ttu-id="79980-216">Termin określający [.NET Standard](#net-standard) i wszystkie [implementacje .NET](#implementation-of-net) i obciążeń.</span><span class="sxs-lookup"><span data-stu-id="79980-216">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="79980-217">Zawsze pisany wielkimi literami, nie ".Net".</span><span class="sxs-lookup"><span data-stu-id="79980-217">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="79980-218">Zobacz [.NET — przewodnik](index.md)</span><span class="sxs-lookup"><span data-stu-id="79980-218">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="79980-219">.NET Core</span><span class="sxs-lookup"><span data-stu-id="79980-219">.NET Core</span></span> 

<span data-ttu-id="79980-220">Implementacja między platformami, wysokiej wydajności typu open source platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="79980-220">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="79980-221">Zawiera podstawowe środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR), drzewa obiektów aplikacji podstawowego środowiska wykonawczego (rozwijany CoreRT), podstawowa Biblioteka klasy podstawowej i Core SDK.</span><span class="sxs-lookup"><span data-stu-id="79980-221">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="79980-222">Zobacz [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="79980-222">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="79980-223">Oprogramowanie .NET core interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="79980-223">.NET Core CLI</span></span>

<span data-ttu-id="79980-224">Łańcuch między platformami, narzędzi do tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="79980-224">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="79980-225">Zobacz [narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="79980-225">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="79980-226">Oprogramowanie .NET core SDK</span><span class="sxs-lookup"><span data-stu-id="79980-226">.NET Core SDK</span></span>

<span data-ttu-id="79980-227">Zestaw biblioteki i narzędzia, które umożliwiają deweloperom tworzenie aplikacji platformy .NET Core i bibliotek.</span><span class="sxs-lookup"><span data-stu-id="79980-227">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="79980-228">Obejmuje [interfejsu wiersza polecenia platformy .NET Core](#net-core-cli) do tworzenia aplikacji, bibliotek .NET Core i środowiska uruchomieniowego do tworzenia i uruchamiania aplikacji i dotnet pliku wykonywalnego (*dotnet.exe*) uruchamia polecenia interfejsu wiersza polecenia i są uruchomione aplikacje.</span><span class="sxs-lookup"><span data-stu-id="79980-228">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="79980-229">Zobacz [Omówienie zestawu SDK .NET Core](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="79980-229">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="79980-230">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="79980-230">.NET Framework</span></span>

<span data-ttu-id="79980-231">Implementacja programu .NET, na którym działa tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="79980-231">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="79980-232">Obejmuje środowiska uruchomieniowego języka wspólnego (CLR), Biblioteka klasy podstawowej i bibliotek platformy aplikacji, takich jak ASP.NET, formularze systemu Windows i WPF.</span><span class="sxs-lookup"><span data-stu-id="79980-232">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="79980-233">Zobacz [.NET Framework — przewodnik](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="79980-233">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="79980-234">Architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="79980-234">.NET Native</span></span>

<span data-ttu-id="79980-235">Łańcuch narzędzi kompilatora tworzącego kodu natywnego z wyprzedzeniem elementu time drzewa obiektów (aplikacji), zamiast just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="79980-235">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="79980-236">Kompilacja odbywa się na komputerze dewelopera, podobnie jak działa kompilatorze i konsolidatorze C++.</span><span class="sxs-lookup"><span data-stu-id="79980-236">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="79980-237">Usunięcie nieużywanych kodu, a zużywa więcej czasu optymalizacji go.</span><span class="sxs-lookup"><span data-stu-id="79980-237">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="79980-238">Wyodrębnia kod z biblioteki, a scala je w pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="79980-238">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="79980-239">Wynik jest jeden moduł, który reprezentuje całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="79980-239">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="79980-240">Platformy uniwersalnej systemu Windows była obsługiwana przez platformę .NET Native pierwszy struktury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="79980-240">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="79980-241">Firma Microsoft obsługuje teraz tworzenia konsoli natywnych aplikacji dla systemu Windows, system macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="79980-241">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="79980-242">Zobacz [wprowadzenie do architektury .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="79980-242">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="79980-243">.NET standard</span><span class="sxs-lookup"><span data-stu-id="79980-243">.NET Standard</span></span>

<span data-ttu-id="79980-244">Formalną specyfikację interfejsów API architektury .NET, które są dostępne w każdej implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="79980-244">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="79980-245">Specyfikacja .NET Standard jest niekiedy nazywany biblioteki w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="79980-245">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="79980-246">Ponieważ biblioteki zawiera implementacji interfejsu API, nie tylko specyfikacje (interfejsy), jest mylący, aby wywołać .NET Standard, "library".</span><span class="sxs-lookup"><span data-stu-id="79980-246">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="79980-247">Firma Microsoft planuje wyeliminować wykorzystanie z dokumentacji, z wyjątkiem w odniesieniu do nazwy .NET Standard metapackage (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="79980-247">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="79980-248">Zobacz [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="79980-248">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="79980-249">NARZĘDZIE NGEN</span><span class="sxs-lookup"><span data-stu-id="79980-249">NGEN</span></span>

<span data-ttu-id="79980-250">Generowanie Native (obraz).</span><span class="sxs-lookup"><span data-stu-id="79980-250">Native (image) generation.</span></span>

<span data-ttu-id="79980-251">Ta technologia można traktować jako trwałe kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="79980-251">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="79980-252">Zazwyczaj kompiluje kodu na komputerze, na którym wykonywany jest kod, ale kompilacji zazwyczaj występuje podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="79980-252">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="79980-253">Pakiet</span><span class="sxs-lookup"><span data-stu-id="79980-253">package</span></span>

<span data-ttu-id="79980-254">Pakiet NuGet &mdash; lub po prostu pakietu &mdash; jest *.zip* plików z jednego lub więcej zestawów o tej samej nazwie, oraz dodatkowe metadane, takie jak nazwisko autora.</span><span class="sxs-lookup"><span data-stu-id="79980-254">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="79980-255">*.Zip* plik ma *.nupkg* rozszerzenia i mogą zawierać zasoby, takie jak *.dll* plików i *.xml* plików do użytku z wielu elementu docelowego struktury i wersje.</span><span class="sxs-lookup"><span data-stu-id="79980-255">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="79980-256">Podczas instalowania aplikacji lub w bibliotece, odpowiednie zasoby są zaznaczone, oparty na platformie docelowej określonej przez aplikację lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="79980-256">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="79980-257">Zasoby, które definiują interfejsu znajdują się w *ref* folderu i zasoby, które definiują implementacji znajdują się w *lib* folderu.</span><span class="sxs-lookup"><span data-stu-id="79980-257">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="79980-258">platforma</span><span class="sxs-lookup"><span data-stu-id="79980-258">platform</span></span>

<span data-ttu-id="79980-259">System operacyjny i sprzętu, który jest uruchamiany na, takie jak Windows, system macOS, Linux, iOS i Android.</span><span class="sxs-lookup"><span data-stu-id="79980-259">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="79980-260">Poniżej przedstawiono przykłady użycia w zdaniach:</span><span class="sxs-lookup"><span data-stu-id="79980-260">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="79980-261">".NET core jest implementacja i platform .NET".</span><span class="sxs-lookup"><span data-stu-id="79980-261">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="79980-262">"PCL profile reprezentują platform firmy Microsoft, gdy .NET Standard jest niezależny od platformy."</span><span class="sxs-lookup"><span data-stu-id="79980-262">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="79980-263">Dokumentacja platformy .NET często używa "Platformy .NET" oznacza implementacja .NET albo stosu .NET, w tym wszystkich implementacji.</span><span class="sxs-lookup"><span data-stu-id="79980-263">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="79980-264">Obie te metody użycia zazwyczaj można pobrać mylić z podstawowe znaczenie (systemu operacyjnego/sprzęt), dlatego firma Microsoft planuje wyeliminować te użycia w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="79980-264">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="79980-265">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="79980-265">runtime</span></span>

<span data-ttu-id="79980-266">Środowiska wykonania programu zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="79980-266">The execution environment for a managed program.</span></span>

<span data-ttu-id="79980-267">System operacyjny jest częścią środowiska uruchomieniowego, ale nie jest częścią środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="79980-267">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="79980-268">Oto kilka przykładów środowisk uruchomieniowych .NET:</span><span class="sxs-lookup"><span data-stu-id="79980-268">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="79980-269">Środowisko uruchomieniowe języka wspólnego (CLR)</span><span class="sxs-lookup"><span data-stu-id="79980-269">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="79980-270">Podstawowe środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="79980-270">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="79980-271">Architektura .NET native (dla platformy uniwersalnej systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="79980-271">.NET Native (for UWP)</span></span>
- <span data-ttu-id="79980-272">Środowisko uruchomieniowe mono</span><span class="sxs-lookup"><span data-stu-id="79980-272">Mono runtime</span></span>

<span data-ttu-id="79980-273">Czasami dokumentację .NET używa "runtime" oznacza implementację programu .NET.</span><span class="sxs-lookup"><span data-stu-id="79980-273">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="79980-274">Na przykład w następujących zdania "runtime" powinna zostać zastąpiona "wdrożenia":</span><span class="sxs-lookup"><span data-stu-id="79980-274">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="79980-275">"Różnych środowisk uruchomieniowych .NET implementuje określonych wersji platformy .NET Standard".</span><span class="sxs-lookup"><span data-stu-id="79980-275">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="79980-276">"Bibliotek, które są przeznaczone do uruchamiania na wiele środowisk uruchomieniowych powinien tej platformy docelowej."</span><span class="sxs-lookup"><span data-stu-id="79980-276">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="79980-277">(odwołujące się do platformy .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="79980-277">(referring to .NET Standard)</span></span>
- <span data-ttu-id="79980-278">"Różnych środowisk uruchomieniowych .NET implementuje określonych wersji platformy .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="79980-278">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="79980-279">…</span><span class="sxs-lookup"><span data-stu-id="79980-279">…</span></span> <span data-ttu-id="79980-280">Każda wersja środowiska uruchomieniowego .NET anonsuje najnowsza wersja platformy .NET Standard obsługiwanych..."</span><span class="sxs-lookup"><span data-stu-id="79980-280">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="79980-281">Firma Microsoft planuje wyeliminować ten niespójne użycie.</span><span class="sxs-lookup"><span data-stu-id="79980-281">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="79980-282">stack</span><span class="sxs-lookup"><span data-stu-id="79980-282">stack</span></span>

<span data-ttu-id="79980-283">Zestaw programowania technologie, które są stosowane razem w celu tworzenia i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="79980-283">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="79980-284">"Stosu .NET" odnosi się do wszystkich implementacji .NET i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="79980-284">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="79980-285">Wyrażenie "stos .NET" może odwoływać się do jednego wdrożenia programu .NET.</span><span class="sxs-lookup"><span data-stu-id="79980-285">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="79980-286">Platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="79980-286">target framework</span></span>

<span data-ttu-id="79980-287">Kolekcja aplikacji .NET lub biblioteki korzysta z interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="79980-287">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="79980-288">Aplikacji lub biblioteki można wersja docelowa platformy .NET Standard (na przykład, .NET Standard 2.0), która jest specyfikacją standardowy zestaw interfejsów API we wszystkich wdrożeniach .NET.</span><span class="sxs-lookup"><span data-stu-id="79980-288">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="79980-289">To aplikacja lub biblioteki można również wersja docelowa platformy konkretnej implementacji .NET, w tym przypadku go pobiera dostępu do konkretnej implementacji interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="79980-289">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="79980-290">Na przykład aplikacja, która jest przeznaczony dla platformy Xamarin.iOS uzyskuje dostęp do otoki dostarczane do platformy Xamarin iOS interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="79980-290">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="79980-291">Dla niektórych docelowych platform (na przykład, .NET Framework) dostępnych interfejsach API są definiowane przez zestawy, które instaluje implementacji programu .NET w systemie, które mogą zawierać struktury aplikacji interfejsów API (na przykład ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="79980-291">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="79980-292">Dla struktury docelowej na podstawie pakietu (na przykład standardowe .NET i .NET Core) framework interfejsy API są definiowane przez pakiety zainstalowane w aplikacji lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="79980-292">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="79980-293">W takim przypadku platforma docelowa określa niejawnie metapackage, który odwołuje się do wszystkich pakietów, które składają się platformę.</span><span class="sxs-lookup"><span data-stu-id="79980-293">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="79980-294">Zobacz [platform docelowych](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="79980-294">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="79980-295">TFM</span><span class="sxs-lookup"><span data-stu-id="79980-295">TFM</span></span>

<span data-ttu-id="79980-296">Moniker platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="79980-296">Target framework moniker.</span></span>

<span data-ttu-id="79980-297">Standardowym formacie token służący do określania platformę docelową aplikacji .NET lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="79980-297">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="79980-298">Docelowych platform zwykle odwołuje się krótką nazwę, taką jak `net462`.</span><span class="sxs-lookup"><span data-stu-id="79980-298">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="79980-299">TFMs długiej (np. NETFramework, Version = 4.6.2) istnieje, ale nie są zwykle używane do określ platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="79980-299">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="79980-300">Zobacz [platform docelowych](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="79980-300">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="79980-301">Platforma UWP</span><span class="sxs-lookup"><span data-stu-id="79980-301">UWP</span></span>

<span data-ttu-id="79980-302">Platforma uniwersalna systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="79980-302">Universal Windows Platform.</span></span>

<span data-ttu-id="79980-303">Implementacja programu .NET, który jest używany do tworzenia nowoczesnych, obsługą dotyku aplikacji systemu Windows, jak i oprogramowania dla Internetu rzeczy (IoT).</span><span class="sxs-lookup"><span data-stu-id="79980-303">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="79980-304">Zostało zaprojektowane do ujednolicenie różne typy urządzeń, które chcesz docelowych, łącznie z komputerami, tablety, phablets, telefony i nawet Xbox.</span><span class="sxs-lookup"><span data-stu-id="79980-304">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="79980-305">Platformy uniwersalnej systemu Windows udostępnia wiele usług, takich jak scentralizowane sklepu, środowiska wykonawczego (AppContainer) i zestaw interfejsów API systemu Windows do użycia zamiast Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="79980-305">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="79980-306">Aplikacje mogą być napisane w języku C++, C#, VB.NET i JavaScript.</span><span class="sxs-lookup"><span data-stu-id="79980-306">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="79980-307">Korzystając z języka C# i VB.NET, interfejsów API architektury .NET są udostępniane przez oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="79980-307">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="79980-308">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79980-308">See also</span></span>

[<span data-ttu-id="79980-309">.NET — przewodnik</span><span class="sxs-lookup"><span data-stu-id="79980-309">.NET Guide</span></span>](index.md)  
[<span data-ttu-id="79980-310">.NET framework — przewodnik</span><span class="sxs-lookup"><span data-stu-id="79980-310">.NET Framework Guide</span></span>](../framework/index.md)  
[<span data-ttu-id="79980-311">.NET Core</span><span class="sxs-lookup"><span data-stu-id="79980-311">.NET Core</span></span>](../core/index.md)  
[<span data-ttu-id="79980-312">Omówienie programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="79980-312">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)  
[<span data-ttu-id="79980-313">Przegląd platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="79980-313">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)  

