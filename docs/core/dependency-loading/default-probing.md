---
title: Domyślna sondowanie — .NET Core
description: Omówienie logiki sondowania platformy <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> .NET Core do lokalizowania zależności.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 2fa8a13bcb08a767fa965621f95bec8619aea5cc
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926406"
---
# <a name="default-probing"></a><span data-ttu-id="e92e2-103">Domyślna sonda</span><span class="sxs-lookup"><span data-stu-id="e92e2-103">Default probing</span></span>

<span data-ttu-id="e92e2-104"><xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Wystąpienie jest odpowiedzialne za lokalizowanie zależności zestawu.</span><span class="sxs-lookup"><span data-stu-id="e92e2-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="e92e2-105">W <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> tym artykule opisano logikę sondowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e92e2-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="e92e2-106">Host skonfigurował właściwości sondowania</span><span class="sxs-lookup"><span data-stu-id="e92e2-106">Host configured probing properties</span></span>

<span data-ttu-id="e92e2-107">Po uruchomieniu środowiska uruchomieniowego host środowiska uruchomieniowego udostępnia zestaw nazwanych właściwości, które konfigurują <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> ścieżki sondy.</span><span class="sxs-lookup"><span data-stu-id="e92e2-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="e92e2-108">Każda właściwość sondowania jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e92e2-108">Each probing property is optional.</span></span>  <span data-ttu-id="e92e2-109">Jeśli jest obecny, Każda właściwość jest wartością ciągu, która zawiera rozdzielaną listę ścieżek bezwzględnych.</span><span class="sxs-lookup"><span data-stu-id="e92e2-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="e92e2-110">Ogranicznik to ";" w systemie Windows i ":" na wszystkich innych platformach.</span><span class="sxs-lookup"><span data-stu-id="e92e2-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="e92e2-111">Nazwa właściwości</span><span class="sxs-lookup"><span data-stu-id="e92e2-111">Property Name</span></span>                 |<span data-ttu-id="e92e2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e92e2-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="e92e2-113">Lista ścieżek plików zestawu platformy i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e92e2-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="e92e2-114">Lista ścieżek katalogów do wyszukiwania zestawów zasobów satelity.</span><span class="sxs-lookup"><span data-stu-id="e92e2-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="e92e2-115">Lista ścieżek katalogów do wyszukiwania niezarządzanych (natywnych) bibliotek.</span><span class="sxs-lookup"><span data-stu-id="e92e2-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="e92e2-116">Lista ścieżek katalogów do wyszukiwania zestawów zarządzanych</span><span class="sxs-lookup"><span data-stu-id="e92e2-116">List of directory paths to search for managed assemblies</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="e92e2-117">Lista ścieżek katalogów do wyszukiwania natywnych obrazów zestawów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="e92e2-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="e92e2-118">Jak są wypełniane właściwości?</span><span class="sxs-lookup"><span data-stu-id="e92e2-118">How are the properties populated?</span></span>

<span data-ttu-id="e92e2-119">Istnieją dwa główne scenariusze wypełniania właściwości w zależności od tego, `<myapp>.deps.json` czy plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="e92e2-119">There are two main scenarios for populating the properties depending on whether the `<myapp>.deps.json` file exists.</span></span>

- <span data-ttu-id="e92e2-120">`*.deps.json` Gdy plik jest obecny, jest analizowany w celu wypełnienia właściwości sondowania.</span><span class="sxs-lookup"><span data-stu-id="e92e2-120">When the `*.deps.json` file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="e92e2-121">`*.deps.json` Gdy plik nie jest obecny, zakłada się, że katalog aplikacji zawiera wszystkie zależności.</span><span class="sxs-lookup"><span data-stu-id="e92e2-121">When the `*.deps.json` file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="e92e2-122">Zawartość katalogu służy do wypełniania właściwości sondowania.</span><span class="sxs-lookup"><span data-stu-id="e92e2-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="e92e2-123">Ponadto pliki dla `*.deps.json` dowolnych platform, do których istnieją odwołania, są podobnie analizowane.</span><span class="sxs-lookup"><span data-stu-id="e92e2-123">Additionally, the `*.deps.json` files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="e92e2-124">Na koniec zmienna `ADDITIONAL_DEPS` środowiskowa może służyć do dodawania dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="e92e2-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="e92e2-125">Jak mogę wyświetlić właściwości sondowania z kodu zarządzanego?</span><span class="sxs-lookup"><span data-stu-id="e92e2-125">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="e92e2-126">Każda właściwość jest dostępna przez wywołanie <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> funkcji z nazwą właściwości z powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e92e2-126">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="e92e2-127">Jak mogę debugować konstrukcję właściwości sondowania?</span><span class="sxs-lookup"><span data-stu-id="e92e2-127">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="e92e2-128">Host środowiska uruchomieniowego platformy .NET Core będzie wyprowadzać przydatne komunikaty śledzenia, gdy są włączone pewne zmienne środowiskowe:</span><span class="sxs-lookup"><span data-stu-id="e92e2-128">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="e92e2-129">Zmienna środowiskowa</span><span class="sxs-lookup"><span data-stu-id="e92e2-129">Environment Variable</span></span>        |<span data-ttu-id="e92e2-130">Opis</span><span class="sxs-lookup"><span data-stu-id="e92e2-130">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="e92e2-131">Włącza śledzenie.</span><span class="sxs-lookup"><span data-stu-id="e92e2-131">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="e92e2-132">Ślady do ścieżki pliku zamiast wartości domyślnej `stderr`.</span><span class="sxs-lookup"><span data-stu-id="e92e2-132">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="e92e2-133">Ustawia poziom szczegółowości od 1 (najniższy) do 4 (najwyższy).</span><span class="sxs-lookup"><span data-stu-id="e92e2-133">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="e92e2-134">Domyślna sondowanie zestawu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="e92e2-134">Managed assembly default probing</span></span>

<span data-ttu-id="e92e2-135">Podczas sondowania w celu zlokalizowania zestawu <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zarządzanego wygląd wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="e92e2-135">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="e92e2-136">Pliki pasujące <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> do `TRUSTED_PLATFORM_ASSEMBLIES` programu (po usunięciu rozszerzeń plików).</span><span class="sxs-lookup"><span data-stu-id="e92e2-136">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="e92e2-137">Pliki zestawu obrazów natywnych `APP_NI_PATHS` w programie ze wspólnymi rozszerzeniami plików.</span><span class="sxs-lookup"><span data-stu-id="e92e2-137">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="e92e2-138">Pliki zestawów w `APP_PATHS` programie ze wspólnymi rozszerzeniami plików.</span><span class="sxs-lookup"><span data-stu-id="e92e2-138">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="e92e2-139">Sonda zestawu (zasobów) dla satelity</span><span class="sxs-lookup"><span data-stu-id="e92e2-139">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="e92e2-140">Aby znaleźć zestaw satelicki dla określonej kultury, należy utworzyć zestaw ścieżek plików.</span><span class="sxs-lookup"><span data-stu-id="e92e2-140">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="e92e2-141">Dla każdej ścieżki w `PLATFORM_RESOURCE_ROOTS` , a `APP_PATHS`następnie Dołącz <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> ciąg, separator katalogu, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> ciąg i rozszerzenie ". dll".</span><span class="sxs-lookup"><span data-stu-id="e92e2-141">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="e92e2-142">Jeśli istnieje odpowiedni plik, spróbuj załadować i zwrócić go.</span><span class="sxs-lookup"><span data-stu-id="e92e2-142">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="e92e2-143">Badanie biblioteki niezarządzanej (natywnej)</span><span class="sxs-lookup"><span data-stu-id="e92e2-143">Unmanaged (native) library probing</span></span>

<span data-ttu-id="e92e2-144">Podczas sondowania w celu zlokalizowania biblioteki `NATIVE_DLL_SEARCH_DIRECTORIES` niezarządzanej są one przeszukiwane w poszukiwaniu zgodnej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e92e2-144">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library,</span></span>
