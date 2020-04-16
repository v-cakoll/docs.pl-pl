---
title: polecenie dotnet clean
description: Polecenie dotnet clean czyści bieżący katalog.
ms.date: 02/14/2020
ms.openlocfilehash: a59922feba75e940a5cee2dfeb500f4f86372870
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463700"
---
# <a name="dotnet-clean"></a><span data-ttu-id="2e2fc-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="2e2fc-103">dotnet clean</span></span>

<span data-ttu-id="2e2fc-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="2e2fc-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2e2fc-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2e2fc-105">Name</span></span>

<span data-ttu-id="2e2fc-106">`dotnet clean`- Czyści wyniki projektu.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2e2fc-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2e2fc-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--interactive]
    [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]

dotnet clean -h|--help
```

## <a name="description"></a><span data-ttu-id="2e2fc-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2e2fc-108">Description</span></span>

<span data-ttu-id="2e2fc-109">Polecenie `dotnet clean` czyści dane wyjściowe poprzedniej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="2e2fc-110">Jest implementowany jako [obiekt docelowy MSBuild,](/visualstudio/msbuild/msbuild-targets)więc projekt jest oceniany po uruchomieniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="2e2fc-111">Tylko dane wyjściowe utworzone podczas kompilacji są czyszczone.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="2e2fc-112">Czyszczone są zarówno foldery pośrednie (*obj)* jak i końcowe wyjście *(bin).*</span><span class="sxs-lookup"><span data-stu-id="2e2fc-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="2e2fc-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2e2fc-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="2e2fc-114">Projekt LUB rozwiązanie MSBuild do czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="2e2fc-115">Jeśli plik projektu lub rozwiązania nie jest określony, MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, które kończy się *proj* lub *sln*i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="2e2fc-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="2e2fc-116">Options</span></span>

* **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="2e2fc-117">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-117">Defines the build configuration.</span></span> <span data-ttu-id="2e2fc-118">Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-118">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span> <span data-ttu-id="2e2fc-119">Ta opcja jest wymagana tylko podczas czyszczenia, jeśli określono ją w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="2e2fc-120">[Struktura,](../../standard/frameworks.md) która została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="2e2fc-121">Struktura musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="2e2fc-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="2e2fc-122">Jeśli określono strukturę w czasie kompilacji, należy określić strukturę podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="2e2fc-123">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="2e2fc-124">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="2e2fc-125">Na przykład, aby zakończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-125">For example, to complete authentication.</span></span> <span data-ttu-id="2e2fc-126">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="2e2fc-127">Nie wyświetla banera startowego ani wiadomości o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="2e2fc-128">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="2e2fc-129">Katalog, który zawiera artefakty kompilacji do czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="2e2fc-130">Określ `-f|--framework <FRAMEWORK>` przełącznik z przełącznikiem katalogu wyjściowego, jeśli określono strukturę podczas budowy projektu.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="2e2fc-131">Czyści folder wyjściowy określonego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="2e2fc-132">Jest to używane podczas tworzenia [samodzielnego wdrożenia.](../deploying/index.md#publish-self-contained)</span><span class="sxs-lookup"><span data-stu-id="2e2fc-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2e2fc-133">Ustawia poziom szczegółowości MSBuild.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-133">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="2e2fc-134">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="2e2fc-134">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2e2fc-135">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="2e2fc-135">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="2e2fc-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2e2fc-136">Examples</span></span>

* <span data-ttu-id="2e2fc-137">Czyszczenie domyślnej kompilacji projektu:</span><span class="sxs-lookup"><span data-stu-id="2e2fc-137">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="2e2fc-138">Czyszczenie projektu utworzonego przy użyciu konfiguracji release:</span><span class="sxs-lookup"><span data-stu-id="2e2fc-138">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
