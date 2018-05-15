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
ms.openlocfilehash: ae96ec40cbbf0a29f780c059b9873c185b2975d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="c8b4f-102">Pakuj URI w WPF</span><span class="sxs-lookup"><span data-stu-id="c8b4f-102">Pack URIs in WPF</span></span>
<span data-ttu-id="c8b4f-103">W konsoli Windows Presentation Foundation (WPF) [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] są używane do identyfikowania i ładować pliki na wiele sposobów, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>  
  
-   <span data-ttu-id="c8b4f-104">Określanie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do wyświetlenia po pierwszym uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>  
  
-   <span data-ttu-id="c8b4f-105">Podczas ładowania obrazów.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-105">Loading images.</span></span>  
  
-   <span data-ttu-id="c8b4f-106">Przechodzenie do strony.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-106">Navigating to pages.</span></span>  
  
-   <span data-ttu-id="c8b4f-107">Ładowanie plików danych z systemem innym niż plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-107">Loading non-executable data files.</span></span>  
  
 <span data-ttu-id="c8b4f-108">Ponadto [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] może służyć do identyfikowania i ładowanie plików z różnych lokalizacji, w tym następujące:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>  
  
-   <span data-ttu-id="c8b4f-109">Bieżący zestaw.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-109">The current assembly.</span></span>  
  
-   <span data-ttu-id="c8b4f-110">Przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-110">A referenced assembly.</span></span>  
  
-   <span data-ttu-id="c8b4f-111">Lokalizacja względem zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-111">A location relative to an assembly.</span></span>  
  
-   <span data-ttu-id="c8b4f-112">Aplikacji witryny pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-112">The application's site of origin.</span></span>  
  
 <span data-ttu-id="c8b4f-113">Aby zapewnić spójny mechanizm identyfikacji i ładowania tych typów plików w tych lokalizacjach [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] korzysta z rozszerzeń z *schemat identyfikatora URI pack*.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="c8b4f-114">Ten temat zawiera omówienie systemu, opisano sposób tworzenia pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla różnych scenariuszy, w tym artykule omówiono bezwzględnym i względnym [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] i [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] rozpoznawania przed pokazaniem jak używać dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] z obu znaczników i kod.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a><span data-ttu-id="c8b4f-115">Schemat identyfikatora URI Pack</span><span class="sxs-lookup"><span data-stu-id="c8b4f-115">The Pack URI Scheme</span></span>  
 <span data-ttu-id="c8b4f-116">Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schemat jest używany przez [otwartych Konwencji pakietów](http://go.microsoft.com/fwlink/?LinkID=71255) specyfikacji (pakietów OPC) opisano model organizowanie i identyfikacji zawartości.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="c8b4f-117">Kluczowe elementy modelu są pakiety i części, których *pakietu* jest kontenerem logicznym dla jednego lub więcej logicznej *części*.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="c8b4f-118">Poniższa ilustracja przedstawia tę koncepcję.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-118">The following figure illustrates this concept.</span></span>  
  
 <span data-ttu-id="c8b4f-119">![Diagram pakietu i części](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span><span class="sxs-lookup"><span data-stu-id="c8b4f-119">![Package and Parts diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span></span>  
  
 <span data-ttu-id="c8b4f-120">Aby zidentyfikować elementy, specyfikacja OPC wykorzystuje funkcjonalność RFC 2396 (identyfikatory URI (Uniform Resource): ogólna składnia) do definiowania pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schematu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>  
  
 <span data-ttu-id="c8b4f-121">Schemat, który jest określony przez [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest definiowana za pomocą jego prefiks; http, ftp i plik znajdują się przykłady dobrze znanego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="c8b4f-122">Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schemat używa "pakiet" jego schemat i zawiera dwa składniki: urzędu i ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="c8b4f-123">Poniżej przedstawiono format pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 <span data-ttu-id="c8b4f-124">dodatkiem Service Pack: / /*urzędu*/*ścieżki*</span><span class="sxs-lookup"><span data-stu-id="c8b4f-124">pack://*authority*/*path*</span></span>
  
 <span data-ttu-id="c8b4f-125">*Urzędu* Określa typ pakietu, który części jest zawarty w, podczas gdy *ścieżki* Określa lokalizację, w części w ramach pakietu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>  
  
 <span data-ttu-id="c8b4f-126">Następujący rysunek przedstawia tę koncepcję:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-126">This concept is illustrated by the following figure:</span></span>  
  
 <span data-ttu-id="c8b4f-127">![Relacja między pakietem, uprawnienia i ścieżka](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span><span class="sxs-lookup"><span data-stu-id="c8b4f-127">![Relationship among package, authority, and path](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span></span>  
  
 <span data-ttu-id="c8b4f-128">Pakiety i części są analogiczne do aplikacji i plików, w której aplikacja (pakiet) może zawierać jeden lub więcej plików (składniki), w tym:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>  
  
-   <span data-ttu-id="c8b4f-129">Pliki zasobów, które są kompilowane do zestawu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-129">Resource files that are compiled into the local assembly.</span></span>  
  
-   <span data-ttu-id="c8b4f-130">Pliki zasobów, które są kompilowane do przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-130">Resource files that are compiled into a referenced assembly.</span></span>  
  
-   <span data-ttu-id="c8b4f-131">Pliki zasobów, które są łączone w odwołaniem do zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-131">Resource files that are compiled into a referencing assembly.</span></span>  
  
-   <span data-ttu-id="c8b4f-132">Pliki zawartości.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-132">Content files.</span></span>  
  
-   <span data-ttu-id="c8b4f-133">Witryny pochodzenia plików.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-133">Site of origin files.</span></span>  
  
 <span data-ttu-id="c8b4f-134">Aby dostęp do tych typów plików, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsługuje dwa urzędy: aplikacji: / / / oraz siteoforigin: / / /.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="c8b4f-135">Aplikacja: / / / urzędu identyfikuje pliki danych aplikacji, które są znane w czasie kompilacji, w tym pliki zasobów i zawartości.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="c8b4f-136">Siteoforigin: lokalizacje urzędu identyfikuje witryny pochodzenia plików.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="c8b4f-137">Na poniższej ilustracji przedstawiono zakres każdego uprawnień.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-137">The scope of each authority is shown in the following figure.</span></span>  
  
 <span data-ttu-id="c8b4f-138">![Schemat identyfikatora URI Pack](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span><span class="sxs-lookup"><span data-stu-id="c8b4f-138">![Pack URI diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8b4f-139">Składnik urzędu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest osadzony [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] punktów do pakietu i musi być zgodna z RFC 2396.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="c8b4f-140">Ponadto muszą zostać zastąpione znakiem "," znak "/", a zastrzeżone znaki, takie jak "%" i "?" muszą być zmienione znaczenie.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="c8b4f-141">Zobacz OPC, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-141">See the OPC for details.</span></span>  
  
 <span data-ttu-id="c8b4f-142">W poniższych sekcjach opisano sposób tworzenia pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] przy użyciu tych dwóch urzędów w połączeniu z odpowiednich ścieżek do identyfikacji zasobu, zawartość i witryny pochodzenia plików.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a><span data-ttu-id="c8b4f-143">Identyfikatory URI pakietu plików zasobów</span><span class="sxs-lookup"><span data-stu-id="c8b4f-143">Resource File Pack URIs</span></span>  
 <span data-ttu-id="c8b4f-144">Pliki zasobów są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` elementów i są kompilowane do zestawów.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="c8b4f-145"> obsługuje konstrukcji pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] można zidentyfikować pliki zasobów, które są kompilowane do zestawu lokalnego lub skompilowany w zestawie, do którego odwołuje się z lokalnym zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-145"> supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a><span data-ttu-id="c8b4f-146">Plik zasobów zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="c8b4f-146">Local Assembly Resource File</span></span>  
 <span data-ttu-id="c8b4f-147">Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zasobu pliku, który jest kompilowany do zestawu lokalnego używa następujących urzędu i ścieżki:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="c8b4f-148">**Urząd**: aplikacji: / / /.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-148">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="c8b4f-149">**Ścieżka**: Nazwa pliku zasobu, wraz ze ścieżką względem katalogu głównego folderu projektu zestawu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>  
  
 <span data-ttu-id="c8b4f-150">W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w katalogu głównym folderu projektu zestawu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="c8b4f-151">W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w podfolderze folderu projektu zestawu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="c8b4f-152">Plik zasobu przywoływanego zestawu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-152">Referenced Assembly Resource File</span></span>  
 <span data-ttu-id="c8b4f-153">Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zasobu pliku, który ma zostać skompilowany w zestawie używa następujących urzędu i ścieżki:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="c8b4f-154">**Urząd**: aplikacji: / / /.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-154">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="c8b4f-155">**Ścieżka**: Nazwa pliku zasobu, który jest kompilowany do przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="c8b4f-156">Ścieżka musi być zgodna z następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-156">The path must conform to the following format:</span></span>  
  
     <span data-ttu-id="c8b4f-157">*AssemblyShortName*{*; Wersja*] {*; PublicKey*]; component /*ścieżki*</span><span class="sxs-lookup"><span data-stu-id="c8b4f-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>  
  
    -   <span data-ttu-id="c8b4f-158">**AssemblyShortName**: krótka nazwa dla przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>  
  
    -   <span data-ttu-id="c8b4f-159">**; Wersja** (opcjonalne): wersja przywoływanego zestawu, który zawiera plik zasobu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="c8b4f-160">Służy to, gdy co najmniej dwa zestawy występujące w odwołaniach o tej samej krótkiej nazwie zostały załadowane.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="c8b4f-161">**; PublicKey** [opcjonalnie]: klucz publiczny, który został użyty do podpisania przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="c8b4f-162">Służy to, gdy co najmniej dwa zestawy występujące w odwołaniach o tej samej krótkiej nazwie zostały załadowane.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="c8b4f-163">**; składnika**: Określa, czy z lokalnego zestawu odwołuje się do zestawu następuje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>  
  
    -   <span data-ttu-id="c8b4f-164">**/ Ścieżki**: Nazwa pliku zasobu, wraz ze ścieżką względem katalogu głównego folderu projektu przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>  
  
 <span data-ttu-id="c8b4f-165">W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w katalogu głównym folderu projektu przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 <span data-ttu-id="c8b4f-166">W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w podfolderze folderu projektu przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 <span data-ttu-id="c8b4f-167">W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zasobu, który znajduje się w folderze głównym folderu projektu zestaw do którego istnieje odwołanie, określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 <span data-ttu-id="c8b4f-168">Należy pamiętać, że pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] składnię przywoływanego zestawu plików zasobów mogą być używane tylko z aplikacji: / / / urzędu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="c8b4f-169">Na przykład następujące nie jest obsługiwany w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a><span data-ttu-id="c8b4f-170">Identyfikatory URI Pack pliku zawartości</span><span class="sxs-lookup"><span data-stu-id="c8b4f-170">Content File Pack URIs</span></span>  
 <span data-ttu-id="c8b4f-171">Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zawartości używa następujących urzędu i ścieżki:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="c8b4f-172">**Urząd**: aplikacji: / / /.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-172">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="c8b4f-173">**Ścieżka**: Nazwa zawartości pliku, wraz ze ścieżką względną wobec lokalizacji pliku systemu głównego pliku wykonywalnego zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>  
  
 <span data-ttu-id="c8b4f-174">W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zawartości pliku, znajdującego się w tym samym folderze co zestawu pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 <span data-ttu-id="c8b4f-175">W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku zawartości, znajduje się w podfolderze, względem pliku wykonywalnego zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]<span data-ttu-id="c8b4f-176"> pliki zawartości nie może zostać przesłane do.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-176"> content files cannot be navigated to.</span></span> <span data-ttu-id="c8b4f-177">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Schemat obsługuje tylko nawigacji do [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] pliki, które znajdują się w witrynie pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] files that are located at the site of origin.</span></span>  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="c8b4f-178">Witryny pochodzenia URI pakietu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-178">Site of Origin Pack URIs</span></span>  
 <span data-ttu-id="c8b4f-179">Ten pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla witryny pochodzenia pliku używa następujących urzędu i ścieżki:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="c8b4f-180">**Urząd**: siteoforigin: / / /.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-180">**Authority**: siteoforigin:///.</span></span>  
  
-   <span data-ttu-id="c8b4f-181">**Ścieżka**: Nazwa witryny pochodzenia pliku, wraz ze ścieżką względną wobec lokalizacji, z którego uruchomiono zestawu pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>  
  
 <span data-ttu-id="c8b4f-182">W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] witryny pochodzenia pliku, przechowywane w lokalizacji, z którego uruchomiono wykonywalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 <span data-ttu-id="c8b4f-183">W poniższym przykładzie przedstawiono pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] witryny pochodzenia pliku, przechowywane w podfolderze względną wobec lokalizacji, w którym jest uruchamiana wykonywalnego zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a><span data-ttu-id="c8b4f-184">Pliki stronicowania</span><span class="sxs-lookup"><span data-stu-id="c8b4f-184">Page Files</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="c8b4f-185"> pliki, które są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementy są kompilowane do zestawów w taki sam sposób jak pliki zasobów.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-185"> files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="c8b4f-186">W rezultacie [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementy mogą zostać zidentyfikowane przy użyciu pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>  
  
 <span data-ttu-id="c8b4f-187">Typy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliki, które zwykle są skonfigurowane jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` elementy mają jeden z następujących jako ich elementu głównego:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="c8b4f-188">Bezwzględny vs. Pakiet względne identyfikatory URI</span><span class="sxs-lookup"><span data-stu-id="c8b4f-188">Absolute vs. Relative Pack URIs</span></span>  
 <span data-ttu-id="c8b4f-189">Pełny pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zawiera schemat, uprawnień i ścieżkę, i jest uznawany za bezwzględna pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="c8b4f-190">Jako uproszczenia dla deweloperów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy umożliwiają zazwyczaj Ustaw odpowiednie atrybuty z pakietem względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], która obejmuje tylko ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>  
  
 <span data-ttu-id="c8b4f-191">Rozważmy na przykład następujący pakiet bezwzględną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla pliku zasobu w zestawie lokalnego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="c8b4f-192">Pakiet względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołujący się do tego zasobu pliku będą następujące.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  <span data-ttu-id="c8b4f-193">Ponieważ witryny pochodzenia pliki nie są skojarzone z zestawów, one tylko można odwoływać się z pakietem bezwzględną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="c8b4f-194">Domyślnie pakiet względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest uznawany za względną wobec lokalizacji znaczników lub kod, który zawiera odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="c8b4f-195">Jeśli używana jest wiodącego ukośnika, jednak względnej pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołanie jest uznawany za następnie względem katalogu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="c8b4f-196">Na przykład należy wziąć pod uwagę następujące struktury projektu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-196">For example, consider the following project structure.</span></span>  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 <span data-ttu-id="c8b4f-197">Jeśli zawiera Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , która odwołuje się *głównego*\SubFolder\Page2.xaml, odwołanie można użyć następujących pakietu względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `Page2.xaml`  
  
 <span data-ttu-id="c8b4f-198">Jeśli zawiera Page1.xaml [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , która odwołuje się *głównego*\Page2.xaml, odwołanie można użyć następujących pakietu względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a><span data-ttu-id="c8b4f-199">Rozpoznawania identyfikatora URI Pack</span><span class="sxs-lookup"><span data-stu-id="c8b4f-199">Pack URI Resolution</span></span>  
 <span data-ttu-id="c8b4f-200">Format pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] sprawia, że istnieje możliwość, że pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla różnych typów plików do przeszukania takie same.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it is possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="c8b4f-201">Rozważmy na przykład następujący pakiet bezwzględną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="c8b4f-202">Ten pakiet bezwzględną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] można odwoływać się do pliku zasobu w zestawie lokalnego lub pliku zawartości.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="c8b4f-203">To samo dotyczy następujących względnej [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="c8b4f-204">Aby określić typ pliku pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołuje się do, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] rozpoznaje [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] dla plików zasobów lokalnych zestawów i plików zawartości przy użyciu następujących Algorytm heurystyczny:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>  
  
1.  <span data-ttu-id="c8b4f-205">Sonda metadanych zestawu <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut, który odpowiada pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
2.  <span data-ttu-id="c8b4f-206">Jeśli <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atrybut zostanie znaleziony, ścieżka pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołuje się do pliku zawartości.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>  
  
3.  <span data-ttu-id="c8b4f-207">Jeśli <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> nie odnaleziono atrybutu, pliki zasobów zestawu, które są kompilowane do zestawu lokalnego sondowania.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>  
  
4.  <span data-ttu-id="c8b4f-208">Jeśli plik zasobów zgodna ze ścieżką pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] zostanie znaleziony, ścieżka pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] odwołuje się do pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>  
  
5.  <span data-ttu-id="c8b4f-209">Jeśli nie można odnaleźć zasobu, utworzone wewnętrznie <xref:System.Uri> jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="c8b4f-210"> rozdzielczość nie jest stosowany dla [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] odwołujące się do następujących:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-210"> resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>  
  
-   <span data-ttu-id="c8b4f-211">Zawartość plików w przywoływanych zestawach: następujące typy plików nie są obsługiwane przez [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
-   <span data-ttu-id="c8b4f-212">Osadzone pliki w przywoływanych zestawach: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] które identyfikują są unikatowe, ponieważ zawierają one nazwę zestawu, do którego istnieje odwołanie i `;component` sufiks.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>  
  
-   <span data-ttu-id="c8b4f-213">Witryny pochodzenia plików: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] które identyfikują są unikatowe, ponieważ są one tylko pliki, które mogą zostać zidentyfikowane przez pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] zawierających siteoforigin: / / / urzędu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>  
  
 <span data-ttu-id="c8b4f-214">Uproszczenie jednego, czy pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] rozpoznawania umożliwia dla kodu nieco niezależnie od lokalizacji zasobów i zawartość plików jest.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="c8b4f-215">Na przykład, jeśli plik zasobu w zestawie lokalnego, który jest konfigurowane jako plik zawartości pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] dla zasobu jest taka sama, jak kod, który korzysta z pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a><span data-ttu-id="c8b4f-216">Programowanie za pomocą identyfikatorów URI pakietu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-216">Programming with Pack URIs</span></span>  
 <span data-ttu-id="c8b4f-217">Wiele [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] klasy implementować właściwości, które można skonfigurować z dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], takie jak:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="c8b4f-218">Te właściwości można ustawić zarówno znaczników i kodu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="c8b4f-219">W tej sekcji przedstawiono podstawowe konstrukcji dla obu, a następnie przedstawiono przykłady typowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="c8b4f-220">W znaczniku przy użyciu identyfikatorów URI pakietu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-220">Using Pack URIs in Markup</span></span>  
 <span data-ttu-id="c8b4f-221">Pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest określony w znaczniku przez ustawienie elementu atrybutu przy użyciu pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="c8b4f-222">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c8b4f-222">For example:</span></span>  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 <span data-ttu-id="c8b4f-223">Tabela 1 przedstawiono różne bezwzględna pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] wskazanym w znaczniku.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="c8b4f-224">Tabela 1: Bezwzględna pakietu URI w znaczniku</span><span class="sxs-lookup"><span data-stu-id="c8b4f-224">Table 1: Absolute Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="c8b4f-225">Plik</span><span class="sxs-lookup"><span data-stu-id="c8b4f-225">File</span></span>|<span data-ttu-id="c8b4f-226">Bezwzględna pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b4f-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="c8b4f-227">Plik zasobów — zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="c8b4f-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|  
|<span data-ttu-id="c8b4f-228">Plik zasobów w podfolderze - zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="c8b4f-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="c8b4f-229">Plik zasobów - przywoływanego zestawu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="c8b4f-230">Plik zasobów w podfolderze przywoływanego zestawu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="c8b4f-231">Plik zasobów w określonej wersji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|<span data-ttu-id="c8b4f-232">Plik zawartości</span><span class="sxs-lookup"><span data-stu-id="c8b4f-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|  
|<span data-ttu-id="c8b4f-233">Zawartość pliku w podfolderze</span><span class="sxs-lookup"><span data-stu-id="c8b4f-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|<span data-ttu-id="c8b4f-234">Witryny pochodzenia pliku</span><span class="sxs-lookup"><span data-stu-id="c8b4f-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|<span data-ttu-id="c8b4f-235">Witryny pochodzenia pliku w podfolderze</span><span class="sxs-lookup"><span data-stu-id="c8b4f-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 <span data-ttu-id="c8b4f-236">Tabela 2 przedstawia różne pakiet względną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] wskazanym w znaczniku.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="c8b4f-237">Tabela 2: URI pakietu względne w znaczniku</span><span class="sxs-lookup"><span data-stu-id="c8b4f-237">Table 2: Relative Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="c8b4f-238">Plik</span><span class="sxs-lookup"><span data-stu-id="c8b4f-238">File</span></span>|<span data-ttu-id="c8b4f-239">Względne pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b4f-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="c8b4f-240">Plik zasobów w zestawie lokalnego</span><span class="sxs-lookup"><span data-stu-id="c8b4f-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|  
|<span data-ttu-id="c8b4f-241">Plik zasobów w podfolderze zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="c8b4f-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="c8b4f-242">Plik zasobów w przywoływanego zestawu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="c8b4f-243">Plik zasobów w podfolderze przywoływanego zestawu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="c8b4f-244">Plik zawartości</span><span class="sxs-lookup"><span data-stu-id="c8b4f-244">Content file</span></span>|`"/ContentFile.xaml"`|  
|<span data-ttu-id="c8b4f-245">Zawartość pliku w podfolderze</span><span class="sxs-lookup"><span data-stu-id="c8b4f-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a><span data-ttu-id="c8b4f-246">Przy użyciu identyfikatorów URI pakietu w kodzie</span><span class="sxs-lookup"><span data-stu-id="c8b4f-246">Using Pack URIs in Code</span></span>  
 <span data-ttu-id="c8b4f-247">Określ pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w kodzie przez utworzenie wystąpienia <xref:System.Uri> klasy i przekazywanie pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jako parametr do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="c8b4f-248">Jest to zaprezentowane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-248">This is demonstrated in the following example.</span></span>  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 <span data-ttu-id="c8b4f-249">Domyślnie <xref:System.Uri> klasy uwzględnia pakiet [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] być bezwzględny.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="c8b4f-250">W rezultacie zgłoszony wyjątek, gdy wystąpienie klasy <xref:System.Uri> klasy jest tworzony z pakietem względną [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8b4f-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 <span data-ttu-id="c8b4f-251">Na szczęście <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> przeciążenia z <xref:System.Uri> konstruktora klasy przyjmuje parametr typu <xref:System.UriKind> pozwala określić, czy pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 <span data-ttu-id="c8b4f-252">Należy określić tylko <xref:System.UriKind.Absolute> lub <xref:System.UriKind.Relative> gdy masz pewność, że podany pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] jest jednego lub drugiego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="c8b4f-253">Jeśli nie znasz typ pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] używany, np. gdy użytkownik wprowadza pakiet [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] w czasie wykonywania, użyj <xref:System.UriKind.RelativeOrAbsolute> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 <span data-ttu-id="c8b4f-254">Tabela 3 przedstawiono różne pakiet względną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] określonego przez użytkownika w kodzie za pomocą <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c8b4f-255">Tabela 3: Bezwzględna pakietu URI w kodzie</span><span class="sxs-lookup"><span data-stu-id="c8b4f-255">Table 3: Absolute Pack URIs in Code</span></span>  
  
|<span data-ttu-id="c8b4f-256">Plik</span><span class="sxs-lookup"><span data-stu-id="c8b4f-256">File</span></span>|<span data-ttu-id="c8b4f-257">Bezwzględna pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b4f-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="c8b4f-258">Plik zasobów — zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="c8b4f-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="c8b4f-259">Plik zasobów w podfolderze - zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="c8b4f-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="c8b4f-260">Plik zasobów - przywoływanego zestawu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="c8b4f-261">Plik zasobów w podfolderze przywoływanego zestawu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="c8b4f-262">Plik zasobów w określonej wersji przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="c8b4f-263">Plik zawartości</span><span class="sxs-lookup"><span data-stu-id="c8b4f-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="c8b4f-264">Zawartość pliku w podfolderze</span><span class="sxs-lookup"><span data-stu-id="c8b4f-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="c8b4f-265">Witryny pochodzenia pliku</span><span class="sxs-lookup"><span data-stu-id="c8b4f-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="c8b4f-266">Witryny pochodzenia pliku w podfolderze</span><span class="sxs-lookup"><span data-stu-id="c8b4f-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 <span data-ttu-id="c8b4f-267">Tabela 4 przedstawiono różne pakiet względną [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] określonego przez użytkownika za pomocą kodu <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c8b4f-268">Tabela 4: URI pakietu względne w kodzie</span><span class="sxs-lookup"><span data-stu-id="c8b4f-268">Table 4: Relative Pack URIs in Code</span></span>  
  
|<span data-ttu-id="c8b4f-269">Plik</span><span class="sxs-lookup"><span data-stu-id="c8b4f-269">File</span></span>|<span data-ttu-id="c8b4f-270">Względne pakietu [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b4f-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="c8b4f-271">Plik zasobów — zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="c8b4f-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="c8b4f-272">Plik zasobów w podfolderze - zestawu lokalnego</span><span class="sxs-lookup"><span data-stu-id="c8b4f-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="c8b4f-273">Plik zasobów - przywoływanego zestawu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="c8b4f-274">Plik zasobów w podfolderze - przywoływanego zestawu</span><span class="sxs-lookup"><span data-stu-id="c8b4f-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="c8b4f-275">Plik zawartości</span><span class="sxs-lookup"><span data-stu-id="c8b4f-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="c8b4f-276">Zawartość pliku w podfolderze</span><span class="sxs-lookup"><span data-stu-id="c8b4f-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="c8b4f-277">Typowe scenariusze identyfikatora URI Pack</span><span class="sxs-lookup"><span data-stu-id="c8b4f-277">Common Pack URI Scenarios</span></span>  
 <span data-ttu-id="c8b4f-278">Poprzednich sekcjach ma opisano sposób tworzenia pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] do identyfikacji zasobu, zawartość i witryny pochodzenia plików.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="c8b4f-279">W [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]tych konstrukcji używanych w różny sposób i w poniższych częściach omówiono kilka typowych użycia.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="c8b4f-280">Określanie interfejsu użytkownika do wyświetlenia w momencie uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="c8b4f-280">Specifying the UI to Show When an Application Starts</span></span>  
 <span data-ttu-id="c8b4f-281"><xref:System.Windows.Application.StartupUri%2A> Określa pierwszy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aby pokazać, kiedy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacja jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="c8b4f-282">Dla aplikacji autonomicznych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] może być oknem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 <span data-ttu-id="c8b4f-283">Aplikacje autonomiczne i [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] można również określić stronę jako początkowa interfejsu użytkownika, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 <span data-ttu-id="c8b4f-284">Jeśli aplikacja to aplikacja autonomiczna, a strona jest określany za pomocą <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] otwiera <xref:System.Windows.Navigation.NavigationWindow> do hostowania strony.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="c8b4f-285">Aby uzyskać [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], strona jest wyświetlana w przeglądarce hosta.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a><span data-ttu-id="c8b4f-286">Przechodzenie do strony</span><span class="sxs-lookup"><span data-stu-id="c8b4f-286">Navigating to a Page</span></span>  
 <span data-ttu-id="c8b4f-287">Poniższy przykład pokazuje, jak można przejść do strony.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-287">The following example shows how to navigate to a page.</span></span>  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 <span data-ttu-id="c8b4f-288">Aby uzyskać więcej informacji na różne sposoby, aby przejść w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c8b4f-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a><span data-ttu-id="c8b4f-289">Określanie ikonę okna</span><span class="sxs-lookup"><span data-stu-id="c8b4f-289">Specifying a Window Icon</span></span>  
 <span data-ttu-id="c8b4f-290">Poniższy przykład przedstawia sposób korzystania z identyfikatora URI, aby określić ikonę okna.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-290">The following example shows how to use a URI to specify a window's icon.</span></span>  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 <span data-ttu-id="c8b4f-291">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Window.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="c8b4f-292">Ładowanie plików wideo, Audio i obrazów</span><span class="sxs-lookup"><span data-stu-id="c8b4f-292">Loading Image, Audio, and Video Files</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="c8b4f-293"> Umożliwia aplikacjom na korzystanie z różnych typów, z których wszystkie zidentyfikowane i załadowany z dodatkiem Service pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-293"> allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 <span data-ttu-id="c8b4f-294">Aby uzyskać więcej informacji na temat pracy z zawartości nośnika, zobacz [grafiki i Multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8b4f-294">For more information on working with media content, see [Graphics and Multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md).</span></span>  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="c8b4f-295">Ładowanie słownika zasobów z witryny pochodzenia</span><span class="sxs-lookup"><span data-stu-id="c8b4f-295">Loading a Resource Dictionary from the Site of Origin</span></span>  
 <span data-ttu-id="c8b4f-296">Słowniki zasobów (<xref:System.Windows.ResourceDictionary>) może służyć do obsługi motywów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="c8b4f-297">Jednym ze sposobów tworzenia i zarządzania nimi kompozycji jest utworzenie wielu motywów jako słowniki zasobów, które znajdują się w witrynie pochodzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="c8b4f-298">Dzięki temu kompozycje do dodania i zaktualizować konieczności ponownego kompilowania ani ponownego wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="c8b4f-299">Te słowniki zasobów mogą zostać zidentyfikowane i ładowane przy użyciu pakietu [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], które przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c8b4f-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 <span data-ttu-id="c8b4f-300">Omówienie motywów w [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="c8b4f-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b4f-301">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8b4f-301">See Also</span></span>  
 [<span data-ttu-id="c8b4f-302">Zasoby aplikacji WPF, zawartość i pliki danych</span><span class="sxs-lookup"><span data-stu-id="c8b4f-302">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
