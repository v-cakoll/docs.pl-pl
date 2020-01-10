---
title: Tworzenie bibliotek za pomocą narzędzi międzyplatformowych
description: Dowiedz się, jak tworzyć biblioteki platformy .NET Core przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core. Utworzysz bibliotekę, która obsługuje wiele platform.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: 4132113037e6c5ec555d2d1859b8217a1a53d07f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714028"
---
# <a name="develop-libraries-with-cross-platform-tools"></a><span data-ttu-id="2018d-104">Tworzenie bibliotek za pomocą narzędzi dla wielu platform</span><span class="sxs-lookup"><span data-stu-id="2018d-104">Develop libraries with cross-platform tools</span></span>

<span data-ttu-id="2018d-105">W tym artykule opisano sposób pisania bibliotek dla platformy .NET przy użyciu międzyplatformowych narzędzi interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2018d-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="2018d-106">Interfejs wiersza polecenia zapewnia wydajne i niskie środowisko, które działa w ramach dowolnego obsługiwanego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2018d-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="2018d-107">Nadal możesz tworzyć biblioteki za pomocą programu Visual Studio, a jeśli jest to preferowane środowisko, [zapoznaj się z przewodnikiem programu Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="2018d-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2018d-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2018d-108">Prerequisites</span></span>

<span data-ttu-id="2018d-109">Na maszynie [jest wymagane zestaw .NET Core SDK i interfejs wiersza polecenia](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="2018d-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="2018d-110">W przypadku sekcji tego dokumentu, w których znajdują się .NET Framework wersje, potrzebne są [.NET Framework](https://dotnet.microsoft.com) zainstalowane na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="2018d-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="2018d-111">Ponadto, jeśli chcesz obsługiwać starsze elementy docelowe .NET Framework, musisz zainstalować pakiety językowe lub pakiety deweloperskie ze [strony archiwa pobierania programu .NET](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="2018d-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="2018d-112">Zapoznaj się z tą tabelą:</span><span class="sxs-lookup"><span data-stu-id="2018d-112">Refer to this table:</span></span>

| <span data-ttu-id="2018d-113">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2018d-113">.NET Framework version</span></span> | <span data-ttu-id="2018d-114">Co należy pobrać</span><span class="sxs-lookup"><span data-stu-id="2018d-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="2018d-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="2018d-115">4.6.1</span></span>                  | <span data-ttu-id="2018d-116">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="2018d-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="2018d-117">4.6</span><span class="sxs-lookup"><span data-stu-id="2018d-117">4.6</span></span>                    | <span data-ttu-id="2018d-118">Pakiet docelowy .NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="2018d-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="2018d-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="2018d-119">4.5.2</span></span>                  | <span data-ttu-id="2018d-120">.NET Framework 4.5.2 — Pakiet dewelopera</span><span class="sxs-lookup"><span data-stu-id="2018d-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="2018d-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="2018d-121">4.5.1</span></span>                  | <span data-ttu-id="2018d-122">.NET Framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="2018d-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="2018d-123">4.5</span><span class="sxs-lookup"><span data-stu-id="2018d-123">4.5</span></span>                    | <span data-ttu-id="2018d-124">Zestaw Windows Software Development Kit dla systemu Windows 8</span><span class="sxs-lookup"><span data-stu-id="2018d-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="2018d-125">4.0</span><span class="sxs-lookup"><span data-stu-id="2018d-125">4.0</span></span>                    | <span data-ttu-id="2018d-126">Windows SDK dla systemów Windows 7 i .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="2018d-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="2018d-127">2,0, 3,0 i 3,5</span><span class="sxs-lookup"><span data-stu-id="2018d-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="2018d-128">Środowisko uruchomieniowe .NET Framework 3,5 z dodatkiem SP1 (lub Windows 8 + wersja)</span><span class="sxs-lookup"><span data-stu-id="2018d-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="2018d-129">Jak kierować .NET Standard</span><span class="sxs-lookup"><span data-stu-id="2018d-129">How to target the .NET Standard</span></span>

<span data-ttu-id="2018d-130">Jeśli nie znasz .NET Standard, zapoznaj się z [.NET Standard](../../standard/net-standard.md) , aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="2018d-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="2018d-131">W tym artykule znajduje się tabela, która mapuje wersje .NET Standard na różne implementacje:</span><span class="sxs-lookup"><span data-stu-id="2018d-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="2018d-132">W tej tabeli przedstawiono informacje na temat celów tworzenia biblioteki:</span><span class="sxs-lookup"><span data-stu-id="2018d-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="2018d-133">Wybrana wersja .NET Standard będzie stanowić kompromis między dostępem do najnowszych interfejsów API i możliwością docelową do większej liczby implementacji platformy .NET i wersji .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2018d-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="2018d-134">Zakres docelowych platform i wersji można kontrolować, wybierając wersję `netstandardX.X` (gdzie `X.X` jest numerem wersji) i dodając do pliku projektu (`.csproj` lub `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="2018d-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="2018d-135">W przypadku .NET Standard, w zależności od potrzeb, są dostępne trzy podstawowe opcje.</span><span class="sxs-lookup"><span data-stu-id="2018d-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="2018d-136">Możesz użyć domyślnej wersji .NET Standard dostarczonej przez szablony `netstandard1.4`, która zapewnia dostęp do większości interfejsów API na .NET Standard przy zachowaniu zgodności z platformy UWP, .NET Framework 4.6.1 i .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="2018d-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="2018d-137">Możesz użyć mniejszej lub wyższej wersji .NET Standard, modyfikując wartość w węźle `TargetFramework` pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2018d-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="2018d-138">Wersje .NET Standard są zgodne z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="2018d-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="2018d-139">Oznacza to, że biblioteki `netstandard1.0` działają na platformach `netstandard1.1` i wyższych.</span><span class="sxs-lookup"><span data-stu-id="2018d-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="2018d-140">Nie ma jednak żadnych zgodności do przodu.</span><span class="sxs-lookup"><span data-stu-id="2018d-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="2018d-141">Niższe .NET Standard platformy nie mogą odwoływać się do wyższych.</span><span class="sxs-lookup"><span data-stu-id="2018d-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="2018d-142">Oznacza to, że biblioteki `netstandard1.0` nie mogą odwoływać się do bibliotek docelowych `netstandard1.1` lub wyższych.</span><span class="sxs-lookup"><span data-stu-id="2018d-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="2018d-143">Wybierz wersję standardową, która ma odpowiednie kombinacje interfejsów API i obsługi platformy dla Twoich potrzeb.</span><span class="sxs-lookup"><span data-stu-id="2018d-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="2018d-144">Zalecamy teraz `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="2018d-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="2018d-145">Jeśli chcesz dowiedzieć się, .NET Framework wersje 4,0 lub starsze, lub chcesz użyć interfejsu API dostępnego w .NET Framework, ale nie w .NET Standard (na przykład `System.Drawing`), przeczytaj następujące sekcje i Dowiedz się, jak utworzyć element.</span><span class="sxs-lookup"><span data-stu-id="2018d-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="2018d-146">Jak kierować .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2018d-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="2018d-147">W tych instrukcjach przyjęto założenie, że na komputerze zainstalowano .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2018d-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="2018d-148">Zapoznaj się z [wymaganiami wstępnymi](#prerequisites) , aby uzyskać zainstalowane zależności.</span><span class="sxs-lookup"><span data-stu-id="2018d-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="2018d-149">Należy pamiętać, że niektóre wersje .NET Framework używane w tym miejscu nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2018d-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="2018d-150">Zapoznaj się z [zasadami cyklu pomocy technicznej .NET Framework — często zadawane pytania](https://support.microsoft.com/gp/framework_faq/en-us) dotyczące nieobsługiwanych wersji.</span><span class="sxs-lookup"><span data-stu-id="2018d-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="2018d-151">Jeśli chcesz osiągnąć maksymalną liczbę deweloperów i projektów, użyj .NET Framework 4,0 jako celu punktu odniesienia.</span><span class="sxs-lookup"><span data-stu-id="2018d-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="2018d-152">Aby docelowa .NET Framework, Zacznij od używania prawidłowej monikera platformy docelowej (TFM) odpowiadającej wersji .NET Framework, która ma być obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="2018d-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="2018d-153">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2018d-153">.NET Framework version</span></span> | <span data-ttu-id="2018d-154">TFM</span><span class="sxs-lookup"><span data-stu-id="2018d-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="2018d-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="2018d-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="2018d-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="2018d-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="2018d-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="2018d-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="2018d-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="2018d-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="2018d-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="2018d-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="2018d-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="2018d-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="2018d-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="2018d-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="2018d-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="2018d-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="2018d-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="2018d-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="2018d-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="2018d-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="2018d-165">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="2018d-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="2018d-166">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="2018d-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="2018d-167">Następnie należy wstawić ten TFM do sekcji `TargetFramework` w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2018d-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="2018d-168">Załóżmy na przykład, że napiszesz bibliotekę, która jest przeznaczona dla .NET Framework 4,0:</span><span class="sxs-lookup"><span data-stu-id="2018d-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="2018d-169">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="2018d-169">And that's it!</span></span> <span data-ttu-id="2018d-170">Chociaż jest to kompilowane tylko dla .NET Framework 4, można użyć biblioteki w nowszych wersjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2018d-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="2018d-171">Jak wieloelementowy</span><span class="sxs-lookup"><span data-stu-id="2018d-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="2018d-172">W poniższych instrukcjach przyjęto założenie, że na komputerze zainstalowano .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2018d-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="2018d-173">Zapoznaj się z sekcją [wymagania wstępne](#prerequisites) , aby dowiedzieć się, które zależności należy zainstalować i skąd mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="2018d-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="2018d-174">Może być konieczne określenie starszych wersji .NET Framework, gdy projekt obsługuje zarówno .NET Framework, jak i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2018d-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="2018d-175">W tym scenariuszu, jeśli chcesz użyć nowszych interfejsów API i konstrukcji językowych dla nowszych elementów docelowych, użyj dyrektyw `#if` w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2018d-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="2018d-176">Może być również konieczne dodanie różnych pakietów i zależności dla każdej platformy docelowej, która obejmuje różne interfejsy API potrzebne do każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="2018d-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="2018d-177">Załóżmy na przykład, że masz bibliotekę, która wykonuje operacje sieciowe za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="2018d-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="2018d-178">W przypadku .NET Standard i .NET Framework wersji 4,5 lub nowszej można użyć klasy `HttpClient` z przestrzeni nazw `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="2018d-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="2018d-179">Jednak wcześniejsze wersje .NET Framework nie mają klasy `HttpClient`, dlatego można zamiast nich użyć klasy `WebClient` z przestrzeni nazw `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="2018d-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="2018d-180">Plik projektu może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="2018d-180">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="2018d-181">Zobaczysz trzy najważniejsze zmiany tutaj:</span><span class="sxs-lookup"><span data-stu-id="2018d-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="2018d-182">Węzeł `TargetFramework` został zastąpiony przez `TargetFrameworks`, a trzy TFMs są wyrażone wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="2018d-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="2018d-183">Istnieje `<ItemGroup>` węzeł do ściągania `net40` docelowego w jednym .NET Framework odwołaniu.</span><span class="sxs-lookup"><span data-stu-id="2018d-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="2018d-184">Istnieje `<ItemGroup>` węzeł, dla którego `net45` docelowy ściągania w dwóch .NET Framework odwołaniach.</span><span class="sxs-lookup"><span data-stu-id="2018d-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="2018d-185">System kompilacji ma świadomość następujących symboli preprocesora używanych w dyrektywach `#if`:</span><span class="sxs-lookup"><span data-stu-id="2018d-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="2018d-186">Oto przykład użycia kompilacji warunkowej dla elementu docelowego:</span><span class="sxs-lookup"><span data-stu-id="2018d-186">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="2018d-187">Jeśli kompilujesz ten projekt przy użyciu `dotnet build`, zobaczysz trzy katalogi w folderze `bin/`:</span><span class="sxs-lookup"><span data-stu-id="2018d-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="2018d-188">Każdy z nich zawiera pliki `.dll` dla każdego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="2018d-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="2018d-189">Testowanie bibliotek w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="2018d-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="2018d-190">Ważne jest, aby móc testować między platformami.</span><span class="sxs-lookup"><span data-stu-id="2018d-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="2018d-191">Możesz użyć [xUnit](https://xunit.github.io/) lub MSTest z pola.</span><span class="sxs-lookup"><span data-stu-id="2018d-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="2018d-192">Oba są doskonale odpowiednie do testowania jednostkowego biblioteki w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2018d-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="2018d-193">Sposób konfigurowania rozwiązania przy użyciu projektów testowych będzie zależeć od [struktury rozwiązania](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="2018d-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="2018d-194">W poniższym przykładzie przyjęto założenie, że katalogi testowe i źródłowe znajdują się w tym samym katalogu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="2018d-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="2018d-195">Spowoduje to użycie niektórych [poleceń interfejs wiersza polecenia platformy .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="2018d-195">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="2018d-196">Aby uzyskać więcej informacji, zobacz temat [dotnet New](../tools/dotnet-new.md) i [dotnet sln](../tools/dotnet-sln.md) .</span><span class="sxs-lookup"><span data-stu-id="2018d-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="2018d-197">Skonfiguruj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="2018d-197">Set up your solution.</span></span> <span data-ttu-id="2018d-198">Można to zrobić za pomocą następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="2018d-198">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="2018d-199">Spowoduje to utworzenie projektów i połączenie ich ze sobą w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="2018d-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="2018d-200">Katalog dla `SolutionWithSrcAndTest` powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="2018d-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="2018d-201">Przejdź do katalogu projektu testowego i Dodaj odwołanie do `MyProject.Test` z `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="2018d-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="2018d-202">Przywróć pakiety i projekty kompilacji:</span><span class="sxs-lookup"><span data-stu-id="2018d-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="2018d-203">Sprawdź, czy xUnit działa, wykonując polecenie `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="2018d-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="2018d-204">W przypadku wybrania opcji używania MSTest, zamiast tego należy uruchomić moduł uruchamiający konsolę programu MSTest.</span><span class="sxs-lookup"><span data-stu-id="2018d-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="2018d-205">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="2018d-205">And that's it!</span></span> <span data-ttu-id="2018d-206">Teraz można testować bibliotekę na wszystkich platformach przy użyciu narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2018d-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="2018d-207">Aby kontynuować testowanie teraz, gdy wszystko jest skonfigurowane, testowanie biblioteki jest bardzo proste:</span><span class="sxs-lookup"><span data-stu-id="2018d-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="2018d-208">Wprowadź zmiany w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="2018d-208">Make changes to your library.</span></span>
1. <span data-ttu-id="2018d-209">Uruchom testy z wiersza polecenia w katalogu testowym przy użyciu polecenia `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="2018d-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="2018d-210">Kod zostanie automatycznie odbudowany po wywołaniu polecenia `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="2018d-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="2018d-211">Jak używać wielu projektów</span><span class="sxs-lookup"><span data-stu-id="2018d-211">How to use multiple projects</span></span>

<span data-ttu-id="2018d-212">Typowym potrzebą dla większych bibliotek jest umieszczenie funkcjonalności w różnych projektach.</span><span class="sxs-lookup"><span data-stu-id="2018d-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="2018d-213">Załóżmy, że chcesz skompilować bibliotekę, która może być używana w idiomatyczne C# i F#.</span><span class="sxs-lookup"><span data-stu-id="2018d-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="2018d-214">Oznacza to, że konsumenci biblioteki wykorzystują ją w sposób naturalny C# lub. F#</span><span class="sxs-lookup"><span data-stu-id="2018d-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="2018d-215">Na przykład w programie C# można użyć biblioteki podobnej do tej:</span><span class="sxs-lookup"><span data-stu-id="2018d-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="2018d-216">W F#programie może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="2018d-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="2018d-217">Scenariusze użycia, takie jak to znaczy, że dostępne interfejsy API muszą mieć inną strukturę dla C# i F#.</span><span class="sxs-lookup"><span data-stu-id="2018d-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="2018d-218">Typowym podejściem do osiągnięcia tego celu jest spełnienie wszystkich logiki biblioteki w projekcie podstawowym, z C# projektami i F# Definiowanie warstw interfejsu API wywołujących ten projekt podstawowy.</span><span class="sxs-lookup"><span data-stu-id="2018d-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="2018d-219">Pozostała część sekcji będzie używać następujących nazw:</span><span class="sxs-lookup"><span data-stu-id="2018d-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="2018d-220">**AwesomeLibrary. Core** — projekt podstawowy, który zawiera wszystkie logike dla biblioteki</span><span class="sxs-lookup"><span data-stu-id="2018d-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="2018d-221">**AwesomeLibrary. CSharp** — projekt z publicznymi interfejsami API przeznaczonymi do użycia w programieC#</span><span class="sxs-lookup"><span data-stu-id="2018d-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="2018d-222">**AwesomeLibrary. FSharp** — projekt z publicznymi interfejsami API przeznaczonymi do użycia w programieF#</span><span class="sxs-lookup"><span data-stu-id="2018d-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="2018d-223">W terminalu można uruchomić następujące polecenia, aby utworzyć tę samą strukturę co ten przewodnik:</span><span class="sxs-lookup"><span data-stu-id="2018d-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="2018d-224">Spowoduje to dodanie trzech projektów powyżej i pliku rozwiązania, który łączy je ze sobą.</span><span class="sxs-lookup"><span data-stu-id="2018d-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="2018d-225">Tworzenie pliku rozwiązania i łączenie projektów umożliwi przywracanie i Kompilowanie projektów na poziomie najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="2018d-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="2018d-226">Odwołanie projektu do projektu</span><span class="sxs-lookup"><span data-stu-id="2018d-226">Project-to-project referencing</span></span>

<span data-ttu-id="2018d-227">Najlepszym sposobem odwoływania się do projektu jest użycie interfejs wiersza polecenia platformy .NET Core, aby dodać odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="2018d-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="2018d-228">Z katalogów projektów **AwesomeLibrary. CSharp** i **AwesomeLibrary. FSharp** można uruchomić następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="2018d-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="2018d-229">Pliki projektu dla obu **AwesomeLibrary. CSharp** i **AwesomeLibrary. FSharp** będą teraz odwoływać się do **AwesomeLibrary. Core** jako element docelowy `ProjectReference`.</span><span class="sxs-lookup"><span data-stu-id="2018d-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="2018d-230">Można to sprawdzić, sprawdzając pliki projektu i wyświetlając następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="2018d-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="2018d-231">Tę sekcję można dodać do każdego pliku projektu ręcznie, jeśli wolisz nie używać interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2018d-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="2018d-232">Tworzenie struktury rozwiązania</span><span class="sxs-lookup"><span data-stu-id="2018d-232">Structuring a solution</span></span>

<span data-ttu-id="2018d-233">Innym ważnym aspektem rozwiązań z zakresu projektów jest ustanowienie dobrej ogólnej struktury projektu.</span><span class="sxs-lookup"><span data-stu-id="2018d-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="2018d-234">Możesz również zorganizować kod, a dopóki każdy projekt zostanie połączony z plikiem rozwiązania za pomocą `dotnet sln add`, będzie można uruchamiać `dotnet restore` i `dotnet build` na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2018d-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
