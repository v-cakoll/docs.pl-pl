---
title: Pakuj URI w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: ad928fb223ce22c65bb86a78c7d4cd006651a2d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950756"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="a5712-102">Pakuj URI w WPF</span><span class="sxs-lookup"><span data-stu-id="a5712-102">Pack URIs in WPF</span></span>

<span data-ttu-id="a5712-103">W Windows Presentation Foundation (WPF) [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] służy do identyfikowania i ładowania plików na wiele sposobów, w tym:</span><span class="sxs-lookup"><span data-stu-id="a5712-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="a5712-104">Określenie elementu [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do wyświetlenia podczas pierwszego uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5712-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="a5712-105">Ładowanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="a5712-105">Loading images.</span></span>

- <span data-ttu-id="a5712-106">Przechodzenie do stron.</span><span class="sxs-lookup"><span data-stu-id="a5712-106">Navigating to pages.</span></span>

- <span data-ttu-id="a5712-107">Ładowanie niewykonywalnych plików danych.</span><span class="sxs-lookup"><span data-stu-id="a5712-107">Loading non-executable data files.</span></span>

<span data-ttu-id="a5712-108">Ponadto program [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] może służyć do identyfikowania i ładowania plików z różnych lokalizacji, w tym następujących:</span><span class="sxs-lookup"><span data-stu-id="a5712-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="a5712-109">Bieżący zestaw.</span><span class="sxs-lookup"><span data-stu-id="a5712-109">The current assembly.</span></span>

- <span data-ttu-id="a5712-110">Przywoływany zestaw.</span><span class="sxs-lookup"><span data-stu-id="a5712-110">A referenced assembly.</span></span>

- <span data-ttu-id="a5712-111">Lokalizacja względem zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5712-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="a5712-112">Lokacja źródłowa aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5712-112">The application's site of origin.</span></span>

<span data-ttu-id="a5712-113">Aby zapewnić spójny mechanizm do identyfikowania i ładowania tych typów plików z tych lokalizacji, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] wykorzystuje rozszerzalność *schematu identyfikatora URI pakietu*.</span><span class="sxs-lookup"><span data-stu-id="a5712-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="a5712-114">Ten temat zawiera omówienie schematu, a także informacje na [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] temat tworzenia pakietu dla różnych scenariuszy, omawiania absolutnej i względnej [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] i rozpoznawania [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] i kod.</span><span class="sxs-lookup"><span data-stu-id="a5712-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="a5712-115">Schemat identyfikatora URI pakietu</span><span class="sxs-lookup"><span data-stu-id="a5712-115">The Pack URI Scheme</span></span>

<span data-ttu-id="a5712-116">Schemat pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest używany przez specyfikację [Open](https://go.microsoft.com/fwlink/?LinkID=71255) Pack Conventions (OPC), która opisuje model służący do organizowania i identyfikowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="a5712-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="a5712-117">Kluczowymi elementami tego modelu są pakiety i części, w przypadku których *pakiet* jest kontenerem logicznym dla co najmniej jednej *części*logicznej.</span><span class="sxs-lookup"><span data-stu-id="a5712-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="a5712-118">Poniższy rysunek ilustruje tę koncepcję.</span><span class="sxs-lookup"><span data-stu-id="a5712-118">The following figure illustrates this concept.</span></span>

![Diagram pakietu i części](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="a5712-120">Aby zidentyfikować części, Specyfikacja OPC korzysta z rozszerzalności RFC 2396 (Uniform Resource Identifiers (URI): Składnia ogólna) do definiowania schematu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a5712-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>

<span data-ttu-id="a5712-121">Schemat, który jest określony przez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , jest definiowany za pomocą jego prefiksu, protokołu HTTP, FTP i pliku są dobrze znane przykłady.</span><span class="sxs-lookup"><span data-stu-id="a5712-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="a5712-122">Schemat pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] używa pakietu "Pack" jako schematu i zawiera dwa składniki: Authority i Path.</span><span class="sxs-lookup"><span data-stu-id="a5712-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="a5712-123">Poniżej przedstawiono format pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5712-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<span data-ttu-id="a5712-124">*ścieżka* *urzędu*/Pack://</span><span class="sxs-lookup"><span data-stu-id="a5712-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="a5712-125">*Urząd* określa typ pakietu, w którym znajduje się część, a *ścieżka* określa lokalizację części w ramach pakietu.</span><span class="sxs-lookup"><span data-stu-id="a5712-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="a5712-126">Pojęcie to jest zilustrowane na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="a5712-126">This concept is illustrated by the following figure:</span></span>

![Relacja między pakietem, Urzędem i ścieżką](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="a5712-128">Pakiety i części są analogiczne do aplikacji i plików, w których aplikacja (pakiet) może zawierać jeden lub więcej plików (części), w tym:</span><span class="sxs-lookup"><span data-stu-id="a5712-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="a5712-129">Pliki zasobów, które są kompilowane do zestawu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a5712-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="a5712-130">Pliki zasobów, które są kompilowane do zestawu, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="a5712-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="a5712-131">Pliki zasobów, które są kompilowane do zestawu, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="a5712-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="a5712-132">Pliki zawartości.</span><span class="sxs-lookup"><span data-stu-id="a5712-132">Content files.</span></span>

- <span data-ttu-id="a5712-133">Lokacja plików pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="a5712-133">Site of origin files.</span></span>

<span data-ttu-id="a5712-134">Aby uzyskać dostęp do tych typów plików [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , program obsługuje dwa urzędy: Application:///i siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="a5712-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="a5712-135">Urząd application:///identyfikuje pliki danych aplikacji, które są znane w czasie kompilacji, w tym pliki zasobów i zawartości.</span><span class="sxs-lookup"><span data-stu-id="a5712-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="a5712-136">Urząd siteoforigin:///określa lokację plików pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="a5712-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="a5712-137">Zakres każdego urzędu pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="a5712-137">The scope of each authority is shown in the following figure.</span></span>

![Diagram URI pakietu](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="a5712-139">Składnik urzędu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest osadzony [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , który wskazuje na pakiet i musi być zgodny ze specyfikacją RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="a5712-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="a5712-140">Ponadto znak "/" musi zostać zastąpiony znakiem "," i znakami zastrzeżonymi, takimi jak "%" i "?", należy zmienić wartość ucieczki.</span><span class="sxs-lookup"><span data-stu-id="a5712-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="a5712-141">Zobacz OPC, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="a5712-141">See the OPC for details.</span></span>

<span data-ttu-id="a5712-142">W poniższych sekcjach opisano sposób tworzenia pakietów [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] przy użyciu tych dwóch urzędów w połączeniu z odpowiednimi ścieżkami służącymi do identyfikowania zasobów, zawartości i lokacji plików pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="a5712-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="a5712-143">Identyfikatory URI pakietu plików zasobów</span><span class="sxs-lookup"><span data-stu-id="a5712-143">Resource File Pack URIs</span></span>

<span data-ttu-id="a5712-144">Pliki zasobów są konfigurowane jako elementy `Resource` programu MSBuild i są kompilowane do zestawów.</span><span class="sxs-lookup"><span data-stu-id="a5712-144">Resource files are configured as MSBuild `Resource` items and are compiled into assemblies.</span></span> <span data-ttu-id="a5712-145">WPF obsługuje konstruowanie identyfikatorów URI pakietów, których można użyć do identyfikowania plików zasobów, które są kompilowane do zestawu lokalnego lub kompilowane do zestawu, do którego odwołuje się zestaw lokalny.</span><span class="sxs-lookup"><span data-stu-id="a5712-145">WPF supports the construction of pack URIs that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="a5712-146">Plik zasobu zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="a5712-146">Local Assembly Resource File</span></span>

<span data-ttu-id="a5712-147">Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zasobów, który jest kompilowany do zestawu lokalnego, używa następującego urzędu i ścieżki:</span><span class="sxs-lookup"><span data-stu-id="a5712-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="a5712-148">**Urząd**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="a5712-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="a5712-149">**Ścieżka**: Nazwa pliku zasobów, łącznie z jego ścieżką, względem katalogu głównego lokalnego folderu projektu zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5712-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="a5712-150">W poniższym przykładzie przedstawiono pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w folderze głównym folderu projektu zestawu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a5712-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="a5712-151">Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w podfolderze folderu projektu zestawu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a5712-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="a5712-152">Przywoływany plik zasobu zestawu</span><span class="sxs-lookup"><span data-stu-id="a5712-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="a5712-153">Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zasobów, który jest kompilowany do zestawu, do którego istnieje odwołanie, używa następującego urzędu i ścieżki:</span><span class="sxs-lookup"><span data-stu-id="a5712-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="a5712-154">**Urząd**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="a5712-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="a5712-155">**Ścieżka**: Nazwa pliku zasobów, który jest kompilowany do przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5712-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="a5712-156">Ścieżka musi być zgodna z następującym formatem:</span><span class="sxs-lookup"><span data-stu-id="a5712-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="a5712-157">*AssemblyShortName* { *; Wersja*] { *; PublicKey*]; składnik/*ścieżka*</span><span class="sxs-lookup"><span data-stu-id="a5712-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="a5712-158">**AssemblyShortName**: krótka nazwa przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5712-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="a5712-159">**; Wersja** [opcjonalna]: wersja przywoływanego zestawu zawierającego plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="a5712-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="a5712-160">Ta wartość jest używana w przypadku załadowania co najmniej dwóch przywoływanych zestawów o tej samej krótkiej nazwie.</span><span class="sxs-lookup"><span data-stu-id="a5712-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="a5712-161">**; PublicKey** [opcjonalnie]: klucz publiczny, który został użyty do podpisania przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a5712-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="a5712-162">Ta wartość jest używana w przypadku załadowania co najmniej dwóch przywoływanych zestawów o tej samej krótkiej nazwie.</span><span class="sxs-lookup"><span data-stu-id="a5712-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="a5712-163">**; składnik**: określa, że zestaw, do którego odwołuje się odwołanie, jest przywoływany z zestawu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a5712-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="a5712-164">**/Path**: nazwa pliku zasobów, łącznie z jego ścieżką, względem katalogu głównego folderu projektu zestawu, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="a5712-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="a5712-165">Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w katalogu głównym folderu projektu zestawu, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="a5712-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="a5712-166">Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w podfolderze folderu projektu zestawu, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="a5712-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="a5712-167">W poniższym przykładzie przedstawiono pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zasobu, który znajduje się w folderze głównym odwołania do folderu projektu zestawu specyficznego dla wersji.</span><span class="sxs-lookup"><span data-stu-id="a5712-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="a5712-168">Należy zauważyć, że [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] składnia pakietu dla plików zasobów zestawu, do których istnieją odwołania, może być używana tylko z urzędem Application:///.</span><span class="sxs-lookup"><span data-stu-id="a5712-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="a5712-169">Na przykład następujące elementy nie są obsługiwane w programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5712-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="a5712-170">Identyfikatory URI pakietu plików zawartości</span><span class="sxs-lookup"><span data-stu-id="a5712-170">Content File Pack URIs</span></span>

<span data-ttu-id="a5712-171">Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zawartości używa następującego urzędu i ścieżki:</span><span class="sxs-lookup"><span data-stu-id="a5712-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="a5712-172">**Urząd**: Application:///.</span><span class="sxs-lookup"><span data-stu-id="a5712-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="a5712-173">**Ścieżka**: Nazwa pliku zawartości, łącznie z ścieżką względną do lokalizacji systemu plików głównego zestawu plików wykonywalnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5712-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="a5712-174">Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zawartości znajdującego się w tym samym folderze co zestaw wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="a5712-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="a5712-175">Poniższy przykład pokazuje pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla pliku zawartości znajdujący się w podfolderze, który jest względny dla zestawu wykonywalnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5712-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="a5712-176">Nie można przejść do plików zawartości HTML.</span><span class="sxs-lookup"><span data-stu-id="a5712-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="a5712-177">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Schemat obsługuje tylko nawigację do plików HTML, które znajdują się w lokalizacji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="a5712-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="a5712-178">Witryna identyfikatorów URI pakietu pochodzenia</span><span class="sxs-lookup"><span data-stu-id="a5712-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="a5712-179">Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla lokacji z plikiem pochodzenia używa następującego urzędu i ścieżki:</span><span class="sxs-lookup"><span data-stu-id="a5712-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="a5712-180">**Urząd**: siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="a5712-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="a5712-181">**Ścieżka**: Nazwa witryny pliku pierwotnego, w tym jej ścieżka względem lokalizacji, z której został uruchomiony zestaw wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="a5712-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="a5712-182">W poniższym przykładzie przedstawiono pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla lokacji pliku pierwotnego, przechowywany w lokalizacji, z której jest uruchamiany zestaw wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="a5712-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="a5712-183">W poniższym przykładzie przedstawiono pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dla lokacji pliku pierwotnego, przechowywane w podfolderze odnoszący się do lokalizacji, z której jest uruchamiany zestaw wykonywalny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5712-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="a5712-184">Pliki stronicowania</span><span class="sxs-lookup"><span data-stu-id="a5712-184">Page Files</span></span>

<span data-ttu-id="a5712-185">Pliki XAML, które są skonfigurowane jako `Page` elementy programu MSBuild, są kompilowane do zestawów w taki sam sposób jak pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="a5712-185">XAML files that are configured as MSBuild `Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="a5712-186">W związku z tym `Page` elementy MSBuild można zidentyfikować przy użyciu identyfikatorów URI pakietów dla plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="a5712-186">Consequently, MSBuild `Page` items can be identified using pack URIs for resource files.</span></span>

<span data-ttu-id="a5712-187">Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików, które są powszechnie skonfigurowane jako elementy programu`Page` MSBuild, mają jeden z następujących elementów jako ich element główny:</span><span class="sxs-lookup"><span data-stu-id="a5712-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as MSBuild`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="a5712-188">Bezwzględne a Względne identyfikatory URI pakietów</span><span class="sxs-lookup"><span data-stu-id="a5712-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="a5712-189">W pełni kwalifikowany pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] obejmuje schemat, Urząd i ścieżkę, a także jest traktowany jako [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]bezwzględny.</span><span class="sxs-lookup"><span data-stu-id="a5712-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="a5712-190">Jako uproszczenie dla deweloperów, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy zwykle umożliwiają ustawienie odpowiednich atrybutów z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]względnym, który zawiera tylko ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="a5712-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>

<span data-ttu-id="a5712-191">Rozważmy na przykład następujący bezwzględny [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] pakiet dla pliku zasobu w lokalnym zestawie.</span><span class="sxs-lookup"><span data-stu-id="a5712-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="a5712-192">Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] względny, który odwołuje się do tego pliku zasobów, będzie następujący.</span><span class="sxs-lookup"><span data-stu-id="a5712-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="a5712-193">Ze względu na to, że lokacja plików pochodzenia nie jest skojarzona z zestawami, można [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]odwoływać się tylko do bezwzględnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="a5712-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>

<span data-ttu-id="a5712-194">Domyślnie pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] względny jest traktowany względem lokalizacji znacznika lub kodu, który zawiera odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a5712-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="a5712-195">Jeśli jest używany [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] wiodący ukośnik odwrotny, jest on traktowany jako odwołanie względne do katalogu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5712-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="a5712-196">Rozważmy na przykład następującą strukturę projektu.</span><span class="sxs-lookup"><span data-stu-id="a5712-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="a5712-197">Jeśli Strona1. XAML zawiera [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołanie do *elementu głównego*\SubFolder\Page2.XAML, można użyć następującego powiązanego pakietu. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5712-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`Page2.xaml`

<span data-ttu-id="a5712-198">Jeśli Strona1. XAML zawiera [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołanie do *elementu głównego*\Page2.XAML, można użyć następującego powiązanego pakietu. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5712-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="a5712-199">Rozpoznawanie identyfikatora URI pakietu</span><span class="sxs-lookup"><span data-stu-id="a5712-199">Pack URI Resolution</span></span>

<span data-ttu-id="a5712-200">Format pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] umożliwia wyszukanie tego samego pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla różnych typów plików.</span><span class="sxs-lookup"><span data-stu-id="a5712-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="a5712-201">Rozważmy na przykład następujący bezwzględny [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]pakiet.</span><span class="sxs-lookup"><span data-stu-id="a5712-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="a5712-202">Ten bezwzględny pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] może odwoływać się do pliku zasobów w zestawie lokalnym lub w pliku zawartości.</span><span class="sxs-lookup"><span data-stu-id="a5712-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="a5712-203">Ta sama wartość dotyczy następujących względnych [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5712-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="a5712-204">Aby określić typ pliku, do którego odwołuje się pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , program [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] usuwa [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pliki zasobów w lokalnych zestawach i plikach zawartości przy użyciu następujących algorytmów heurystycznych:</span><span class="sxs-lookup"><span data-stu-id="a5712-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="a5712-205">Sondowanie metadanych zestawu dla <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybutu, który jest zgodny z pakietem. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5712-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

2. <span data-ttu-id="a5712-206">Jeśli atrybut zostanie znaleziony, ścieżka do pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odnosi się do pliku zawartości. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute></span><span class="sxs-lookup"><span data-stu-id="a5712-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>

3. <span data-ttu-id="a5712-207"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Jeśli atrybut nie zostanie znaleziony, sonduje pliki zasobów zestawu, które są kompilowane do zestawu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a5712-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="a5712-208">Jeśli zostanie znaleziony plik zasobów zgodny ze ścieżką pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , ścieżka do pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odnosi się do pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="a5712-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>

5. <span data-ttu-id="a5712-209">Jeśli zasób nie zostanie znaleziony, wewnętrznie utworzony <xref:System.Uri> jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a5712-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="a5712-210">rozwiązanie nie ma zastosowania w [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] odniesieniu do następujących informacji:</span><span class="sxs-lookup"><span data-stu-id="a5712-210">resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>

- <span data-ttu-id="a5712-211">Pliki zawartości w przywoływanych zestawach: te typy plików nie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]są obsługiwane przez program.</span><span class="sxs-lookup"><span data-stu-id="a5712-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

- <span data-ttu-id="a5712-212">Osadzone pliki w przywoływanych [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] zestawach: identyfikują one są unikatowe `;component` , ponieważ obejmują zarówno nazwę przywoływanego zestawu, jak i sufiks.</span><span class="sxs-lookup"><span data-stu-id="a5712-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="a5712-213">Lokacja plików pierwotnych [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] : określa, że są one unikatowe, ponieważ są to jedyne pliki, które mogą [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] być zidentyfikowane przez pakiet zawierający urząd siteoforigin:///.</span><span class="sxs-lookup"><span data-stu-id="a5712-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="a5712-214">Jednym z uproszczeń [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , które może rozpoznać pakiet, jest to, aby kod był nieco niezależny od lokalizacji plików zasobów i zawartości.</span><span class="sxs-lookup"><span data-stu-id="a5712-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="a5712-215">Jeśli na przykład plik zasobów w lokalnym zestawie, który zostanie ponownie skonfigurowany jako plik zawartości, pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zasobu pozostaje taki sam, jak kod, który używa pakietu. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5712-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="a5712-216">Programowanie przy użyciu identyfikatorów URI pakietów</span><span class="sxs-lookup"><span data-stu-id="a5712-216">Programming with Pack URIs</span></span>

<span data-ttu-id="a5712-217">Wiele [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] klas implementuje właściwości, które można ustawić za pomocą [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]pakietu, w tym:</span><span class="sxs-lookup"><span data-stu-id="a5712-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="a5712-218">Te właściwości można ustawić zarówno przy użyciu znacznika, jak i kodu.</span><span class="sxs-lookup"><span data-stu-id="a5712-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="a5712-219">W tej sekcji przedstawiono podstawowe konstrukcje obu programów, a następnie przedstawiono przykłady typowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="a5712-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="a5712-220">Używanie identyfikatorów URI pakietów w znacznikach</span><span class="sxs-lookup"><span data-stu-id="a5712-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="a5712-221">Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest określony w znacznikach przez ustawienie elementu atrybutu z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5712-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="a5712-222">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a5712-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="a5712-223">Tabela 1 ilustruje różne bezwzględne [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] pakiety, które można określić w znacznikach.</span><span class="sxs-lookup"><span data-stu-id="a5712-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="a5712-224">Tabela 1: Bezwzględne identyfikatory URI pakietów w znacznikach</span><span class="sxs-lookup"><span data-stu-id="a5712-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="a5712-225">Plik</span><span class="sxs-lookup"><span data-stu-id="a5712-225">File</span></span>|<span data-ttu-id="a5712-226">Bezwzględny pakiet[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5712-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="a5712-227">Plik zasobu — zestaw lokalny</span><span class="sxs-lookup"><span data-stu-id="a5712-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="a5712-228">Plik zasobów w podfolderze — zestaw lokalny</span><span class="sxs-lookup"><span data-stu-id="a5712-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="a5712-229">Przywoływany zestaw plików zasobów</span><span class="sxs-lookup"><span data-stu-id="a5712-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="a5712-230">Plik zasobów w podfolderze zestawu, do którego się odwołuje</span><span class="sxs-lookup"><span data-stu-id="a5712-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="a5712-231">Plik zasobów w przywoływanym zestawie</span><span class="sxs-lookup"><span data-stu-id="a5712-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="a5712-232">Plik zawartości</span><span class="sxs-lookup"><span data-stu-id="a5712-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="a5712-233">Plik zawartości w podfolderze</span><span class="sxs-lookup"><span data-stu-id="a5712-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="a5712-234">Lokacja pliku źródłowego</span><span class="sxs-lookup"><span data-stu-id="a5712-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="a5712-235">Lokacja pliku źródłowego w podfolderze</span><span class="sxs-lookup"><span data-stu-id="a5712-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="a5712-236">Tabela 2 ilustruje różne pakiety [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] względne, które można określić w znacznikach.</span><span class="sxs-lookup"><span data-stu-id="a5712-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="a5712-237">Tabela 2: Względne identyfikatory URI pakietu w znaczniku</span><span class="sxs-lookup"><span data-stu-id="a5712-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="a5712-238">Plik</span><span class="sxs-lookup"><span data-stu-id="a5712-238">File</span></span>|<span data-ttu-id="a5712-239">Pakiet względny[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5712-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="a5712-240">Plik zasobów w lokalnym zestawie</span><span class="sxs-lookup"><span data-stu-id="a5712-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="a5712-241">Plik zasobów w podfolderze zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="a5712-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="a5712-242">Plik zasobów w przywoływanym zestawie</span><span class="sxs-lookup"><span data-stu-id="a5712-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="a5712-243">Plik zasobów w podfolderze zestawu, do którego się odwołuje</span><span class="sxs-lookup"><span data-stu-id="a5712-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="a5712-244">Plik zawartości</span><span class="sxs-lookup"><span data-stu-id="a5712-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="a5712-245">Plik zawartości w podfolderze</span><span class="sxs-lookup"><span data-stu-id="a5712-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="a5712-246">Używanie identyfikatorów URI pakietów w kodzie</span><span class="sxs-lookup"><span data-stu-id="a5712-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="a5712-247">Należy określić pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w kodzie, tworząc wystąpienie <xref:System.Uri> klasy i przekazując pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametr do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a5712-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="a5712-248">Jest to zaprezentowane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a5712-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="a5712-249">Domyślnie <xref:System.Uri> Klasa traktuje pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] jako bezwzględny.</span><span class="sxs-lookup"><span data-stu-id="a5712-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="a5712-250">W związku z tym wyjątek jest zgłaszany, gdy wystąpienie <xref:System.Uri> klasy jest tworzone z pakietem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]względnym.</span><span class="sxs-lookup"><span data-stu-id="a5712-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="a5712-251">Na szczęście <xref:System.Uri> <xref:System.UriKind> przeciążenie konstruktora klasy akceptuje parametr typu, aby można było określić, czy pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest bezwzględny, czy względny. <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29></span><span class="sxs-lookup"><span data-stu-id="a5712-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="a5712-252">Należy określić tylko <xref:System.UriKind.Absolute> lub <xref:System.UriKind.Relative> wtedy, gdy masz pewność, że dostarczony pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] to jeden lub drugi.</span><span class="sxs-lookup"><span data-stu-id="a5712-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="a5712-253">Jeśli nie znasz typu używanego pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , na przykład gdy użytkownik wprowadzi pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w czasie wykonywania, użyj <xref:System.UriKind.RelativeOrAbsolute> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="a5712-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="a5712-254">Tabela 3 ilustruje różne pakiety [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] względne, które można określić w kodzie przy użyciu. <xref:System.Uri?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a5712-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a5712-255">Tabela 3: Bezwzględne identyfikatory URI pakietów w kodzie</span><span class="sxs-lookup"><span data-stu-id="a5712-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="a5712-256">Plik</span><span class="sxs-lookup"><span data-stu-id="a5712-256">File</span></span>|<span data-ttu-id="a5712-257">Bezwzględny pakiet[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5712-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="a5712-258">Plik zasobu — zestaw lokalny</span><span class="sxs-lookup"><span data-stu-id="a5712-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="a5712-259">Plik zasobów w podfolderze — zestaw lokalny</span><span class="sxs-lookup"><span data-stu-id="a5712-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="a5712-260">Przywoływany zestaw plików zasobów</span><span class="sxs-lookup"><span data-stu-id="a5712-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="a5712-261">Plik zasobów w podfolderze zestawu, do którego się odwołuje</span><span class="sxs-lookup"><span data-stu-id="a5712-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="a5712-262">Plik zasobów w przywoływanym zestawie</span><span class="sxs-lookup"><span data-stu-id="a5712-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="a5712-263">Plik zawartości</span><span class="sxs-lookup"><span data-stu-id="a5712-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="a5712-264">Plik zawartości w podfolderze</span><span class="sxs-lookup"><span data-stu-id="a5712-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="a5712-265">Lokacja pliku źródłowego</span><span class="sxs-lookup"><span data-stu-id="a5712-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="a5712-266">Lokacja pliku źródłowego w podfolderze</span><span class="sxs-lookup"><span data-stu-id="a5712-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="a5712-267">W tabeli 4 przedstawiono różne powiązane pakiety [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , które można określić w kodzie przy <xref:System.Uri?displayProperty=nameWithType>użyciu.</span><span class="sxs-lookup"><span data-stu-id="a5712-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a5712-268">Tabela 4: Względne identyfikatory URI pakietu w kodzie</span><span class="sxs-lookup"><span data-stu-id="a5712-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="a5712-269">Plik</span><span class="sxs-lookup"><span data-stu-id="a5712-269">File</span></span>|<span data-ttu-id="a5712-270">Pakiet względny[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5712-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="a5712-271">Plik zasobu — zestaw lokalny</span><span class="sxs-lookup"><span data-stu-id="a5712-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="a5712-272">Plik zasobów w podfolderze — zestaw lokalny</span><span class="sxs-lookup"><span data-stu-id="a5712-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="a5712-273">Przywoływany zestaw plików zasobów</span><span class="sxs-lookup"><span data-stu-id="a5712-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="a5712-274">Plik zasobów w zestawie podfolderów, do którego się odwołuje</span><span class="sxs-lookup"><span data-stu-id="a5712-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="a5712-275">Plik zawartości</span><span class="sxs-lookup"><span data-stu-id="a5712-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="a5712-276">Plik zawartości w podfolderze</span><span class="sxs-lookup"><span data-stu-id="a5712-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="a5712-277">Scenariusze typowych identyfikatorów URI pakietu</span><span class="sxs-lookup"><span data-stu-id="a5712-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="a5712-278">W poprzednich sekcjach omówiono sposób konstruowania pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] do identyfikowania zasobów, zawartości i lokalizacji plików pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="a5712-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="a5712-279">W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]programie te konstrukcje są używane na różne sposoby, a poniższe sekcje obejmują kilka typowych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="a5712-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="a5712-280">Określanie interfejsu użytkownika do wyświetlania podczas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="a5712-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="a5712-281"><xref:System.Windows.Application.StartupUri%2A>Określa pierwszy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , który ma być wyświetlany [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , gdy aplikacja jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="a5712-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="a5712-282">W przypadku aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] autonomicznych może to być okno, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a5712-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="a5712-283">Aplikacje autonomiczne [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] i mogą również określać stronę jako początkowy interfejs użytkownika, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a5712-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="a5712-284">Jeśli aplikacja jest aplikacją autonomiczną, a strona jest określona za pomocą <xref:System.Windows.Application.StartupUri%2A>programu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , program <xref:System.Windows.Navigation.NavigationWindow> otwiera na potrzeby hostowania strony.</span><span class="sxs-lookup"><span data-stu-id="a5712-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="a5712-285">W [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]przypadku programu strona jest wyświetlana w przeglądarce hosta.</span><span class="sxs-lookup"><span data-stu-id="a5712-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="a5712-286">Przechodzenie do strony</span><span class="sxs-lookup"><span data-stu-id="a5712-286">Navigating to a Page</span></span>

<span data-ttu-id="a5712-287">Poniższy przykład pokazuje, jak przejść do strony.</span><span class="sxs-lookup"><span data-stu-id="a5712-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="a5712-288">Aby uzyskać więcej informacji na temat różnych sposobów nawigowania [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]w programie, zobacz [Omówienie nawigacji](navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a5712-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="a5712-289">Określanie ikony okna</span><span class="sxs-lookup"><span data-stu-id="a5712-289">Specifying a Window Icon</span></span>

<span data-ttu-id="a5712-290">Poniższy przykład pokazuje, jak używać identyfikatora URI, aby określić ikonę okna.</span><span class="sxs-lookup"><span data-stu-id="a5712-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="a5712-291">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5712-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="a5712-292">Ładowanie plików obrazów, audio i wideo</span><span class="sxs-lookup"><span data-stu-id="a5712-292">Loading Image, Audio, and Video Files</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="a5712-293">zezwala aplikacjom na korzystanie z różnych typów nośników, które mogą być zidentyfikowane i ładowane z pakietem [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="a5712-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="a5712-294">Aby uzyskać więcej informacji na temat pracy z zawartością multimedialną, zobacz [grafika i multimedia](../graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="a5712-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="a5712-295">Ładowanie słownika zasobów z lokacji źródłowej</span><span class="sxs-lookup"><span data-stu-id="a5712-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="a5712-296">Słowniki zasobów<xref:System.Windows.ResourceDictionary>() mogą służyć do obsługi motywów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5712-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="a5712-297">Jednym ze sposobów tworzenia motywów i zarządzania nimi jest utworzenie wielu motywów jako słowników zasobów, które znajdują się w lokacji źródłowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5712-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="a5712-298">Dzięki temu można dodawać i aktualizować motywy bez ponownego kompilowania i wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5712-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="a5712-299">Te słowniki zasobów można identyfikować i ładować przy [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]użyciu pakietu, który jest przedstawiony w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a5712-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="a5712-300">Aby zapoznać się z omówieniem motywów w programie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="a5712-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../controls/styling-and-templating.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5712-301">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5712-301">See also</span></span>

- [<span data-ttu-id="a5712-302">Zasoby aplikacji WPF, zawartość i pliki danych</span><span class="sxs-lookup"><span data-stu-id="a5712-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
