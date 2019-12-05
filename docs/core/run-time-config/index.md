---
title: Konfiguracja czasu wykonywania
description: Dowiedz się, jak skonfigurować aplikacje platformy .NET Core za pomocą ustawień konfiguracji czasu wykonywania.
ms.date: 11/13/2019
ms.openlocfilehash: 2665026347e94d26026821beb2bfcf8441f755f6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801914"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="11610-103">Ustawienia konfiguracji środowiska uruchomieniowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="11610-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="11610-104">Platforma .NET Core obsługuje używanie plików konfiguracji i zmiennych środowiskowych w celu skonfigurowania zachowania aplikacji .NET Core w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="11610-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="11610-105">Konfiguracja czasu wykonywania jest atrakcyjną opcją, jeśli:</span><span class="sxs-lookup"><span data-stu-id="11610-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="11610-106">Nie jesteś własnością ani nie kontrolujesz kodu źródłowego dla aplikacji, dlatego nie można programowo skonfigurować go.</span><span class="sxs-lookup"><span data-stu-id="11610-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="11610-107">Wiele wystąpień aplikacji jest wykonywanych w tym samym czasie w pojedynczym systemie i chcesz skonfigurować każdą z nich w celu uzyskania optymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="11610-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="11610-108">Ta dokumentacja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="11610-108">This documentation is a work in progress.</span></span> <span data-ttu-id="11610-109">Jeśli zauważysz, że informacje przedstawione w tym miejscu są niekompletne lub niedokładne, należy [otworzyć problem](https://github.com/dotnet/docs/issues) , aby poinformować nas o tym lub [przesłać żądanie ściągnięcia](https://github.com/dotnet/docs/pulls) w celu rozwiązania problemu.</span><span class="sxs-lookup"><span data-stu-id="11610-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="11610-110">Informacje dotyczące przesyłania żądań ściągnięcia dla repozytorium dotnet/docs można znaleźć w [przewodniku współautora](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="11610-110">For information on submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="11610-111">Platforma .NET Core udostępnia następujące mechanizmy konfigurowania aplikacji w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="11610-111">.NET Core provides the following mechanisms for configuring applications at run time:</span></span>

- <span data-ttu-id="11610-112">[Plik runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="11610-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="11610-113">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="11610-113">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="11610-114">Artykuły w tej sekcji dokumentacji obejmują elementy uporządkowane według kategorii, na przykład debugowania i wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="11610-114">The articles in this section of the documentation include are organized by category, for example, debugging and garbage collection.</span></span> <span data-ttu-id="11610-115">Jeśli ma to zastosowanie, opcje konfiguracji są wyświetlane dla *runtimeconfig. JSON* (tylko dla platformy .NET Core), *App. config* (tylko .NET Framework) i zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="11610-115">Where applicable, configuration options are shown for *runtimeconfig.json* (.NET Core only), *app.config* (.NET Framework only), and environment variables.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="11610-116">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="11610-116">runtimeconfig.json</span></span>

<span data-ttu-id="11610-117">Określ opcje konfiguracji czasu wykonywania w sekcji **configProperties** w pliku *runtimeconfig. JSON* aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11610-117">Specify run-time configuration options in the **configProperties** section of the app's *runtimeconfig.json* file.</span></span> <span data-ttu-id="11610-118">Ta sekcja ma postać:</span><span class="sxs-lookup"><span data-stu-id="11610-118">This section has the form:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

<span data-ttu-id="11610-119">Oto przykładowy plik:</span><span class="sxs-lookup"><span data-stu-id="11610-119">Here is an example file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

<span data-ttu-id="11610-120">Plik *runtimeconfig. JSON* jest tworzony automatycznie w katalogu kompilacji przez polecenie [kompilacji dotnet](../tools/dotnet-build.md) .</span><span class="sxs-lookup"><span data-stu-id="11610-120">The *runtimeconfig.json* file is automatically created in the build directory by the [dotnet build](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="11610-121">Jest również tworzony w przypadku wybrania opcji menu **kompilacja** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11610-121">It's also created when you select the **Build** menu option in Visual Studio.</span></span> <span data-ttu-id="11610-122">Następnie można edytować plik po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="11610-122">You can then edit the file once it's created.</span></span>

<span data-ttu-id="11610-123">Niektóre wartości konfiguracji można również ustawić programowo, wywołując metodę <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="11610-123">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="11610-124">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="11610-124">Environment variables</span></span>

<span data-ttu-id="11610-125">Zmienne środowiskowe mogą służyć do dostarczania niektórych informacji o konfiguracji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="11610-125">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="11610-126">Pokrętła konfiguracji określone jako zmienne środowiskowe zwykle mają prefiks **COMPlus_** .</span><span class="sxs-lookup"><span data-stu-id="11610-126">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="11610-127">Zmienne środowiskowe można definiować w panelu sterowania systemu Windows, w wierszu polecenia lub programowo, wywołując metodę <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> w systemach Windows i UNIX.</span><span class="sxs-lookup"><span data-stu-id="11610-127">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="11610-128">W poniższych przykładach pokazano, jak ustawić zmienną środowiskową w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="11610-128">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
