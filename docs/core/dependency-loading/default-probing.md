---
title: Sondowanie domyślne — .NET Core
description: Omówienie .NET Core's System.Runtime.Loader.AssemblyLoadContext.Default sondowania logiki, aby zlokalizować zależności.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399092"
---
# <a name="default-probing"></a><span data-ttu-id="8022b-103">Sondowanie domyślne</span><span class="sxs-lookup"><span data-stu-id="8022b-103">Default probing</span></span>

<span data-ttu-id="8022b-104">Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> jest odpowiedzialny za lokalizowanie zależności zestawu.</span><span class="sxs-lookup"><span data-stu-id="8022b-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="8022b-105">W tym <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> artykule opisano logikę sondowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8022b-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="8022b-106">Host skonfigurowane właściwości sondowania</span><span class="sxs-lookup"><span data-stu-id="8022b-106">Host configured probing properties</span></span>

<span data-ttu-id="8022b-107">Po uruchomieniu czasu uruchomieniowego host akcesoryjna udostępnia <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zestaw nazwanych właściwości sondowania, które konfigurują ścieżki sondowania.</span><span class="sxs-lookup"><span data-stu-id="8022b-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="8022b-108">Każda właściwość sondowania jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8022b-108">Each probing property is optional.</span></span> <span data-ttu-id="8022b-109">Jeśli jest obecny, każda właściwość jest wartością ciągu, która zawiera rozdzieloną listę ścieżek bezwzględnych.</span><span class="sxs-lookup"><span data-stu-id="8022b-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="8022b-110">Ogranicznik jest ';' w systemie Windows i ':' na wszystkich innych platformach.</span><span class="sxs-lookup"><span data-stu-id="8022b-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="8022b-111">Nazwa właściwości</span><span class="sxs-lookup"><span data-stu-id="8022b-111">Property Name</span></span>                 |<span data-ttu-id="8022b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8022b-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="8022b-113">Lista ścieżek plików zestawów platform i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8022b-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="8022b-114">Lista ścieżek katalogów do wyszukiwania zestawów zasobów satelitarnych.</span><span class="sxs-lookup"><span data-stu-id="8022b-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="8022b-115">Lista ścieżek katalogów do wyszukiwania bibliotek niezarządzanych (natywnych).</span><span class="sxs-lookup"><span data-stu-id="8022b-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="8022b-116">Lista ścieżek katalogów do wyszukiwania zestawów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="8022b-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="8022b-117">Lista ścieżek katalogów do wyszukiwania obrazów macierzystych zestawów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="8022b-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="8022b-118">Jak są wypełniane właściwości?</span><span class="sxs-lookup"><span data-stu-id="8022b-118">How are the properties populated?</span></span>

<span data-ttu-id="8022b-119">Istnieją dwa główne scenariusze wypełniania właściwości w zależności od tego, czy istnieje plik \* \<myapp>.deps.json.\*</span><span class="sxs-lookup"><span data-stu-id="8022b-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="8022b-120">Gdy plik \* \*.deps.json\* jest obecny, jest analizowany, aby wypełnić właściwości sondowania.</span><span class="sxs-lookup"><span data-stu-id="8022b-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="8022b-121">Gdy plik \* \*.deps.json\* nie jest obecny, przyjmuje się, że katalog aplikacji zawiera wszystkie zależności.</span><span class="sxs-lookup"><span data-stu-id="8022b-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="8022b-122">Zawartość katalogu służy do wypełniania właściwości sondowania.</span><span class="sxs-lookup"><span data-stu-id="8022b-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="8022b-123">Ponadto pliki \* \*.deps.json\* dla wszelkich struktur, do których istnieje odwołanie, są podobnie analizowane.</span><span class="sxs-lookup"><span data-stu-id="8022b-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="8022b-124">Na koniec `ADDITIONAL_DEPS` zmienna środowiskowa może służyć do dodawania dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="8022b-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="8022b-125">Jak wyświetlić właściwości sondowania z kodu zarządzanego?</span><span class="sxs-lookup"><span data-stu-id="8022b-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="8022b-126">Każda właściwość jest dostępna <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> przez wywołanie funkcji z nazwą właściwości z powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8022b-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="8022b-127">Jak debugować konstrukcję właściwości sondowania?</span><span class="sxs-lookup"><span data-stu-id="8022b-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="8022b-128">Host środowiska uruchomieniowego .NET Core wygeneruje przydatne komunikaty śledzenia, gdy pewne zmienne środowiskowe są włączone:</span><span class="sxs-lookup"><span data-stu-id="8022b-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="8022b-129">Zmienna środowiskowa</span><span class="sxs-lookup"><span data-stu-id="8022b-129">Environment Variable</span></span>        |<span data-ttu-id="8022b-130">Opis</span><span class="sxs-lookup"><span data-stu-id="8022b-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="8022b-131">Umożliwia śledzenie.</span><span class="sxs-lookup"><span data-stu-id="8022b-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="8022b-132">Ślady do ścieżki pliku zamiast `stderr`domyślnej .</span><span class="sxs-lookup"><span data-stu-id="8022b-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="8022b-133">Ustawia szczegółowość od 1 (najniższa) do 4 (najwyższa).</span><span class="sxs-lookup"><span data-stu-id="8022b-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="8022b-134">Domyślne sondowanie zestawu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="8022b-134">Managed assembly default probing</span></span>

<span data-ttu-id="8022b-135">Podczas sondowania w celu zlokalizowania zarządzanego <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zestawu, wygląda w kolejności na:</span><span class="sxs-lookup"><span data-stu-id="8022b-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="8022b-136">Pliki pasujące <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` do in (po usunięciu rozszerzeń plików).</span><span class="sxs-lookup"><span data-stu-id="8022b-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="8022b-137">Pliki natywnego zestawu obrazów `APP_NI_PATHS` ze wspólnymi rozszerzeniami plików.</span><span class="sxs-lookup"><span data-stu-id="8022b-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="8022b-138">Pliki zestawów `APP_PATHS` ze wspólnymi rozszerzeniami plików.</span><span class="sxs-lookup"><span data-stu-id="8022b-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="8022b-139">Sondowanie zestawu satelitarnego (zasobu)</span><span class="sxs-lookup"><span data-stu-id="8022b-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="8022b-140">Aby znaleźć zestaw satelicki dla określonej kultury, skonstruować zestaw ścieżek plików.</span><span class="sxs-lookup"><span data-stu-id="8022b-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="8022b-141">Dla każdej `PLATFORM_RESOURCE_ROOTS` ścieżki `APP_PATHS`w i <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> następnie dołączaciąg, separator katalogu, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> ciąg i rozszerzenie '.dll'.</span><span class="sxs-lookup"><span data-stu-id="8022b-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="8022b-142">Jeśli istnieje dowolny pasujący plik, spróbuj go załadować i zwrócić.</span><span class="sxs-lookup"><span data-stu-id="8022b-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="8022b-143">Sondowanie biblioteki niezarządzanej (natywnej)</span><span class="sxs-lookup"><span data-stu-id="8022b-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="8022b-144">Podczas sondowania w celu zlokalizowania `NATIVE_DLL_SEARCH_DIRECTORIES` biblioteki niezarządzanej przeszukiwane są wyszukiwane w poszukiwaniu pasującej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="8022b-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
