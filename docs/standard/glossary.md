---
title: Słownik platformy .NET
description: Dowiedz się, jak awioduje znaczenie wybranych terminów używanych w dokumentacji .NET.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 8da1d858835210590a80a624fb8989fbfe8e0a91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400436"
---
# <a name="net-glossary"></a><span data-ttu-id="5bcd2-103">Słownik platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5bcd2-103">.NET Glossary</span></span>

<span data-ttu-id="5bcd2-104">Głównym celem tego glosariusza jest wyjaśnienie znaczeń wybranych terminów i akronimów, które często pojawiają się w dokumentacji .NET bez definicji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="5bcd2-105">AOT</span><span class="sxs-lookup"><span data-stu-id="5bcd2-105">AOT</span></span>

<span data-ttu-id="5bcd2-106">Kompilator z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="5bcd2-107">Podobnie jak [JIT](#jit), ten kompilator tłumaczy również [IL](#il) na kod maszynowy.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="5bcd2-108">W przeciwieństwie do kompilacji JIT kompilacji AOT dzieje się przed wykonaniem aplikacji i jest zwykle wykonywane na innym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="5bcd2-109">Ponieważ łańcuchy narzędzi AOT nie są kompilowane w czasie wykonywania, nie muszą minimalizować czasu spędzonego na kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="5bcd2-110">Oznacza to, że mogą poświęcić więcej czasu na optymalizację.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="5bcd2-111">Ponieważ kontekst AOT jest cała aplikacja, kompilator AOT wykonuje również łączenie modułów krzyżowych i analizy całego programu, co oznacza, że wszystkie odwołania są przestrzegane i jeden plik wykonywalny jest produkowany.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="5bcd2-112">Zobacz [CoreRT](#corert) i [.NET Native](#net-native).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="5bcd2-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bcd2-113">ASP.NET</span></span>

<span data-ttu-id="5bcd2-114">Oryginalny ASP.NET implementacji, która jest dostarczana z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="5bcd2-115">Czasami ASP.NET jest terminem parasolowym, który odnosi się zarówno do ASP.NET implementacji, w tym ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="5bcd2-116">Znaczenie, że termin niesie w danym przypadku jest określana przez kontekst.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="5bcd2-117">Zapoznaj się z ASP.NET 4.x, jeśli chcesz wyjaśnić, że nie używasz ASP.NET oznacza obie implementacje.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-117">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="5bcd2-118">Zobacz [dokumentację ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="5bcd2-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bcd2-119">ASP.NET Core</span></span>

<span data-ttu-id="5bcd2-120">Wieloplatformowa, wydajna implementacja open source ASP.NET zbudowana na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-120">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="5bcd2-121">Zobacz [ASP.NET dokumentację core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="5bcd2-122">zestaw</span><span class="sxs-lookup"><span data-stu-id="5bcd2-122">assembly</span></span>

<span data-ttu-id="5bcd2-123">Plik *.dll*/*.exe,* który może zawierać kolekcję interfejsów API, które mogą być wywoływane przez aplikacje lub inne zestawy.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="5bcd2-124">Zestaw może zawierać typy, takie jak interfejsy, klasy, struktury, wyliczenia i delegatów.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="5bcd2-125">Zestawy w folderze *bin* projektu są czasami nazywane *plikami binarnymi.*</span><span class="sxs-lookup"><span data-stu-id="5bcd2-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="5bcd2-126">Zobacz też [biblioteka](#library).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="5bcd2-127">CLR</span><span class="sxs-lookup"><span data-stu-id="5bcd2-127">CLR</span></span>

<span data-ttu-id="5bcd2-128">Czas wykonywania języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-128">Common Language Runtime.</span></span>

<span data-ttu-id="5bcd2-129">Dokładne znaczenie zależy od kontekstu, ale zwykle odnosi się do czasu wykonywania .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-129">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="5bcd2-130">Clr obsługuje alokację pamięci i zarządzanie.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="5bcd2-131">ŚRODOWISKO CLR jest również maszyną wirtualną, która nie tylko wykonuje aplikacje, ale także generuje i kompiluje kod w locie przy użyciu kompilatora [JIT.](#jit)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span> <span data-ttu-id="5bcd2-132">Bieżąca implementacja programu Microsoft CLR to tylko system Windows.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="5bcd2-133">CoreCLR (Rdzeń CLR)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-133">CoreCLR</span></span>

<span data-ttu-id="5bcd2-134">Program .NET Core Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="5bcd2-135">Ten clr jest zbudowany z tej samej bazy kodu jako CLR.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="5bcd2-136">Pierwotnie CoreCLR był środowiskom uruchomieniowym programu Silverlight i został zaprojektowany do uruchamiania na wielu platformach, w szczególności windows i OS X. CoreCLR jest teraz częścią .NET Core i reprezentuje uproszczoną wersję CLR.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="5bcd2-137">Nadal jest to [wieloplatformowy](#cross-platform) czas pracy, w tym obsługa wielu dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-137">It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="5bcd2-138">CoreCLR jest również maszyną wirtualną z możliwościami jit i wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="5bcd2-139">CoreFX (Polski)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-139">CoreFX</span></span>

<span data-ttu-id="5bcd2-140">Biblioteka klas podstawowych .NET Core (BCL)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-140">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="5bcd2-141">Zestaw bibliotek, które składają się na System. \* (i w ograniczonym\*zakresie Microsoft. ) przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-141">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="5bcd2-142">BCL jest ogólnego przeznaczenia, niższego poziomu struktury, że ramy aplikacji wyższego poziomu, takich jak ASP.NET Core, opierać się na.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-142">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="5bcd2-143">Kod źródłowy bcl .NET Core jest zawarty w [repozytorium runtime .NET Core](https://github.com/dotnet/runtime).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-143">The source code of the .NET Core BCL is contained in the [.NET Core runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="5bcd2-144">Jednak większość interfejsów API .NET Core są również dostępne w .NET Framework, dzięki czemu można myśleć o CoreFX jako rozwidlęce .NET Framework BCL.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-144">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="5bcd2-145">CoreRT (corert)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-145">CoreRT</span></span>

<span data-ttu-id="5bcd2-146">Program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-146">.NET Core runtime.</span></span>

<span data-ttu-id="5bcd2-147">W przeciwieństwie do CLR/CoreCLR, CoreRT nie jest maszyną wirtualną, co oznacza, że nie zawiera urządzeń do generowania i uruchamiania kodu w locie, ponieważ nie zawiera [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-147">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="5bcd2-148">Obejmuje jednak [GC](#gc) i możliwość identyfikacji typu runtime (RTTI) i odbicia.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-148">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="5bcd2-149">Jednak jego system typów został zaprojektowany tak, aby metadane do odbicia nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-149">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="5bcd2-150">Dzięki temu o łańcuch narzędzi [AOT,](#aot) które można połączyć z dala zbędne metadane i (co ważniejsze) zidentyfikować kod, który nie używa aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-150">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="5bcd2-151">CoreRT jest w fazie rozwoju.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-151">CoreRT is in development.</span></span>

<span data-ttu-id="5bcd2-152">Zobacz [Wprowadzenie do .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-152">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="5bcd2-153">na wiele platform</span><span class="sxs-lookup"><span data-stu-id="5bcd2-153">cross-platform</span></span>

<span data-ttu-id="5bcd2-154">Możliwość tworzenia i wykonywania aplikacji, która może być używana w wielu różnych systemach operacyjnych, takich jak Linux, Windows i iOS, bez konieczności ponownego pisania specjalnie dla każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-154">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows and iOS, without having to re-write specifically for each one.</span></span> <span data-ttu-id="5bcd2-155">Umożliwia to ponowne użycie kodu i spójność między aplikacjami na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-155">This enables code re-use and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="5bcd2-156">Ekosystemu</span><span class="sxs-lookup"><span data-stu-id="5bcd2-156">ecosystem</span></span>

<span data-ttu-id="5bcd2-157">Całe oprogramowanie środowiska uruchomieniowego, narzędzia programistyczne i zasoby społeczności, które są używane do tworzenia i uruchamiania aplikacji dla danej technologii.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-157">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="5bcd2-158">Termin "ekosystem.NET" różni się od podobnych terminów, takich jak ".NET stack" w jego włączenie aplikacji innych firm i bibliotek.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-158">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="5bcd2-159">Oto przykład w zdaniu:</span><span class="sxs-lookup"><span data-stu-id="5bcd2-159">Here's an example in a sentence:</span></span>

- <span data-ttu-id="5bcd2-160">"Motywacją standardu [.NET](#net-standard) jest ustanowienie większej jednolitości w ekosystemie .NET."</span><span class="sxs-lookup"><span data-stu-id="5bcd2-160">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="5bcd2-161">szablon</span><span class="sxs-lookup"><span data-stu-id="5bcd2-161">framework</span></span>

<span data-ttu-id="5bcd2-162">Ogólnie rzecz biorąc, kompleksowy zbiór interfejsów API, który ułatwia tworzenie i wdrażanie aplikacji, które są oparte na określonej technologii.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-162">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="5bcd2-163">W tym sensie ogólnym ASP.NET Core i Windows Forms są przykładami struktur aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-163">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="5bcd2-164">Zobacz też [biblioteka](#library).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-164">See also [library](#library).</span></span>

<span data-ttu-id="5bcd2-165">Słowo "framework" ma bardziej szczegółowe znaczenie techniczne w następujących kategoriach:</span><span class="sxs-lookup"><span data-stu-id="5bcd2-165">The word "framework" has a more specific technical meaning in the following terms:</span></span>

- [<span data-ttu-id="5bcd2-166">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5bcd2-166">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="5bcd2-167">ramy docelowe</span><span class="sxs-lookup"><span data-stu-id="5bcd2-167">target framework</span></span>](#target-framework)
- [<span data-ttu-id="5bcd2-168">TFM (pseudonim struktury docelowej)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-168">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="5bcd2-169">W istniejącej dokumentacji "framework" czasami odnosi się do [implementacji .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-169">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="5bcd2-170">Na przykład artykuł może wywołać .NET Core framework.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-170">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="5bcd2-171">Planujemy wyeliminować to mylące użycie z dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-171">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="5bcd2-172">GC</span><span class="sxs-lookup"><span data-stu-id="5bcd2-172">GC</span></span>

<span data-ttu-id="5bcd2-173">Moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-173">Garbage collector.</span></span>

<span data-ttu-id="5bcd2-174">Moduł zbierający elementy bezużyteczne jest implementacją automatycznego zarządzania pamięcią.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-174">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="5bcd2-175">GC zwalnia pamięć zajmowaną przez obiekty, które nie są już używane.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-175">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="5bcd2-176">Zobacz [Wyrzucanie elementów bezużytecznych](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-176">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="5bcd2-177">IL</span><span class="sxs-lookup"><span data-stu-id="5bcd2-177">IL</span></span>

<span data-ttu-id="5bcd2-178">Język pośredni.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-178">Intermediate language.</span></span>

<span data-ttu-id="5bcd2-179">Języki .NET wyższego poziomu, takie jak C#, kompilują się do zestawu instrukcji sprzętowo-agnostycznych, który nazywa się językiem pośrednim (IL).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-179">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="5bcd2-180">IL jest czasami określane jako MSIL (Microsoft IL) lub CIL (Common IL).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-180">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="5bcd2-181">JIT</span><span class="sxs-lookup"><span data-stu-id="5bcd2-181">JIT</span></span>

<span data-ttu-id="5bcd2-182">Kompilator just-in-time.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-182">Just-in-time compiler.</span></span>

<span data-ttu-id="5bcd2-183">Podobnie jak [AOT](#aot), ten kompilator tłumaczy [IL](#il) na kod maszynowy, który rozumie procesor.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-183">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="5bcd2-184">W przeciwieństwie do AOT kompilacji JIT odbywa się na żądanie i jest wykonywana na tym samym komputerze, że kod musi działać na.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-184">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="5bcd2-185">Ponieważ kompilacja JIT występuje podczas wykonywania aplikacji, czas kompilacji jest częścią czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-185">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="5bcd2-186">W związku z tym kompilatory JIT muszą równoważyć czas poświęcony na optymalizację kodu z oszczędnościami, które może wygenerować wynikowy kod.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-186">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="5bcd2-187">Ale JIT zna rzeczywisty sprzęt i może uwolnić programistów od konieczności wysłania różnych implementacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-187">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="5bcd2-188">wdrożenie programu .NET</span><span class="sxs-lookup"><span data-stu-id="5bcd2-188">implementation of .NET</span></span>

<span data-ttu-id="5bcd2-189">Implementacja programu .NET obejmuje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5bcd2-189">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="5bcd2-190">Co najmniej jeden bieg.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-190">One or more runtimes.</span></span> <span data-ttu-id="5bcd2-191">Przykłady: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-191">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="5bcd2-192">Biblioteka klas, która implementuje wersję standardu .NET i może zawierać dodatkowe interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-192">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="5bcd2-193">Przykłady: Biblioteka klas podstawowych .NET Framework, biblioteka podstawowych klas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-193">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="5bcd2-194">Opcjonalnie co najmniej jedna struktura aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-194">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="5bcd2-195">Przykłady: ASP.NET, Formularze systemu Windows i WPF są zawarte w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-195">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="5bcd2-196">Opcjonalnie narzędzia programistyczne.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-196">Optionally, development tools.</span></span> <span data-ttu-id="5bcd2-197">Niektóre narzędzia programistyczne są współużytkowane przez wiele implementacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-197">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="5bcd2-198">Przykłady implementacji .NET:</span><span class="sxs-lookup"><span data-stu-id="5bcd2-198">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="5bcd2-199">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5bcd2-199">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="5bcd2-200">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bcd2-200">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="5bcd2-201">Platforma uniwersalna systemu Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-201">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="5bcd2-202">biblioteka</span><span class="sxs-lookup"><span data-stu-id="5bcd2-202">library</span></span>

<span data-ttu-id="5bcd2-203">Kolekcja interfejsów API, które mogą być wywoływane przez aplikacje lub inne biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-203">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="5bcd2-204">Biblioteka .NET składa się z jednego lub większej [liczby zestawów](#assembly).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-204">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="5bcd2-205">Biblioteki słów i [framework](#framework) są często używane synonimie.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-205">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="5bcd2-206">Metapakiet</span><span class="sxs-lookup"><span data-stu-id="5bcd2-206">metapackage</span></span>

<span data-ttu-id="5bcd2-207">Pakiet NuGet, który nie ma własnej biblioteki, ale jest tylko lista zależności.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-207">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="5bcd2-208">Dołączone pakiety mogą opcjonalnie ustanowić interfejs API dla struktury docelowej.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-208">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="5bcd2-209">Zobacz [pakiety, metapakiety i struktury](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-209">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="5bcd2-210">Mono</span><span class="sxs-lookup"><span data-stu-id="5bcd2-210">Mono</span></span>

<span data-ttu-id="5bcd2-211">Mono jest open source, [cross-platform](#cross-platform) .NET implementacji, która jest używana głównie wtedy, gdy wymagane jest małe źródło.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-211">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="5bcd2-212">Jest to środowisko wykonawcze, które zasila aplikacje Xamarin na Androida, Mac, iOS, tvOS i watchOS i koncentruje się przede wszystkim na aplikacjach, które wymagają niewielkich rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-212">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="5bcd2-213">Obsługuje wszystkie aktualnie opublikowane wersje .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-213">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="5bcd2-214">W przeszłości mono implementowane większy interfejs API .NET Framework i emulował niektóre z najbardziej popularnych funkcji na Unix.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-214">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="5bcd2-215">Czasami jest używany do uruchamiania aplikacji .NET, które opierają się na tych możliwości ach w uniksie.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-215">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="5bcd2-216">Mono jest zwykle używany z kompilatorem just-in-time, ale zawiera również pełny kompilator statyczny (kompilacja z wyprzedzeniem), który jest używany na platformach takich jak iOS.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-216">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="5bcd2-217">Aby dowiedzieć się więcej o mono, zobacz [dokumentację Mono](https://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-217">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="5bcd2-218">.NET</span><span class="sxs-lookup"><span data-stu-id="5bcd2-218">.NET</span></span>

<span data-ttu-id="5bcd2-219">Termin parasolowy dla [.NET Standard](#net-standard) i wszystkich implementacji i obciążeń [.NET.](#implementation-of-net)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-219">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="5bcd2-220">Zawsze kapitalizowane, nigdy ".Net".</span><span class="sxs-lookup"><span data-stu-id="5bcd2-220">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="5bcd2-221">Zobacz [przewodnik .NET](index.md)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-221">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="5bcd2-222">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bcd2-222">.NET Core</span></span>

<span data-ttu-id="5bcd2-223">Implementacja programu .NET o dużej wydajności i wydajności.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-223">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="5bcd2-224">Zawiera core common language runtime (CoreCLR), core AOT Runtime (CoreRT, w rozwoju), core base class library i Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-224">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="5bcd2-225">Zobacz [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-225">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="5bcd2-226">Interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="5bcd2-226">.NET Core CLI</span></span>

<span data-ttu-id="5bcd2-227">Wieloplatformowy łańcuch narzędzi do tworzenia aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-227">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="5bcd2-228">Zobacz [.NET Core CLI](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-228">See [.NET Core CLI](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="5bcd2-229">Zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5bcd2-229">.NET Core SDK</span></span>

<span data-ttu-id="5bcd2-230">Zestaw bibliotek i narzędzi, które umożliwiają deweloperom tworzenie aplikacji i bibliotek .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-230">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="5bcd2-231">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-231">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="5bcd2-232">Zobacz [omówienie sdk rdzenia .NET .](../core/sdk.md)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-232">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="5bcd2-233">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5bcd2-233">.NET Framework</span></span>

<span data-ttu-id="5bcd2-234">Implementacja .NET, która jest uruchamiana tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-234">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="5bcd2-235">Zawiera środowisko uruchomieniowe języka wspólnego (CLR), bibliotekę klas podstawowych i biblioteki struktury aplikacji, takie jak ASP.NET, Formularze systemu Windows i WPF.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-235">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="5bcd2-236">Zobacz [.NET Framework Guide](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-236">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="5bcd2-237">Architektura .NET Native</span><span class="sxs-lookup"><span data-stu-id="5bcd2-237">.NET Native</span></span>

<span data-ttu-id="5bcd2-238">Łańcuch narzędzi kompilatora, który tworzy kod macierzysty z wyprzedzeniem (AOT), w przeciwieństwie do just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-238">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="5bcd2-239">Kompilacja odbywa się na komputerze dewelopera podobny do sposobu kompilator c++ i konsolidator działa.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-239">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="5bcd2-240">Usuwa nieużywany kod i poświęca więcej czasu na jego optymalizację.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-240">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="5bcd2-241">Wyodrębnia kod z bibliotek i scala je z plikiem wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-241">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="5bcd2-242">Wynik jest pojedynczy moduł, który reprezentuje całą aplikację.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-242">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="5bcd2-243">Platforma UWP była pierwszą strukturą aplikacji obsługiwaną przez serwer .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-243">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="5bcd2-244">Teraz obsługujemy tworzenie natywnych aplikacji konsolowych dla systemów Windows, macOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-244">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="5bcd2-245">Zobacz [Wprowadzenie do .NET Native i CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-245">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="5bcd2-246">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="5bcd2-246">.NET Standard</span></span>

<span data-ttu-id="5bcd2-247">Formalna specyfikacja interfejsów API .NET, które są dostępne w każdej implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-247">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="5bcd2-248">Specyfikacja standardu .NET jest czasami nazywana biblioteką w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-248">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="5bcd2-249">Ponieważ biblioteka zawiera implementacje interfejsu API, nie tylko specyfikacje (interfejsy), nazywanie .NET Standard "biblioteką" jest mylące.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-249">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="5bcd2-250">Planujemy wyeliminować to użycie z dokumentacji, z wyjątkiem odwołania do nazwy`NETStandard.Library`metapakietu .NET Standard ( ).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-250">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="5bcd2-251">Zobacz [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-251">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="5bcd2-252">Ngen</span><span class="sxs-lookup"><span data-stu-id="5bcd2-252">NGEN</span></span>

<span data-ttu-id="5bcd2-253">Generacja natywna (obrazu).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-253">Native (image) generation.</span></span>

<span data-ttu-id="5bcd2-254">Tę technologię można pomyśleć jako trwały kompilator JIT.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-254">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="5bcd2-255">Zazwyczaj kompiluje kod na komputerze, na którym wykonywany jest kod, ale kompilacja zwykle występuje w czasie instalacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-255">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="5bcd2-256">Pakiet</span><span class="sxs-lookup"><span data-stu-id="5bcd2-256">package</span></span>

<span data-ttu-id="5bcd2-257">Pakiet &mdash; NuGet lub tylko &mdash; pakiet jest plik *zip* z jednym lub więcej zestawów o tej samej nazwie wraz z dodatkowych metadanych, takich jak nazwa autora.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-257">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="5bcd2-258">Plik *zip* ma rozszerzenie *.nupkg* i może zawierać zasoby, takie jak pliki *dll* i *xml,* do użytku z wieloma platformami docelowymi i wersjami.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-258">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="5bcd2-259">Po zainstalowaniu w aplikacji lub bibliotece odpowiednie zasoby są wybierane na podstawie struktury docelowej określonej przez aplikację lub bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-259">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="5bcd2-260">Zasoby, które definiują interfejs znajdują się w folderze *ref,* a zasoby definiujące implementację znajdują się w folderze *lib.*</span><span class="sxs-lookup"><span data-stu-id="5bcd2-260">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="5bcd2-261">platforma</span><span class="sxs-lookup"><span data-stu-id="5bcd2-261">platform</span></span>

<span data-ttu-id="5bcd2-262">System operacyjny i sprzęt, na który działa, takich jak Windows, macOS, Linux, iOS i Android.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-262">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="5bcd2-263">Oto przykłady użycia w zdaniach:</span><span class="sxs-lookup"><span data-stu-id="5bcd2-263">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="5bcd2-264">".NET Core to implementacja programu .NET na wielu platformach".</span><span class="sxs-lookup"><span data-stu-id="5bcd2-264">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="5bcd2-265">"Profile PCL reprezentują platformy firmy Microsoft, podczas gdy standard .NET jest nieskrępowy dla platformy".</span><span class="sxs-lookup"><span data-stu-id="5bcd2-265">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="5bcd2-266">Dokumentacja platformy .NET często używa "platformy.NET" oznacza implementację .NET lub stos .NET, w tym wszystkie implementacje.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-266">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="5bcd2-267">Oba te użycia mają tendencję do mylone z podstawowym (OS / hardware) znaczenie, więc planujemy wyeliminować te użycia z dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-267">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="5bcd2-268">środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5bcd2-268">runtime</span></span>

<span data-ttu-id="5bcd2-269">Środowisko wykonywania programu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-269">The execution environment for a managed program.</span></span>

<span data-ttu-id="5bcd2-270">Środowisko operacyjne jest częścią środowiska środowiska uruchomieniowego, ale nie jest częścią środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-270">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="5bcd2-271">Oto kilka przykładów uruchomień programu .NET:</span><span class="sxs-lookup"><span data-stu-id="5bcd2-271">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="5bcd2-272">Środowisko uruchomieniowe języka wspólnego (CLR)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-272">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="5bcd2-273">Podstawowy czas wykonywania języka wspólnego (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-273">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="5bcd2-274">Natywna .NET (dla programu UWP)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-274">.NET Native (for UWP)</span></span>
- <span data-ttu-id="5bcd2-275">Czas pracy mono</span><span class="sxs-lookup"><span data-stu-id="5bcd2-275">Mono runtime</span></span>

<span data-ttu-id="5bcd2-276">Dokumentacja .NET czasami używa "runtime" oznacza implementację .NET.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-276">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="5bcd2-277">Na przykład w następujących zdaniach "runtime" należy zastąpić "implementacji":</span><span class="sxs-lookup"><span data-stu-id="5bcd2-277">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="5bcd2-278">"Różne uruchomienia .NET implementują określone wersje standardu .NET."</span><span class="sxs-lookup"><span data-stu-id="5bcd2-278">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="5bcd2-279">"Biblioteki, które są przeznaczone do uruchamiania w wielu serwerach uruchamianych powinny być przeznaczone dla tej struktury."</span><span class="sxs-lookup"><span data-stu-id="5bcd2-279">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="5bcd2-280">(w odniesieniu do .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="5bcd2-280">(referring to .NET Standard)</span></span>
- <span data-ttu-id="5bcd2-281">"Różne uruchomienia programu .NET implementują określone wersje standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-281">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="5bcd2-282">…</span><span class="sxs-lookup"><span data-stu-id="5bcd2-282">…</span></span> <span data-ttu-id="5bcd2-283">Każda wersja programu .NET jest anonsuje najwyższą wersję standardu .NET, która obsługuje ..."</span><span class="sxs-lookup"><span data-stu-id="5bcd2-283">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="5bcd2-284">Planujemy wyeliminować to niespójne użycie.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-284">We plan to eliminate this inconsistent usage.</span></span>

## <a name="stack"></a><span data-ttu-id="5bcd2-285">stack</span><span class="sxs-lookup"><span data-stu-id="5bcd2-285">stack</span></span>

<span data-ttu-id="5bcd2-286">Zestaw technologii programowania, które są używane razem do tworzenia i uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-286">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="5bcd2-287">"Stos .NET" odnosi się do standardu .NET i wszystkich implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-287">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="5bcd2-288">Wyrażenie "stos .NET" może odwoływać się do jednej implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-288">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="5bcd2-289">ramy docelowe</span><span class="sxs-lookup"><span data-stu-id="5bcd2-289">target framework</span></span>

<span data-ttu-id="5bcd2-290">Kolekcja interfejsów API, na których opiera się aplikacja lub biblioteka .NET.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-290">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="5bcd2-291">Aplikacja lub biblioteka może kierować na wersję .NET Standard (na przykład .NET Standard 2.0), która jest specyfikacją standardowego zestawu interfejsów API we wszystkich implementacjach .NET.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-291">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="5bcd2-292">Aplikacja lub biblioteka może również kierować wersję określonej implementacji .NET, w którym to przypadku uzyskuje dostęp do interfejsów API specyficznych dla implementacji.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-292">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="5bcd2-293">Na przykład aplikacja, która jest przeznaczona dla interfejsu Xamarin.iOS, uzyskuje dostęp do otoki interfejsu API z interfejsem iOS dostarczonych przez interfejsy Xamarin.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-293">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="5bcd2-294">W przypadku niektórych platform docelowych (na przykład .NET Framework) dostępne interfejsy API są definiowane przez zestawy, które implementacja .NET instaluje w systemie, co może obejmować interfejsy API platformy aplikacji (na przykład ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-294">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="5bcd2-295">W przypadku platform docelowych opartych na pakiecie (takich jak .NET Standard i .NET Core) interfejsy API struktury są definiowane przez pakiety zainstalowane w aplikacji lub bibliotece.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-295">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="5bcd2-296">W takim przypadku platformy docelowej niejawnie określa metapakiet, który odwołuje się do wszystkich pakietów, które razem tworzą framework.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-296">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="5bcd2-297">Zobacz [platformy docelowe](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-297">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="5bcd2-298">Tfm</span><span class="sxs-lookup"><span data-stu-id="5bcd2-298">TFM</span></span>

<span data-ttu-id="5bcd2-299">Moniker framework docelowy.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-299">Target framework moniker.</span></span>

<span data-ttu-id="5bcd2-300">Znormalizowany format tokenu do określania struktury docelowej aplikacji lub biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-300">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="5bcd2-301">Platformdocelowych są zazwyczaj odwołuje się krótką nazwę, takich jak `net462`.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-301">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="5bcd2-302">Długie tfmy (takie jak . NETFramework,Version=4.6.2) istnieją, ale nie są zazwyczaj używane do określania struktury docelowej.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-302">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="5bcd2-303">Zobacz [platformy docelowe](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-303">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="5bcd2-304">Platforma UWP</span><span class="sxs-lookup"><span data-stu-id="5bcd2-304">UWP</span></span>

<span data-ttu-id="5bcd2-305">Uniwersalna platforma systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-305">Universal Windows Platform.</span></span>

<span data-ttu-id="5bcd2-306">Implementacja .NET, która jest używana do tworzenia nowoczesnych aplikacji i oprogramowania systemu Windows z obsługą dotyku dla Internetu rzeczy (IoT).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-306">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="5bcd2-307">Został zaprojektowany w celu uniewinnienia różnych typów urządzeń, na które chcesz kierować reklamy, w tym komputerów, tabletów, phabletów, telefonów, a nawet konsoli Xbox.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-307">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="5bcd2-308">Platforma UWP udostępnia wiele usług, takich jak scentralizowany sklep z aplikacjami, środowisko wykonywania (AppContainer) i zestaw interfejsów API systemu Windows do użycia zamiast Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="5bcd2-308">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="5bcd2-309">Aplikacje można zapisywać w językach C++, C#, Visual Basic i JavaScript.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-309">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="5bcd2-310">Korzystając z języka C# i Języka Visual Basic, interfejsy API .NET są dostarczane przez .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bcd2-310">When using C# and Visual Basic, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bcd2-311">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bcd2-311">See also</span></span>

- [<span data-ttu-id="5bcd2-312">.NET — przewodnik</span><span class="sxs-lookup"><span data-stu-id="5bcd2-312">.NET Guide</span></span>](index.md)
- [<span data-ttu-id="5bcd2-313">.NET framework — przewodnik</span><span class="sxs-lookup"><span data-stu-id="5bcd2-313">.NET Framework Guide</span></span>](../framework/index.md)
- [<span data-ttu-id="5bcd2-314">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5bcd2-314">.NET Core</span></span>](../core/index.md)
- [<span data-ttu-id="5bcd2-315">Przegląd ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5bcd2-315">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="5bcd2-316">ASP.NET Podstawowe omówienie</span><span class="sxs-lookup"><span data-stu-id="5bcd2-316">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
