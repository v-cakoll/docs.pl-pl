---
title: polecenie pakietu listy DotNet
description: Polecenia dotnet wyświetlenia listy pakietów zapewnia wygodny sposób, aby wyświetlić listę odwołania do pakietu dla projektu lub rozwiązania.
ms.date: 04/09/2019
ms.openlocfilehash: bc38b94201f85ed4b22e11722ef5cabcb6fbf040
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481599"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="d508c-103">polecenia DotNet wyświetlenia listy pakietów</span><span class="sxs-lookup"><span data-stu-id="d508c-103">dotnet list package</span></span>

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a><span data-ttu-id="d508c-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d508c-104">Name</span></span>

`dotnet list package` <span data-ttu-id="d508c-105">— Wyświetla listę odwołań do pakietów dla projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d508c-105">- Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d508c-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d508c-106">Synopsis</span></span>

```
dotnet list [<PROJECT | SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="d508c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d508c-107">Description</span></span>

<span data-ttu-id="d508c-108">`dotnet list package` Polecenie zapewnia wygodny sposób, aby wyświetlić listę wszystkich odwołań do pakietów NuGet dla określonego projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d508c-108">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="d508c-109">Należy najpierw skompilować projekt, aby mogła mieć zasoby wymagane dla tego polecenia do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="d508c-109">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="d508c-110">Poniższy przykład przedstawia dane wyjściowe `dotnet list package` polecenie, aby uzyskać [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projektu:</span><span class="sxs-lookup"><span data-stu-id="d508c-110">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="d508c-111">**Żądana** kolumna odwołuje się do wersji pakietu, określone w pliku projektu i może być zakresem.</span><span class="sxs-lookup"><span data-stu-id="d508c-111">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="d508c-112">**Rozwiązane** kolumna zawiera listę wersji, że projekt jest obecnie używany i zawsze jest wartość typu single.</span><span class="sxs-lookup"><span data-stu-id="d508c-112">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="d508c-113">Pakiety wyświetlanie `(A)` reprezentują obok ich nazwy [odwołania do pakietu niejawne](csproj.md#implicit-package-references) , są dedukowane z ustawień projektu (`Sdk` typu `<TargetFramework>` lub `<TargetFrameworks>` właściwości itp.)</span><span class="sxs-lookup"><span data-stu-id="d508c-113">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="d508c-114">Użyj `--outdated` opcję, aby dowiedzieć się, jeśli dostępne są nowsze wersje pakietów używane w projektach.</span><span class="sxs-lookup"><span data-stu-id="d508c-114">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="d508c-115">Domyślnie `--outdated` Wyświetla listę najnowszych pakietów stabilny, chyba że rozwiązane jest także wersja wstępna wersja.</span><span class="sxs-lookup"><span data-stu-id="d508c-115">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="d508c-116">Aby dołączyć wstępnej wersji, podczas wyświetlania nowszych wersji, należy także określić `--include-prerelease` opcji.</span><span class="sxs-lookup"><span data-stu-id="d508c-116">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="d508c-117">Następujące przykłady przedstawiają dane wyjściowe `dotnet list package --outdated --include-prerelease` polecenia dla tego samego projektu, jak w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d508c-117">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

<span data-ttu-id="d508c-118">Jeśli musisz sprawdzić, czy projekt ma przechodnie zależności, użyj `--include-transitive` opcji.</span><span class="sxs-lookup"><span data-stu-id="d508c-118">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="d508c-119">Przechodnie zależności wystąpić, gdy dodasz pakiet do projektu, która z kolei zależy od innego pakietu.</span><span class="sxs-lookup"><span data-stu-id="d508c-119">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="d508c-120">Poniższy przykład przedstawia dane wyjściowe uruchamianie `dotnet list package --include-transitive` polecenie, aby uzyskać [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projektu, który wyświetla najwyższego pakiety i pakiety, są one zależne od:</span><span class="sxs-lookup"><span data-stu-id="d508c-120">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

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

## <a name="arguments"></a><span data-ttu-id="d508c-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d508c-121">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="d508c-122">Plik projektu lub rozwiązania do wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="d508c-122">The project or solution file to operate on.</span></span> <span data-ttu-id="d508c-123">Jeśli nie zostanie określony, polecenie wyszukuje w bieżącym katalogu dla jednego.</span><span class="sxs-lookup"><span data-stu-id="d508c-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="d508c-124">Jeśli więcej niż jedno rozwiązanie lub projekt zostanie znaleziony, zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="d508c-124">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="d508c-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="d508c-125">Options</span></span>

* **`--config <SOURCE>`**

  <span data-ttu-id="d508c-126">Źródła NuGet do użycia podczas wyszukiwania dla nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="d508c-126">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="d508c-127">Wymaga `--outdated` opcji.</span><span class="sxs-lookup"><span data-stu-id="d508c-127">Requires the `--outdated` option.</span></span>

* **`--framework <FRAMEWORK>`**

  <span data-ttu-id="d508c-128">Wyświetla tylko te pakiety, które są odpowiednie dla określonego [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d508c-128">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d508c-129">Aby określić wiele struktur, powtórz opcję wiele razy.</span><span class="sxs-lookup"><span data-stu-id="d508c-129">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="d508c-130">Na przykład: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="d508c-130">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="d508c-131">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="d508c-131">Prints out a short help for the command.</span></span>

* **`--highest-minor`**

  <span data-ttu-id="d508c-132">Uwzględnia tylko pakiety za pomocą dopasowywania główny numer wersji, podczas wyszukiwania dla nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="d508c-132">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="d508c-133">Wymaga `--outdated` opcji.</span><span class="sxs-lookup"><span data-stu-id="d508c-133">Requires the `--outdated` option.</span></span>

* **`--highest-patch`**

  <span data-ttu-id="d508c-134">Uwzględnia tylko pakiety z pasującą główne i pomocnicze numery wersji podczas wyszukiwania dla nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="d508c-134">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="d508c-135">Wymaga `--outdated` opcji.</span><span class="sxs-lookup"><span data-stu-id="d508c-135">Requires the `--outdated` option.</span></span>

* **`--include-prerelease`**

  <span data-ttu-id="d508c-136">Uwzględnia pakiety z wersji wstępnych podczas wyszukiwania dla nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="d508c-136">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="d508c-137">Wymaga `--outdated` opcji.</span><span class="sxs-lookup"><span data-stu-id="d508c-137">Requires the `--outdated` option.</span></span>

* **`--include-transitive`**

  <span data-ttu-id="d508c-138">Zawiera listę pakietów przechodnich, oprócz pakietów najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d508c-138">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="d508c-139">Gdy użycie tej opcji, masz dostęp do listy pakietów, które zależą od pakietów najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d508c-139">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

* **`--outdated`**

  <span data-ttu-id="d508c-140">Zawiera listę pakietów, które mają nowszych wersji będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="d508c-140">Lists packages that have newer versions available.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="d508c-141">Źródła NuGet do użycia podczas wyszukiwania dla nowszych pakietów.</span><span class="sxs-lookup"><span data-stu-id="d508c-141">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="d508c-142">Wymaga `--outdated` opcji.</span><span class="sxs-lookup"><span data-stu-id="d508c-142">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="d508c-143">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d508c-143">Examples</span></span>

* <span data-ttu-id="d508c-144">Lista odwołania do pakietu z określonego projektu:</span><span class="sxs-lookup"><span data-stu-id="d508c-144">List package references of a specific project:</span></span>

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* <span data-ttu-id="d508c-145">Lista odwołania do pakietu, które mają nowszych wersji będą dostępne wersje wstępne w tym:</span><span class="sxs-lookup"><span data-stu-id="d508c-145">List package references that have newer versions available, including prerelease versions:</span></span>

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* <span data-ttu-id="d508c-146">Wyświetl odwołania do pakietu dla określonej platformy:</span><span class="sxs-lookup"><span data-stu-id="d508c-146">List package references for a specific target framework:</span></span>

  ```console
  dotnet list package --framework netcoreapp3.0
  ```