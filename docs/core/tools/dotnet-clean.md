---
title: czyszczenie polecenia — .NET Core wiersz polecenia DotNet
description: Polecenia dotnet clean czyści bieżącego katalogu.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 5553e4b4423a2d824c05caf7114c47b5f1c20477
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710145"
---
# <a name="dotnet-clean"></a><span data-ttu-id="0cbe7-103">Wyczyść DotNet</span><span class="sxs-lookup"><span data-stu-id="0cbe7-103">dotnet clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0cbe7-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0cbe7-104">Name</span></span>

<span data-ttu-id="0cbe7-105">`dotnet clean` -Czyści dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0cbe7-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="0cbe7-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0cbe7-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0cbe7-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0cbe7-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0cbe7-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="0cbe7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0cbe7-109">Description</span></span>

<span data-ttu-id="0cbe7-110">`dotnet clean` Polecenia czyści dane wyjściowe poprzednią kompilację.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="0cbe7-111">Jest implementowany jako [programu MSBuild](/visualstudio/msbuild/msbuild-targets), więc projekt jest oceniany, jeśli polecenie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="0cbe7-112">Tylko dane wyjściowe, utworzony podczas kompilacji są czyszczone.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="0cbe7-113">Zarówno pośredni (*obj*) i końcowych danych wyjściowych (*bin*) foldery zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="0cbe7-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0cbe7-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="0cbe7-115">Projekt programu MSBuild do czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-115">The MSBuild project to clean.</span></span> <span data-ttu-id="0cbe7-116">Jeśli nie określono pliku projektu, MSBuild przeszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="0cbe7-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="0cbe7-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0cbe7-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0cbe7-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="0cbe7-119">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-119">Defines the build configuration.</span></span> <span data-ttu-id="0cbe7-120">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-120">The default value is `Debug`.</span></span> <span data-ttu-id="0cbe7-121">Ta opcja jest tylko wymagane podczas czyszczenia, jeśli została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0cbe7-122">[Framework](../../standard/frameworks.md) , która została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="0cbe7-123">Struktura musi być zdefiniowany w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="0cbe7-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="0cbe7-124">Jeśli struktura jest określona w czasie kompilacji, należy określić platformę, podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="0cbe7-125">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0cbe7-126">Katalog, w której są umieszczane dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="0cbe7-127">Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu danych wyjściowych, jeśli określona struktura podczas kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="0cbe7-128">Czyści folderze wyjściowym określonym środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="0cbe7-129">Jest on używany podczas [niezależna wdrożenia](../deploying/index.md#self-contained-deployments-scd) został utworzony.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0cbe7-130">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0cbe7-131">Dozwolone poziomy są q [uiet], m [najmniej], [ormal] n, d [egółowy] i diag [Diagnostyka].</span><span class="sxs-lookup"><span data-stu-id="0cbe7-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0cbe7-132">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0cbe7-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="0cbe7-133">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-133">Defines the build configuration.</span></span> <span data-ttu-id="0cbe7-134">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-134">The default value is `Debug`.</span></span> <span data-ttu-id="0cbe7-135">Ta opcja jest tylko wymagane podczas czyszczenia, jeśli została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0cbe7-136">[Framework](../../standard/frameworks.md) , która została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="0cbe7-137">Struktura musi być zdefiniowany w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="0cbe7-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="0cbe7-138">Jeśli struktura jest określona w czasie kompilacji, należy określić platformę, podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="0cbe7-139">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0cbe7-140">Katalog, w której są umieszczane dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="0cbe7-141">Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu danych wyjściowych, jeśli określona struktura podczas kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0cbe7-142">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="0cbe7-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0cbe7-143">Dozwolone poziomy są q [uiet], m [najmniej], [ormal] n, d [egółowy] i diag [Diagnostyka].</span><span class="sxs-lookup"><span data-stu-id="0cbe7-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="0cbe7-144">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0cbe7-144">Examples</span></span>

<span data-ttu-id="0cbe7-145">Czyszczenie kompilacji domyślnego projektu:</span><span class="sxs-lookup"><span data-stu-id="0cbe7-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="0cbe7-146">Wyczyść projekt, który został skompilowany przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="0cbe7-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
