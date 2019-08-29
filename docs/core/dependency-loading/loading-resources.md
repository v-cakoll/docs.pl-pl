---
title: Algorytm ładowania zestawu satelitarnego — .NET Core
description: Opis szczegółów algorytmu ładowania zestawu satelickiego w programie .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105315"
---
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="9315b-103">Algorytm ładowania zestawu satelitarnego</span><span class="sxs-lookup"><span data-stu-id="9315b-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="9315b-104">Zestawy satelickie są używane do przechowywania zlokalizowanych zasobów dostosowane do języka i kultury.</span><span class="sxs-lookup"><span data-stu-id="9315b-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="9315b-105">Zestawy satelickie używają innego algorytmu ładowania niż ogólne zestawy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="9315b-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="9315b-106">Kiedy są ładowane zestawy satelickie?</span><span class="sxs-lookup"><span data-stu-id="9315b-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="9315b-107">Zestawy satelickie są ładowane podczas ładowania zlokalizowanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="9315b-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="9315b-108">Podstawowy interfejs API do załadowania zlokalizowanych zasobów <xref:System.Resources.ResourceManager?displayProperty=fullName> jest klasą.</span><span class="sxs-lookup"><span data-stu-id="9315b-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="9315b-109">Ostatecznie Klasa wywoła <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> metodę dla każdej z nich <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>. <xref:System.Resources.ResourceManager></span><span class="sxs-lookup"><span data-stu-id="9315b-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="9315b-110">Interfejsy API wyższego poziomu mogą być abstrakcyjne dla interfejsu API niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="9315b-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="9315b-111">Algorytm</span><span class="sxs-lookup"><span data-stu-id="9315b-111">Algorithm</span></span>

<span data-ttu-id="9315b-112">Proces rezerwowy zasobów platformy .NET Core obejmuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="9315b-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="9315b-113">`active` Określ<xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="9315b-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="9315b-114">We wszystkich przypadkach `active` wystąpienie jest <xref:System.Runtime.Loader.AssemblyLoadContext>zestawem wykonawczym.</span><span class="sxs-lookup"><span data-stu-id="9315b-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="9315b-115">`active` Wystąpienie próbuje załadować zestaw satelicki dla wymaganej kultury w kolejności priorytetu przez:</span><span class="sxs-lookup"><span data-stu-id="9315b-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="9315b-116">Sprawdzanie jego pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="9315b-116">Checking its cache.</span></span>
    - <span data-ttu-id="9315b-117">Sprawdzanie katalogu aktualnie wykonywanego zestawu dla podkatalogu zgodnego z żądanym <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (na przykład `es-MX`).</span><span class="sxs-lookup"><span data-stu-id="9315b-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="9315b-118">Ta funkcja nie została zaimplementowana w środowisku .NET Core przed 3,0.</span><span class="sxs-lookup"><span data-stu-id="9315b-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="9315b-119">W przypadku systemu Linux i macOS w podkatalogu jest rozróżniana wielkość liter i musi to być:</span><span class="sxs-lookup"><span data-stu-id="9315b-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        > - <span data-ttu-id="9315b-120">Dokładnie dopasowanie wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="9315b-120">Exactly match case.</span></span>
        > - <span data-ttu-id="9315b-121">Małymi literami.</span><span class="sxs-lookup"><span data-stu-id="9315b-121">Be in lower case.</span></span>

    - <span data-ttu-id="9315b-122">`active` Jeśli<xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> jest wystąpieniem, uruchamiając domyślną logikę [sondowania zestawu dla satelity (zasobu)](default-probing.md#satellite-resource-assembly-probing) .</span><span class="sxs-lookup"><span data-stu-id="9315b-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="9315b-123">Wywoływanie <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> funkcji.</span><span class="sxs-lookup"><span data-stu-id="9315b-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="9315b-124">Podnoszenie <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> poziomu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9315b-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="9315b-125">Podnoszenie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> poziomu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9315b-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="9315b-126">Jeśli jest ładowany zestaw satelicki:</span><span class="sxs-lookup"><span data-stu-id="9315b-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="9315b-127"><xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> Zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="9315b-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="9315b-128">Zestaw jest przeszukiwany dla żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="9315b-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="9315b-129">Jeśli środowisko uruchomieniowe odnajdzie zasób w zestawie, użyje go.</span><span class="sxs-lookup"><span data-stu-id="9315b-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="9315b-130">Jeśli zasób nie zostanie znaleziony, będzie kontynuował wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="9315b-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9315b-131">Aby znaleźć zasób w ramach zestawu satelickiego, środowisko uruchomieniowe wyszukuje plik zasobów żądany przez <xref:System.Resources.ResourceManager> dla bieżącego. <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9315b-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9315b-132">W pliku zasobów szuka żądanej nazwy zasobu.</span><span class="sxs-lookup"><span data-stu-id="9315b-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="9315b-133">Jeśli nie zostanie znaleziony, zasób jest traktowany jako nieodnaleziony.</span><span class="sxs-lookup"><span data-stu-id="9315b-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="9315b-134">Środowisko uruchomieniowe następnym szuka zestawów kultur nadrzędnych za pomocą wielu możliwych poziomów, za każdym razem, gdy powtarzają się kroki 2 & 3.</span><span class="sxs-lookup"><span data-stu-id="9315b-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="9315b-135">Każda kultura ma tylko jeden element nadrzędny, który jest zdefiniowany przez <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="9315b-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="9315b-136">Wyszukiwanie kultur nadrzędnych jest zatrzymywane, gdy <xref:System.Globalization.CultureInfo.Parent%2A> właściwość kultury to. <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9315b-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="9315b-137">Dla programu <xref:System.Globalization.CultureInfo.InvariantCulture>nie powrócimy do kroków 2 & 3, ale należy kontynuować krok 5.</span><span class="sxs-lookup"><span data-stu-id="9315b-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="9315b-138">Jeśli zasób nadal nie zostanie znaleziony, zostanie użyta domyślna kultura (rezerwowa).</span><span class="sxs-lookup"><span data-stu-id="9315b-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="9315b-139">Zazwyczaj zasoby dla kultury domyślnej są zawarte w głównym zestawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9315b-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="9315b-140">Można jednak określić <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="9315b-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9315b-141">Ta wartość wskazuje, że ostateczna lokalizacja rezerwowa dla zasobów jest zestawem satelity, a nie głównym zestawem.</span><span class="sxs-lookup"><span data-stu-id="9315b-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9315b-142">Domyślna kultura to ostateczna rezerwa.</span><span class="sxs-lookup"><span data-stu-id="9315b-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="9315b-143">Dlatego zaleca się, aby zawsze obejmować pełny zestaw zasobów w domyślnym pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="9315b-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="9315b-144">Pomaga to zapobiegać zgłaszaniu wyjątków.</span><span class="sxs-lookup"><span data-stu-id="9315b-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="9315b-145">Mając pełny zestaw, należy podać rezerwę dla wszystkich zasobów i upewnić się, że co najmniej jeden zasób jest zawsze obecny dla użytkownika, nawet jeśli nie jest specyficzny dla kultury.</span><span class="sxs-lookup"><span data-stu-id="9315b-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="9315b-146">Ostateczny</span><span class="sxs-lookup"><span data-stu-id="9315b-146">Finally,</span></span>
   - <span data-ttu-id="9315b-147">Jeśli środowisko wykonawcze nie odnajdzie pliku zasobów dla kultury domyślnej (rezerwowej), <xref:System.Resources.MissingManifestResourceException> zostanie zgłoszony wyjątek lub. <xref:System.Resources.MissingSatelliteAssemblyException></span><span class="sxs-lookup"><span data-stu-id="9315b-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="9315b-148">Jeśli plik zasobów zostanie znaleziony, ale żądany zasób nie istnieje, żądanie zwróci wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="9315b-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>
