---
title: Manifest zestawu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df64129a0ae15b5bad387a62ca60bb4b1b92f7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-manifest"></a><span data-ttu-id="b4bb8-102">Manifest zestawu</span><span class="sxs-lookup"><span data-stu-id="b4bb8-102">Assembly Manifest</span></span>
<span data-ttu-id="b4bb8-103">Każdy zestaw statyczny i dynamiczny zawiera kolekcję danych, które opisują powiązania między elementami zawartymi w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-103">Every assembly, whether static or dynamic, contains a collection of data that describes how the elements in the assembly relate to each other.</span></span> <span data-ttu-id="b4bb8-104">Manifest zestawu zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-104">The assembly manifest contains this assembly metadata.</span></span> <span data-ttu-id="b4bb8-105">W manifeście zestawu znajdują się wszystkie metadane potrzebne do określenia wymagań w zakresie wersji zestawu i tożsamości jego zabezpieczeń, a także wszystkie metadane niezbędne do definiowania zakresu zestawu oraz rozpoznawania odwołań do zasobów i klas.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-105">An assembly manifest contains all the metadata needed to specify the assembly's version requirements and security identity, and all metadata needed to define the scope of the assembly and resolve references to resources and classes.</span></span> <span data-ttu-id="b4bb8-106">Manifest zestawu może być przechowywany w pliku PE (.exe lub .dll) mającym kod w języku Microsoft Intermediate Language (MSIL) lub w samodzielnym pliku PE, który zawiera tylko dane manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-106">The assembly manifest can be stored in either a PE file (an .exe or .dll) with Microsoft intermediate language (MSIL) code or in a standalone PE file that contains only assembly manifest information.</span></span>  
  
 <span data-ttu-id="b4bb8-107">Na ilustracji poniżej widać różne sposoby przechowywania manifestu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-107">The following illustration shows the different ways the manifest can be stored.</span></span>  
  
 <span data-ttu-id="b4bb8-108">![Pojedynczy &#45; zestawu plików](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span><span class="sxs-lookup"><span data-stu-id="b4bb8-108">![A single&#45;file assembly](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span></span>  
<span data-ttu-id="b4bb8-109">Typy zestawów</span><span class="sxs-lookup"><span data-stu-id="b4bb8-109">Types of assemblies</span></span>  
  
 <span data-ttu-id="b4bb8-110">Dla zestawu o jednym skojarzonym pliku manifest jest umieszczony w pliku PE, co tworzy zestaw jednoplikowy.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-110">For an assembly with one associated file, the manifest is incorporated into the PE file to form a single-file assembly.</span></span> <span data-ttu-id="b4bb8-111">Zestaw wieloplikowy może zawierać autonomiczny plik manifestu lub manifest umieszczony w jednym z plików PE w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-111">You can create a multifile assembly with a standalone manifest file or with the manifest incorporated into one of the PE files in the assembly.</span></span>  
  
 <span data-ttu-id="b4bb8-112">Manifest każdego zestawu wykonuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="b4bb8-112">Each assembly's manifest performs the following functions:</span></span>  
  
-   <span data-ttu-id="b4bb8-113">Wylicza pliki tworzące zestaw.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-113">Enumerates the files that make up the assembly.</span></span>  
  
-   <span data-ttu-id="b4bb8-114">Określa, w jaki sposób odwołania do typów i zasobów zestawów są mapowane na pliki zawierające ich deklaracje i implementacje.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-114">Governs how references to the assembly's types and resources map to the files that contain their declarations and implementations.</span></span>  
  
-   <span data-ttu-id="b4bb8-115">Wylicza inne zestawy, od których zależy zestaw.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-115">Enumerates other assemblies on which the assembly depends.</span></span>  
  
-   <span data-ttu-id="b4bb8-116">Tworzy poziom pośredni między obiektami używającymi zestawu a szczegółami implementacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-116">Provides a level of indirection between consumers of the assembly and the assembly's implementation details.</span></span>  
  
-   <span data-ttu-id="b4bb8-117">Sprawia, że zestaw sam siebie opisuje.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-117">Renders the assembly self-describing.</span></span>  
  
## <a name="assembly-manifest-contents"></a><span data-ttu-id="b4bb8-118">Zawartość manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="b4bb8-118">Assembly Manifest Contents</span></span>  
 <span data-ttu-id="b4bb8-119">Poniższa tabela pokazuje informacje zawarte w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-119">The following table shows the information contained in the assembly manifest.</span></span> <span data-ttu-id="b4bb8-120">Pierwsze cztery elementy — nazwa zestawu, numer wersji, kultura i informacje o silnej nazwie — tworzą tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-120">The first four items—the assembly name, version number, culture, and strong name information—make up the assembly's identity.</span></span>  
  
|<span data-ttu-id="b4bb8-121">Informacje</span><span class="sxs-lookup"><span data-stu-id="b4bb8-121">Information</span></span>|<span data-ttu-id="b4bb8-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b4bb8-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b4bb8-123">Nazwa zestawu</span><span class="sxs-lookup"><span data-stu-id="b4bb8-123">Assembly name</span></span>|<span data-ttu-id="b4bb8-124">Ciąg tekstowy określający nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-124">A text string specifying the assembly's name.</span></span>|  
|<span data-ttu-id="b4bb8-125">Numer wersji</span><span class="sxs-lookup"><span data-stu-id="b4bb8-125">Version number</span></span>|<span data-ttu-id="b4bb8-126">Główny i pomocniczy numer wersji oraz numery poprawki i kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-126">A major and minor version number, and a revision and build number.</span></span> <span data-ttu-id="b4bb8-127">Na podstawie tych numerów środowisko uruchomieniowe języka wspólnego wymusza zasady dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-127">The common language runtime uses these numbers to enforce version policy.</span></span>|  
|<span data-ttu-id="b4bb8-128">Kultury</span><span class="sxs-lookup"><span data-stu-id="b4bb8-128">Culture</span></span>|<span data-ttu-id="b4bb8-129">Informacje o kulturze lub języku obsługiwanym przez zestaw.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-129">Information on the culture or language the assembly supports.</span></span> <span data-ttu-id="b4bb8-130">Informacji tych należy używać wyłącznie w celu oznaczenia zestawu jako zestawu satelickiego zawierającego informacje specyficzne dla kultury lub języka.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-130">This information should be used only to designate an assembly as a satellite assembly containing culture- or language-specific information.</span></span> <span data-ttu-id="b4bb8-131">(Zestaw z informacjami o kulturze jest automatycznie traktowany jako satelicki).</span><span class="sxs-lookup"><span data-stu-id="b4bb8-131">(An assembly with culture information is automatically assumed to be a satellite assembly.)</span></span>|  
|<span data-ttu-id="b4bb8-132">Informacje o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="b4bb8-132">Strong name information</span></span>|<span data-ttu-id="b4bb8-133">Klucz publiczny od wydawcy, jeśli zestawowi nadano silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-133">The public key from the publisher if the assembly has been given a strong name.</span></span>|  
|<span data-ttu-id="b4bb8-134">Lista wszystkich plików w zestawie</span><span class="sxs-lookup"><span data-stu-id="b4bb8-134">List of all files in the assembly</span></span>|<span data-ttu-id="b4bb8-135">Skrót utworzony na podstawie zawartości każdego pliku w zestawie i nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-135">A hash of each file contained in the assembly and a file name.</span></span> <span data-ttu-id="b4bb8-136">Wszystkie pliki tworzące zestaw muszą być w tym samym katalogu co plik zawierający manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-136">Note that all files that make up the assembly must be in the same directory as the file containing the assembly manifest.</span></span>|  
|<span data-ttu-id="b4bb8-137">Informacje o odwołaniu do typu</span><span class="sxs-lookup"><span data-stu-id="b4bb8-137">Type reference information</span></span>|<span data-ttu-id="b4bb8-138">Informacje, na podstawie których środowisko uruchomieniowe mapuje odwołanie do typu na plik zawierający jego deklarację i implementację.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-138">Information used by the runtime to map a type reference to the file that contains its declaration and implementation.</span></span> <span data-ttu-id="b4bb8-139">Wykorzystywane do typów eksportowanych z zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-139">This is used for types that are exported from the assembly.</span></span>|  
|<span data-ttu-id="b4bb8-140">Informacje o przywoływanych zestawach</span><span class="sxs-lookup"><span data-stu-id="b4bb8-140">Information on referenced assemblies</span></span>|<span data-ttu-id="b4bb8-141">Lista innych zestawów, do których prowadzą statyczne odwołania z zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-141">A list of other assemblies that are statically referenced by the assembly.</span></span> <span data-ttu-id="b4bb8-142">Każde odwołanie zawiera nazwę zależnego zestawu, metadane zestawu (wersja, kultura, system operacyjny itd.) oraz klucz publiczny, jeśli zestaw ma silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-142">Each reference includes the dependent assembly's name, assembly metadata (version, culture, operating system, and so on), and public key, if the assembly is strong named.</span></span>|  
  
 <span data-ttu-id="b4bb8-143">Niektóre informacje w manifeście zestawu można dodawać i zmieniać w kodzie za pomocą atrybutów zestawu.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-143">You can add or change some information in the assembly manifest by using assembly attributes in your code.</span></span> <span data-ttu-id="b4bb8-144">M.in. można zmienić informacje o wersji i atrybuty informacyjne, w tym dotyczące znaku towarowego, praw autorskich, produktu, firmy i danych informacyjnych wersji.</span><span class="sxs-lookup"><span data-stu-id="b4bb8-144">You can change version information and informational attributes, including Trademark, Copyright, Product, Company, and Informational Version.</span></span> <span data-ttu-id="b4bb8-145">Aby uzyskać pełną listę atrybutów zestawu, zobacz [ustawienie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b4bb8-145">For a complete list of assembly attributes, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4bb8-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4bb8-146">See Also</span></span>  
 [<span data-ttu-id="b4bb8-147">Zawartość zestawu</span><span class="sxs-lookup"><span data-stu-id="b4bb8-147">Assembly Contents</span></span>](../../../docs/framework/app-domains/assembly-contents.md)  
 [<span data-ttu-id="b4bb8-148">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="b4bb8-148">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 [<span data-ttu-id="b4bb8-149">Tworzenie zestawów satelickich</span><span class="sxs-lookup"><span data-stu-id="b4bb8-149">Creating Satellite Assemblies</span></span>](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [<span data-ttu-id="b4bb8-150">Zestawy o silnych nazwach</span><span class="sxs-lookup"><span data-stu-id="b4bb8-150">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
