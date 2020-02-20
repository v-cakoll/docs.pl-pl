---
title: polecenie pakietu list dotnet
description: Polecenie "pakiet listy dotnet" udostępnia wygodną opcję wyświetlania odwołań do pakietów dla projektu lub rozwiązania.
ms.date: 02/14/2020
ms.openlocfilehash: bd275c308c3a213661d5cc6c7e60817620f076a5
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503736"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="15c00-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="15c00-103">dotnet list package</span></span>

<span data-ttu-id="15c00-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,2 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="15c00-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="15c00-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="15c00-105">Name</span></span>

<span data-ttu-id="15c00-106">`dotnet list package` — wyświetla listę odwołań do pakietu dla projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="15c00-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="15c00-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="15c00-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="15c00-108">Opis</span><span class="sxs-lookup"><span data-stu-id="15c00-108">Description</span></span>

<span data-ttu-id="15c00-109">Polecenie `dotnet list package` udostępnia wygodną opcję wyświetlania wszystkich odwołań do pakietów NuGet dla określonego projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="15c00-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="15c00-110">Najpierw należy skompilować projekt w celu uzyskania zasobów potrzebnych do przetworzenia tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="15c00-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="15c00-111">Poniższy przykład przedstawia dane wyjściowe polecenia `dotnet list package` dla projektu [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :</span><span class="sxs-lookup"><span data-stu-id="15c00-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="15c00-112">**Żądana** kolumna odwołuje się do wersji pakietu określonej w pliku projektu i może być zakresem.</span><span class="sxs-lookup"><span data-stu-id="15c00-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="15c00-113">W kolumnie **rozwiązane** są wyświetlane wersje, które są obecnie używane w projekcie i zawsze jest pojedyncza wartość.</span><span class="sxs-lookup"><span data-stu-id="15c00-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="15c00-114">Pakiety wyświetlające `(A)` bezpośrednio obok ich nazw reprezentują [niejawne odwołania do pakietów](csproj.md#implicit-package-references) , które są wywnioskowane z ustawień projektu (typ`Sdk`, `<TargetFramework>` lub właściwość `<TargetFrameworks>` itp.)</span><span class="sxs-lookup"><span data-stu-id="15c00-114">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="15c00-115">Użyj opcji `--outdated`, aby dowiedzieć się, czy są dostępne nowsze wersje pakietów używanych w projektach.</span><span class="sxs-lookup"><span data-stu-id="15c00-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="15c00-116">Domyślnie program `--outdated` wyświetla listę najnowszych stabilnych pakietów, chyba że rozpoznana wersja to również wersja wstępna.</span><span class="sxs-lookup"><span data-stu-id="15c00-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="15c00-117">Aby uwzględnić wersje wstępne podczas wyświetlania listy nowszych wersji, należy również określić opcję `--include-prerelease`.</span><span class="sxs-lookup"><span data-stu-id="15c00-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="15c00-118">Poniższe przykłady przedstawiają dane wyjściowe polecenia `dotnet list package --outdated --include-prerelease` dla tego samego projektu, co w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="15c00-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="15c00-119">Jeśli chcesz dowiedzieć się, czy projekt zawiera zależności przechodnie, użyj opcji `--include-transitive`.</span><span class="sxs-lookup"><span data-stu-id="15c00-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="15c00-120">Zależności przechodnie występują po dodaniu pakietu do projektu, który z kolei jest zależny od innego pakietu.</span><span class="sxs-lookup"><span data-stu-id="15c00-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="15c00-121">Poniższy przykład przedstawia dane wyjściowe uruchamiania `dotnet list package --include-transitive` polecenie dla projektu [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) , który wyświetla pakiety najwyższego poziomu i pakiety, od których zależą:</span><span class="sxs-lookup"><span data-stu-id="15c00-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="15c00-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="15c00-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="15c00-123">Plik projektu lub rozwiązania do działania.</span><span class="sxs-lookup"><span data-stu-id="15c00-123">The project or solution file to operate on.</span></span> <span data-ttu-id="15c00-124">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="15c00-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="15c00-125">Jeśli znaleziono więcej niż jedno rozwiązanie lub projekt, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="15c00-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="15c00-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="15c00-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="15c00-127">Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="15c00-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="15c00-128">Wymaga opcji `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="15c00-128">Requires the `--outdated` option.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="15c00-129">Wyświetla tylko pakiety mające zastosowanie do określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="15c00-129">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="15c00-130">Aby określić wiele struktur, Powtarzaj tę opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="15c00-130">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="15c00-131">Na przykład: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="15c00-131">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="15c00-132">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="15c00-132">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="15c00-133">Podczas wyszukiwania nowszych pakietów uwzględnia tylko te pakiety, które pasują do numeru głównego.</span><span class="sxs-lookup"><span data-stu-id="15c00-133">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="15c00-134">Wymaga opcji `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="15c00-134">Requires the `--outdated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="15c00-135">Podczas wyszukiwania nowszych pakietów uwzględnia tylko te pakiety, które mają pasujące główne i pomocnicze numery wersji.</span><span class="sxs-lookup"><span data-stu-id="15c00-135">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="15c00-136">Wymaga opcji `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="15c00-136">Requires the `--outdated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="15c00-137">Traktuje pakiety z wersjami wstępnymi podczas wyszukiwania nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="15c00-137">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="15c00-138">Wymaga opcji `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="15c00-138">Requires the `--outdated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="15c00-139">Wyświetla listę pakietów przechodnich oprócz pakietów najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="15c00-139">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="15c00-140">Po wybraniu tej opcji otrzymujesz listę pakietów, od których zależą pakiety najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="15c00-140">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="15c00-141">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="15c00-141">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="15c00-142">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="15c00-142">For example, to complete authentication.</span></span> <span data-ttu-id="15c00-143">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="15c00-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="15c00-144">Wyświetla listę pakietów, które mają dostępne nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="15c00-144">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="15c00-145">Źródła NuGet do użycia podczas wyszukiwania nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="15c00-145">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="15c00-146">Wymaga opcji `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="15c00-146">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="15c00-147">Przykłady</span><span class="sxs-lookup"><span data-stu-id="15c00-147">Examples</span></span>

- <span data-ttu-id="15c00-148">Utwórz listę odwołań do pakietów dla określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="15c00-148">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="15c00-149">Wyświetl listę odwołań do pakietów, które mają dostępne nowsze wersje, w tym wersje wstępne:</span><span class="sxs-lookup"><span data-stu-id="15c00-149">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="15c00-150">Utwórz listę odwołań do pakietów dla konkretnej platformy docelowej:</span><span class="sxs-lookup"><span data-stu-id="15c00-150">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
