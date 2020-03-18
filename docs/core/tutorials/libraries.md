---
title: Tworzenie bibliotek za pomocą cli .NET Core
description: Dowiedz się, jak tworzyć biblioteki .NET Core przy użyciu.NET Core CLI. Utworzysz bibliotekę, która obsługuje wiele struktur.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: c23c1f027b4d6d09c50eb2257d34f72ec56302f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503505"
---
# <a name="develop-libraries-with-the-net-core-cli"></a><span data-ttu-id="7eaf9-104">Tworzenie bibliotek za pomocą cli .NET Core</span><span class="sxs-lookup"><span data-stu-id="7eaf9-104">Develop libraries with the .NET Core CLI</span></span>

<span data-ttu-id="7eaf9-105">W tym artykule omówiono sposób pisania bibliotek dla programu .NET przy użyciu cli.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-105">This article covers how to write libraries for .NET using the .NET Core CLI.</span></span> <span data-ttu-id="7eaf9-106">CLI zapewnia wydajne i niskiego poziomu środowiska, który działa w każdym obsługiwanym środowisku operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="7eaf9-107">Nadal można tworzyć biblioteki za pomocą programu Visual Studio, a jeśli jest to preferowane środowisko [odnoszą się do przewodnika programu Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="7eaf9-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7eaf9-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7eaf9-108">Prerequisites</span></span>

<span data-ttu-id="7eaf9-109">Potrzebujesz [.NET Core SDK i CLI](https://dotnet.microsoft.com/download) zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="7eaf9-110">W przypadku sekcji tego dokumentu dotyczących wersji .NET Framework potrzebna jest zainstalowana platforma [.NET Framework](https://dotnet.microsoft.com) na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="7eaf9-111">Ponadto jeśli chcesz obsługiwać starsze obiekty docelowe .NET Framework, musisz zainstalować pakiety docelowe lub pakiety deweloperskie ze [strony archiwum pobierania .NET](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="7eaf9-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="7eaf9-112">Zapoznaj się z poniższą tabelą:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-112">Refer to this table:</span></span>

| <span data-ttu-id="7eaf9-113">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7eaf9-113">.NET Framework version</span></span> | <span data-ttu-id="7eaf9-114">Co pobrać</span><span class="sxs-lookup"><span data-stu-id="7eaf9-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="7eaf9-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="7eaf9-115">4.6.1</span></span>                  | <span data-ttu-id="7eaf9-116">Pakiet kierowania .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="7eaf9-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="7eaf9-117">4.6</span><span class="sxs-lookup"><span data-stu-id="7eaf9-117">4.6</span></span>                    | <span data-ttu-id="7eaf9-118">Pakiet targetowania .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="7eaf9-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="7eaf9-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="7eaf9-119">4.5.2</span></span>                  | <span data-ttu-id="7eaf9-120">Pakiet deweloperski .NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="7eaf9-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="7eaf9-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7eaf9-121">4.5.1</span></span>                  | <span data-ttu-id="7eaf9-122">Pakiet deweloperski .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="7eaf9-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="7eaf9-123">4.5</span><span class="sxs-lookup"><span data-stu-id="7eaf9-123">4.5</span></span>                    | <span data-ttu-id="7eaf9-124">Zestaw Windows Software Development Kit dla systemu Windows 8</span><span class="sxs-lookup"><span data-stu-id="7eaf9-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="7eaf9-125">4.0</span><span class="sxs-lookup"><span data-stu-id="7eaf9-125">4.0</span></span>                    | <span data-ttu-id="7eaf9-126">Zestaw Windows SDK dla systemów Windows 7 i .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="7eaf9-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="7eaf9-127">2,0, 3,0 i 3,5</span><span class="sxs-lookup"><span data-stu-id="7eaf9-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="7eaf9-128">Środowisko uruchomieniowe programu .NET Framework 3.5 z dodatkiem SP1 (lub wersja systemu Windows 8+)</span><span class="sxs-lookup"><span data-stu-id="7eaf9-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="7eaf9-129">Jak kierować reklamy na standard .NET</span><span class="sxs-lookup"><span data-stu-id="7eaf9-129">How to target the .NET Standard</span></span>

<span data-ttu-id="7eaf9-130">Jeśli nie znasz standardu .NET, zapoznaj się z [.NET Standard,](../../standard/net-standard.md) aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="7eaf9-131">W tym artykule znajduje się tabela, która mapuje wersje .NET Standard do różnych implementacji:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="7eaf9-132">Oto, co ta tabela oznacza dla celów tworzenia biblioteki:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="7eaf9-133">Wersja .NET Standard, którą wybierzesz, będzie kompromisem między dostępem do najnowszych interfejsów API a możliwością kierowania większej liczby implementacji .NET i wersji .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="7eaf9-134">Możesz kontrolować zakres platform docelowych i wersji, `netstandardX.X` wybierając `X.X` wersję (gdzie jest numer wersji)`.csproj` i `.fsproj`dodając ją do pliku projektu (lub ).</span><span class="sxs-lookup"><span data-stu-id="7eaf9-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="7eaf9-135">Podczas kierowania na standard .NET są dostępne trzy opcje podstawowe, w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="7eaf9-136">Można użyć domyślnej wersji .NET Standard dostarczonej `netstandard1.4`przez szablony, która zapewnia dostęp do większości interfejsów API w standardzie .NET, a jednocześnie jest zgodna z platformą UWP, .NET Framework 4.6.1 i .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="7eaf9-137">Można użyć niższej lub wyższej wersji programu .NET Standard, `TargetFramework` modyfikując wartość w węźle pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="7eaf9-138">Wersje .NET Standard są wstecznie kompatybilne.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="7eaf9-139">Oznacza to, że `netstandard1.0` `netstandard1.1` biblioteki działają na platformach i wyższe.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="7eaf9-140">Jednak nie ma zgodności z przyszłością.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="7eaf9-141">Niższe platformy .NET Standard nie mogą odwoływać się do wyższych.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="7eaf9-142">Oznacza to, że `netstandard1.0` biblioteki nie `netstandard1.1` mogą odwoływać się do bibliotek przeznaczonych do pracy lub wyższych.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="7eaf9-143">Wybierz wersję standardową, która ma odpowiednią kombinację interfejsów API i obsługi platform y dla Twoich potrzeb.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="7eaf9-144">Polecamy `netstandard1.4` na razie.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="7eaf9-145">Jeśli chcesz kierować .NET Framework w wersji 4.0 lub poniżej lub chcesz użyć interfejsu API dostępnego w `System.Drawing`.NET Framework, ale nie w .NET Standard (na przykład), przeczytaj poniższe sekcje i dowiedz się, jak kierować wiele.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="7eaf9-146">Jak kierować reklamy do programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7eaf9-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="7eaf9-147">W tych instrukcjach założono, że na komputerze jest zainstalowana platforma .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="7eaf9-148">Zapoznaj się z [wymaganiami wstępnymi,](#prerequisites) aby zainstalować zależności.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="7eaf9-149">Należy pamiętać, że niektóre wersje .NET Framework używane w tym miejscu nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="7eaf9-150">Zapoznaj się z często [zadawanymi pytaniami](https://support.microsoft.com/gp/framework_faq/en-us) dotyczącymi zasad cyklu pomocy technicznej programu .NET Framework dotyczące nieobsługiwanych wersji.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="7eaf9-151">Jeśli chcesz osiągnąć maksymalną liczbę deweloperów i projektów, użyj .NET Framework 4.0 jako cel linii bazowej.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="7eaf9-152">Aby kierować .NET Framework, rozpocząć przy użyciu poprawnego moniker struktury docelowej (TFM), który odpowiada .NET Framework wersji, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="7eaf9-153">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7eaf9-153">.NET Framework version</span></span> | <span data-ttu-id="7eaf9-154">Tfm</span><span class="sxs-lookup"><span data-stu-id="7eaf9-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="7eaf9-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="7eaf9-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="7eaf9-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="7eaf9-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="7eaf9-157">Program .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="7eaf9-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="7eaf9-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="7eaf9-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="7eaf9-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="7eaf9-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="7eaf9-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="7eaf9-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="7eaf9-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="7eaf9-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="7eaf9-162">Program .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="7eaf9-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="7eaf9-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="7eaf9-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="7eaf9-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="7eaf9-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="7eaf9-165">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="7eaf9-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="7eaf9-166"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="7eaf9-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="7eaf9-167">Następnie wstaw ten TFM do `TargetFramework` sekcji pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="7eaf9-168">Na przykład oto jak można napisać bibliotekę, która jest przeznaczona dla .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="7eaf9-169">I to wszystko.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-169">And that's it!</span></span> <span data-ttu-id="7eaf9-170">Mimo że jest to skompilowane tylko dla .NET Framework 4, można użyć biblioteki w nowszych wersjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="7eaf9-171">Jak wielocelowe</span><span class="sxs-lookup"><span data-stu-id="7eaf9-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="7eaf9-172">W poniższych instrukcjach przyjęto założenie, że na komputerze jest zainstalowana platforma .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="7eaf9-173">Zapoznaj się z sekcją [Wymagania wstępne,](#prerequisites) aby dowiedzieć się, z których zależności należy zainstalować i skąd je pobrać.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="7eaf9-174">Może być konieczne kierowanie starszych wersji programu .NET Framework, gdy projekt obsługuje zarówno .NET Framework, jak i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="7eaf9-175">W tym scenariuszu, jeśli chcesz użyć nowszych interfejsów API `#if` i konstrukcji języka dla nowszych obiektów docelowych, użyj dyrektyw w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="7eaf9-176">Może być również konieczne dodanie różnych pakietów i zależności dla każdej platformy, na którą kierujesz reklamy, aby uwzględnić różne interfejsy API potrzebne dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="7eaf9-177">Załóżmy na przykład, że masz bibliotekę, która wykonuje operacje sieciowe za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="7eaf9-178">W przypadku standardu .NET i wersji .NET Framework w `HttpClient` wersji `System.Net.Http` 4.5 lub nowszej można użyć tej klasy z obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="7eaf9-179">Jednak wcześniejsze wersje .NET Framework nie mają `HttpClient` klasy, więc można `WebClient` użyć `System.Net` klasy z obszaru nazw dla tych zamiast.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="7eaf9-180">Plik projektu może wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-180">Your project file could look like this:</span></span>

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

<span data-ttu-id="7eaf9-181">Tutaj zauważasz trzy główne zmiany:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="7eaf9-182">Węzeł `TargetFramework` został zastąpiony przez `TargetFrameworks`, a trzy TFM są wyrażone wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="7eaf9-183">Istnieje `<ItemGroup>` węzeł dla `net40` obiektu docelowego ściągając w jednym .NET Framework odwołania.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="7eaf9-184">Istnieje `<ItemGroup>` węzeł dla `net45` obiektu docelowego ciągnąc w dwóch odwołaniach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="7eaf9-185">System kompilacji jest świadomy następujących symboli `#if` preprocesora używanych w dyrektywach:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="7eaf9-186">Oto przykład korzystania z kompilacji warunkowej na miejsce docelowe:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-186">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="7eaf9-187">Jeśli stworzysz `dotnet build`ten projekt z , zauważysz trzy katalogi w folderze: `bin/`</span><span class="sxs-lookup"><span data-stu-id="7eaf9-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="7eaf9-188">Każdy z nich `.dll` zawiera pliki dla każdego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="7eaf9-189">Jak testować biblioteki w usiułm.NET Core</span><span class="sxs-lookup"><span data-stu-id="7eaf9-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="7eaf9-190">Ważne jest, aby móc testować na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="7eaf9-191">Można użyć [xUnit](https://xunit.github.io/) lub MSTest po wyjęciu z pudełka.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="7eaf9-192">Oba są idealnie odpowiednie do testowania jednostkowego biblioteki na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="7eaf9-193">Sposób konfigurowania rozwiązania w projektach testowych zależy od [struktury rozwiązania.](#structuring-a-solution)</span><span class="sxs-lookup"><span data-stu-id="7eaf9-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="7eaf9-194">W poniższym przykładzie przyjęto założenie, że katalogi testowe i źródłowe są aktywne w tym samym katalogu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="7eaf9-195">Używa niektórych poleceń [cli programu .NET Core.](../tools/index.md)</span><span class="sxs-lookup"><span data-stu-id="7eaf9-195">This uses some [.NET Core CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="7eaf9-196">Zobacz [dotnet nowy](../tools/dotnet-new.md) i [dotnet sln](../tools/dotnet-sln.md) aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="7eaf9-197">Skonfiguruj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-197">Set up your solution.</span></span> <span data-ttu-id="7eaf9-198">Można to zrobić za pomocą następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-198">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="7eaf9-199">Spowoduje to utworzenie projektów i połączenie ich w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="7eaf9-200">Twój katalog `SolutionWithSrcAndTest` powinien wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="7eaf9-201">Przejdź do katalogu projektu testowego i `MyProject.Test` dodaj `MyProject`odwołanie do z .</span><span class="sxs-lookup"><span data-stu-id="7eaf9-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="7eaf9-202">Przywracanie pakietów i tworzenie projektów:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="7eaf9-203">Sprawdź, czy xUnit działa, wykonując `dotnet test` polecenie.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="7eaf9-204">Jeśli wybrano użycie narzędzia MSTest, zamiast tego powinien zostać uruchomiony program uruchamiany konsoli MSTest.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="7eaf9-205">I to wszystko.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-205">And that's it!</span></span> <span data-ttu-id="7eaf9-206">Teraz można przetestować bibliotekę na wszystkich platformach za pomocą narzędzi wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="7eaf9-207">Aby kontynuować testowanie teraz, gdy wszystko jest skonfigurowane, testowanie biblioteki jest bardzo proste:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="7eaf9-208">Wprowadzanie zmian w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-208">Make changes to your library.</span></span>
1. <span data-ttu-id="7eaf9-209">Uruchom testy z wiersza polecenia, w `dotnet test` katalogu testowym, za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="7eaf9-210">Kod zostanie automatycznie przebudowany podczas wywoływania `dotnet test` polecenia.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="7eaf9-211">Jak korzystać z wielu projektów</span><span class="sxs-lookup"><span data-stu-id="7eaf9-211">How to use multiple projects</span></span>

<span data-ttu-id="7eaf9-212">Częstą potrzebą większych bibliotek jest umieszczenie funkcji w różnych projektach.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="7eaf9-213">Wyobraź sobie, że chcesz utworzyć bibliotekę, która może być zużywana w idiomatycznych językach C# i F#.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="7eaf9-214">Oznaczałoby to, że konsumenci biblioteki zużywają go w sposób, który jest naturalny dla Języka C# lub F#.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="7eaf9-215">Na przykład w języku C# można użyć biblioteki w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="7eaf9-216">W F#, może to wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="7eaf9-217">Scenariusze zużycia, takie jak to oznacza, że interfejsy API, do których uzyskuje się dostęp, muszą mieć inną strukturę dla języka C# i F#.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="7eaf9-218">Wspólne podejście do osiągnięcia tego jest uwzględnienie wszystkich logiki biblioteki do projektu podstawowego, z C# i F# projektów definiujących warstwy interfejsu API, które wywołują do tego projektu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="7eaf9-219">W pozostałej części sekcji będą używane następujące nazwy:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="7eaf9-220">**AwesomeLibrary.Core** - podstawowy projekt, który zawiera całą logikę dla biblioteki</span><span class="sxs-lookup"><span data-stu-id="7eaf9-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="7eaf9-221">**AwesomeLibrary.CSharp** — projekt z publicznymi interfejsami API przeznaczony do użycia w c #</span><span class="sxs-lookup"><span data-stu-id="7eaf9-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="7eaf9-222">**AwesomeLibrary.FSharp** — projekt z publicznymi interfejsami API przeznaczony do użycia w F #</span><span class="sxs-lookup"><span data-stu-id="7eaf9-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="7eaf9-223">W terminalu można uruchomić następujące polecenia, aby utworzyć tę samą strukturę, co ten przewodnik:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```dotnetcli
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

<span data-ttu-id="7eaf9-224">Spowoduje to dodanie trzech powyższych projektów i pliku rozwiązania, który łączy je ze sobą.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="7eaf9-225">Tworzenie pliku rozwiązania i łączenie projektów pozwoli przywrócić i zbudować projekty z najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="7eaf9-226">Odwoływanie się do projektu</span><span class="sxs-lookup"><span data-stu-id="7eaf9-226">Project-to-project referencing</span></span>

<span data-ttu-id="7eaf9-227">Najlepszym sposobem odwoływania się do projektu jest użycie cli .NET Core, aby dodać odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="7eaf9-228">Z **awesomelibrary.CSharp** i **AwesomeLibrary.FSharp** katalogów projektu, można uruchomić następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="7eaf9-229">Pliki projektu dla **awesomelibrary.CSharp** i **AwesomeLibrary.FSharp** będzie teraz odwoływać **AwesomeLibrary.Core** jako `ProjectReference` miejsce docelowe.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="7eaf9-230">Można to sprawdzić, sprawdzając pliki projektu i wyświetlając w nich następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="7eaf9-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="7eaf9-231">Tę sekcję można dodać do każdego pliku projektu ręcznie, jeśli nie chcesz używać.NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="7eaf9-232">Strukturyzacja rozwiązania</span><span class="sxs-lookup"><span data-stu-id="7eaf9-232">Structuring a solution</span></span>

<span data-ttu-id="7eaf9-233">Innym ważnym aspektem rozwiązań wieloprojektowych jest stworzenie dobrej ogólnej struktury projektu.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="7eaf9-234">Możesz zorganizować kod, jak chcesz, i tak długo, jak `dotnet sln add`połączyć każdy projekt do `dotnet restore` `dotnet build` pliku rozwiązania z , będzie można uruchomić i na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7eaf9-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
