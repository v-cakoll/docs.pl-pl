---
title: polecenie magazynu DotNet
description: Polecenie "dotnet magazynu" przechowuje określonych zestawów w magazynie pakietów środowiska wykonawczego.
author: bleroy
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 54654522207157f7d49bb86223b7986acccf51ee
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696328"
---
# <a name="dotnet-store"></a><span data-ttu-id="bf983-103">Magazyn DotNet</span><span class="sxs-lookup"><span data-stu-id="bf983-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="bf983-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="bf983-104">Name</span></span>

<span data-ttu-id="bf983-105">`dotnet store` -Przechowuje określonych zestawów w [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="bf983-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="bf983-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="bf983-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="bf983-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bf983-107">Description</span></span>

<span data-ttu-id="bf983-108">`dotnet store` przechowuje określonych zestawów w [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="bf983-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="bf983-109">Domyślnie zestawy są zoptymalizowane pod kątem docelowego środowiska uruchomieniowego i framework.</span><span class="sxs-lookup"><span data-stu-id="bf983-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="bf983-110">Aby uzyskać więcej informacji, zobacz [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bf983-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="bf983-111">Wymagane opcje</span><span class="sxs-lookup"><span data-stu-id="bf983-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="bf983-112">Określa [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="bf983-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="bf983-113">*Pliku manifestu sklepu pakietu* jest plik XML, który zawiera listę pakietów do przechowywania.</span><span class="sxs-lookup"><span data-stu-id="bf983-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="bf983-114">Format pliku manifestu jest zgodny z formatem projektu stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="bf983-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="bf983-115">Tak, można użyć pliku projektu, odwołujący się odpowiednie pakiety z `-m|--manifest` umożliwia przechowywanie zestawów w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="bf983-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="bf983-116">Aby określić wiele plików manifestu, powtórz opcja i ścieżki dla każdego pliku.</span><span class="sxs-lookup"><span data-stu-id="bf983-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="bf983-117">Na przykład: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="bf983-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="bf983-118">[Identyfikator środowiska uruchomieniowego](../rid-catalog.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="bf983-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="bf983-119">Dodatkowe opcje</span><span class="sxs-lookup"><span data-stu-id="bf983-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="bf983-120">Określa wersję zestawu SDK programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bf983-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="bf983-121">Ta opcja umożliwia wybranie określonych framework w wersji poza framework określona przez `-f|--framework` opcji.</span><span class="sxs-lookup"><span data-stu-id="bf983-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="bf983-122">Pokazuje informacje pomocy.</span><span class="sxs-lookup"><span data-stu-id="bf983-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="bf983-123">Określa ścieżkę do magazynu pakiet środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="bf983-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="bf983-124">Jeśli nie zostanie określony, domyślnie *przechowywania* podkatalogu w katalogu instalacji platformy .NET Core profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf983-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="bf983-125">Pomija fazy optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="bf983-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="bf983-126">Pomija Generowanie symboli.</span><span class="sxs-lookup"><span data-stu-id="bf983-126">Skips symbol generation.</span></span> <span data-ttu-id="bf983-127">Obecnie można generować tylko symbole w systemach Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="bf983-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="bf983-128">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="bf983-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bf983-129">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bf983-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="bf983-130">Katalog roboczy używany przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="bf983-130">The working directory used by the command.</span></span> <span data-ttu-id="bf983-131">Jeśli nie zostanie określony, używa *obj* podkatalog bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="bf983-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="bf983-132">Przykłady</span><span class="sxs-lookup"><span data-stu-id="bf983-132">Examples</span></span>

<span data-ttu-id="bf983-133">Przechowywania pakietów określone w *packages.csproj* pliku projektu dla platformy .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="bf983-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="bf983-134">Przechowywania pakietów określone w *packages.csproj* bez optymalizacji:</span><span class="sxs-lookup"><span data-stu-id="bf983-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="bf983-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf983-135">See also</span></span>

[<span data-ttu-id="bf983-136">Magazyn pakietu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="bf983-136">Runtime package store</span></span>](../deploying/runtime-store.md)