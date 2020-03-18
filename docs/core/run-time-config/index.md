---
title: Opcje konfiguracji w czasie wykonywania
description: Dowiedz się, jak skonfigurować aplikacje .NET Core przy użyciu ustawień konfiguracji w czasie wykonywania.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399162"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="3f826-103">Ustawienia konfiguracji środowiska .NET Core w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="3f826-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="3f826-104">Program .NET Core obsługuje używanie plików konfiguracyjnych i zmiennych środowiskowych w celu skonfigurowania zachowania aplikacji .NET Core w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3f826-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="3f826-105">Konfiguracja w czasie wykonywania jest atrakcyjną opcją, jeśli:</span><span class="sxs-lookup"><span data-stu-id="3f826-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="3f826-106">Nie jesteś właścicielem lub kontrolować kod źródłowy dla aplikacji i dlatego nie można skonfigurować go programowo.</span><span class="sxs-lookup"><span data-stu-id="3f826-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="3f826-107">Wiele wystąpień aplikacji uruchamia się w tym samym czasie w jednym systemie i chcesz skonfigurować każdy dla optymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="3f826-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="3f826-108">Ta dokumentacja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="3f826-108">This documentation is a work in progress.</span></span> <span data-ttu-id="3f826-109">Jeśli zauważysz, że przedstawione tutaj informacje są niekompletne lub niedokładne, [otwórz problem,](https://github.com/dotnet/docs/issues) aby poinformować nas o tym, albo [prześlij żądanie ściągnięcia,](https://github.com/dotnet/docs/pulls) aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="3f826-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="3f826-110">Aby uzyskać informacje na temat przesyłania żądań ściągnięcia dla repozytorium dotnet/docs, zobacz [przewodnik współautora](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="3f826-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="3f826-111">Program .NET Core udostępnia następujące mechanizmy konfigurowania zachowania aplikacji w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="3f826-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="3f826-112">[Plik runtimeconfig.json](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="3f826-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="3f826-113">MsBuild właściwości</span><span class="sxs-lookup"><span data-stu-id="3f826-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="3f826-114">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="3f826-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="3f826-115">Niektóre wartości konfiguracji można również ustawić programowo, wywołując <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="3f826-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="3f826-116">Artykuły w tej sekcji dokumentacji są zorganizowane według kategorii, na przykład [debugowania](debugging-profiling.md) i [wyrzucania elementów bezużytecznych](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="3f826-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="3f826-117">W stosownych przypadkach opcje konfiguracji są wyświetlane dla plików *runtimeconfig.json,* właściwości MSBuild, zmiennych środowiskowych i, dla odsyłacza, plików *app.config* dla projektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f826-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="3f826-118">runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="3f826-118">runtimeconfig.json</span></span>

<span data-ttu-id="3f826-119">Po [skonstruowaniu](../tools/dotnet-build.md)projektu w katalogu wyjściowym generowany jest plik *[nazwa_aplikacji].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="3f826-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="3f826-120">Jeśli plik *runtimeconfig.template.json* istnieje w tym samym folderze co plik projektu, wszystkie opcje konfiguracji, które zawiera, są scalane z *plikiem [nazwa_aplikacji].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="3f826-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="3f826-121">Jeśli samodzielnie budujesz aplikację, umieść dowolne opcje konfiguracji w pliku *runtimeconfig.template.json.*</span><span class="sxs-lookup"><span data-stu-id="3f826-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="3f826-122">Jeśli po prostu używasz aplikacji, wstaw je bezpośrednio do pliku *[nazwa aplikacji].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="3f826-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="3f826-123">Plik *[nazwa aplikacji].runtimeconfig.json* zostanie zastąpiony na kolejnych kompilacjach.</span><span class="sxs-lookup"><span data-stu-id="3f826-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="3f826-124">Określ opcje konfiguracji w czasie wykonywania w sekcji **configProperties** plików *runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="3f826-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="3f826-125">Ta sekcja ma formularz:</span><span class="sxs-lookup"><span data-stu-id="3f826-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="3f826-126">Przykładowy plik [nazwa aplikacji].runtimeconfig.json file</span><span class="sxs-lookup"><span data-stu-id="3f826-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="3f826-127">Jeśli umieszczasz opcje w wyjściowym pliku JSON, `runtimeOptions` zagnieździć je pod właściwością.</span><span class="sxs-lookup"><span data-stu-id="3f826-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

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

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="3f826-128">Przykładowy plik runtimeconfig.template.json</span><span class="sxs-lookup"><span data-stu-id="3f826-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="3f826-129">Jeśli umieszczasz opcje w pliku JSON szablonu, pomiń właściwość. `runtimeOptions`</span><span class="sxs-lookup"><span data-stu-id="3f826-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="3f826-130">właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="3f826-130">MSBuild properties</span></span>

<span data-ttu-id="3f826-131">Niektóre opcje konfiguracji w czasie wykonywania można ustawić przy użyciu właściwości MSBuild w pliku *csproj* lub *.vbproj* projektów .NET Core w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="3f826-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="3f826-132">Właściwości MSBuild mają pierwszeństwo przed opcjami ustawionymi w pliku *runtimeconfig.template.json.*</span><span class="sxs-lookup"><span data-stu-id="3f826-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="3f826-133">Zastępują one również wszystkie opcje ustawione w pliku *[nazwa_aplikacji].runtimeconfig.json* w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3f826-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="3f826-134">Oto przykładowy plik projektu w stylu SDK z właściwościami MSBuild do konfigurowania zachowania w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="3f826-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

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

<span data-ttu-id="3f826-135">MsBuild właściwości do konfigurowania zachowania w czasie wykonywania są odnotowane w poszczególnych artykułów dla każdego obszaru, na przykład [wyrzucania elementów bezużytecznych](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="3f826-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="3f826-136">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="3f826-136">Environment variables</span></span>

<span data-ttu-id="3f826-137">Zmiennych środowiskowych może służyć do dostarczania niektórych informacji o konfiguracji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3f826-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="3f826-138">Pokrętła konfiguracji określone jako zmienne środowiskowe mają zazwyczaj prefiks **COMPlus_**.</span><span class="sxs-lookup"><span data-stu-id="3f826-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="3f826-139">Zmienne środowiskowe można definiować z Panelu sterowania systemu Windows, w <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> wierszu polecenia lub programowo, wywołując metodę zarówno w systemach Windows, jak i Unix.</span><span class="sxs-lookup"><span data-stu-id="3f826-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="3f826-140">W poniższych przykładach przedstawiono sposób ustawiania zmiennej środowiskowej w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="3f826-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
