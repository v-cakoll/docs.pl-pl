---
title: Programowanie za pomocą zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921430"
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="aea6e-102">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="aea6e-102">Programming with Assemblies</span></span>
<span data-ttu-id="aea6e-103">Zestawy są blokami konstrukcyjnymi .NET Framework; tworzą one podstawową jednostkę wdrożenia, kontrolę wersji, ponowne użycie, zakres aktywacji i uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="aea6e-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="aea6e-104">Zestaw udostępnia środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadome implementacji typów.</span><span class="sxs-lookup"><span data-stu-id="aea6e-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="aea6e-105">Jest to Kolekcja typów i zasobów, które są tworzone w celu współdziałania i tworzą logiczną jednostkę funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="aea6e-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="aea6e-106">Dla środowiska uruchomieniowego typ nie istnieje poza kontekstem zestawu.</span><span class="sxs-lookup"><span data-stu-id="aea6e-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="aea6e-107">W tej sekcji opisano sposób tworzenia modułów, tworzenia zestawów z modułów, tworzenia pary kluczy i podpisywania zestawu o silnej nazwie, a następnie instalowania zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="aea6e-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="aea6e-108">Ponadto w tej sekcji opisano sposób używania [Dezasembler MSIL (Ildasm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) do wyświetlania informacji manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="aea6e-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aea6e-109">Począwszy od .NET Framework w wersji 2,0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji .NET Framework, która ma wyższy numer wersji niż aktualnie załadowane środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="aea6e-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="aea6e-110">Dotyczy to kombinacji głównych i pomocniczych składników numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="aea6e-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aea6e-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="aea6e-111">In This Section</span></span>  
 [<span data-ttu-id="aea6e-112">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="aea6e-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="aea6e-113">Zawiera omówienie zestawów jednoplikowych i wieloplikowych.</span><span class="sxs-lookup"><span data-stu-id="aea6e-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="aea6e-114">Nazwy zestawów</span><span class="sxs-lookup"><span data-stu-id="aea6e-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="aea6e-115">Zawiera omówienie nazewnictwa zestawów.</span><span class="sxs-lookup"><span data-stu-id="aea6e-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="aea6e-116">Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu</span><span class="sxs-lookup"><span data-stu-id="aea6e-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="aea6e-117">Opisuje sposób określania w pełni kwalifikowanej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="aea6e-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="aea6e-118">Uruchamianie aplikacji intranetowych w trybie pełnego zaufania</span><span class="sxs-lookup"><span data-stu-id="aea6e-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="aea6e-119">Opisuje sposób określania starszych zasad zabezpieczeń dla zestawów pełnego zaufania w udziale intranetowym.</span><span class="sxs-lookup"><span data-stu-id="aea6e-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="aea6e-120">Lokalizacja zestawu</span><span class="sxs-lookup"><span data-stu-id="aea6e-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="aea6e-121">Zawiera omówienie lokalizacji lokalizowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="aea6e-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="aea6e-122">Instrukcje: Kompilowanie zestawu jednoplikowego</span><span class="sxs-lookup"><span data-stu-id="aea6e-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="aea6e-123">Opisuje sposób tworzenia zestawu jednoplikowego.</span><span class="sxs-lookup"><span data-stu-id="aea6e-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="aea6e-124">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="aea6e-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="aea6e-125">Opisuje przyczyny tworzenia zestawów wieloplikowych.</span><span class="sxs-lookup"><span data-stu-id="aea6e-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="aea6e-126">Instrukcje: Kompilowanie zestawu wieloplikowego</span><span class="sxs-lookup"><span data-stu-id="aea6e-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="aea6e-127">Opisuje sposób tworzenia zestawu wieloplikowego.</span><span class="sxs-lookup"><span data-stu-id="aea6e-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="aea6e-128">Ustawienie atrybutów zestawu</span><span class="sxs-lookup"><span data-stu-id="aea6e-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="aea6e-129">Opisuje atrybuty zestawu i sposób ich ustawiania.</span><span class="sxs-lookup"><span data-stu-id="aea6e-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="aea6e-130">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="aea6e-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="aea6e-131">Opisuje, jak i dlaczego podpisać zestaw za pomocą silnej nazwy i zawiera tematy porad.</span><span class="sxs-lookup"><span data-stu-id="aea6e-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="aea6e-132">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="aea6e-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="aea6e-133">Opisuje, jak opóźnić podpisywanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="aea6e-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="aea6e-134">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="aea6e-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="aea6e-135">Opisuje, jak i dlaczego należy dodać zestawy do globalnej pamięci podręcznej zestawów i zawiera tematy porad.</span><span class="sxs-lookup"><span data-stu-id="aea6e-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="aea6e-136">Instrukcje: Wyświetl zawartość zestawu</span><span class="sxs-lookup"><span data-stu-id="aea6e-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="aea6e-137">Opisuje sposób używania Dezasembler MSIL (Ildasm. exe) do wyświetlania zawartości zestawu.</span><span class="sxs-lookup"><span data-stu-id="aea6e-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="aea6e-138">Przekazywanie dalej typu w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="aea6e-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="aea6e-139">Opisuje, jak używać przekazywania typów do przenoszenia typu do innego zestawu bez przerywania istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aea6e-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aea6e-140">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="aea6e-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="aea6e-141">Klasa .NET Framework, która reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="aea6e-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aea6e-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="aea6e-142">Related Sections</span></span>  
 [<span data-ttu-id="aea6e-143">Instrukcje: Uzyskiwanie informacji o typie i elemencie członkowskim z zestawu</span><span class="sxs-lookup"><span data-stu-id="aea6e-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="aea6e-144">Opisuje, w jaki sposób programowo uzyskać typ i inne informacje z zestawu.</span><span class="sxs-lookup"><span data-stu-id="aea6e-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="aea6e-145">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="aea6e-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="aea6e-146">Zawiera omówienie pojęć dotyczących zestawów środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="aea6e-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="aea6e-147">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="aea6e-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="aea6e-148">Zawiera omówienie powiązań zestawów i <xref:System.Reflection.AssemblyVersionAttribute> atrybutów i. <xref:System.Reflection.AssemblyInformationalVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="aea6e-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="aea6e-149">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="aea6e-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="aea6e-150">Opisuje, jak środowisko uruchomieniowe określa, który zestaw ma być używany do realizacji żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="aea6e-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="aea6e-151">Odbicie</span><span class="sxs-lookup"><span data-stu-id="aea6e-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="aea6e-152">Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="aea6e-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
