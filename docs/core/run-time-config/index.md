---
title: Opcje konfiguracji czasu wykonywania
description: Dowiedz się, jak skonfigurować aplikacje platformy .NET Core za pomocą ustawień konfiguracji czasu wykonywania.
ms.date: 01/21/2020
ms.openlocfilehash: 68690689fd4f936e3af76ab647f0b58d8ec6ca27
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761957"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="9a7dd-103">Ustawienia konfiguracji środowiska uruchomieniowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a7dd-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="9a7dd-104">Platforma .NET Core obsługuje używanie plików konfiguracji i zmiennych środowiskowych w celu skonfigurowania zachowania aplikacji .NET Core w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="9a7dd-105">Konfiguracja czasu wykonywania jest atrakcyjną opcją, jeśli:</span><span class="sxs-lookup"><span data-stu-id="9a7dd-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="9a7dd-106">Nie jesteś własnością ani nie kontrolujesz kodu źródłowego dla aplikacji, dlatego nie można programowo skonfigurować go.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="9a7dd-107">Wiele wystąpień aplikacji jest wykonywanych w tym samym czasie w pojedynczym systemie i chcesz skonfigurować każdą z nich w celu uzyskania optymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="9a7dd-108">Ta dokumentacja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-108">This documentation is a work in progress.</span></span> <span data-ttu-id="9a7dd-109">Jeśli zauważysz, że informacje przedstawione w tym miejscu są niekompletne lub niedokładne, należy [otworzyć problem](https://github.com/dotnet/docs/issues) , aby poinformować nas o tym lub [przesłać żądanie ściągnięcia](https://github.com/dotnet/docs/pulls) w celu rozwiązania problemu.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="9a7dd-110">Informacje o przesyłaniu żądań ściągnięcia dla repozytorium dotnet/docs można znaleźć w [przewodniku współautora](https://docs.microsoft.com/contribute/dotnet/dotnet-contribute).</span><span class="sxs-lookup"><span data-stu-id="9a7dd-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://docs.microsoft.com/contribute/dotnet/dotnet-contribute).</span></span>

<span data-ttu-id="9a7dd-111">Platforma .NET Core udostępnia następujące mechanizmy konfigurowania zachowania aplikacji w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="9a7dd-111">.NET Core provides the following mechanisms for configuring application behavior at run time:</span></span>

- <span data-ttu-id="9a7dd-112">[Plik runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="9a7dd-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="9a7dd-113">Właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="9a7dd-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="9a7dd-114">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="9a7dd-114">Environment variables</span></span>](#environment-variables)

> [!TIP]
> <span data-ttu-id="9a7dd-115">Skonfigurowanie opcji czasu wykonywania przy użyciu zmiennej środowiskowej stosuje ustawienie do wszystkich aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-115">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="9a7dd-116">Skonfigurowanie opcji czasu wykonywania w pliku *runtimeconfig. JSON* lub projektu powoduje zastosowanie ustawienia tylko do tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-116">Configuring a run-time option in the *runtimeconfig.json* or project file applies the setting to that application only.</span></span>

<span data-ttu-id="9a7dd-117">Niektóre wartości konfiguracji można również ustawić programowo, wywołując <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-117">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9a7dd-118">Artykuły w tej sekcji dokumentacji są zorganizowane według kategorii, na przykład [debugowania](debugging-profiling.md) i [wyrzucania elementów bezużytecznych](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="9a7dd-118">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="9a7dd-119">W stosownych przypadkach opcje konfiguracji są wyświetlane dla plików *runtimeconfig. JSON* , właściwości programu MSBuild, zmiennych środowiskowych i, w przypadku plików z odsyłaczem, *pliku App. config* dla projektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-119">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="9a7dd-120">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="9a7dd-120">runtimeconfig.json</span></span>

<span data-ttu-id="9a7dd-121">Po [skompilowaniu](../tools/dotnet-build.md)projektu w katalogu wyjściowym zostanie wygenerowany plik *[nazwa_aplikacji]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a7dd-121">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="9a7dd-122">Jeśli plik *runtimeconfig. Template. JSON* istnieje w tym samym folderze co plik projektu, wszystkie opcje konfiguracji, które zawiera, są scalane w pliku *[nazwa_aplikacji]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a7dd-122">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="9a7dd-123">Jeśli tworzysz aplikację samodzielnie, umieść wszystkie opcje konfiguracji w pliku *runtimeconfig. Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a7dd-123">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="9a7dd-124">Jeśli właśnie uruchamiasz aplikację, Wstaw ją bezpośrednio do pliku *[nazwa_aplikacji]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a7dd-124">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="9a7dd-125">Plik *[nazwa_aplikacji]. runtimeconfig. JSON* zostanie nadpisany po kolejnych kompilacjach.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-125">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="9a7dd-126">Określ opcje konfiguracji czasu wykonywania w sekcji **configProperties** plików *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a7dd-126">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="9a7dd-127">Ta sekcja ma postać:</span><span class="sxs-lookup"><span data-stu-id="9a7dd-127">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="9a7dd-128">Przykład [nazwa_aplikacji]. runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="9a7dd-128">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="9a7dd-129">Jeśli umieszczasz opcje w wyjściowym pliku JSON, zastąp je `runtimeOptions` właściwością.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-129">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="9a7dd-130">Przykład pliku runtimeconfig. Template. JSON</span><span class="sxs-lookup"><span data-stu-id="9a7dd-130">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="9a7dd-131">Jeśli umieszczasz opcje w pliku JSON szablonu, Pomiń `runtimeOptions` Właściwość.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-131">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="9a7dd-132">właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="9a7dd-132">MSBuild properties</span></span>

<span data-ttu-id="9a7dd-133">Niektóre opcje konfiguracji czasu wykonywania można ustawić przy użyciu właściwości programu MSBuild w pliku *. csproj* lub *. vbproj* projektów .NET Core w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-133">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="9a7dd-134">Właściwości programu MSBuild mają pierwszeństwo przed opcjami ustawionymi w pliku *runtimeconfig. Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="9a7dd-134">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="9a7dd-135">Zastąpią także wszystkie opcje ustawione w pliku *[nazwa_aplikacji]. runtimeconfig. JSON* w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-135">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="9a7dd-136">Oto przykładowy plik projektu w stylu zestawu SDK z właściwościami MSBuild służący do konfigurowania zachowania w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="9a7dd-136">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="9a7dd-137">Właściwości programu MSBuild służące do konfigurowania zachowania w czasie wykonywania są zanotowane w poszczególnych artykułach dla każdego obszaru, na przykład na [wyrzucaniu elementów bezużytecznych](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="9a7dd-137">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="9a7dd-138">Są one również wymienione w sekcji [Konfiguracja czasu wykonywania](../project-sdk/msbuild-props.md#run-time-configuration-properties) w temacie Informacje o właściwościach programu MSBuild dla projektów w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-138">They are also listed in the [Run-time configuration](../project-sdk/msbuild-props.md#run-time-configuration-properties) section of the MSBuild properties reference for SDK-style projects.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="9a7dd-139">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="9a7dd-139">Environment variables</span></span>

<span data-ttu-id="9a7dd-140">Zmienne środowiskowe mogą służyć do dostarczania niektórych informacji o konfiguracji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-140">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="9a7dd-141">Skonfigurowanie opcji czasu wykonywania przy użyciu zmiennej środowiskowej stosuje ustawienie do wszystkich aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-141">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="9a7dd-142">Pokrętła konfiguracji określone jako zmienne środowiskowe zwykle mają prefiks **COMPlus_**.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-142">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="9a7dd-143">Zmienne środowiskowe można definiować w panelu sterowania systemu Windows, w wierszu polecenia lub programowo poprzez wywołanie <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> metody w systemach Windows i UNIX.</span><span class="sxs-lookup"><span data-stu-id="9a7dd-143">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="9a7dd-144">W poniższych przykładach pokazano, jak ustawić zmienną środowiskową w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="9a7dd-144">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
