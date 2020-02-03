---
title: polecenie magazynu dotnet
description: Polecenie "Sklep dotnet" przechowuje określone zestawy w magazynie pakietów środowiska uruchomieniowego.
ms.date: 05/29/2018
ms.openlocfilehash: cc5b4b6160ba296e1529f006c15e238746d9e08a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733055"
---
# <a name="dotnet-store"></a><span data-ttu-id="3ddc9-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="3ddc9-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="3ddc9-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3ddc9-104">Name</span></span>

<span data-ttu-id="3ddc9-105">`dotnet store` — przechowuje określone zestawy w [magazynie pakietów środowiska uruchomieniowego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="3ddc9-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="3ddc9-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3ddc9-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="3ddc9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3ddc9-107">Description</span></span>

<span data-ttu-id="3ddc9-108">`dotnet store` przechowuje określone zestawy w [magazynie pakietów środowiska uruchomieniowego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="3ddc9-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="3ddc9-109">Domyślnie zestawy są zoptymalizowane pod kątem docelowego środowiska uruchomieniowego i struktury.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="3ddc9-110">Aby uzyskać więcej informacji, zobacz temat [Magazyn pakietów środowiska uruchomieniowego](../deploying/runtime-store.md) .</span><span class="sxs-lookup"><span data-stu-id="3ddc9-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="3ddc9-111">Wymagane opcje</span><span class="sxs-lookup"><span data-stu-id="3ddc9-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3ddc9-112">Określa [platformę docelową](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="3ddc9-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="3ddc9-113">*Plik manifestu magazynu pakietów* to plik XML zawierający listę pakietów do przechowywania.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="3ddc9-114">Format pliku manifestu jest zgodny z formatem projektu w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="3ddc9-115">Dlatego plik projektu, który odwołuje się do żądanych pakietów, może być używany z opcją `-m|--manifest`, aby przechowywać zestawy w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="3ddc9-116">Aby określić wiele plików manifestu, powtórz opcję i ścieżkę dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="3ddc9-117">Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3ddc9-118">[Identyfikator środowiska uruchomieniowego](../rid-catalog.md) dla elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="3ddc9-119">Opcje opcjonalne</span><span class="sxs-lookup"><span data-stu-id="3ddc9-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="3ddc9-120">Określa wersję zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="3ddc9-121">Ta opcja umożliwia wybranie określonej wersji struktury poza strukturą określoną przez opcję `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="3ddc9-122">Wyświetla informacje pomocy.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3ddc9-123">Określa ścieżkę do magazynu pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="3ddc9-124">Jeśli nie zostanie określony, domyślnie jest to podkatalog *sklepu* w katalogu instalacyjnym programu .NET Core profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="3ddc9-125">Pomija fazę optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="3ddc9-126">Pomija generowanie symboli.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-126">Skips symbol generation.</span></span> <span data-ttu-id="3ddc9-127">Obecnie można generować tylko symbole w systemach Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3ddc9-128">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3ddc9-129">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="3ddc9-130">Katalog roboczy używany przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-130">The working directory used by the command.</span></span> <span data-ttu-id="3ddc9-131">Jeśli nie zostanie określony, używa podkatalogu *obj* w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3ddc9-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="3ddc9-132">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3ddc9-132">Examples</span></span>

<span data-ttu-id="3ddc9-133">Przechowuj pakiety określone w pliku projektu *Packages. csproj* dla programu .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="3ddc9-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="3ddc9-134">Przechowuj pakiety określone w *Packages. csproj* bez optymalizacji:</span><span class="sxs-lookup"><span data-stu-id="3ddc9-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="3ddc9-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ddc9-135">See also</span></span>

- [<span data-ttu-id="3ddc9-136">Magazyn pakietu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3ddc9-136">Runtime package store</span></span>](../deploying/runtime-store.md)
