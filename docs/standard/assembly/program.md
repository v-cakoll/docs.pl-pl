---
title: Programowanie przy użyciu zestawów
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
ms.openlocfilehash: 9f07d36d9e47189d53e367fd1406e5684c024aa3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107056"
---
# <a name="program-with-assemblies"></a><span data-ttu-id="9eb92-102">Programowanie przy użyciu zestawów</span><span class="sxs-lookup"><span data-stu-id="9eb92-102">Program with assemblies</span></span>
<span data-ttu-id="9eb92-103">Zestawy są blokami konstrukcyjnymi .NET Framework; tworzą one podstawową jednostkę wdrożenia, kontrolę wersji, ponowne użycie, zakres aktywacji i uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9eb92-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="9eb92-104">Zestaw udostępnia środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadome implementacji typów.</span><span class="sxs-lookup"><span data-stu-id="9eb92-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="9eb92-105">Jest to Kolekcja typów i zasobów, które są tworzone w celu współdziałania i tworzą logiczną jednostkę funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="9eb92-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="9eb92-106">Dla środowiska uruchomieniowego typ nie istnieje poza kontekstem zestawu.</span><span class="sxs-lookup"><span data-stu-id="9eb92-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="9eb92-107">W tej sekcji opisano sposób tworzenia modułów, tworzenia zestawów z modułów, tworzenia pary kluczy i podpisywania zestawu o silnej nazwie, a następnie instalowania zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="9eb92-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="9eb92-108">Ponadto w tej sekcji opisano sposób używania [Dezasembler MSIL (Ildasm. exe)](../../framework/tools/ildasm-exe-il-disassembler.md) do wyświetlania informacji manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="9eb92-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9eb92-109">Począwszy od .NET Framework w wersji 2,0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji .NET Framework, która ma wyższy numer wersji niż aktualnie załadowane środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="9eb92-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="9eb92-110">Dotyczy to kombinacji głównych i pomocniczych składników numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="9eb92-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9eb92-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9eb92-111">In this section</span></span>  
 [<span data-ttu-id="9eb92-112">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="9eb92-112">Create assemblies</span></span>](create.md)  
 <span data-ttu-id="9eb92-113">Zawiera omówienie zestawów jednoplikowych i wieloplikowych.</span><span class="sxs-lookup"><span data-stu-id="9eb92-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="9eb92-114">Nazwy zestawów</span><span class="sxs-lookup"><span data-stu-id="9eb92-114">Assembly names</span></span>](names.md)  
 <span data-ttu-id="9eb92-115">Zawiera omówienie nazewnictwa zestawów.</span><span class="sxs-lookup"><span data-stu-id="9eb92-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="9eb92-116">Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu</span><span class="sxs-lookup"><span data-stu-id="9eb92-116">How to: Determine an assembly's fully qualified name</span></span>](find-fully-qualified-name.md)  
 <span data-ttu-id="9eb92-117">Opisuje sposób określania w pełni kwalifikowanej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="9eb92-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="9eb92-118">Uruchamianie aplikacji intranetowych w trybie pełnego zaufania</span><span class="sxs-lookup"><span data-stu-id="9eb92-118">Run intranet applications in full trust</span></span>](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="9eb92-119">Opisuje sposób określania starszych zasad zabezpieczeń dla zestawów pełnego zaufania w udziale intranetowym.</span><span class="sxs-lookup"><span data-stu-id="9eb92-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="9eb92-120">Lokalizacja zestawu</span><span class="sxs-lookup"><span data-stu-id="9eb92-120">Assembly location</span></span>](location.md)  
 <span data-ttu-id="9eb92-121">Zawiera omówienie lokalizacji lokalizowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="9eb92-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="9eb92-122">Instrukcje: kompilowanie zestawu jednoplikowego</span><span class="sxs-lookup"><span data-stu-id="9eb92-122">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)  
 <span data-ttu-id="9eb92-123">Opisuje sposób tworzenia zestawu jednoplikowego.</span><span class="sxs-lookup"><span data-stu-id="9eb92-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="9eb92-124">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="9eb92-124">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="9eb92-125">Opisuje przyczyny tworzenia zestawów wieloplikowych.</span><span class="sxs-lookup"><span data-stu-id="9eb92-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="9eb92-126">Instrukcje: kompilowanie zestawu wieloplikowego</span><span class="sxs-lookup"><span data-stu-id="9eb92-126">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)  
 <span data-ttu-id="9eb92-127">Opisuje sposób tworzenia zestawu wieloplikowego.</span><span class="sxs-lookup"><span data-stu-id="9eb92-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="9eb92-128">Ustawianie atrybutów zestawu</span><span class="sxs-lookup"><span data-stu-id="9eb92-128">Set assembly attributes</span></span>](set-attributes.md)  
 <span data-ttu-id="9eb92-129">Opisuje atrybuty zestawu i sposób ich ustawiania.</span><span class="sxs-lookup"><span data-stu-id="9eb92-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="9eb92-130">Tworzenie i używanie zestawów o silnych nazwach</span><span class="sxs-lookup"><span data-stu-id="9eb92-130">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)  
 <span data-ttu-id="9eb92-131">Opisuje, jak i dlaczego podpisać zestaw za pomocą silnej nazwy i zawiera tematy porad.</span><span class="sxs-lookup"><span data-stu-id="9eb92-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="9eb92-132">Opóźnij podpisanie zestawu</span><span class="sxs-lookup"><span data-stu-id="9eb92-132">Delay-sign an assembly</span></span>](delay-sign.md)  
 <span data-ttu-id="9eb92-133">Opisuje, jak opóźnić podpisywanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="9eb92-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="9eb92-134">Pracuj z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="9eb92-134">Work with assemblies and the global assembly cache</span></span>](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="9eb92-135">Opisuje, jak i dlaczego należy dodać zestawy do globalnej pamięci podręcznej zestawów i zawiera tematy porad.</span><span class="sxs-lookup"><span data-stu-id="9eb92-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="9eb92-136">Instrukcje: wyświetlanie zawartości zestawu</span><span class="sxs-lookup"><span data-stu-id="9eb92-136">How to: View assembly contents</span></span>](view-contents.md)  
 <span data-ttu-id="9eb92-137">Opisuje sposób używania Dezasembler MSIL (Ildasm. exe) do wyświetlania zawartości zestawu.</span><span class="sxs-lookup"><span data-stu-id="9eb92-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="9eb92-138">Przekazywanie typu w środowisku uruchomieniowym języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="9eb92-138">Type forwarding in the common language runtime</span></span>](type-forwarding.md)  
 <span data-ttu-id="9eb92-139">Opisuje, jak używać przekazywania typów do przenoszenia typu do innego zestawu bez przerywania istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9eb92-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9eb92-140">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="9eb92-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="9eb92-141">Klasa .NET Framework, która reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="9eb92-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9eb92-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9eb92-142">Related sections</span></span>  
 [<span data-ttu-id="9eb92-143">Instrukcje: uzyskiwanie informacji o typie i elemencie członkowskim z zestawu</span><span class="sxs-lookup"><span data-stu-id="9eb92-143">How to: Obtain type and member information from an assembly</span></span>](../../framework/reflection-and-codedom/get-type-member-information.md)  
 <span data-ttu-id="9eb92-144">Opisuje, w jaki sposób programowo uzyskać typ i inne informacje z zestawu.</span><span class="sxs-lookup"><span data-stu-id="9eb92-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="9eb92-145">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="9eb92-145">Assemblies in .NET</span></span>](index.md)  
 <span data-ttu-id="9eb92-146">Zawiera omówienie pojęć dotyczących zestawów środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="9eb92-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="9eb92-147">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="9eb92-147">Assembly versioning</span></span>](versioning.md)  
 <span data-ttu-id="9eb92-148">Zawiera omówienie powiązań zestawów i atrybutów <xref:System.Reflection.AssemblyVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9eb92-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="9eb92-149">Jak środowisko uruchomieniowe lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="9eb92-149">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="9eb92-150">Opisuje, jak środowisko uruchomieniowe określa, który zestaw ma być używany do realizacji żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="9eb92-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 <span data-ttu-id="9eb92-151">  [odbicia](../../framework/reflection-and-codedom/reflection.md)</span><span class="sxs-lookup"><span data-stu-id="9eb92-151">[Reflection](../../framework/reflection-and-codedom/reflection.md) </span></span>  
 <span data-ttu-id="9eb92-152">Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="9eb92-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
