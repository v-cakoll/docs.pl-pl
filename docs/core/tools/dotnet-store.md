---
title: polecenie dotnet store
description: Polecenie "dotnet store" przechowuje określone zestawy w magazynie pakietów w czasie wykonywania.
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503579"
---
# <a name="dotnet-store"></a><span data-ttu-id="e4ac5-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="e4ac5-103">dotnet store</span></span>

<span data-ttu-id="e4ac5-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="e4ac5-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e4ac5-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e4ac5-105">Name</span></span>

<span data-ttu-id="e4ac5-106">`dotnet store`- Przechowuje określone zestawy w [magazynie pakietów w czasie wykonywania](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="e4ac5-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="e4ac5-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e4ac5-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a><span data-ttu-id="e4ac5-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e4ac5-108">Description</span></span>

<span data-ttu-id="e4ac5-109">`dotnet store`przechowuje określone zestawy w [magazynie pakietów w czasie wykonywania](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="e4ac5-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="e4ac5-110">Domyślnie zestawy są zoptymalizowane dla docelowego czasu wykonywania i struktury.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="e4ac5-111">Aby uzyskać więcej informacji, zobacz temat [magazynu pakietów czasu wykonywania.](../deploying/runtime-store.md)</span><span class="sxs-lookup"><span data-stu-id="e4ac5-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="e4ac5-112">Wymagane opcje</span><span class="sxs-lookup"><span data-stu-id="e4ac5-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e4ac5-113">Określa [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e4ac5-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e4ac5-114">Platforma docelowa musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="e4ac5-115">*Plik manifestu magazynu pakietów* jest plikiem XML, który zawiera listę pakietów do przechowywania.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="e4ac5-116">Format pliku manifestu jest zgodny z formatem projektu w stylu SDK.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="e4ac5-117">W ten sposób plik projektu, który odwołuje `-m|--manifest` się do żądanych pakietów może służyć z opcją do przechowywania zestawów w magazynie pakietów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="e4ac5-118">Aby określić wiele plików manifestu, powtórz opcję i ścieżkę dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="e4ac5-119">Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e4ac5-120">[Identyfikator czasu wykonywania](../rid-catalog.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="e4ac5-121">Opcje opcjonalne</span><span class="sxs-lookup"><span data-stu-id="e4ac5-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="e4ac5-122">Określa wersję sdk .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-122">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="e4ac5-123">Ta opcja umożliwia wybranie określonej wersji framework poza `-f|--framework` ramach określonych przez opcję.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e4ac5-124">Pokazuje informacje pomocy.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e4ac5-125">Określa ścieżkę do magazynu pakietów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="e4ac5-126">Jeśli nie zostanie określony, domyślnie w podkatalogu *magazynu* katalogu instalacyjnego profilu użytkownika .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="e4ac5-127">Pomija fazę optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="e4ac5-128">Pomija generowanie symboli.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-128">Skips symbol generation.</span></span> <span data-ttu-id="e4ac5-129">Obecnie symbole można generować tylko w systemach Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e4ac5-130">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e4ac5-131">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="e4ac5-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="e4ac5-132">Katalog roboczy używany przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-132">The working directory used by the command.</span></span> <span data-ttu-id="e4ac5-133">Jeśli nie zostanie określony, używa podkatalogu *obj* bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="e4ac5-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="e4ac5-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e4ac5-134">Examples</span></span>

- <span data-ttu-id="e4ac5-135">Przechowywanie pakietów określonych w pliku projektu *packages.csproj* dla .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="e4ac5-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="e4ac5-136">Przechowuj pakiety określone w *packages.csproj* bez optymalizacji:</span><span class="sxs-lookup"><span data-stu-id="e4ac5-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="e4ac5-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4ac5-137">See also</span></span>

- [<span data-ttu-id="e4ac5-138">Magazyn pakietu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e4ac5-138">Runtime package store</span></span>](../deploying/runtime-store.md)
