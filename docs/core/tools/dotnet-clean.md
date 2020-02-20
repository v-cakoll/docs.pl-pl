---
title: polecenie "isclean" dotnet
description: Polecenie "Wyczyść" programu dotnet czyści bieżący katalog.
ms.date: 06/26/2019
ms.openlocfilehash: 715a33a8a1aa13a2a76f9d4522413dcc72e4b4aa
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451359"
---
# <a name="dotnet-clean"></a><span data-ttu-id="70a67-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="70a67-103">dotnet clean</span></span>

<span data-ttu-id="70a67-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="70a67-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="70a67-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="70a67-105">Name</span></span>

<span data-ttu-id="70a67-106">`dotnet clean` — czyści dane wyjściowe projektu.</span><span class="sxs-lookup"><span data-stu-id="70a67-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="70a67-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="70a67-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="70a67-108">Opis</span><span class="sxs-lookup"><span data-stu-id="70a67-108">Description</span></span>

<span data-ttu-id="70a67-109">Polecenie `dotnet clean` czyści dane wyjściowe poprzedniej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70a67-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="70a67-110">Jest ona zaimplementowana jako [obiekt docelowy MSBuild](/visualstudio/msbuild/msbuild-targets), dlatego projekt jest oceniany, gdy polecenie jest uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="70a67-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="70a67-111">Oczyszczone zostaną tylko dane wyjściowe utworzone podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70a67-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="70a67-112">Są czyszczone zarówno pośrednie (*obj*), jak i końcowe (*bin*) foldery wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="70a67-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="70a67-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="70a67-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="70a67-114">Projekt programu MSBuild lub rozwiązanie do czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="70a67-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="70a67-115">Jeśli plik projektu lub rozwiązania nie zostanie określony, program MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, które kończy się w *proj* lub *sln*, i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="70a67-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="70a67-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="70a67-116">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="70a67-117">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70a67-117">Defines the build configuration.</span></span> <span data-ttu-id="70a67-118">Wartością domyślną jest `Debug`.</span><span class="sxs-lookup"><span data-stu-id="70a67-118">The default value is `Debug`.</span></span> <span data-ttu-id="70a67-119">Ta opcja jest wymagana tylko w przypadku czyszczenia, jeśli została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70a67-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="70a67-120">[Struktura](../../standard/frameworks.md) , która została określona w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="70a67-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="70a67-121">Struktura musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="70a67-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="70a67-122">Jeśli określono strukturę w czasie kompilacji, należy określić strukturę podczas czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="70a67-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="70a67-123">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="70a67-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="70a67-124">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="70a67-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="70a67-125">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="70a67-125">For example, to complete authentication.</span></span> <span data-ttu-id="70a67-126">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="70a67-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="70a67-127">Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="70a67-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="70a67-128">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="70a67-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="70a67-129">Katalog, który zawiera artefakty kompilacji do oczyszczenia.</span><span class="sxs-lookup"><span data-stu-id="70a67-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="70a67-130">Określ przełącznik `-f|--framework <FRAMEWORK>` z przełącznikiem katalogu wyjściowego, jeśli określono strukturę podczas kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="70a67-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="70a67-131">Czyści folder wyjściowy określonego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="70a67-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="70a67-132">Ta funkcja jest używana podczas tworzenia wdrożenia z dowolnego [siebie](../deploying/index.md#publish-self-contained) .</span><span class="sxs-lookup"><span data-stu-id="70a67-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span> <span data-ttu-id="70a67-133">Opcja dostępna od wersji .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="70a67-133">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="70a67-134">Ustawia poziom szczegółowości programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="70a67-134">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="70a67-135">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="70a67-135">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="70a67-136">Wartość domyślna to `normal`.</span><span class="sxs-lookup"><span data-stu-id="70a67-136">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="70a67-137">Przykłady</span><span class="sxs-lookup"><span data-stu-id="70a67-137">Examples</span></span>

* <span data-ttu-id="70a67-138">Wyczyść domyślną kompilację projektu:</span><span class="sxs-lookup"><span data-stu-id="70a67-138">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="70a67-139">Wyczyść projekt utworzony przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="70a67-139">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
