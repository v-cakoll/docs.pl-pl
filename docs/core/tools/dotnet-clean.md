---
title: polecenie dotnet clean
description: Polecenie dotnet clean czyści bieżący katalog.
ms.date: 02/14/2020
ms.openlocfilehash: 186f1ea07718a8e178f88c3d079cf6e2f1f8660b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503755"
---
# <a name="dotnet-clean"></a><span data-ttu-id="1f6d9-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="1f6d9-103">dotnet clean</span></span>

<span data-ttu-id="1f6d9-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="1f6d9-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1f6d9-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1f6d9-105">Name</span></span>

<span data-ttu-id="1f6d9-106">`dotnet clean`- Czyści wyniki projektu.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1f6d9-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="1f6d9-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="1f6d9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="1f6d9-108">Description</span></span>

<span data-ttu-id="1f6d9-109">Polecenie `dotnet clean` czyści dane wyjściowe poprzedniej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="1f6d9-110">Jest implementowany jako [cel MSBuild,](/visualstudio/msbuild/msbuild-targets)więc projekt jest oceniany po uruchomieniu polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="1f6d9-111">Tylko dane wyjściowe utworzone podczas kompilacji są czyszczone.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="1f6d9-112">Wyczyszczone są zarówno foldery pośrednie *(obj),* jak i końcowe *(bin).*</span><span class="sxs-lookup"><span data-stu-id="1f6d9-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="1f6d9-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="1f6d9-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="1f6d9-114">Projekt MSBuild lub rozwiązanie do czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="1f6d9-115">Jeśli plik projektu lub rozwiązania nie jest określony, MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, który kończy się *proj* lub *sln*i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="1f6d9-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="1f6d9-116">Options</span></span>

* **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="1f6d9-117">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-117">Defines the build configuration.</span></span> <span data-ttu-id="1f6d9-118">Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-118">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span> <span data-ttu-id="1f6d9-119">Ta opcja jest wymagana tylko podczas czyszczenia, jeśli została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="1f6d9-120">[Struktura,](../../standard/frameworks.md) która została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="1f6d9-121">Struktura musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="1f6d9-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="1f6d9-122">Jeśli określono framework w czasie kompilacji, należy określić struktury podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="1f6d9-123">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="1f6d9-124">Umożliwia zatrzymanie polecenia i oczekiwanie na wejście użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="1f6d9-125">Na przykład, aby zakończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-125">For example, to complete authentication.</span></span> <span data-ttu-id="1f6d9-126">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="1f6d9-127">Nie wyświetla banera startowego ani wiadomości o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="1f6d9-128">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="1f6d9-129">Katalog, który zawiera artefakty kompilacji do czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="1f6d9-130">Określ `-f|--framework <FRAMEWORK>` przełącznik za pomocą przełącznika katalogu wyjściowego, jeśli określono strukturę podczas budowy projektu.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="1f6d9-131">Czyści folder wyjściowy określonego czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="1f6d9-132">Jest to używane podczas tworzenia [samodzielnego wdrażania.](../deploying/index.md#publish-self-contained)</span><span class="sxs-lookup"><span data-stu-id="1f6d9-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="1f6d9-133">Ustawia poziom szczegółowości MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-133">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="1f6d9-134">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="1f6d9-134">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1f6d9-135">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="1f6d9-135">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="1f6d9-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="1f6d9-136">Examples</span></span>

* <span data-ttu-id="1f6d9-137">Wyczyść domyślną kompilację projektu:</span><span class="sxs-lookup"><span data-stu-id="1f6d9-137">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="1f6d9-138">Czyszczenie projektu utworzonego przy użyciu konfiguracji wersji:</span><span class="sxs-lookup"><span data-stu-id="1f6d9-138">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
