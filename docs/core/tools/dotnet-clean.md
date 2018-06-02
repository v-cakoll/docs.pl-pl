---
title: polecenie - .NET Core interfejsu wiersza polecenia czyszczenia DotNet
description: Polecenie Wyczyść dotnet czyści bieżącego katalogu.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 9e68781fe00590f3c8d429631a3f72d525d29fa9
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697034"
---
# <a name="dotnet-clean"></a><span data-ttu-id="13318-103">Wyczyść DotNet</span><span class="sxs-lookup"><span data-stu-id="13318-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="13318-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="13318-104">Name</span></span>

<span data-ttu-id="13318-105">`dotnet clean` -Czyści dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="13318-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="13318-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="13318-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="13318-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="13318-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="13318-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="13318-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="13318-109">Opis</span><span class="sxs-lookup"><span data-stu-id="13318-109">Description</span></span>

<span data-ttu-id="13318-110">`dotnet clean` Polecenie czyści dane wyjściowe ostatniej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13318-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="13318-111">Jest zaimplementowany jako [docelowy programu MSBuild](/visualstudio/msbuild/msbuild-targets), więc projekt jest oceniane w czasie uruchomienia polecenia.</span><span class="sxs-lookup"><span data-stu-id="13318-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="13318-112">Tylko dane wyjściowe tworzone podczas kompilacji zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="13318-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="13318-113">Zarówno pośredni (*obj*) i pliku wyjściowego (*bin*) foldery zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="13318-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="13318-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="13318-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="13318-115">Aby wyczyścić projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="13318-115">The MSBuild project to clean.</span></span> <span data-ttu-id="13318-116">Jeśli nie określono pliku projektu, MSBuild wyszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="13318-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="13318-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="13318-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="13318-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="13318-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="13318-119">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13318-119">Defines the build configuration.</span></span> <span data-ttu-id="13318-120">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="13318-120">The default value is `Debug`.</span></span> <span data-ttu-id="13318-121">Ta opcja jest tylko wymagane podczas oczyszczania, jeśli określono w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13318-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="13318-122">[Framework](../../standard/frameworks.md) , która została określona podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13318-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="13318-123">Platformę musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="13318-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="13318-124">Jeśli określono platformę w czasie kompilacji, należy określić platformę podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="13318-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="13318-125">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="13318-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="13318-126">Katalog, w którym są umieszczane dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13318-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="13318-127">Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu wyjściowego, jeśli określony platformę, gdy projekt został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="13318-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="13318-128">Czyści folderze wyjściowym określonym środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="13318-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="13318-129">Ten element jest używany podczas [niezależne wdrożenia](../deploying/index.md#self-contained-deployments-scd) został utworzony.</span><span class="sxs-lookup"><span data-stu-id="13318-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="13318-130">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="13318-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="13318-131">Dozwolone poziomy są q [uiet], [najmniej] m, n [ormal], d [egółowy] i diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="13318-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="13318-132">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="13318-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="13318-133">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13318-133">Defines the build configuration.</span></span> <span data-ttu-id="13318-134">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="13318-134">The default value is `Debug`.</span></span> <span data-ttu-id="13318-135">Ta opcja jest tylko wymagane podczas oczyszczania, jeśli określono w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13318-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="13318-136">[Framework](../../standard/frameworks.md) , która została określona podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13318-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="13318-137">Platformę musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="13318-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="13318-138">Jeśli określono platformę w czasie kompilacji, należy określić platformę podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="13318-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="13318-139">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="13318-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="13318-140">Katalog, w którym są umieszczane dane wyjściowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13318-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="13318-141">Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu wyjściowego, jeśli określony platformę, gdy projekt został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="13318-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="13318-142">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="13318-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="13318-143">Dozwolone poziomy są q [uiet], [najmniej] m, n [ormal], d [egółowy] i diag [nostic].</span><span class="sxs-lookup"><span data-stu-id="13318-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="13318-144">Przykłady</span><span class="sxs-lookup"><span data-stu-id="13318-144">Examples</span></span>

<span data-ttu-id="13318-145">Czyszczenie kompilacji domyślnego projektu:</span><span class="sxs-lookup"><span data-stu-id="13318-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="13318-146">Wyczyść projekt utworzony przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="13318-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
