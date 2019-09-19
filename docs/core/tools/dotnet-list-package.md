---
title: polecenie pakietu list dotnet
description: Polecenie "pakiet listy dotnet" udostępnia wygodną opcję wyświetlania odwołań do pakietów dla projektu lub rozwiązania.
ms.date: 06/26/2019
ms.openlocfilehash: fe95f3898c5bd85956f4312eb4d20259227e9ff0
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117730"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="94cf9-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="94cf9-103">dotnet list package</span></span>

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a><span data-ttu-id="94cf9-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="94cf9-104">Name</span></span>

<span data-ttu-id="94cf9-105">`dotnet list package`-Wyświetla listę odwołań do pakietu dla projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="94cf9-105">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="94cf9-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="94cf9-106">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="94cf9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="94cf9-107">Description</span></span>

<span data-ttu-id="94cf9-108">`dotnet list package` Polecenie udostępnia wygodną opcję wyświetlania listy wszystkich odwołań pakietów NuGet dla określonego projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="94cf9-108">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="94cf9-109">Najpierw należy skompilować projekt w celu uzyskania zasobów potrzebnych do przetworzenia tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="94cf9-109">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="94cf9-110">Poniższy przykład przedstawia dane wyjściowe `dotnet list package` polecenia dla projektu [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :</span><span class="sxs-lookup"><span data-stu-id="94cf9-110">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="94cf9-111">**Żądana** kolumna odwołuje się do wersji pakietu określonej w pliku projektu i może być zakresem.</span><span class="sxs-lookup"><span data-stu-id="94cf9-111">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="94cf9-112">W kolumnie **rozwiązane** są wyświetlane wersje, które są obecnie używane w projekcie i zawsze jest pojedyncza wartość.</span><span class="sxs-lookup"><span data-stu-id="94cf9-112">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="94cf9-113">Pakiety wyświetlające `(A)` prawo obok ich nazw reprezentują [niejawne odwołania do pakietów](csproj.md#implicit-package-references) , które są wywnioskowane z`Sdk` `<TargetFramework>` ustawień projektu (typ lub `<TargetFrameworks>` Właściwość itp.)</span><span class="sxs-lookup"><span data-stu-id="94cf9-113">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="94cf9-114">Użyj opcji `--outdated` , aby dowiedzieć się, czy są dostępne nowsze wersje pakietów używanych w projektach.</span><span class="sxs-lookup"><span data-stu-id="94cf9-114">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="94cf9-115">Domyślnie program wyświetla `--outdated` listę najnowszych stabilnych pakietów, chyba że rozpoznana wersja stanowi również wersję wstępną.</span><span class="sxs-lookup"><span data-stu-id="94cf9-115">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="94cf9-116">Aby uwzględnić wersje wstępne podczas wyświetlania listy nowszych wersji, należy również określić `--include-prerelease` opcję.</span><span class="sxs-lookup"><span data-stu-id="94cf9-116">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="94cf9-117">Poniższe przykłady przedstawiają dane wyjściowe `dotnet list package --outdated --include-prerelease` polecenia dla tego samego projektu, co w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="94cf9-117">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

<span data-ttu-id="94cf9-118">Jeśli chcesz dowiedzieć się, czy projekt zawiera zależności przechodnie, użyj `--include-transitive` opcji.</span><span class="sxs-lookup"><span data-stu-id="94cf9-118">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="94cf9-119">Zależności przechodnie występują po dodaniu pakietu do projektu, który z kolei jest zależny od innego pakietu.</span><span class="sxs-lookup"><span data-stu-id="94cf9-119">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="94cf9-120">Poniższy przykład przedstawia dane wyjściowe uruchamiania `dotnet list package --include-transitive` polecenia dla projektu [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) , w którym są wyświetlane pakiety najwyższego poziomu i pakiety, od których zależą:</span><span class="sxs-lookup"><span data-stu-id="94cf9-120">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a><span data-ttu-id="94cf9-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="94cf9-121">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="94cf9-122">Plik projektu lub rozwiązania do działania.</span><span class="sxs-lookup"><span data-stu-id="94cf9-122">The project or solution file to operate on.</span></span> <span data-ttu-id="94cf9-123">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="94cf9-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="94cf9-124">Jeśli znaleziono więcej niż jedno rozwiązanie lub projekt, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="94cf9-124">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="94cf9-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="94cf9-125">Options</span></span>

* **`--config <SOURCE>`**

  <span data-ttu-id="94cf9-126">Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="94cf9-126">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="94cf9-127">`--outdated` Wymaga opcji.</span><span class="sxs-lookup"><span data-stu-id="94cf9-127">Requires the `--outdated` option.</span></span>

* **`--framework <FRAMEWORK>`**

  <span data-ttu-id="94cf9-128">Wyświetla tylko pakiety mające zastosowanie do określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="94cf9-128">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="94cf9-129">Aby określić wiele struktur, Powtarzaj tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="94cf9-129">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="94cf9-130">Na przykład: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="94cf9-130">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="94cf9-131">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="94cf9-131">Prints out a short help for the command.</span></span>

* **`--highest-minor`**

  <span data-ttu-id="94cf9-132">Podczas wyszukiwania nowszych pakietów uwzględnia tylko te pakiety, które pasują do numeru głównego.</span><span class="sxs-lookup"><span data-stu-id="94cf9-132">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="94cf9-133">`--outdated` Wymaga opcji.</span><span class="sxs-lookup"><span data-stu-id="94cf9-133">Requires the `--outdated` option.</span></span>

* **`--highest-patch`**

  <span data-ttu-id="94cf9-134">Podczas wyszukiwania nowszych pakietów uwzględnia tylko te pakiety, które mają pasujące główne i pomocnicze numery wersji.</span><span class="sxs-lookup"><span data-stu-id="94cf9-134">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="94cf9-135">`--outdated` Wymaga opcji.</span><span class="sxs-lookup"><span data-stu-id="94cf9-135">Requires the `--outdated` option.</span></span>

* **`--include-prerelease`**

  <span data-ttu-id="94cf9-136">Traktuje pakiety z wersjami wstępnymi podczas wyszukiwania nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="94cf9-136">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="94cf9-137">`--outdated` Wymaga opcji.</span><span class="sxs-lookup"><span data-stu-id="94cf9-137">Requires the `--outdated` option.</span></span>

* **`--include-transitive`**

  <span data-ttu-id="94cf9-138">Wyświetla listę pakietów przechodnich oprócz pakietów najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="94cf9-138">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="94cf9-139">Po wybraniu tej opcji otrzymujesz listę pakietów, od których zależą pakiety najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="94cf9-139">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

* **`--interactive`**

  <span data-ttu-id="94cf9-140">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="94cf9-140">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="94cf9-141">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="94cf9-141">For example, to complete authentication.</span></span> <span data-ttu-id="94cf9-142">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="94cf9-142">Available since .NET Core 3.0 SDK.</span></span>

* **`--outdated`**

  <span data-ttu-id="94cf9-143">Wyświetla listę pakietów, które mają dostępne nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="94cf9-143">Lists packages that have newer versions available.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="94cf9-144">Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="94cf9-144">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="94cf9-145">`--outdated` Wymaga opcji.</span><span class="sxs-lookup"><span data-stu-id="94cf9-145">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="94cf9-146">Przykłady</span><span class="sxs-lookup"><span data-stu-id="94cf9-146">Examples</span></span>

* <span data-ttu-id="94cf9-147">Utwórz listę odwołań do pakietów dla określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="94cf9-147">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

* <span data-ttu-id="94cf9-148">Wyświetl listę odwołań do pakietów, które mają dostępne nowsze wersje, w tym wersje wstępne:</span><span class="sxs-lookup"><span data-stu-id="94cf9-148">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

* <span data-ttu-id="94cf9-149">Utwórz listę odwołań do pakietów dla konkretnej platformy docelowej:</span><span class="sxs-lookup"><span data-stu-id="94cf9-149">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
