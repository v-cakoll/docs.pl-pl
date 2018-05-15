---
title: polecenie magazynu DotNet
description: Polecenie "dotnet magazynu" przechowuje określonych zestawów w magazynie pakietów środowiska wykonawczego.
author: bleroy
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: f819444c92afde0e1a5349a58918f993868a0143
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-store"></a><span data-ttu-id="6666f-103">Magazyn DotNet</span><span class="sxs-lookup"><span data-stu-id="6666f-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="6666f-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6666f-104">Name</span></span>

<span data-ttu-id="6666f-105">`dotnet store` -Przechowuje określonych zestawów w [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="6666f-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="6666f-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="6666f-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="6666f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6666f-107">Description</span></span>

<span data-ttu-id="6666f-108">`dotnet store` przechowuje określonych zestawów w [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="6666f-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="6666f-109">Domyślnie zestawy są zoptymalizowane pod kątem docelowego środowiska uruchomieniowego i framework.</span><span class="sxs-lookup"><span data-stu-id="6666f-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="6666f-110">Aby uzyskać więcej informacji, zobacz [Magazyn pakietu środowiska uruchomieniowego](../deploying/runtime-store.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="6666f-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="6666f-111">Wymagane opcje</span><span class="sxs-lookup"><span data-stu-id="6666f-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6666f-112">Określa [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6666f-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="6666f-113">*Pliku manifestu sklepu pakietu* jest plik XML, który zawiera listę pakietów do przechowywania.</span><span class="sxs-lookup"><span data-stu-id="6666f-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="6666f-114">Format pliku manifestu jest zgodny z *csproj* format.</span><span class="sxs-lookup"><span data-stu-id="6666f-114">The format of the manifest file is compatible with the *csproj* format.</span></span> <span data-ttu-id="6666f-115">Tak *csproj* pliku projektu, który odwołuje się do żądanego pakietów można używać z `-m|--manifest` umożliwia przechowywanie zestawów w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="6666f-115">So, a *csproj* project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="6666f-116">Aby określić wiele plików manifestu, należy powtórzyć dla każdego pliku opcji i ścieżka: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="6666f-116">To specify multiple manifest files, repeat the option and path for each file: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="6666f-117">[Identyfikator środowiska uruchomieniowego](../rid-catalog.md) do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="6666f-117">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="6666f-118">Dodatkowe opcje</span><span class="sxs-lookup"><span data-stu-id="6666f-118">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="6666f-119">Określa wersję zestawu SDK programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6666f-119">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="6666f-120">Ta opcja umożliwia wybranie określonych framework w wersji poza framework określona przez `-f|--framework` opcji.</span><span class="sxs-lookup"><span data-stu-id="6666f-120">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="6666f-121">Pokazuje informacje pomocy.</span><span class="sxs-lookup"><span data-stu-id="6666f-121">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="6666f-122">Określa ścieżkę do magazynu pakiet środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="6666f-122">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="6666f-123">Jeśli nie zostanie określony, domyślnie *przechowywania* podkatalogu w katalogu instalacji platformy .NET Core profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6666f-123">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="6666f-124">Pomija fazy optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="6666f-124">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="6666f-125">Pomija Generowanie symboli.</span><span class="sxs-lookup"><span data-stu-id="6666f-125">Skips symbol generation.</span></span> <span data-ttu-id="6666f-126">Obecnie można generować tylko symbole w systemach Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="6666f-126">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6666f-127">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="6666f-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6666f-128">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6666f-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="6666f-129">Katalog roboczy używany przez polecenie.</span><span class="sxs-lookup"><span data-stu-id="6666f-129">The working directory used by the command.</span></span> <span data-ttu-id="6666f-130">Jeśli nie zostanie określony, używa *obj* podkatalog bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="6666f-130">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="6666f-131">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6666f-131">Examples</span></span>

<span data-ttu-id="6666f-132">Przechowywania pakietów określone w *packages.csproj* pliku projektu dla platformy .NET Core 2.0.0:</span><span class="sxs-lookup"><span data-stu-id="6666f-132">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="6666f-133">Przechowywania pakietów określone w *packages.csproj* bez optymalizacji:</span><span class="sxs-lookup"><span data-stu-id="6666f-133">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="6666f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6666f-134">See also</span></span>

[<span data-ttu-id="6666f-135">Magazyn pakietu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6666f-135">Runtime package store</span></span>](../deploying/runtime-store.md)   
