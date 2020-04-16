---
title: Polecenie dotnet store
description: Polecenie "dotnet store" przechowuje określone zestawy w magazynie pakietów środowiska wykonawczego.
ms.date: 02/14/2020
ms.openlocfilehash: 2f28a9bc287a87f600bda385c579e8070cbaa5ab
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463386"
---
# <a name="dotnet-store"></a><span data-ttu-id="d98ea-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d98ea-103">dotnet store</span></span>

<span data-ttu-id="d98ea-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="d98ea-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d98ea-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d98ea-105">Name</span></span>

<span data-ttu-id="d98ea-106">`dotnet store`- Przechowuje określone zestawy w [magazynie pakietów środowiska wykonawczego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="d98ea-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="d98ea-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d98ea-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest <PATH_TO_MANIFEST_FILE>
    -f|--framework <FRAMEWORK_VERSION> -r|--runtime <RUNTIME_IDENTIFIER>
    [--framework-version <FRAMEWORK_VERSION>] [--output <OUTPUT_DIRECTORY>]
    [--skip-optimization] [--skip-symbols] [-v|--verbosity <LEVEL>]
    [--working-dir <WORKING_DIRECTORY>]

dotnet store -h|--help
```

## <a name="description"></a><span data-ttu-id="d98ea-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d98ea-108">Description</span></span>

<span data-ttu-id="d98ea-109">`dotnet store`przechowuje określone zestawy w [magazynie pakietów środowiska wykonawczego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="d98ea-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="d98ea-110">Domyślnie zestawy są zoptymalizowane pod kątem docelowego środowiska uruchomieniowego i struktury.</span><span class="sxs-lookup"><span data-stu-id="d98ea-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="d98ea-111">Aby uzyskać więcej informacji, zobacz temat [magazynu pakietów środowiska wykonawczego.](../deploying/runtime-store.md)</span><span class="sxs-lookup"><span data-stu-id="d98ea-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="d98ea-112">Wymagane opcje</span><span class="sxs-lookup"><span data-stu-id="d98ea-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d98ea-113">Określa [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d98ea-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d98ea-114">Struktura docelowa musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d98ea-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="d98ea-115">*Plik manifestu magazynu pakietów* jest plikiem XML, który zawiera listę pakietów do przechowywania.</span><span class="sxs-lookup"><span data-stu-id="d98ea-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="d98ea-116">Format pliku manifestu jest zgodny z formatem projektu w stylu SDK.</span><span class="sxs-lookup"><span data-stu-id="d98ea-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="d98ea-117">Tak więc plik projektu, który odwołuje się do `-m|--manifest` żądanych pakietów może służyć z opcją do przechowywania zestawów w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="d98ea-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="d98ea-118">Aby określić wiele plików manifestu, powtórz opcję i ścieżkę dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="d98ea-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="d98ea-119">Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="d98ea-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="d98ea-120">[Identyfikator środowiska wykonawczego](../rid-catalog.md) do docelowego.</span><span class="sxs-lookup"><span data-stu-id="d98ea-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="d98ea-121">Opcje opcjonalne</span><span class="sxs-lookup"><span data-stu-id="d98ea-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="d98ea-122">Określa wersję SDK rdzenia .NET.</span><span class="sxs-lookup"><span data-stu-id="d98ea-122">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="d98ea-123">Ta opcja umożliwia wybranie określonej wersji framework `-f|--framework` poza strukturą określoną przez tę opcję.</span><span class="sxs-lookup"><span data-stu-id="d98ea-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d98ea-124">Pokazuje informacje o pomocy.</span><span class="sxs-lookup"><span data-stu-id="d98ea-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d98ea-125">Określa ścieżkę do magazynu pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="d98ea-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="d98ea-126">Jeśli nie zostanie określony, domyślnie jest to podkatalog *magazynu* katalogu instalacyjnego profilu użytkownika .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d98ea-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="d98ea-127">Pomija fazę optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="d98ea-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="d98ea-128">Pomija generowanie symboli.</span><span class="sxs-lookup"><span data-stu-id="d98ea-128">Skips symbol generation.</span></span> <span data-ttu-id="d98ea-129">Obecnie symbole można generować tylko w systemach Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="d98ea-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d98ea-130">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="d98ea-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d98ea-131">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="d98ea-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="d98ea-132">Katalog roboczy używany przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="d98ea-132">The working directory used by the command.</span></span> <span data-ttu-id="d98ea-133">Jeśli nie zostanie określony, używa podkatalogu *obj* bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="d98ea-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="d98ea-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d98ea-134">Examples</span></span>

- <span data-ttu-id="d98ea-135">Przechowuj pakiety określone w pliku projektu *packages.csproj* dla .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="d98ea-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="d98ea-136">Przechowuj pakiety określone w *pliku packages.csproj* bez optymalizacji:</span><span class="sxs-lookup"><span data-stu-id="d98ea-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="d98ea-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d98ea-137">See also</span></span>

- [<span data-ttu-id="d98ea-138">Magazyn pakietu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d98ea-138">Runtime package store</span></span>](../deploying/runtime-store.md)
