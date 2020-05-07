---
title: Domyślna sondowanie — .NET Core
description: Omówienie elementu System. Runtime. Loader. AssemblyLoadContext. default sondowania w celu lokalizowania zależności.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 1e347c716c2d739a1bd03be056b57fdbda6c678f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859513"
---
# <a name="default-probing"></a><span data-ttu-id="fe045-103">Domyślna sonda</span><span class="sxs-lookup"><span data-stu-id="fe045-103">Default probing</span></span>

<span data-ttu-id="fe045-104"><xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Wystąpienie jest odpowiedzialne za lokalizowanie zależności zestawu.</span><span class="sxs-lookup"><span data-stu-id="fe045-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="fe045-105">W <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> tym artykule opisano logikę sondowania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fe045-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="fe045-106">Host skonfigurował właściwości sondowania</span><span class="sxs-lookup"><span data-stu-id="fe045-106">Host configured probing properties</span></span>

<span data-ttu-id="fe045-107">Po uruchomieniu środowiska uruchomieniowego host środowiska uruchomieniowego udostępnia zestaw nazwanych właściwości, które konfigurują <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> ścieżki sondy.</span><span class="sxs-lookup"><span data-stu-id="fe045-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="fe045-108">Każda właściwość sondowania jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="fe045-108">Each probing property is optional.</span></span> <span data-ttu-id="fe045-109">Jeśli jest obecny, Każda właściwość jest wartością ciągu, która zawiera rozdzielaną listę ścieżek bezwzględnych.</span><span class="sxs-lookup"><span data-stu-id="fe045-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="fe045-110">Ogranicznik to ";" w systemie Windows i ":" na wszystkich innych platformach.</span><span class="sxs-lookup"><span data-stu-id="fe045-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="fe045-111">Nazwa właściwości</span><span class="sxs-lookup"><span data-stu-id="fe045-111">Property Name</span></span>                 |<span data-ttu-id="fe045-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fe045-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="fe045-113">Lista ścieżek plików zestawu platformy i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe045-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="fe045-114">Lista ścieżek katalogów do wyszukiwania zestawów zasobów satelity.</span><span class="sxs-lookup"><span data-stu-id="fe045-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="fe045-115">Lista ścieżek katalogów do wyszukiwania niezarządzanych (natywnych) bibliotek.</span><span class="sxs-lookup"><span data-stu-id="fe045-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="fe045-116">Lista ścieżek katalogów do wyszukiwania zestawów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="fe045-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="fe045-117">Lista ścieżek katalogów do wyszukiwania natywnych obrazów zestawów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="fe045-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="fe045-118">Jak są wypełniane właściwości?</span><span class="sxs-lookup"><span data-stu-id="fe045-118">How are the properties populated?</span></span>

<span data-ttu-id="fe045-119">Istnieją dwa główne scenariusze wypełniania właściwości w zależności od tego, \* \<czy istnieje plik MojaApl>. deps. JSON\* .</span><span class="sxs-lookup"><span data-stu-id="fe045-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="fe045-120">Gdy plik \* \*. deps. JSON\* jest obecny, jest analizowany w celu wypełnienia właściwości sondowania.</span><span class="sxs-lookup"><span data-stu-id="fe045-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="fe045-121">Gdy plik \* \*. deps. JSON\* nie istnieje, zakłada się, że katalog aplikacji zawiera wszystkie zależności.</span><span class="sxs-lookup"><span data-stu-id="fe045-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="fe045-122">Zawartość katalogu służy do wypełniania właściwości sondowania.</span><span class="sxs-lookup"><span data-stu-id="fe045-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="fe045-123">Ponadto pliki \* \*. deps. JSON\* dla wszystkich platform, do których istnieją odwołania, są podobnie analizowane.</span><span class="sxs-lookup"><span data-stu-id="fe045-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="fe045-124">Na koniec zmienna `ADDITIONAL_DEPS` środowiskowa może służyć do dodawania dodatkowych zależności.</span><span class="sxs-lookup"><span data-stu-id="fe045-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>

<span data-ttu-id="fe045-125">Właściwości `APP_PATHS` i `APP_NI_PATHS` nie są domyślnie wypełniane i pomijane w przypadku większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fe045-125">The `APP_PATHS` and `APP_NI_PATHS` properties are not populated by default and are omitted for most applications.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="fe045-126">Jak mogę wyświetlić właściwości sondowania z kodu zarządzanego?</span><span class="sxs-lookup"><span data-stu-id="fe045-126">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="fe045-127">Każda właściwość jest dostępna przez wywołanie <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> funkcji z nazwą właściwości z powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="fe045-127">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="fe045-128">Jak mogę debugować konstrukcję właściwości sondowania?</span><span class="sxs-lookup"><span data-stu-id="fe045-128">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="fe045-129">Host środowiska uruchomieniowego platformy .NET Core będzie wyprowadzać przydatne komunikaty śledzenia, gdy są włączone pewne zmienne środowiskowe:</span><span class="sxs-lookup"><span data-stu-id="fe045-129">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="fe045-130">Zmienna środowiskowa</span><span class="sxs-lookup"><span data-stu-id="fe045-130">Environment Variable</span></span>        |<span data-ttu-id="fe045-131">Opis</span><span class="sxs-lookup"><span data-stu-id="fe045-131">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="fe045-132">Włącza śledzenie.</span><span class="sxs-lookup"><span data-stu-id="fe045-132">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="fe045-133">Ślady do ścieżki pliku zamiast wartości domyślnej `stderr`.</span><span class="sxs-lookup"><span data-stu-id="fe045-133">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="fe045-134">Ustawia poziom szczegółowości od 1 (najniższy) do 4 (najwyższy).</span><span class="sxs-lookup"><span data-stu-id="fe045-134">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="fe045-135">Domyślna sondowanie zestawu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="fe045-135">Managed assembly default probing</span></span>

<span data-ttu-id="fe045-136">Podczas sondowania w celu zlokalizowania zestawu zarządzanego <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> wygląd wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="fe045-136">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="fe045-137">Pliki pasujące <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> do `TRUSTED_PLATFORM_ASSEMBLIES` programu (po usunięciu rozszerzeń plików).</span><span class="sxs-lookup"><span data-stu-id="fe045-137">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="fe045-138">Pliki zestawu obrazów natywnych `APP_NI_PATHS` w programie ze wspólnymi rozszerzeniami plików.</span><span class="sxs-lookup"><span data-stu-id="fe045-138">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="fe045-139">Pliki zestawów w `APP_PATHS` programie ze wspólnymi rozszerzeniami plików.</span><span class="sxs-lookup"><span data-stu-id="fe045-139">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="fe045-140">Sonda zestawu (zasobów) dla satelity</span><span class="sxs-lookup"><span data-stu-id="fe045-140">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="fe045-141">Aby znaleźć zestaw satelicki dla określonej kultury, należy utworzyć zestaw ścieżek plików.</span><span class="sxs-lookup"><span data-stu-id="fe045-141">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="fe045-142">Dla każdej ścieżki w `PLATFORM_RESOURCE_ROOTS` , a `APP_PATHS`następnie Dołącz <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> ciąg, separator katalogu, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> ciąg i rozszerzenie ". dll".</span><span class="sxs-lookup"><span data-stu-id="fe045-142">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="fe045-143">Jeśli istnieje odpowiedni plik, spróbuj załadować i zwrócić go.</span><span class="sxs-lookup"><span data-stu-id="fe045-143">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="fe045-144">Badanie biblioteki niezarządzanej (natywnej)</span><span class="sxs-lookup"><span data-stu-id="fe045-144">Unmanaged (native) library probing</span></span>

<span data-ttu-id="fe045-145">Podczas sondowania w celu zlokalizowania biblioteki niezarządzanej `NATIVE_DLL_SEARCH_DIRECTORIES` są one przeszukiwane w poszukiwaniu zgodnej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="fe045-145">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
