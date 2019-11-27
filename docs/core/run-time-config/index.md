---
title: Konfiguracja czasu wykonywania
description: Dowiedz się, jak skonfigurować aplikacje platformy .NET Core za pomocą ustawień konfiguracji czasu wykonywania.
ms.date: 11/13/2019
ms.openlocfilehash: f7074b07bdd5aca23b6caae78952d630d905c489
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283990"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="70aa0-103">Ustawienia konfiguracji środowiska uruchomieniowego .NET Core</span><span class="sxs-lookup"><span data-stu-id="70aa0-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="70aa0-104">Platforma .NET Core obsługuje używanie plików konfiguracji i zmiennych środowiskowych w celu skonfigurowania zachowania aplikacji .NET Core w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="70aa0-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="70aa0-105">Konfiguracja czasu wykonywania jest atrakcyjną opcją, jeśli:</span><span class="sxs-lookup"><span data-stu-id="70aa0-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="70aa0-106">Nie jesteś własnością ani nie kontrolujesz kodu źródłowego dla aplikacji, dlatego nie można programowo skonfigurować go.</span><span class="sxs-lookup"><span data-stu-id="70aa0-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="70aa0-107">Wiele wystąpień aplikacji jest wykonywanych w tym samym czasie w pojedynczym systemie i chcesz skonfigurować każdą z nich w celu uzyskania optymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="70aa0-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="70aa0-108">Ta dokumentacja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="70aa0-108">This documentation is a work in progress.</span></span> <span data-ttu-id="70aa0-109">Jeśli zauważysz, że informacje przedstawione w tym miejscu są niekompletne lub niedokładne, należy [otworzyć problem](https://github.com/dotnet/docs/issues) , aby poinformować nas o tym lub [przesłać żądanie ściągnięcia](https://github.com/dotnet/docs/pulls) w celu rozwiązania problemu.</span><span class="sxs-lookup"><span data-stu-id="70aa0-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="70aa0-110">Informacje dotyczące przesyłania żądań ściągnięcia dla repozytorium dotnet/docs można znaleźć w [przewodniku współautora](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="70aa0-110">For information on submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="70aa0-111">Platforma .NET Core udostępnia następujące mechanizmy konfigurowania aplikacji w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="70aa0-111">.NET Core provides the following mechanisms for configuring applications at run time:</span></span>

- <span data-ttu-id="70aa0-112">[Plik runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="70aa0-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="70aa0-113">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="70aa0-113">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="70aa0-114">Artykuły w tej sekcji dokumentacji obejmują elementy uporządkowane według kategorii, na przykład debugowania i wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="70aa0-114">The articles in this section of the documentation include are organized by category, for example, debugging and garbage collection.</span></span> <span data-ttu-id="70aa0-115">Dostępne opcje konfiguracji są wyświetlane dla *runtimeconfig. JSON* (tylko dla platformy .NET Core), *App. config* (tylko .NET Framework) i zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="70aa0-115">Available configuration options are shown for *runtimeconfig.json* (.NET Core only), *app.config* (.NET Framework only), and environment variables.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="70aa0-116">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="70aa0-116">runtimeconfig.json</span></span>

<span data-ttu-id="70aa0-117">Określ opcje konfiguracji czasu wykonywania w sekcji **configProperties** pliku *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="70aa0-117">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* file.</span></span> <span data-ttu-id="70aa0-118">Ta sekcja ma postać:</span><span class="sxs-lookup"><span data-stu-id="70aa0-118">This section has the form:</span></span>

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

<span data-ttu-id="70aa0-119">Oto przykładowy plik:</span><span class="sxs-lookup"><span data-stu-id="70aa0-119">Here is an example file:</span></span>

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

<span data-ttu-id="70aa0-120">Plik *runtimeconfig. JSON* jest tworzony automatycznie w katalogu kompilacji przez polecenie [kompilacji dotnet](../tools/dotnet-build.md) .</span><span class="sxs-lookup"><span data-stu-id="70aa0-120">The *runtimeconfig.json* file is automatically created in the build directory by the [dotnet build](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="70aa0-121">Jest również tworzony w przypadku wybrania opcji menu **kompilacja** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70aa0-121">It's also created when you select the **Build** menu option in Visual Studio.</span></span> <span data-ttu-id="70aa0-122">Następnie można edytować plik po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="70aa0-122">You can then edit the file once it's created.</span></span>

<span data-ttu-id="70aa0-123">Niektóre wartości konfiguracji można również ustawić programowo, wywołując metodę <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70aa0-123">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="70aa0-124">Zmienne środowiskowe</span><span class="sxs-lookup"><span data-stu-id="70aa0-124">Environment variables</span></span>

<span data-ttu-id="70aa0-125">Zmienne środowiskowe mogą służyć do podawania informacji o konfiguracji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="70aa0-125">Environment variables can be used to to supply some run-time configuration information.</span></span> <span data-ttu-id="70aa0-126">Pokrętła konfiguracji określone jako zmienne środowiskowe zwykle mają prefiks **COMPlus_** .</span><span class="sxs-lookup"><span data-stu-id="70aa0-126">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="70aa0-127">Zmienne środowiskowe można definiować w panelu sterowania systemu Windows, w wierszu polecenia lub programowo, wywołując metodę <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> w systemach Windows i UNIX.</span><span class="sxs-lookup"><span data-stu-id="70aa0-127">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="70aa0-128">W poniższych przykładach pokazano, jak ustawić zmienną środowiskową w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="70aa0-128">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
