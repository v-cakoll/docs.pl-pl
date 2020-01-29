---
title: Opcje konfiguracji czasu wykonywania
description: Dowiedz się, jak skonfigurować aplikacje platformy .NET Core za pomocą ustawień konfiguracji czasu wykonywania.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733439"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="2e282-103">Ustawienia konfiguracji środowiska uruchomieniowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e282-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="2e282-104">Platforma .NET Core obsługuje używanie plików konfiguracji i zmiennych środowiskowych w celu skonfigurowania zachowania aplikacji .NET Core w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2e282-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="2e282-105">Konfiguracja czasu wykonywania jest atrakcyjną opcją, jeśli:</span><span class="sxs-lookup"><span data-stu-id="2e282-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="2e282-106">Nie jesteś własnością ani nie kontrolujesz kodu źródłowego dla aplikacji, dlatego nie można programowo skonfigurować go.</span><span class="sxs-lookup"><span data-stu-id="2e282-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="2e282-107">Wiele wystąpień aplikacji jest wykonywanych w tym samym czasie w pojedynczym systemie i chcesz skonfigurować każdą z nich w celu uzyskania optymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="2e282-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="2e282-108">Ta dokumentacja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="2e282-108">This documentation is a work in progress.</span></span> <span data-ttu-id="2e282-109">Jeśli zauważysz, że informacje przedstawione w tym miejscu są niekompletne lub niedokładne, należy [otworzyć problem](https://github.com/dotnet/docs/issues) , aby poinformować nas o tym lub [przesłać żądanie ściągnięcia](https://github.com/dotnet/docs/pulls) w celu rozwiązania problemu.</span><span class="sxs-lookup"><span data-stu-id="2e282-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="2e282-110">Informacje o przesyłaniu żądań ściągnięcia dla repozytorium dotnet/docs można znaleźć w [przewodniku współautora](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="2e282-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="2e282-111">Platforma .NET Core udostępnia następujące mechanizmy konfigurowania zachowania aplikacji w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="2e282-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="2e282-112">[Plik runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="2e282-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="2e282-113">Właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="2e282-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="2e282-114">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="2e282-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="2e282-115">Niektóre wartości konfiguracji można również ustawić programowo, wywołując metodę <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2e282-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2e282-116">Artykuły w tej sekcji dokumentacji są zorganizowane według kategorii, na przykład [debugowania](debugging-profiling.md) i [wyrzucania elementów bezużytecznych](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="2e282-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="2e282-117">W stosownych przypadkach opcje konfiguracji są wyświetlane dla plików *runtimeconfig. JSON* , właściwości programu MSBuild, zmiennych środowiskowych i, w przypadku plików z odsyłaczem, *pliku App. config* dla projektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2e282-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="2e282-118">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="2e282-118">runtimeconfig.json</span></span>

<span data-ttu-id="2e282-119">Po [skompilowaniu](../tools/dotnet-build.md)projektu w katalogu wyjściowym zostanie wygenerowany plik *[nazwa_aplikacji]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2e282-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="2e282-120">Jeśli plik *runtimeconfig. Template. JSON* istnieje w tym samym folderze co plik projektu, wszystkie opcje konfiguracji, które zawiera, są scalane w pliku *[nazwa_aplikacji]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2e282-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="2e282-121">Jeśli tworzysz aplikację samodzielnie, umieść wszystkie opcje konfiguracji w pliku *runtimeconfig. Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2e282-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="2e282-122">Jeśli właśnie uruchamiasz aplikację, Wstaw ją bezpośrednio do pliku *[nazwa_aplikacji]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2e282-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="2e282-123">Plik *[nazwa_aplikacji]. runtimeconfig. JSON* zostanie nadpisany po kolejnych kompilacjach.</span><span class="sxs-lookup"><span data-stu-id="2e282-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="2e282-124">Określ opcje konfiguracji czasu wykonywania w sekcji **configProperties** plików *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2e282-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="2e282-125">Ta sekcja ma postać:</span><span class="sxs-lookup"><span data-stu-id="2e282-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="2e282-126">Przykład [nazwa_aplikacji]. runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="2e282-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="2e282-127">Jeśli umieszczasz opcje w wyjściowym pliku JSON, zastąp je właściwością `runtimeOptions`.</span><span class="sxs-lookup"><span data-stu-id="2e282-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

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

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="2e282-128">Przykład pliku runtimeconfig. Template. JSON</span><span class="sxs-lookup"><span data-stu-id="2e282-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="2e282-129">Jeśli umieszczasz opcje w pliku JSON szablonu, Pomiń Właściwość `runtimeOptions`.</span><span class="sxs-lookup"><span data-stu-id="2e282-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="2e282-130">właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="2e282-130">MSBuild properties</span></span>

<span data-ttu-id="2e282-131">Niektóre opcje konfiguracji czasu wykonywania można ustawić przy użyciu właściwości programu MSBuild w pliku *. csproj* lub *. vbproj* projektów .NET Core w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="2e282-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="2e282-132">Właściwości programu MSBuild mają pierwszeństwo przed opcjami ustawionymi w pliku *runtimeconfig. Template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="2e282-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="2e282-133">Zastąpią także wszystkie opcje ustawione w pliku *[nazwa_aplikacji]. runtimeconfig. JSON* w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2e282-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="2e282-134">Oto przykładowy plik projektu w stylu zestawu SDK z właściwościami MSBuild służący do konfigurowania zachowania w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="2e282-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

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

<span data-ttu-id="2e282-135">Właściwości programu MSBuild służące do konfigurowania zachowania w czasie wykonywania są zanotowane w poszczególnych artykułach dla każdego obszaru, na przykład na [wyrzucaniu elementów bezużytecznych](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="2e282-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="2e282-136">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="2e282-136">Environment variables</span></span>

<span data-ttu-id="2e282-137">Zmienne środowiskowe mogą służyć do dostarczania niektórych informacji o konfiguracji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2e282-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="2e282-138">Pokrętła konfiguracji określone jako zmienne środowiskowe zwykle mają prefiks **COMPlus_** .</span><span class="sxs-lookup"><span data-stu-id="2e282-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="2e282-139">Zmienne środowiskowe można definiować w panelu sterowania systemu Windows, w wierszu polecenia lub programowo, wywołując metodę <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> w systemach Windows i UNIX.</span><span class="sxs-lookup"><span data-stu-id="2e282-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="2e282-140">W poniższych przykładach pokazano, jak ustawić zmienną środowiskową w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="2e282-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
