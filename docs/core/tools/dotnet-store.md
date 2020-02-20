---
title: polecenie magazynu dotnet
description: Polecenie "Sklep dotnet" przechowuje określone zestawy w magazynie pakietów środowiska uruchomieniowego.
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503579"
---
# <a name="dotnet-store"></a><span data-ttu-id="99ded-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="99ded-103">dotnet store</span></span>

<span data-ttu-id="99ded-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="99ded-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="99ded-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="99ded-105">Name</span></span>

<span data-ttu-id="99ded-106">`dotnet store` — przechowuje określone zestawy w [magazynie pakietów środowiska uruchomieniowego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="99ded-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="99ded-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="99ded-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a><span data-ttu-id="99ded-108">Opis</span><span class="sxs-lookup"><span data-stu-id="99ded-108">Description</span></span>

<span data-ttu-id="99ded-109">`dotnet store` przechowuje określone zestawy w [magazynie pakietów środowiska uruchomieniowego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="99ded-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="99ded-110">Domyślnie zestawy są zoptymalizowane pod kątem docelowego środowiska uruchomieniowego i struktury.</span><span class="sxs-lookup"><span data-stu-id="99ded-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="99ded-111">Aby uzyskać więcej informacji, zobacz temat [Magazyn pakietów środowiska uruchomieniowego](../deploying/runtime-store.md) .</span><span class="sxs-lookup"><span data-stu-id="99ded-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="99ded-112">Wymagane opcje</span><span class="sxs-lookup"><span data-stu-id="99ded-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="99ded-113">Określa [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="99ded-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="99ded-114">W pliku projektu należy określić platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="99ded-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="99ded-115">*Plik manifestu magazynu pakietów* to plik XML zawierający listę pakietów do przechowywania.</span><span class="sxs-lookup"><span data-stu-id="99ded-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="99ded-116">Format pliku manifestu jest zgodny z formatem projektu w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="99ded-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="99ded-117">Dlatego plik projektu, który odwołuje się do żądanych pakietów, może być używany z opcją `-m|--manifest`, aby przechowywać zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="99ded-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="99ded-118">Aby określić wiele plików manifestu, powtórz opcję i ścieżkę dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="99ded-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="99ded-119">Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="99ded-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="99ded-120">[Identyfikator środowiska uruchomieniowego](../rid-catalog.md) dla elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="99ded-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="99ded-121">Opcje opcjonalne</span><span class="sxs-lookup"><span data-stu-id="99ded-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="99ded-122">Określa wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="99ded-122">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="99ded-123">Ta opcja umożliwia wybranie określonej wersji struktury poza strukturą określoną przez opcję `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="99ded-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="99ded-124">Wyświetla informacje pomocy.</span><span class="sxs-lookup"><span data-stu-id="99ded-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="99ded-125">Określa ścieżkę do magazynu pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="99ded-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="99ded-126">Jeśli nie zostanie określony, domyślnie jest to podkatalog *sklepu* w katalogu instalacyjnym programu .NET Core profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99ded-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="99ded-127">Pomija fazę optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="99ded-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="99ded-128">Pomija generowanie symboli.</span><span class="sxs-lookup"><span data-stu-id="99ded-128">Skips symbol generation.</span></span> <span data-ttu-id="99ded-129">Obecnie można generować tylko symbole w systemach Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="99ded-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="99ded-130">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="99ded-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="99ded-131">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="99ded-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="99ded-132">Katalog roboczy używany przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="99ded-132">The working directory used by the command.</span></span> <span data-ttu-id="99ded-133">Jeśli nie zostanie określony, używa podkatalogu *obj* w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="99ded-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="99ded-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="99ded-134">Examples</span></span>

- <span data-ttu-id="99ded-135">Przechowuj pakiety określone w pliku projektu *Packages. csproj* dla programu .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="99ded-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="99ded-136">Przechowuj pakiety określone w *Packages. csproj* bez optymalizacji:</span><span class="sxs-lookup"><span data-stu-id="99ded-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="99ded-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99ded-137">See also</span></span>

- [<span data-ttu-id="99ded-138">Magazyn pakietu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="99ded-138">Runtime package store</span></span>](../deploying/runtime-store.md)
