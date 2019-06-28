---
title: czyszczenie polecenia DotNet
description: Polecenia dotnet clean czyści bieżącego katalogu.
ms.date: 06/26/2019
ms.openlocfilehash: 36630c046ff8f1ad8d513b4e64cfb74a8625776b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422016"
---
# <a name="dotnet-clean"></a><span data-ttu-id="74e77-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="74e77-103">dotnet clean</span></span>

<span data-ttu-id="74e77-104">**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="74e77-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="74e77-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="74e77-105">Name</span></span>

<span data-ttu-id="74e77-106">`dotnet clean` -Czyści dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="74e77-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="74e77-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="74e77-107">Synopsis</span></span>

```
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] 
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="74e77-108">Opis</span><span class="sxs-lookup"><span data-stu-id="74e77-108">Description</span></span>

<span data-ttu-id="74e77-109">`dotnet clean` Polecenia czyści dane wyjściowe poprzednią kompilację.</span><span class="sxs-lookup"><span data-stu-id="74e77-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="74e77-110">Jest implementowany jako [programu MSBuild](/visualstudio/msbuild/msbuild-targets), więc projekt jest oceniany, jeśli polecenie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="74e77-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="74e77-111">Tylko dane wyjściowe, utworzony podczas kompilacji są czyszczone.</span><span class="sxs-lookup"><span data-stu-id="74e77-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="74e77-112">Zarówno pośredni (*obj*) i końcowych danych wyjściowych (*bin*) foldery zostały wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="74e77-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="74e77-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="74e77-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="74e77-114">Projektu programu MSBuild lub rozwiązanie do czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="74e77-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="74e77-115">Jeśli nie określono pliku projektu lub rozwiązania, MSBuild przeszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* lub *sln*oraz korzysta z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="74e77-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="74e77-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="74e77-116">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="74e77-117">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="74e77-117">Defines the build configuration.</span></span> <span data-ttu-id="74e77-118">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="74e77-118">The default value is `Debug`.</span></span> <span data-ttu-id="74e77-119">Ta opcja jest tylko wymagane podczas czyszczenia, jeśli została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="74e77-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="74e77-120">[Framework](../../standard/frameworks.md) , która została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="74e77-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="74e77-121">Struktura musi być zdefiniowany w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="74e77-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="74e77-122">Jeśli struktura jest określona w czasie kompilacji, należy określić platformę, podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="74e77-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="74e77-123">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="74e77-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="74e77-124">Umożliwia polecenie, aby zatrzymać i czeka na dane wejściowe użytkownika lub akcji.</span><span class="sxs-lookup"><span data-stu-id="74e77-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="74e77-125">Na przykład w celu ukończenia uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="74e77-125">For example, to complete authentication.</span></span> <span data-ttu-id="74e77-126">Dostępne, ponieważ .NET Core SDK w wersji 3.0.</span><span class="sxs-lookup"><span data-stu-id="74e77-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="74e77-127">Nie wyświetla transparentu lub komunikat o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="74e77-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="74e77-128">Dostępne, ponieważ .NET Core SDK w wersji 3.0.</span><span class="sxs-lookup"><span data-stu-id="74e77-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="74e77-129">Katalog, który zawiera artefaktów kompilacji, aby wyczyścić.</span><span class="sxs-lookup"><span data-stu-id="74e77-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="74e77-130">Określ `-f|--framework <FRAMEWORK>` przełącznika z przełącznikiem katalogu danych wyjściowych, jeśli określona struktura podczas kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="74e77-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="74e77-131">Czyści folderze wyjściowym określonym środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="74e77-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="74e77-132">Jest on używany podczas [niezależna wdrożenia](../deploying/index.md#self-contained-deployments-scd) został utworzony.</span><span class="sxs-lookup"><span data-stu-id="74e77-132">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="74e77-133">Opcja dostępna od .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="74e77-133">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="74e77-134">Ustawia poziom szczegółowości MSBuild.</span><span class="sxs-lookup"><span data-stu-id="74e77-134">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="74e77-135">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="74e77-135">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="74e77-136">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="74e77-136">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="74e77-137">Przykłady</span><span class="sxs-lookup"><span data-stu-id="74e77-137">Examples</span></span>

* <span data-ttu-id="74e77-138">Czyszczenie kompilacji domyślnego projektu:</span><span class="sxs-lookup"><span data-stu-id="74e77-138">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="74e77-139">Wyczyść projekt, który został skompilowany przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="74e77-139">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```
