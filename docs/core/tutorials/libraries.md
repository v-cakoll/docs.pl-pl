---
title: "Tworzenie bibliotek z wielu narzędzi platformy"
description: "Dowiedz się, jak utworzyć biblioteki dla platformy .NET przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core."
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
ms.workload: dotnetcore
ms.openlocfilehash: 8b809fbe73dfd382d568aba5d0f074915d727546
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="b35f0-104">Tworzenie bibliotek z wielu narzędzi platformy</span><span class="sxs-lookup"><span data-stu-id="b35f0-104">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="b35f0-105">W tym artykule omówiono sposób zapisania biblioteki dla platformy .NET przy użyciu narzędzi interfejsu wiersza polecenia i platform.</span><span class="sxs-lookup"><span data-stu-id="b35f0-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="b35f0-106">Interfejsu wiersza polecenia zapewnia wydajne i niskiego poziomu, który działa z dowolnym obsługiwany system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="b35f0-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="b35f0-107">Można nadal tworzyć bibliotek w programie Visual Studio i jeśli jest to preferowany środowiska [można znaleźć w podręczniku programu Visual Studio](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b35f0-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b35f0-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b35f0-108">Prerequisites</span></span>

<span data-ttu-id="b35f0-109">Należy [.NET Core SDK i interfejsu wiersza polecenia](https://www.microsoft.com/net/core) zainstalowana na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b35f0-109">You need [the .NET Core SDK and CLI](https://www.microsoft.com/net/core) installed on your machine.</span></span>

<span data-ttu-id="b35f0-110">Dla sekcji tego dokumentu dotyczącej wersji systemu .NET Framework należy [.NET Framework](http://getdotnet.azurewebsites.net/) zainstalowany na komputerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="b35f0-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](http://getdotnet.azurewebsites.net/) installed on a Windows machine.</span></span>

<span data-ttu-id="b35f0-111">Ponadto, jeśli chcesz obsługiwać starszych docelowych .NET Framework należy zainstalować pakiety przeznaczonych dla deweloperów dla starszych wersji framework z [strony platformy docelowej .NET](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span><span class="sxs-lookup"><span data-stu-id="b35f0-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET target platforms page](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span></span> <span data-ttu-id="b35f0-112">Można skorzystać z tej tabeli:</span><span class="sxs-lookup"><span data-stu-id="b35f0-112">Refer to this table:</span></span>

| <span data-ttu-id="b35f0-113">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b35f0-113">.NET Framework Version</span></span> | <span data-ttu-id="b35f0-114">Co do pobrania</span><span class="sxs-lookup"><span data-stu-id="b35f0-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="b35f0-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="b35f0-115">4.6.1</span></span>                  | <span data-ttu-id="b35f0-116">.NET framework 4.6.1 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="b35f0-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="b35f0-117">4.6</span><span class="sxs-lookup"><span data-stu-id="b35f0-117">4.6</span></span>                    | <span data-ttu-id="b35f0-118">.NET framework 4.6 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="b35f0-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="b35f0-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="b35f0-119">4.5.2</span></span>                  | <span data-ttu-id="b35f0-120">.NET framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="b35f0-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="b35f0-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="b35f0-121">4.5.1</span></span>                  | <span data-ttu-id="b35f0-122">.NET framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="b35f0-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="b35f0-123">4.5</span><span class="sxs-lookup"><span data-stu-id="b35f0-123">4.5</span></span>                    | <span data-ttu-id="b35f0-124">Zestaw Windows Software Development Kit dla systemu Windows 8</span><span class="sxs-lookup"><span data-stu-id="b35f0-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="b35f0-125">4.0</span><span class="sxs-lookup"><span data-stu-id="b35f0-125">4.0</span></span>                    | <span data-ttu-id="b35f0-126">Zestaw Windows SDK dla systemu Windows 7 i .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="b35f0-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="b35f0-127">2.0, 3.0 i 3.5</span><span class="sxs-lookup"><span data-stu-id="b35f0-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="b35f0-128">Środowisko uruchomieniowe platformy .NET framework 3.5 z dodatkiem SP1 (lub wersji systemu Windows 8 +)</span><span class="sxs-lookup"><span data-stu-id="b35f0-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="b35f0-129">Jak docelowy .NET Standard</span><span class="sxs-lookup"><span data-stu-id="b35f0-129">How to target the .NET Standard</span></span>

<span data-ttu-id="b35f0-130">Jeśli nie znasz jeszcze przy użyciu platformy .NET Standard, zapoznaj się [.NET Standard](../../standard/net-standard.md) Aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="b35f0-130">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="b35f0-131">W tym artykule nie istnieje tabela, który mapuje wersje .NET Standard na różnych implementacji:</span><span class="sxs-lookup"><span data-stu-id="b35f0-131">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

<span data-ttu-id="b35f0-132">Oto tej tabeli oznacza na potrzeby tworzenia biblioteki:</span><span class="sxs-lookup"><span data-stu-id="b35f0-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="b35f0-133">Wersja programu .NET Standard możesz wybrać będzie zależności między dostęp do najnowszych interfejsów API oraz możliwość docelowego więcej implementacje .NET oraz wersji platformy .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b35f0-133">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="b35f0-134">Kontrolowanie zakresu targetable platform i wersje wybierając wersję `netstandardX.X` (gdzie `X.X` jest numer wersji) i dodanie go do pliku projektu (`.csproj` lub `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="b35f0-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="b35f0-135">Dostępne są trzy opcje podstawowego przeznaczonych dla platformy .NET Standard, w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="b35f0-135">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="b35f0-136">Korzystając z domyślną wersją .NET Standard dostarczonych przez szablony — `netstandard1.4` — która zapewnia dostęp do większości interfejsów API platformy .NET Standard przy zachowaniu zgodny z platformy uniwersalnej systemu Windows, .NET Framework 4.6.1 i nadchodzącego .NET Standard w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="b35f0-136">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="b35f0-137">Można użyć niższych lub nowszej wersji programu .NET Standard przez zmodyfikowanie wartości w `TargetFramework` węzła pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b35f0-137">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>
    
    <span data-ttu-id="b35f0-138">Wersje .NET standard są zgodne z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="b35f0-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="b35f0-139">Oznacza to, że `netstandard1.0` biblioteki Uruchom na `netstandard1.1` platform i wyższych.</span><span class="sxs-lookup"><span data-stu-id="b35f0-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="b35f0-140">Jednak nie istnieje żadne zgodność z nowszymi wersjami — niższe platformy .NET Standard nie może odwoływać się wyższym z nich.</span><span class="sxs-lookup"><span data-stu-id="b35f0-140">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="b35f0-141">Oznacza to, że `netstandard1.0` bibliotek nie odwołanie bibliotek przeznaczonych `netstandard1.1` lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="b35f0-141">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="b35f0-142">Wybierz wersję Standard z odpowiedniej kombinacji obsługę interfejsów API i platforma do potrzeb.</span><span class="sxs-lookup"><span data-stu-id="b35f0-142">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="b35f0-143">Firma Microsoft zaleca `netstandard1.4` teraz.</span><span class="sxs-lookup"><span data-stu-id="b35f0-143">We recommend `netstandard1.4` for now.</span></span>
    
3. <span data-ttu-id="b35f0-144">Jeśli chcesz korzystać z wersji .NET Framework 4.0 lub poniżej, lub chcesz użyć interfejsu API, które są dostępne w programie .NET Framework, ale nie w .NET Standard (na przykład `System.Drawing`), powinien przeczytać poniższe sekcje i Dowiedz się, jak multitarget.</span><span class="sxs-lookup"><span data-stu-id="b35f0-144">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="b35f0-145">Jak docelowej platformy .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b35f0-145">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="b35f0-146">W instrukcjach przyjęto założenie, że ma programu .NET Framework na komputerze jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="b35f0-146">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="b35f0-147">Zapoznaj się [wymagania wstępne](#prerequisites) uzyskać zależności zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="b35f0-147">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="b35f0-148">Należy pamiętać, że niektóre wersje programu .NET Framework, używane w tym miejscu nie są już w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="b35f0-148">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="b35f0-149">Zapoznaj się [.NET Framework wsparcia technicznego](https://support.microsoft.com/gp/framework_faq/en-us) o nieobsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="b35f0-149">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="b35f0-150">Aby osiągnąć maksymalną liczbę deweloperów i projekty, należy użyć programu .NET Framework 4.0 jako urządzenie docelowe linii bazowej.</span><span class="sxs-lookup"><span data-stu-id="b35f0-150">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="b35f0-151">Docelowy .NET Framework, należy rozpocząć przy użyciu poprawny docelowy Framework Moniker (TFM) umożliwiająca wersja architektury .NET Framework, które chcesz obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="b35f0-151">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.7   --> net47
```

<span data-ttu-id="b35f0-152">Następnie wstaw ten TFM do `TargetFramework` sekcji w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b35f0-152">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="b35f0-153">Na przykład poniżej przedstawiono sposób piszesz bibliotekę, która jest przeznaczony dla programu .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="b35f0-153">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b35f0-154">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="b35f0-154">And that's it!</span></span> <span data-ttu-id="b35f0-155">Mimo że to skompilowany tylko dla programu .NET Framework 4, biblioteki można używać w nowszej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b35f0-155">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="b35f0-156">Jak Multitarget</span><span class="sxs-lookup"><span data-stu-id="b35f0-156">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="b35f0-157">Poniższe instrukcje założono, że na komputerze jest zainstalowany w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b35f0-157">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="b35f0-158">Zapoznaj się [wymagania wstępne](#prerequisites) sekcji, aby dowiedzieć się zależności, które należy zainstalować i skąd pobrać je z.</span><span class="sxs-lookup"><span data-stu-id="b35f0-158">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="b35f0-159">Konieczne może być celem starsze wersje programu .NET Framework, gdy projekt obsługuje program .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b35f0-159">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="b35f0-160">W tym scenariuszu, jeśli chcesz użyć nowszej interfejsów API i konstrukcji języka dla nowszej celów, użyj `#if` dyrektywy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b35f0-160">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="b35f0-161">Należy również dodać różnych pakietów i zależności dla poszczególnych platform docelowych do uwzględnienia różnych interfejsów API potrzebne w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="b35f0-161">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="b35f0-162">Załóżmy na przykład, że biblioteka, która wykonuje operacje sieciowe za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b35f0-162">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="b35f0-163">W przypadku standardowych .NET i .NET Framework w wersji 4.5 lub nowszej, można użyć `HttpClient` klasę z `System.Net.Http` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b35f0-163">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="b35f0-164">Jednak nie ma wcześniejszych wersji programu .NET Framework `HttpClient` klasy, aby można było używać `WebClient` klasę z `System.Net` przestrzeń nazw dla tych zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b35f0-164">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="b35f0-165">Plik projektu może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="b35f0-165">Your project file could look like this:</span></span>

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

<span data-ttu-id="b35f0-166">Można zauważyć trzy istotne zmiany w tym miejscu:</span><span class="sxs-lookup"><span data-stu-id="b35f0-166">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="b35f0-167">`TargetFramework` Węzeł został zastąpiony przez `TargetFrameworks`, i trzy TFMs są wyrażane w.</span><span class="sxs-lookup"><span data-stu-id="b35f0-167">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="b35f0-168">Brak `<ItemGroup>` węzeł `net40 ` docelowej ściąganie w jedno odwołanie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b35f0-168">There is an `<ItemGroup>` node for the `net40 ` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="b35f0-169">Brak `<ItemGroup>` węzeł `net45` docelowej ściąganie w dwóch odwołań platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b35f0-169">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="b35f0-170">System kompilacji jest pamiętać o następujących symboli preprocesora używane w `#if` dyrektywy:</span><span class="sxs-lookup"><span data-stu-id="b35f0-170">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="b35f0-171">Oto przykład korzystające z kompilacji warunkowej na docelowym:</span><span class="sxs-lookup"><span data-stu-id="b35f0-171">Here is an example making use of conditional compilation per-target:</span></span>

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
            string url = "http://www.dotnetfoundation.org/";

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
            string url = "http://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="b35f0-172">W przypadku tworzenia tego projektu z `dotnet build`, można zauważyć trzy katalogi w ramach `bin/` folderu:</span><span class="sxs-lookup"><span data-stu-id="b35f0-172">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="b35f0-173">Każdy z tych zawierać `.dll` plików dla każdego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="b35f0-173">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="b35f0-174">Jak przetestować bibliotek .NET Core</span><span class="sxs-lookup"><span data-stu-id="b35f0-174">How to test libraries on .NET Core</span></span>

<span data-ttu-id="b35f0-175">Jest ważne można było przetestować na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="b35f0-175">It's important to be able to test across platforms.</span></span> <span data-ttu-id="b35f0-176">Możesz użyć dowolnej [xUnit](http://xunit.github.io/) lub MSTest poza pole.</span><span class="sxs-lookup"><span data-stu-id="b35f0-176">You can use either [xUnit](http://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="b35f0-177">Oba są doskonale nadające się do biblioteki programu .NET Core testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="b35f0-177">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="b35f0-178">Sposób konfigurowania rozwiązania z projekty testowe będzie zależeć od [struktury rozwiązania](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="b35f0-178">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="b35f0-179">W poniższym przykładzie założono, że katalogi testu oraz źródła na żywo w tym samym katalogu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="b35f0-179">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="b35f0-180">Niektóre używa [polecenia interfejsu wiersza polecenia platformy .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="b35f0-180">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="b35f0-181">Zobacz [dotnet nowe](../tools/dotnet-new.md) i [dotnet sln](../tools/dotnet-sln.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b35f0-181">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="b35f0-182">Konfigurowanie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b35f0-182">Set up your solution.</span></span> <span data-ttu-id="b35f0-183">Możesz to zrobić za pomocą następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="b35f0-183">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="b35f0-184">Spowoduje to utworzenie projektów i połączyć je w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="b35f0-184">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="b35f0-185">W katalogu `SolutionWithSrcAndTest` powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="b35f0-185">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="b35f0-186">Przejdź do katalogu projektu testowego i Dodaj odwołanie do `MyProject.Test` z `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="b35f0-186">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="b35f0-187">Przywracanie pakietów i kompilacji projektów:</span><span class="sxs-lookup"><span data-stu-id="b35f0-187">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. <span data-ttu-id="b35f0-188">Sprawdź, że xUnit działa, wykonując `dotnet test` polecenia.</span><span class="sxs-lookup"><span data-stu-id="b35f0-188">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="b35f0-189">Jeśli chcesz użyć przełącznika MSTest konsoli MSTest modułu uruchamiającego testy należy uruchomić zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b35f0-189">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>
    
<span data-ttu-id="b35f0-190">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="b35f0-190">And that's it!</span></span> <span data-ttu-id="b35f0-191">Teraz możesz przetestować biblioteki na wszystkich platformach za pomocą narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b35f0-191">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="b35f0-192">Aby kontynuować testowanie teraz, gdy masz wszystkie elementy skonfigurować, testowanie biblioteki jest bardzo prosty:</span><span class="sxs-lookup"><span data-stu-id="b35f0-192">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="b35f0-193">Wprowadzanie zmian do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b35f0-193">Make changes to your library.</span></span>
1. <span data-ttu-id="b35f0-194">Uruchom testy z wiersza polecenia w katalogu testu z `dotnet test` polecenia.</span><span class="sxs-lookup"><span data-stu-id="b35f0-194">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="b35f0-195">Kod zostanie automatycznie odbudować po wywołaniu `dotnet test` polecenia.</span><span class="sxs-lookup"><span data-stu-id="b35f0-195">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="b35f0-196">Jak używać wielu projektów</span><span class="sxs-lookup"><span data-stu-id="b35f0-196">How to use multiple projects</span></span>

<span data-ttu-id="b35f0-197">Potrzebują większych biblioteki jest umieścić funkcji w różnych projektów.</span><span class="sxs-lookup"><span data-stu-id="b35f0-197">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="b35f0-198">Załóżmy, że zamierza utworzyć bibliotekę, która może być używana w idiomatyczne C# i F #.</span><span class="sxs-lookup"><span data-stu-id="b35f0-198">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="b35f0-199">Oznacza to, że konsumenci biblioteki mogły ich używać w sposób fizyczne do języka C# lub języka F #.</span><span class="sxs-lookup"><span data-stu-id="b35f0-199">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="b35f0-200">Na przykład w języku C# mogą używać biblioteki następująco:</span><span class="sxs-lookup"><span data-stu-id="b35f0-200">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="b35f0-201">W języku F # może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="b35f0-201">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="b35f0-202">Scenariusze użycia, takich jak ta oznaczają, że dostęp do interfejsów API muszą mieć inną strukturę języka C# i F #.</span><span class="sxs-lookup"><span data-stu-id="b35f0-202">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="b35f0-203">Typowym podejściem do realizacji tego zadania jest uwzględnić wszystkie logiki biblioteki projektu podstawowych, z projektami C# i F # Definiowanie warstwy interfejsu API, które wywołują projektu core.</span><span class="sxs-lookup"><span data-stu-id="b35f0-203">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="b35f0-204">Pozostała część sekcji użyjemy następujące nazwy:</span><span class="sxs-lookup"><span data-stu-id="b35f0-204">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="b35f0-205">**AwesomeLibrary.Core** -projektu core, która zawiera całą logikę biblioteki</span><span class="sxs-lookup"><span data-stu-id="b35f0-205">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="b35f0-206">**AwesomeLibrary.CSharp** -projekt o publiczne interfejsy API przeznaczonych do użycia w języku C#</span><span class="sxs-lookup"><span data-stu-id="b35f0-206">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="b35f0-207">**AwesomeLibrary.FSharp** -projekt o publiczne interfejsy API przeznaczonych do użycia w języku F #</span><span class="sxs-lookup"><span data-stu-id="b35f0-207">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="b35f0-208">W terminalu, aby utworzyć taką samą strukturę jak w tym przewodniku można uruchomić następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="b35f0-208">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="b35f0-209">Spowoduje to dodanie trzy projekty powyżej i plik rozwiązania, który łączy je razem.</span><span class="sxs-lookup"><span data-stu-id="b35f0-209">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="b35f0-210">Tworzenie pliku rozwiązania, a następnie połączenie projektów pozwoli przywracania oraz tworzenie projektów z typem najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="b35f0-210">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="b35f0-211">Odwołanie do projektu do projektu</span><span class="sxs-lookup"><span data-stu-id="b35f0-211">Project-to-project referencing</span></span>

<span data-ttu-id="b35f0-212">Najlepszym sposobem odwoływać się do projektu jest dodać odwołanie do projektu za pomocą interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b35f0-212">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="b35f0-213">Z **AwesomeLibrary.CSharp** i **AwesomeLibrary.FSharp** katalogu projektu można uruchomić następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b35f0-213">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="b35f0-214">Pliki projektu dla obu **AwesomeLibrary.CSharp** i **AwesomeLibrary.FSharp** będzie teraz odwołanie **AwesomeLibrary.Core** jako `ProjectReference` docelowej.</span><span class="sxs-lookup"><span data-stu-id="b35f0-214">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="b35f0-215">Można to sprawdzić, przeprowadzanie inspekcji plików projektu i sprawdzając następujące w nich:</span><span class="sxs-lookup"><span data-stu-id="b35f0-215">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="b35f0-216">Można dodać tej sekcji do każdego pliku projektu ręcznie, jeśli nie chcesz korzystać z interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b35f0-216">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="b35f0-217">Tworzenie struktury rozwiązania</span><span class="sxs-lookup"><span data-stu-id="b35f0-217">Structuring a solution</span></span>

<span data-ttu-id="b35f0-218">Innym ważnym aspektem rozwiązań dotyczących wielu projektów jest ustanowienie dobrej ogólnej struktury projektu.</span><span class="sxs-lookup"><span data-stu-id="b35f0-218">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="b35f0-219">Kod można organizować w dowolny sposób oraz tak długo, jak połączyć każdego projektu w pliku rozwiązania z `dotnet sln add`, będzie można uruchomić `dotnet restore` i `dotnet build` na poziomie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="b35f0-219">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
