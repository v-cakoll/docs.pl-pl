---
title: Tworzenie bibliotek za pomocą narzędzi międzyplatformowych
description: Dowiedz się, jak tworzyć biblioteki platformy .NET Core przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core. Utworzysz bibliotekę, która obsługuje wiele platform.
author: cartermp
ms.date: 05/01/2017
ms.custom: seodec18
ms.openlocfilehash: 536319bc02b45e7948c89ae67988e821a55a842d
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117412"
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="d76d1-104">Tworzenie bibliotek za pomocą narzędzi międzyplatformowych</span><span class="sxs-lookup"><span data-stu-id="d76d1-104">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="d76d1-105">W tym artykule opisano sposób pisania bibliotek dla platformy .NET przy użyciu międzyplatformowych narzędzi interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d76d1-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="d76d1-106">Interfejs wiersza polecenia zapewnia wydajne i niskie środowisko, które działa w ramach dowolnego obsługiwanego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d76d1-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="d76d1-107">Nadal możesz tworzyć biblioteki za pomocą programu Visual Studio, a jeśli jest to preferowane środowisko, [zapoznaj się z przewodnikiem programu Visual Studio](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d76d1-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d76d1-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d76d1-108">Prerequisites</span></span>

<span data-ttu-id="d76d1-109">Na maszynie [jest wymagane zestaw .NET Core SDK i interfejs wiersza polecenia](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="d76d1-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="d76d1-110">W przypadku sekcji tego dokumentu, w których znajdują się .NET Framework wersje, potrzebne są [.NET Framework](https://dotnet.microsoft.com) zainstalowane na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="d76d1-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="d76d1-111">Ponadto, jeśli chcesz obsługiwać starsze elementy docelowe .NET Framework, musisz zainstalować pakiety dla starszych wersji programu, korzystając ze [strony archiwa pobierania programu .NET](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="d76d1-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="d76d1-112">Zapoznaj się z tą tabelą:</span><span class="sxs-lookup"><span data-stu-id="d76d1-112">Refer to this table:</span></span>

| <span data-ttu-id="d76d1-113">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d76d1-113">.NET Framework Version</span></span> | <span data-ttu-id="d76d1-114">Co należy pobrać</span><span class="sxs-lookup"><span data-stu-id="d76d1-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="d76d1-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="d76d1-115">4.6.1</span></span>                  | <span data-ttu-id="d76d1-116">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="d76d1-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="d76d1-117">4.6</span><span class="sxs-lookup"><span data-stu-id="d76d1-117">4.6</span></span>                    | <span data-ttu-id="d76d1-118">Pakiet docelowy .NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="d76d1-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="d76d1-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="d76d1-119">4.5.2</span></span>                  | <span data-ttu-id="d76d1-120">.NET Framework 4.5.2 — Pakiet dewelopera</span><span class="sxs-lookup"><span data-stu-id="d76d1-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="d76d1-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d76d1-121">4.5.1</span></span>                  | <span data-ttu-id="d76d1-122">.NET Framework 4.5.1 — pakiet dewelopera</span><span class="sxs-lookup"><span data-stu-id="d76d1-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="d76d1-123">4.5</span><span class="sxs-lookup"><span data-stu-id="d76d1-123">4.5</span></span>                    | <span data-ttu-id="d76d1-124">Zestaw Windows Software Development Kit dla systemu Windows 8</span><span class="sxs-lookup"><span data-stu-id="d76d1-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="d76d1-125">4.0</span><span class="sxs-lookup"><span data-stu-id="d76d1-125">4.0</span></span>                    | <span data-ttu-id="d76d1-126">Windows SDK dla systemów Windows 7 i .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="d76d1-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="d76d1-127">2,0, 3,0 i 3,5</span><span class="sxs-lookup"><span data-stu-id="d76d1-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="d76d1-128">Środowisko uruchomieniowe .NET Framework 3,5 z dodatkiem SP1 (lub Windows 8 + wersja)</span><span class="sxs-lookup"><span data-stu-id="d76d1-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="d76d1-129">Jak kierować .NET Standard</span><span class="sxs-lookup"><span data-stu-id="d76d1-129">How to target the .NET Standard</span></span>

<span data-ttu-id="d76d1-130">Jeśli nie znasz .NET Standard, zapoznaj się z [.NET Standard](../../standard/net-standard.md) , aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="d76d1-130">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="d76d1-131">W tym artykule znajduje się tabela, która mapuje .NET Standard wersje na różne implementacje:</span><span class="sxs-lookup"><span data-stu-id="d76d1-131">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="d76d1-132">W tej tabeli przedstawiono informacje na temat celów tworzenia biblioteki:</span><span class="sxs-lookup"><span data-stu-id="d76d1-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="d76d1-133">Wybrana wersja .NET Standard będzie stanowić kompromis między dostępem do najnowszych interfejsów API i możliwością docelową do większej liczby implementacji platformy .NET i wersji .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d76d1-133">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="d76d1-134">Możesz kontrolować zakres docelowych platform i wersji `netstandardX.X` , wybierając wersję (gdzie `X.X` jest numerem wersji) i dodając ją do pliku projektu (`.csproj` lub `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="d76d1-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="d76d1-135">Podczas określania .NET Standard są dostępne trzy podstawowe opcje, w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="d76d1-135">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="d76d1-136">Możesz użyć domyślnej wersji .NET Standard dostarczonej przez szablony — `netstandard1.4` która zapewnia dostęp do większości interfejsów API na .NET Standard, mimo że są one zgodne z platformy UWP, .NET Framework 4.6.1 i nadchodzące .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="d76d1-136">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="d76d1-137">Możesz użyć mniejszej lub wyższej wersji .NET Standard, modyfikując wartość w `TargetFramework` węźle pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d76d1-137">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="d76d1-138">Wersje .NET Standard są zgodne z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="d76d1-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="d76d1-139">Oznacza to, `netstandard1.0` że biblioteki są `netstandard1.1` uruchamiane na platformach i wyższych.</span><span class="sxs-lookup"><span data-stu-id="d76d1-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="d76d1-140">Nie istnieje jednak żadna zgodność z niższymi wersjami .NET Standard platformy nie mogą odwoływać się do wyższych.</span><span class="sxs-lookup"><span data-stu-id="d76d1-140">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="d76d1-141">Oznacza to, `netstandard1.0` że biblioteki nie mogą odwoływać się do bibliotek docelowych `netstandard1.1` ani wyższych.</span><span class="sxs-lookup"><span data-stu-id="d76d1-141">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="d76d1-142">Wybierz wersję standardową, która ma odpowiednie kombinacje interfejsów API i obsługi platformy dla Twoich potrzeb.</span><span class="sxs-lookup"><span data-stu-id="d76d1-142">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="d76d1-143">Zalecamy `netstandard1.4` teraz.</span><span class="sxs-lookup"><span data-stu-id="d76d1-143">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="d76d1-144">Jeśli chcesz dowiedzieć się, co .NET Framework w wersji 4,0 lub niższej, lub chcesz użyć interfejsu API dostępnego w .NET Framework, ale nie w .NET Standard (na przykład `System.Drawing`), zapoznaj się z następującymi sekcjami i Dowiedz się, jak utworzyć obiekt.</span><span class="sxs-lookup"><span data-stu-id="d76d1-144">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="d76d1-145">Jak kierować .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d76d1-145">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="d76d1-146">W tych instrukcjach przyjęto założenie, że na maszynie zainstalowano .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d76d1-146">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="d76d1-147">Zapoznaj się z [wymaganiami wstępnymi](#prerequisites) , aby uzyskać zainstalowane zależności.</span><span class="sxs-lookup"><span data-stu-id="d76d1-147">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="d76d1-148">Należy pamiętać, że niektóre wersje .NET Framework używane w tym miejscu nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d76d1-148">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="d76d1-149">Zapoznaj się z [zasadami cyklu pomocy technicznej .NET Framework — często zadawane pytania](https://support.microsoft.com/gp/framework_faq/en-us) dotyczące nieobsługiwanych wersji.</span><span class="sxs-lookup"><span data-stu-id="d76d1-149">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="d76d1-150">Jeśli chcesz uzyskać dostęp do maksymalnej liczby deweloperów i projektów, użyj .NET Framework 4,0 jako celu punktu odniesienia.</span><span class="sxs-lookup"><span data-stu-id="d76d1-150">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="d76d1-151">Aby docelowa .NET Framework, należy rozpocząć od poprawnej monikera platformy docelowej (TFM) odpowiadającej wersji .NET Framework, która ma być obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="d76d1-151">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="d76d1-152">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d76d1-152">.NET Framework version</span></span> | <span data-ttu-id="d76d1-153">TFM</span><span class="sxs-lookup"><span data-stu-id="d76d1-153">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="d76d1-154">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="d76d1-154">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="d76d1-155">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="d76d1-155">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="d76d1-156">Program .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="d76d1-156">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="d76d1-157">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="d76d1-157">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="d76d1-158">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d76d1-158">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="d76d1-159">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="d76d1-159">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="d76d1-160">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="d76d1-160">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="d76d1-161">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="d76d1-161">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="d76d1-162">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="d76d1-162">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="d76d1-163">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="d76d1-163">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="d76d1-164">.NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="d76d1-164">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="d76d1-165">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="d76d1-165">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="d76d1-166">Następnie należy wstawić ten TFM do `TargetFramework` sekcji pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d76d1-166">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="d76d1-167">Załóżmy na przykład, że napiszesz bibliotekę, która jest przeznaczona dla .NET Framework 4,0:</span><span class="sxs-lookup"><span data-stu-id="d76d1-167">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="d76d1-168">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="d76d1-168">And that's it!</span></span> <span data-ttu-id="d76d1-169">Chociaż jest to kompilowane tylko dla .NET Framework 4, można użyć biblioteki w nowszych wersjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d76d1-169">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="d76d1-170">Jak wieloelementowy</span><span class="sxs-lookup"><span data-stu-id="d76d1-170">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="d76d1-171">W poniższych instrukcjach przyjęto założenie, że na komputerze zainstalowano .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d76d1-171">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="d76d1-172">Zapoznaj się z sekcją [wymagania wstępne](#prerequisites) , aby dowiedzieć się, które zależności należy zainstalować i skąd mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="d76d1-172">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="d76d1-173">Może być konieczne określenie starszych wersji .NET Framework, gdy projekt obsługuje zarówno .NET Framework, jak i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76d1-173">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="d76d1-174">W tym scenariuszu, jeśli chcesz użyć nowszych interfejsów API i konstrukcji językowych dla nowszych elementów docelowych, `#if` Użyj dyrektyw w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d76d1-174">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="d76d1-175">Może być również konieczne dodanie różnych pakietów i zależności dla każdej platformy docelowej, która obejmuje różne interfejsy API potrzebne do każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="d76d1-175">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="d76d1-176">Załóżmy na przykład, że masz bibliotekę, która wykonuje operacje sieciowe za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d76d1-176">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="d76d1-177">W przypadku .NET Standard i .NET Framework wersji 4,5 lub nowszej można użyć `HttpClient` klasy `System.Net.Http` z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d76d1-177">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="d76d1-178">Jednak wcześniejsze wersje .NET Framework nie posiadają `HttpClient` klasy, więc zamiast tego można `WebClient` użyć klasy z `System.Net` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d76d1-178">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="d76d1-179">Plik projektu może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d76d1-179">Your project file could look like this:</span></span>

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

<span data-ttu-id="d76d1-180">Zobaczysz trzy najważniejsze zmiany tutaj:</span><span class="sxs-lookup"><span data-stu-id="d76d1-180">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="d76d1-181">Węzeł został zastąpiony przez `TargetFrameworks`, a trzy TFMs są wyrażone wewnątrz. `TargetFramework`</span><span class="sxs-lookup"><span data-stu-id="d76d1-181">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="d76d1-182">`<ItemGroup>` Istnieje węzeł `net40` docelowy ściągania w jednym .NET Framework odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d76d1-182">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="d76d1-183">`<ItemGroup>` Istnieje węzeł `net45` docelowy ściągania dwóch odwołań .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d76d1-183">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="d76d1-184">System kompilacji ma świadomość następujących symboli preprocesora używanych w `#if` dyrektywach:</span><span class="sxs-lookup"><span data-stu-id="d76d1-184">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="d76d1-185">Oto przykład użycia kompilacji warunkowej dla elementu docelowego:</span><span class="sxs-lookup"><span data-stu-id="d76d1-185">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="d76d1-186">W przypadku skompilowania projektu za `dotnet build`pomocą programu zauważysz, że trzy katalogi `bin/` w folderze:</span><span class="sxs-lookup"><span data-stu-id="d76d1-186">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="d76d1-187">Każdy z nich zawiera `.dll` pliki dla każdego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d76d1-187">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="d76d1-188">Testowanie bibliotek w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="d76d1-188">How to test libraries on .NET Core</span></span>

<span data-ttu-id="d76d1-189">Ważne jest, aby móc testować między platformami.</span><span class="sxs-lookup"><span data-stu-id="d76d1-189">It's important to be able to test across platforms.</span></span> <span data-ttu-id="d76d1-190">Możesz użyć [xUnit](https://xunit.github.io/) lub MSTest z pola.</span><span class="sxs-lookup"><span data-stu-id="d76d1-190">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="d76d1-191">Oba są doskonale odpowiednie do testowania jednostkowego biblioteki w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76d1-191">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="d76d1-192">Sposób konfigurowania rozwiązania przy użyciu projektów testowych będzie zależeć od [struktury rozwiązania](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="d76d1-192">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="d76d1-193">W poniższym przykładzie przyjęto założenie, że katalogi testowe i źródłowe znajdują się w tym samym katalogu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d76d1-193">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="d76d1-194">Spowoduje to użycie niektórych [poleceń interfejs wiersza polecenia platformy .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="d76d1-194">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="d76d1-195">Aby uzyskać więcej informacji, zobacz temat [dotnet New](../tools/dotnet-new.md) i [dotnet sln](../tools/dotnet-sln.md) .</span><span class="sxs-lookup"><span data-stu-id="d76d1-195">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="d76d1-196">Skonfiguruj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="d76d1-196">Set up your solution.</span></span> <span data-ttu-id="d76d1-197">Można to zrobić za pomocą następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="d76d1-197">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="d76d1-198">Spowoduje to utworzenie projektów i połączenie ich ze sobą w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="d76d1-198">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="d76d1-199">Katalog dla `SolutionWithSrcAndTest` powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d76d1-199">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="d76d1-200">Przejdź do katalogu projektu testowego i Dodaj odwołanie do `MyProject.Test` elementu from. `MyProject`</span><span class="sxs-lookup"><span data-stu-id="d76d1-200">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="d76d1-201">Przywróć pakiety i projekty kompilacji:</span><span class="sxs-lookup"><span data-stu-id="d76d1-201">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="d76d1-202">Sprawdź, czy xUnit jest uruchamiana `dotnet test` przez wykonanie polecenia.</span><span class="sxs-lookup"><span data-stu-id="d76d1-202">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="d76d1-203">W przypadku wybrania opcji używania MSTest, zamiast tego należy uruchomić moduł uruchamiający konsolę programu MSTest.</span><span class="sxs-lookup"><span data-stu-id="d76d1-203">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="d76d1-204">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="d76d1-204">And that's it!</span></span> <span data-ttu-id="d76d1-205">Teraz można testować bibliotekę na wszystkich platformach przy użyciu narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d76d1-205">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="d76d1-206">Aby kontynuować testowanie teraz, gdy wszystko jest skonfigurowane, testowanie biblioteki jest bardzo proste:</span><span class="sxs-lookup"><span data-stu-id="d76d1-206">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="d76d1-207">Wprowadź zmiany w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="d76d1-207">Make changes to your library.</span></span>
1. <span data-ttu-id="d76d1-208">Uruchom testy z wiersza polecenia w katalogu testowym przy użyciu `dotnet test` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d76d1-208">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="d76d1-209">Kod zostanie automatycznie odbudowany po wywołaniu `dotnet test` polecenia.</span><span class="sxs-lookup"><span data-stu-id="d76d1-209">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="d76d1-210">Jak używać wielu projektów</span><span class="sxs-lookup"><span data-stu-id="d76d1-210">How to use multiple projects</span></span>

<span data-ttu-id="d76d1-211">Typowym potrzebą dla większych bibliotek jest umieszczenie funkcjonalności w różnych projektach.</span><span class="sxs-lookup"><span data-stu-id="d76d1-211">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="d76d1-212">Wyobraź sobie, że chcesz skompilować bibliotekę, która może być używana w idiomatyczne C# i F#.</span><span class="sxs-lookup"><span data-stu-id="d76d1-212">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="d76d1-213">Oznacza to, że konsumenci biblioteki używają ich w sposób naturalny C# lub. F#</span><span class="sxs-lookup"><span data-stu-id="d76d1-213">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="d76d1-214">Na przykład w programie C# można użyć biblioteki podobnej do tej:</span><span class="sxs-lookup"><span data-stu-id="d76d1-214">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="d76d1-215">W F#programie może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d76d1-215">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="d76d1-216">Scenariusze użycia, takie jak to znaczy, że dostępne interfejsy API muszą mieć inną strukturę dla C# i F#.</span><span class="sxs-lookup"><span data-stu-id="d76d1-216">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="d76d1-217">Typowym podejściem do osiągnięcia tego celu jest spełnienie wszystkich logiki biblioteki w projekcie podstawowym, z C# projektami i F# Definiowanie warstw interfejsu API wywołujących ten projekt podstawowy.</span><span class="sxs-lookup"><span data-stu-id="d76d1-217">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="d76d1-218">Pozostała część sekcji będzie używać następujących nazw:</span><span class="sxs-lookup"><span data-stu-id="d76d1-218">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="d76d1-219">**AwesomeLibrary. Core** — projekt podstawowy, który zawiera wszystkie logike dla biblioteki</span><span class="sxs-lookup"><span data-stu-id="d76d1-219">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="d76d1-220">**AwesomeLibrary. CSharp** — projekt z publicznymi interfejsami API przeznaczonymi do użycia w programieC#</span><span class="sxs-lookup"><span data-stu-id="d76d1-220">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="d76d1-221">**AwesomeLibrary. FSharp** — projekt z publicznymi interfejsami API przeznaczonymi do użycia w programieF#</span><span class="sxs-lookup"><span data-stu-id="d76d1-221">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="d76d1-222">W terminalu można uruchomić następujące polecenia, aby utworzyć tę samą strukturę co ten przewodnik:</span><span class="sxs-lookup"><span data-stu-id="d76d1-222">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="d76d1-223">Spowoduje to dodanie trzech projektów powyżej i pliku rozwiązania, który łączy je ze sobą.</span><span class="sxs-lookup"><span data-stu-id="d76d1-223">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="d76d1-224">Tworzenie pliku rozwiązania i łączenie projektów umożliwi przywracanie i Kompilowanie projektów z poziomu najwyższego.</span><span class="sxs-lookup"><span data-stu-id="d76d1-224">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="d76d1-225">Odwołanie projektu do projektu</span><span class="sxs-lookup"><span data-stu-id="d76d1-225">Project-to-project referencing</span></span>

<span data-ttu-id="d76d1-226">Najlepszym sposobem odwoływania się do projektu jest użycie interfejs wiersza polecenia platformy .NET Core, aby dodać odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="d76d1-226">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="d76d1-227">Z katalogów projektów **AwesomeLibrary. CSharp** i **AwesomeLibrary. FSharp** można uruchomić następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d76d1-227">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="d76d1-228">Pliki projektu dla obu **AwesomeLibrary. CSharp** i **AwesomeLibrary. FSharp** będą teraz odwoływać się do **AwesomeLibrary** `ProjectReference` . Core jako element docelowy.</span><span class="sxs-lookup"><span data-stu-id="d76d1-228">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="d76d1-229">Można to sprawdzić, sprawdzając pliki projektu i wyświetlając następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="d76d1-229">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="d76d1-230">Tę sekcję można dodać do każdego pliku projektu ręcznie, jeśli wolisz nie używać interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d76d1-230">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="d76d1-231">Tworzenie struktury rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d76d1-231">Structuring a solution</span></span>

<span data-ttu-id="d76d1-232">Innym ważnym aspektem rozwiązań z zakresu projektów jest ustanowienie dobrej ogólnej struktury projektu.</span><span class="sxs-lookup"><span data-stu-id="d76d1-232">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="d76d1-233">Możesz zorganizować kod w dowolny sposób, a dopóki każdy projekt zostanie połączony z plikiem rozwiązania za pomocą `dotnet sln add`programu, będzie można uruchamiać `dotnet restore` i `dotnet build` na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d76d1-233">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
