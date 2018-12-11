---
title: czyszczenie polecenia DotNet
description: Polecenia dotnet clean czyści bieżącego katalogu.
ms.date: 12/04/2018
ms.openlocfilehash: a25b7930794795e3dff5051a8ca1dd1b9c261dfd
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169862"
---
# <a name="dotnet-clean"></a><span data-ttu-id="18bc1-103">Wyczyść DotNet</span><span class="sxs-lookup"><span data-stu-id="18bc1-103">dotnet clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="18bc1-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="18bc1-104">Name</span></span>

<span data-ttu-id="18bc1-105">`dotnet clean` -Czyści dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="18bc1-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="18bc1-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="18bc1-106">Synopsis</span></span>

```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="18bc1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="18bc1-107">Description</span></span>

<span data-ttu-id="18bc1-108">`dotnet clean` Polecenia czyści dane wyjściowe poprzednią kompilację.</span><span class="sxs-lookup"><span data-stu-id="18bc1-108">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="18bc1-109">Jest implementowany jako [programu MSBuild](/visualstudio/msbuild/msbuild-targets), więc projekt jest oceniany, jeśli polecenie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="18bc1-109">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="18bc1-110">Tylko dane wyjściowe, utworzony podczas kompilacji są czyszczone.</span><span class="sxs-lookup"><span data-stu-id="18bc1-110">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="18bc1-111">Zarówno pośredni (*obj*) i końcowych danych wyjściowych (*bin*) foldery zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="18bc1-111">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="18bc1-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="18bc1-112">Arguments</span></span>

`PROJECT`

<span data-ttu-id="18bc1-113">Projekt programu MSBuild do czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="18bc1-113">The MSBuild project to clean.</span></span> <span data-ttu-id="18bc1-114">Jeśli nie określono pliku projektu, MSBuild przeszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="18bc1-114">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="18bc1-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="18bc1-115">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="18bc1-116">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="18bc1-116">Defines the build configuration.</span></span> <span data-ttu-id="18bc1-117">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="18bc1-117">The default value is `Debug`.</span></span> <span data-ttu-id="18bc1-118">Ta opcja jest tylko wymagane podczas czyszczenia, jeśli została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="18bc1-118">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="18bc1-119">[Framework](../../standard/frameworks.md) , która została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="18bc1-119">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="18bc1-120">Struktura musi być zdefiniowany w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="18bc1-120">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="18bc1-121">Jeśli struktura jest określona w czasie kompilacji, należy określić platformę, podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="18bc1-121">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="18bc1-122">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="18bc1-122">Prints out a short help for the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="18bc1-123">Katalog, w której są umieszczane dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="18bc1-123">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="18bc1-124">Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu danych wyjściowych, jeśli określona struktura podczas kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="18bc1-124">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="18bc1-125">Czyści folderze wyjściowym określonym środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="18bc1-125">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="18bc1-126">Jest on używany podczas [niezależna wdrożenia](../deploying/index.md#self-contained-deployments-scd) został utworzony.</span><span class="sxs-lookup"><span data-stu-id="18bc1-126">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="18bc1-127">Opcja dostępna od .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="18bc1-127">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="18bc1-128">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="18bc1-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="18bc1-129">Dozwolone poziomy są q [uiet], m [najmniej], [ormal] n, d [egółowy] i diag [Diagnostyka].</span><span class="sxs-lookup"><span data-stu-id="18bc1-129">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

## <a name="examples"></a><span data-ttu-id="18bc1-130">Przykłady</span><span class="sxs-lookup"><span data-stu-id="18bc1-130">Examples</span></span>

* <span data-ttu-id="18bc1-131">Czyszczenie kompilacji domyślnego projektu:</span><span class="sxs-lookup"><span data-stu-id="18bc1-131">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="18bc1-132">Wyczyść projekt, który został skompilowany przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="18bc1-132">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```