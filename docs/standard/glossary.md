---
title: ".NET — słownik"
description: "Dowiedz się znaczenie wybranych terminów używanych w dokumentacji programu .NET."
keywords: ".NET — słownik, słownik platformy .NET, terminologii .NET, platformy .NET, .NET framework, środowisko uruchomieniowe platformy .NET"
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
ms.openlocfilehash: 112be2518ddfb396fce8a14c5056c16cce9f376d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="net-glossary"></a><span data-ttu-id="0fe7f-104">.NET — słownik</span><span class="sxs-lookup"><span data-stu-id="0fe7f-104">.NET Glossary</span></span>

<span data-ttu-id="0fe7f-105">Podstawowym celem tego słownika jest wyjaśnienie znaczenia wybranego terminów i skrótów, które często pojawiają się w dokumentacji programu .NET, bez definicji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-105">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="0fe7f-106">DRZEWA OBIEKTÓW APLIKACJI</span><span class="sxs-lookup"><span data-stu-id="0fe7f-106">AOT</span></span>

<span data-ttu-id="0fe7f-107">Kompilator z wyprzedzeniem o czasie.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-107">Ahead-of-time compiler.</span></span>

<span data-ttu-id="0fe7f-108">Podobnie jak [JIT](#jit), tłumaczy także ten kompilator [IL](#il) do kodu maszyny.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-108">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="0fe7f-109">W przeciwieństwie do kompilacji JIT kompilacji drzewa obiektów aplikacji odbywa się przed aplikacji jest wykonywane i jest zazwyczaj wykonywane na innym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-109">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="0fe7f-110">Ponieważ drzewa obiektów aplikacji narzędzia łańcuchów nie kompilacji w czasie wykonywania, nie będą musieli zminimalizować czas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-110">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="0fe7f-111">Oznacza to, że może poświęcić więcej czasu optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-111">That means they can spend more time optimizing.</span></span> <span data-ttu-id="0fe7f-112">Ponieważ kontekście drzewa obiektów aplikacji jest całej aplikacji, kompilator drzewa obiektów aplikacji wykonuje także łączenie między modułami i analizy całego programu, co oznacza, że wszystkie odwołania zostaną wykonane i pojedynczy plik wykonywalny jest generowany.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-112">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="0fe7f-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0fe7f-113">ASP.NET</span></span> 

<span data-ttu-id="0fe7f-114">Oryginalny implementacja ASP.NET jest dostarczany z programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="0fe7f-115">Czasami ASP.NET jest ogólny termin odnoszący się do obu implementacje ASP.NET, w tym również platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="0fe7f-116">Co oznacza, że termin niesie w danym przypadku zależy od kontekstu.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="0fe7f-117">Odwołuje się do platformy ASP.NET 4.x, aby wyjaśnić, że nie będziesz jej używać ASP.NET oznacza zarówno implementacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-117">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="0fe7f-118">Zobacz [dokumentacji ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="0fe7f-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0fe7f-119">ASP.NET Core</span></span>

<span data-ttu-id="0fe7f-120">Między platformami, implementacji wysokiej wydajności typu open source platformy ASP.NET w oparciu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-120">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="0fe7f-121">Zobacz [dokumentacji platformy ASP.NET Core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="0fe7f-122">zestaw</span><span class="sxs-lookup"><span data-stu-id="0fe7f-122">assembly</span></span>

<span data-ttu-id="0fe7f-123">A *.dll* pliku, który zawiera kolekcję interfejsów API, które może być wywoływany przez aplikacje lub innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-123">A *.dll* file that contains a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="0fe7f-124">Zestaw .NET jest kolekcją typów.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-124">A .NET assembly is a collection of types.</span></span> <span data-ttu-id="0fe7f-125">Zestaw zawiera interfejsy, klasy, struktury, wyliczenia i delegaty.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-125">An assembly includes interfaces, classes, structures, enumerations, and delegates.</span></span>  <span data-ttu-id="0fe7f-126">Zestawy w projekcie *bin* folderu są czasami określane jako *plików binarnych*.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-126">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="0fe7f-127">Zobacz też [biblioteki](#library).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-127">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="0fe7f-128">CLR</span><span class="sxs-lookup"><span data-stu-id="0fe7f-128">CLR</span></span>

<span data-ttu-id="0fe7f-129">Środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-129">Common Language Runtime.</span></span>

<span data-ttu-id="0fe7f-130">Dokładne znaczenie zależy od kontekstu, ale zazwyczaj odnosi się do środowiska wykonawczego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-130">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="0fe7f-131">Środowisko CLR obsługuje alokacją pamięci i zarządzania.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-131">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="0fe7f-132">Środowisko CLR jest również maszyny wirtualnej, który nie tylko wykonuje aplikacji, ale także generuje i kompiluje kodu na bieżąco przy użyciu kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-132">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="0fe7f-133">Bieżąca implementacja Microsoft CLR to tylko systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-133">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="0fe7f-134">Środowisko CoreCLR</span><span class="sxs-lookup"><span data-stu-id="0fe7f-134">CoreCLR</span></span>

<span data-ttu-id="0fe7f-135">.NET core środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-135">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="0fe7f-136">Ta CLR składa się z tego samego kodu podstawowej jako środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-136">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="0fe7f-137">Pierwotnie, środowisko CoreCLR został środowiska uruchomieniowego programu Silverlight i był przeznaczony do działania na wielu platformach, w szczególności systemu Windows i OS X. w środowisko CoreCLR jest obecnie częścią .NET Core i reprezentuje uproszczonej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-137">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="0fe7f-138">Jest ono nadal międzyplatformowego środowiska uruchomieniowego, teraz tym obsługę wielu dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-138">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="0fe7f-139">Środowisko CoreCLR jest również maszynę wirtualną z możliwości wykonywania JIT i kod.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-139">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="0fe7f-140">CoreFX</span><span class="sxs-lookup"><span data-stu-id="0fe7f-140">CoreFX</span></span>

<span data-ttu-id="0fe7f-141">Biblioteka klasy podstawowej platformy .NET core (BCL)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-141">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="0fe7f-142">Przestrzenie nazw bibliotek, które obejmują System.* (oraz w ograniczonym zakresie Microsoft.*).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-142">A set of libraries that comprise the System.* (and to a limited extent  Microsoft.*) namespaces.</span></span> <span data-ttu-id="0fe7f-143">BCL jest ogólnego przeznaczenia, rozbudowywać wyższego poziomu struktur aplikacji, takich jak ASP.NET Core framework niższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-143">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="0fe7f-144">Kod źródłowy .NET Core BCL znajduje się w [repozytorium CoreFX](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-144">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="0fe7f-145">Jednak większość podstawowych interfejsów API .NET są również dostępne w programie .NET Framework, można traktować CoreFX jako rozwidlenia .NET Framework BCL.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-145">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="0fe7f-146">CoreRT</span><span class="sxs-lookup"><span data-stu-id="0fe7f-146">CoreRT</span></span>

<span data-ttu-id="0fe7f-147">Środowisko uruchomieniowe .NET core.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-147">.NET Core runtime.</span></span>

<span data-ttu-id="0fe7f-148">W przeciwieństwie do środowiska CLR/na środowisko CoreCLR CoreRT nie jest maszyny wirtualnej, co oznacza, że nie ma wśród nich urządzeń do Generowanie i uruchamianie kodu na bieżąco, ponieważ nie ma wśród nich [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-148">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="0fe7f-149">Jednak zawierać [GC](#gc) z możliwością identyfikacji typu środowiska uruchomieniowego (RTTI) i odbicia.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-149">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="0fe7f-150">Jednak system jego typ zaprojektowano tak, aby metadanych w celu odbicia nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-150">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="0fe7f-151">Dzięki temu o [drzewa obiektów aplikacji](#aot) narzędzia łańcucha, który umożliwia łączenie zadań zbędny metadanych (ważniejsze) identyfikację kodu, który nie korzysta z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-151">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="0fe7f-152">CoreRT trwa opracowywanie.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-152">CoreRT is in development.</span></span>

<span data-ttu-id="0fe7f-153">Zobacz [wprowadzenie do architektury .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-153">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="0fe7f-154">ekosystemu</span><span class="sxs-lookup"><span data-stu-id="0fe7f-154">ecosystem</span></span>

<span data-ttu-id="0fe7f-155">Wszystkie środowiska uruchomieniowego oprogramowania, narzędzia do programowania i zasoby społecznościowe, które są używane do tworzenia i uruchamiania aplikacji dla danej technologii.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-155">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="0fe7f-156">Termin "Ekosystemu platformy .NET" różni się od podobnych warunkach, takich jak "Stosu .NET" w jej włączenia aplikacji innych firm i bibliotek.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-156">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="0fe7f-157">Oto przykład w zdaniu na wyraz:</span><span class="sxs-lookup"><span data-stu-id="0fe7f-157">Here's an example in a sentence:</span></span>

- <span data-ttu-id="0fe7f-158">"Motywacją za [.NET Standard](#net-standard) jest ustanowienie większej jednolitości w ekosystemie .NET."</span><span class="sxs-lookup"><span data-stu-id="0fe7f-158">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="0fe7f-159">szablon</span><span class="sxs-lookup"><span data-stu-id="0fe7f-159">framework</span></span>

<span data-ttu-id="0fe7f-160">Ogólnie rzecz biorąc wszechstronny zbiór interfejsów API, które ułatwia opracowywania i wdrażania aplikacji, które są oparte na konkretnej technologii.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-160">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="0fe7f-161">W tym sensie ogólne platformy ASP.NET Core i formularze systemu Windows to przykłady struktury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-161">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="0fe7f-162">Zobacz też [biblioteki](#library).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-162">See also [library](#library).</span></span>

<span data-ttu-id="0fe7f-163">Wyraz "framework" ma więcej określone znaczenie techniczne w następujących warunkach:</span><span class="sxs-lookup"><span data-stu-id="0fe7f-163">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="0fe7f-164">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0fe7f-164">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="0fe7f-165">Platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="0fe7f-165">target framework</span></span>](#target-framework)
* [<span data-ttu-id="0fe7f-166">TFM (moniker platformy docelowej)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-166">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="0fe7f-167">W dokumentacji istniejących "framework" czasami odwołuje się do [implementacji .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-167">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="0fe7f-168">Na przykład artykuł może wywołać .NET Core framework.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-168">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="0fe7f-169">Firma Microsoft planuje wyeliminować mylące użycia w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-169">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="0fe7f-170">GC</span><span class="sxs-lookup"><span data-stu-id="0fe7f-170">GC</span></span>

<span data-ttu-id="0fe7f-171">Moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-171">Garbage collector.</span></span>

<span data-ttu-id="0fe7f-172">Moduł zbierający elementy bezużyteczne jest implementacją automatyczne zarządzanie pamięcią.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-172">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="0fe7f-173">Wykaz Globalny zwalnia pamięć zajmowany przez obiekty, które nie są już w użyciu.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-173">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="0fe7f-174">Zobacz [wyrzucanie elementów bezużytecznych](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-174">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="0fe7f-175">IL</span><span class="sxs-lookup"><span data-stu-id="0fe7f-175">IL</span></span>

<span data-ttu-id="0fe7f-176">Język pośredni.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-176">Intermediate language.</span></span>

<span data-ttu-id="0fe7f-177">Kompiluj wyższego poziomu języków .NET, takich jak C#, dół zestaw instrukcji niezależny od sprzętu, który jest nazywany języku pośrednim (IL).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-177">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="0fe7f-178">IL czasami nazywa się MSIL (Microsoft IL) lub CIL (język Common IL).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-178">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="0fe7f-179">JIT</span><span class="sxs-lookup"><span data-stu-id="0fe7f-179">JIT</span></span>

<span data-ttu-id="0fe7f-180">Kompilatora just in time.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-180">Just-in-time compiler.</span></span>

<span data-ttu-id="0fe7f-181">Podobnie jak [drzewa obiektów aplikacji](#aot), tłumaczy ten kompilator [IL](#il) do kodu maszyny, która obsługuje usługę procesora.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-181">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="0fe7f-182">W przeciwieństwie do drzewa obiektów aplikacji kompilacja JIT wykonywany jest na żądanie i odbywa się na tym samym komputerze, który kod musi być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-182">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="0fe7f-183">Ponieważ kompilacja JIT odbywa się podczas wykonywania aplikacji, kompilowania wchodzi w skład w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-183">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="0fe7f-184">W związku z tym kompilatory JIT trzeba saldo czas optymalizacji kodu oszczędności, które mogą wytwarzać wynikowy kod.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-184">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="0fe7f-185">Ale JIT zna rzeczywistego sprzętu i można zwolnić deweloperzy z konieczności wysłać różnych implementacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-185">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="0fe7f-186">Implementacja programu .NET</span><span class="sxs-lookup"><span data-stu-id="0fe7f-186">implementation of .NET</span></span>

<span data-ttu-id="0fe7f-187">Implementacja .NET obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="0fe7f-187">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="0fe7f-188">Jeden lub więcej środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-188">One or more runtimes.</span></span> <span data-ttu-id="0fe7f-189">Przykłady: CLR, środowisko CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-189">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="0fe7f-190">Biblioteka klas, które implementuje w wersji programu .NET Standard i może zawierać dodatkowe interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-190">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="0fe7f-191">Przykłady: Klasa podstawowa Biblioteka programu .NET Framework, .NET Core klasy podstawowej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-191">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="0fe7f-192">Opcjonalnie co najmniej jeden struktury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-192">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="0fe7f-193">Przykłady: ASP.NET, formularzy systemu Windows i WPF znajdują się w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-193">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="0fe7f-194">Opcjonalnie narzędzia do programowania.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-194">Optionally, development tools.</span></span> <span data-ttu-id="0fe7f-195">Niektóre narzędzia do programowania są współużytkowane przez wiele implementacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-195">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="0fe7f-196">Przykłady implementacji .NET:</span><span class="sxs-lookup"><span data-stu-id="0fe7f-196">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="0fe7f-197">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0fe7f-197">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="0fe7f-198">.NET Core</span><span class="sxs-lookup"><span data-stu-id="0fe7f-198">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="0fe7f-199">Platforma uniwersalna systemu Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-199">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="0fe7f-200">biblioteka</span><span class="sxs-lookup"><span data-stu-id="0fe7f-200">library</span></span>

<span data-ttu-id="0fe7f-201">Kolekcja interfejsów API, które może być wywoływany przez aplikacje lub inne biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-201">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="0fe7f-202">Biblioteka .NET składa się z co najmniej jeden [zestawy](#assembly).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-202">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="0fe7f-203">Biblioteka słów i [framework](#framework) są często używane jako synonim.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-203">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="0fe7f-204">metapackage</span><span class="sxs-lookup"><span data-stu-id="0fe7f-204">metapackage</span></span>

<span data-ttu-id="0fe7f-205">Pakiet NuGet, który ma żadnej biblioteki oddzielnie, ale jest tylko listę zależności.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-205">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="0fe7f-206">Dołączonych pakietów można opcjonalnie ustanowić interfejsu API dla struktury docelowej.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-206">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="0fe7f-207">Zobacz [pakietów, Metapackages i platform](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-207">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="0fe7f-208">Mono</span><span class="sxs-lookup"><span data-stu-id="0fe7f-208">Mono</span></span>

<span data-ttu-id="0fe7f-209">Mono jest implementację .NET, która jest głównie używane, gdy wymagana jest mała środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-209">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="0fe7f-210">To środowisko uruchomieniowe, które uprawnienia aplikacji platformy Xamarin Android, Mac, iOS, systemu tvOS i watchOS i koncentruje się przede wszystkim na aplikacje, które wymagają niewielkie rozmiary.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-210">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="0fe7f-211">Obsługuje wszystkie obecnie opublikowanej wersji platformy .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-211">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="0fe7f-212">W przeszłości Mono zaimplementowana większych interfejsu API programu .NET Framework i emulowane niektóre najpopularniejsze funkcje w systemie Unix.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-212">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="0fe7f-213">Czasami służy do uruchamiania aplikacji .NET, które zależą od tych funkcji w systemie Unix.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-213">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="0fe7f-214">Mono jest zwykle używana z kompilatora just in time, ale także kompilatora pełnej statyczne (kompilacja z wyprzedzeniem o czasie) używaną na platformach, np. z systemem iOS.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-214">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="0fe7f-215">Aby dowiedzieć się więcej na temat Mono, zobacz [Mono dokumentacji](http://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-215">To learn more about Mono, see the [Mono documentation](http://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="0fe7f-216">.NET</span><span class="sxs-lookup"><span data-stu-id="0fe7f-216">.NET</span></span>

<span data-ttu-id="0fe7f-217">Termin określający [.NET Standard](#net-standard) i wszystkie [implementacje .NET](#implementation-of-net) i obciążeń.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-217">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="0fe7f-218">Zawsze pisany wielkimi literami, nie ".Net".</span><span class="sxs-lookup"><span data-stu-id="0fe7f-218">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="0fe7f-219">Zobacz [.NET — przewodnik](index.md)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-219">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="0fe7f-220">.NET Core</span><span class="sxs-lookup"><span data-stu-id="0fe7f-220">.NET Core</span></span> 

<span data-ttu-id="0fe7f-221">Implementacja między platformami, wysokiej wydajności typu open source platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-221">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="0fe7f-222">Zawiera podstawowe środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR), drzewa obiektów aplikacji podstawowego środowiska wykonawczego (rozwijany CoreRT), podstawowa Biblioteka klasy podstawowej i Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-222">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="0fe7f-223">Zobacz [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-223">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="0fe7f-224">Oprogramowanie .NET core interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="0fe7f-224">.NET Core CLI</span></span>

<span data-ttu-id="0fe7f-225">Łańcuch między platformami, narzędzi do tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-225">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="0fe7f-226">Zobacz [narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-226">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="0fe7f-227">Oprogramowanie .NET core SDK</span><span class="sxs-lookup"><span data-stu-id="0fe7f-227">.NET Core SDK</span></span>

<span data-ttu-id="0fe7f-228">Zestaw biblioteki i narzędzia, które umożliwiają deweloperom tworzenie aplikacji platformy .NET Core i bibliotek.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-228">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="0fe7f-229">Obejmuje [interfejsu wiersza polecenia platformy .NET Core](#net-core-cli) do tworzenia aplikacji, bibliotek .NET Core i środowiska uruchomieniowego do tworzenia i uruchamiania aplikacji i dotnet pliku wykonywalnego (*dotnet.exe*) uruchamia polecenia interfejsu wiersza polecenia i są uruchomione aplikacje.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-229">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="0fe7f-230">Zobacz [Omówienie zestawu SDK .NET Core](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-230">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="0fe7f-231">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0fe7f-231">.NET Framework</span></span>

<span data-ttu-id="0fe7f-232">Implementacja programu .NET, na którym działa tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-232">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="0fe7f-233">Obejmuje środowiska uruchomieniowego języka wspólnego (CLR), Biblioteka klasy podstawowej i bibliotek platformy aplikacji, takich jak ASP.NET, formularze systemu Windows i WPF.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-233">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="0fe7f-234">Zobacz [.NET Framework — przewodnik](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-234">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="0fe7f-235">Architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="0fe7f-235">.NET Native</span></span>

<span data-ttu-id="0fe7f-236">Łańcuch narzędzi kompilatora tworzącego kodu natywnego z wyprzedzeniem elementu time drzewa obiektów (aplikacji), zamiast just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-236">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="0fe7f-237">Kompilacja odbywa się na komputerze dewelopera, podobnie jak działa kompilatorze i konsolidatorze C++.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-237">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="0fe7f-238">Usunięcie nieużywanych kodu, a zużywa więcej czasu optymalizacji go.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-238">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="0fe7f-239">Wyodrębnia kod z biblioteki, a scala je w pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-239">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="0fe7f-240">Wynik jest jeden moduł, który reprezentuje całej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-240">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="0fe7f-241">Platformy uniwersalnej systemu Windows była obsługiwana przez platformę .NET Native pierwszy struktury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-241">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="0fe7f-242">Firma Microsoft obsługuje teraz tworzenia konsoli natywnych aplikacji dla systemu Windows, system macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-242">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="0fe7f-243">Zobacz [wprowadzenie do architektury .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-243">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="0fe7f-244">.NET standard</span><span class="sxs-lookup"><span data-stu-id="0fe7f-244">.NET Standard</span></span>

<span data-ttu-id="0fe7f-245">Formalną specyfikację interfejsów API architektury .NET, które są dostępne w każdej implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-245">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="0fe7f-246">Specyfikacja .NET Standard jest niekiedy nazywany biblioteki w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-246">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="0fe7f-247">Ponieważ biblioteki zawiera implementacji interfejsu API, nie tylko specyfikacje (interfejsy), jest mylący, aby wywołać .NET Standard, "library".</span><span class="sxs-lookup"><span data-stu-id="0fe7f-247">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="0fe7f-248">Firma Microsoft planuje wyeliminować wykorzystanie z dokumentacji, z wyjątkiem w odniesieniu do nazwy .NET Standard metapackage (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-248">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="0fe7f-249">Zobacz [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-249">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="0fe7f-250">NARZĘDZIE NGEN</span><span class="sxs-lookup"><span data-stu-id="0fe7f-250">NGEN</span></span>

<span data-ttu-id="0fe7f-251">Generowanie Native (obraz).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-251">Native (image) generation.</span></span>

<span data-ttu-id="0fe7f-252">Ta technologia można traktować jako trwałe kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-252">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="0fe7f-253">Zazwyczaj kompiluje kodu na komputerze, na którym wykonywany jest kod, ale kompilacji zazwyczaj występuje podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-253">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="0fe7f-254">Pakiet</span><span class="sxs-lookup"><span data-stu-id="0fe7f-254">package</span></span>

<span data-ttu-id="0fe7f-255">Pakiet NuGet &mdash; lub po prostu pakietu &mdash; jest *.zip* plików z jednego lub więcej zestawów o tej samej nazwie, oraz dodatkowe metadane, takie jak nazwisko autora.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-255">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="0fe7f-256">*.Zip* plik ma *.nupkg* rozszerzenia i mogą zawierać zasoby, takie jak *.dll* plików i *.xml* plików do użytku z wielu struktury i wersje.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-256">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple frameworks and versions.</span></span> <span data-ttu-id="0fe7f-257">Podczas instalowania aplikacji lub w bibliotece, odpowiednie zasoby są zaznaczone, oparty na platformie docelowej określonej przez aplikację lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-257">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="0fe7f-258">Zasoby, które definiują interfejsu znajdują się w *ref* folderu i zasoby, które definiują implementacji znajdują się w *lib* folderu.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-258">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="0fe7f-259">platforma</span><span class="sxs-lookup"><span data-stu-id="0fe7f-259">platform</span></span>

<span data-ttu-id="0fe7f-260">System operacyjny i sprzętu, który jest uruchamiany na, takie jak Windows, system macOS, Linux, iOS i Android.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-260">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="0fe7f-261">Poniżej przedstawiono przykłady użycia w zdaniach:</span><span class="sxs-lookup"><span data-stu-id="0fe7f-261">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="0fe7f-262">".NET core jest implementacja i platform .NET".</span><span class="sxs-lookup"><span data-stu-id="0fe7f-262">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="0fe7f-263">"PCL profile reprezentują platform firmy Microsoft, gdy .NET Standard jest niezależny od platformy."</span><span class="sxs-lookup"><span data-stu-id="0fe7f-263">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="0fe7f-264">Dokumentacja platformy .NET często używa "Platformy .NET" oznacza implementacja .NET albo stosu .NET, w tym wszystkich implementacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-264">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="0fe7f-265">Obie te metody użycia zazwyczaj można pobrać mylić z podstawowe znaczenie (systemu operacyjnego/sprzęt), dlatego firma Microsoft planuje wyeliminować te użycia w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-265">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="0fe7f-266">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0fe7f-266">runtime</span></span>

<span data-ttu-id="0fe7f-267">Środowiska wykonania programu zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-267">The execution environment for a managed program.</span></span>

<span data-ttu-id="0fe7f-268">System operacyjny jest częścią środowiska uruchomieniowego, ale nie jest częścią środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-268">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="0fe7f-269">Oto kilka przykładów środowisk uruchomieniowych .NET:</span><span class="sxs-lookup"><span data-stu-id="0fe7f-269">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="0fe7f-270">Środowisko uruchomieniowe języka wspólnego (CLR)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-270">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="0fe7f-271">Podstawowe środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-271">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="0fe7f-272">Architektura .NET native (dla platformy uniwersalnej systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-272">.NET Native (for UWP)</span></span>
- <span data-ttu-id="0fe7f-273">Środowisko uruchomieniowe mono</span><span class="sxs-lookup"><span data-stu-id="0fe7f-273">Mono runtime</span></span>

<span data-ttu-id="0fe7f-274">Czasami dokumentację .NET używa "runtime" oznacza implementację programu .NET.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-274">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="0fe7f-275">Na przykład w następujących zdania "runtime" powinna zostać zastąpiona "wdrożenia":</span><span class="sxs-lookup"><span data-stu-id="0fe7f-275">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="0fe7f-276">"Różnych środowisk uruchomieniowych .NET implementuje określonych wersji platformy .NET Standard".</span><span class="sxs-lookup"><span data-stu-id="0fe7f-276">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="0fe7f-277">"Bibliotek, które są przeznaczone do uruchamiania na wiele środowisk uruchomieniowych powinien tej platformy docelowej."</span><span class="sxs-lookup"><span data-stu-id="0fe7f-277">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="0fe7f-278">(odwołujące się do platformy .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="0fe7f-278">(referring to .NET Standard)</span></span>
- <span data-ttu-id="0fe7f-279">"Różnych środowisk uruchomieniowych .NET implementuje określonych wersji platformy .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-279">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="0fe7f-280">…</span><span class="sxs-lookup"><span data-stu-id="0fe7f-280">…</span></span> <span data-ttu-id="0fe7f-281">Każda wersja środowiska uruchomieniowego .NET anonsuje najnowsza wersja platformy .NET Standard obsługiwanych..."</span><span class="sxs-lookup"><span data-stu-id="0fe7f-281">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="0fe7f-282">Firma Microsoft planuje wyeliminować ten niespójne użycie.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-282">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="0fe7f-283">stack</span><span class="sxs-lookup"><span data-stu-id="0fe7f-283">stack</span></span>

<span data-ttu-id="0fe7f-284">Zestaw programowania technologie, które są stosowane razem w celu tworzenia i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-284">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="0fe7f-285">"Stosu .NET" odnosi się do wszystkich implementacji .NET i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-285">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="0fe7f-286">Wyrażenie "stos .NET" może odwoływać się do jednego wdrożenia programu .NET.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-286">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="0fe7f-287">Platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="0fe7f-287">target framework</span></span>

<span data-ttu-id="0fe7f-288">Kolekcja aplikacji .NET lub biblioteki korzysta z interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-288">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="0fe7f-289">Aplikacji lub biblioteki można wersja docelowa platformy .NET Standard (na przykład, .NET Standard 2.0), która jest specyfikacją standardowy zestaw interfejsów API we wszystkich wdrożeniach .NET.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-289">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="0fe7f-290">To aplikacja lub biblioteki można również wersja docelowa platformy konkretnej implementacji .NET, w tym przypadku go pobiera dostępu do konkretnej implementacji interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-290">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="0fe7f-291">Na przykład aplikacja, która jest przeznaczony dla platformy Xamarin.iOS uzyskuje dostęp do otoki dostarczane do platformy Xamarin iOS interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-291">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="0fe7f-292">Dla niektórych docelowych platform (na przykład, .NET Framework) dostępnych interfejsach API są definiowane przez zestawy, które instaluje implementacji programu .NET w systemie, które mogą zawierać struktury aplikacji interfejsów API (na przykład ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-292">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="0fe7f-293">Dla struktury docelowej na podstawie pakietu (na przykład standardowe .NET i .NET Core) framework interfejsy API są definiowane przez pakiety zainstalowane w aplikacji lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-293">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="0fe7f-294">W takim przypadku platforma docelowa określa niejawnie metapackage, który odwołuje się do wszystkich pakietów, które składają się platformę.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-294">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="0fe7f-295">Zobacz [platform docelowych](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-295">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="0fe7f-296">TFM</span><span class="sxs-lookup"><span data-stu-id="0fe7f-296">TFM</span></span>

<span data-ttu-id="0fe7f-297">Moniker platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-297">Target framework moniker.</span></span>

<span data-ttu-id="0fe7f-298">Standardowym formacie token służący do określania platformę docelową aplikacji .NET lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-298">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="0fe7f-299">Docelowych platform zwykle odwołuje się krótką nazwę, taką jak `net462`.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-299">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="0fe7f-300">TFMs długiej (np. NETFramework, Version = 4.6.2) istnieje, ale nie są zwykle używane do określ platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-300">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="0fe7f-301">Zobacz [platform docelowych](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-301">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="0fe7f-302">Platforma UWP</span><span class="sxs-lookup"><span data-stu-id="0fe7f-302">UWP</span></span>

<span data-ttu-id="0fe7f-303">Platforma uniwersalna systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-303">Universal Windows Platform.</span></span>

<span data-ttu-id="0fe7f-304">Implementacja programu .NET, który jest używany do tworzenia nowoczesnych, obsługą dotyku aplikacji systemu Windows, jak i oprogramowania dla Internetu rzeczy (IoT).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-304">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="0fe7f-305">Zostało zaprojektowane do ujednolicenie różne typy urządzeń, które chcesz docelowych, łącznie z komputerami, tablety, phablets, telefony i nawet Xbox.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-305">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="0fe7f-306">Platformy uniwersalnej systemu Windows udostępnia wiele usług, takich jak scentralizowane sklepu, środowiska wykonawczego (AppContainer) i zestaw interfejsów API systemu Windows do użycia zamiast Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="0fe7f-306">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="0fe7f-307">Aplikacje mogą być napisane w języku C++, C#, VB.NET i JavaScript.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-307">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="0fe7f-308">Korzystając z języka C# i VB.NET, interfejsów API architektury .NET są udostępniane przez oprogramowanie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fe7f-308">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fe7f-309">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fe7f-309">See also</span></span>

[<span data-ttu-id="0fe7f-310">.NET — przewodnik</span><span class="sxs-lookup"><span data-stu-id="0fe7f-310">.NET Guide</span></span>](index.md)  
[<span data-ttu-id="0fe7f-311">.NET framework — przewodnik</span><span class="sxs-lookup"><span data-stu-id="0fe7f-311">.NET Framework Guide</span></span>](../framework/index.md)  
[<span data-ttu-id="0fe7f-312">.NET Core</span><span class="sxs-lookup"><span data-stu-id="0fe7f-312">.NET Core</span></span>](../core/index.md)  
[<span data-ttu-id="0fe7f-313">Omówienie programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0fe7f-313">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)  
[<span data-ttu-id="0fe7f-314">Przegląd platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0fe7f-314">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)  

