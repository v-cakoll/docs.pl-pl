---
title: Programowanie za pomocą zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a20a2e678c10157fed7da6f5de9f3ffee0c9ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705548"
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="32cb2-102">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="32cb2-102">Programming with Assemblies</span></span>
<span data-ttu-id="32cb2-103">Zestawy są blokami konstrukcyjnymi .NET Framework; tworzą one podstawową jednostką wdrażania, kontroli wersji, ponownego użycia, określania zakresu aktywacji i uprawnień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="32cb2-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="32cb2-104">Zestaw zawiera środowisko uruchomieniowe języka wspólnego informacje potrzebne do należy pamiętać o implementacji typu.</span><span class="sxs-lookup"><span data-stu-id="32cb2-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="32cb2-105">Jest to kolekcja typów i zasobów, które zostały opracowane w celu współpracują ze sobą i tworzą jednostkę logiczną funkcji.</span><span class="sxs-lookup"><span data-stu-id="32cb2-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="32cb2-106">Do środowiska uruchomieniowego typem nie istnieje poza kontekstem zestawu.</span><span class="sxs-lookup"><span data-stu-id="32cb2-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="32cb2-107">W tej sekcji opisano sposób tworzenia modułów, tworzenie zestawów z modułów, utworzyć parę kluczy i podpisać zestaw silną nazwą i Instalowanie zestawu w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="32cb2-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="32cb2-108">Ponadto w tej sekcji opisano sposób używania [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić dane manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="32cb2-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32cb2-109">Począwszy od programu .NET Framework w wersji 2.0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji programu .NET Framework, który ma wyższy numer wersji niż obecnie załadowanym środowiskiem uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="32cb2-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="32cb2-110">Dotyczy to kombinacja składniki główny i pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="32cb2-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="32cb2-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="32cb2-111">In This Section</span></span>  
 [<span data-ttu-id="32cb2-112">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="32cb2-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="32cb2-113">Zawiera omówienie pojedynczego pliku i wieloplikowe zestawy.</span><span class="sxs-lookup"><span data-stu-id="32cb2-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="32cb2-114">Nazwy zestawów</span><span class="sxs-lookup"><span data-stu-id="32cb2-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="32cb2-115">Omówienie zestawów nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="32cb2-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="32cb2-116">Instrukcje: Określić w pełni kwalifikowanej nazwy zestawu</span><span class="sxs-lookup"><span data-stu-id="32cb2-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="32cb2-117">W tym artykule opisano, jak określić w pełni kwalifikowana nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="32cb2-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="32cb2-118">Uruchamianie aplikacji intranetowych w trybie pełnego zaufania</span><span class="sxs-lookup"><span data-stu-id="32cb2-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="32cb2-119">Opisuje sposób określania zasad zabezpieczeń w starszej wersji dla zestawów pełnego zaufania w udziale sieci intranet.</span><span class="sxs-lookup"><span data-stu-id="32cb2-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="32cb2-120">Lokalizacja zestawu</span><span class="sxs-lookup"><span data-stu-id="32cb2-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="32cb2-121">Zawiera omówienie gdzie umieścić zestawy.</span><span class="sxs-lookup"><span data-stu-id="32cb2-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="32cb2-122">Instrukcje: Kompilacja zestawów pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="32cb2-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="32cb2-123">W tym artykule opisano sposób tworzenia zestawu pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="32cb2-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="32cb2-124">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="32cb2-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="32cb2-125">W tym artykule opisano tworzenie zespołów wieloplikowych przyczyny.</span><span class="sxs-lookup"><span data-stu-id="32cb2-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="32cb2-126">Instrukcje: Kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="32cb2-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="32cb2-127">W tym artykule opisano, jak utworzyć zestaw wieloplikowy.</span><span class="sxs-lookup"><span data-stu-id="32cb2-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="32cb2-128">Ustawienie atrybutów zestawu</span><span class="sxs-lookup"><span data-stu-id="32cb2-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="32cb2-129">Zawiera opis atrybutów zestawu i sposobu ich ustawiania.</span><span class="sxs-lookup"><span data-stu-id="32cb2-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="32cb2-130">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="32cb2-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="32cb2-131">W tym artykule opisano, jak i dlaczego należy podpisać zestaw silną nazwą i zawiera tematy Pomocy.</span><span class="sxs-lookup"><span data-stu-id="32cb2-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="32cb2-132">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="32cb2-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="32cb2-133">W tym artykule opisano sposób Opóźnij podpisanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="32cb2-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="32cb2-134">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="32cb2-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="32cb2-135">W tym artykule opisano, jak i dlaczego dodawania zestawów do globalnej pamięci podręcznej i zawiera tematy Pomocy.</span><span class="sxs-lookup"><span data-stu-id="32cb2-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="32cb2-136">Instrukcje: Wyświetlanie zawartości zestawu</span><span class="sxs-lookup"><span data-stu-id="32cb2-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="32cb2-137">Opisuje sposób używania MSIL Disassembler (Ildasm.exe), aby wyświetlić zawartość zestawu.</span><span class="sxs-lookup"><span data-stu-id="32cb2-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="32cb2-138">Przekazywanie dalej typu w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="32cb2-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="32cb2-139">Opisuje sposób używania przekazywanie dalej typu na przeniesienie typu do innego zestawu bez przerywania istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32cb2-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="32cb2-140">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="32cb2-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="32cb2-141">Klasa .NET Framework, która reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="32cb2-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="32cb2-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="32cb2-142">Related Sections</span></span>  
 [<span data-ttu-id="32cb2-143">Instrukcje: Uzyskiwanie informacji dotyczących elementu członkowskiego typów i z zestawu</span><span class="sxs-lookup"><span data-stu-id="32cb2-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="32cb2-144">W tym artykule opisano, jak programowo uzyskać typ i inne informacje z zestawu.</span><span class="sxs-lookup"><span data-stu-id="32cb2-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="32cb2-145">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="32cb2-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="32cb2-146">Zawiera omówienie pojęć dotyczących języka wspólnego zestawów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="32cb2-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="32cb2-147">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="32cb2-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="32cb2-148">Zawiera omówienie powiązania zestawu oraz o <xref:System.Reflection.AssemblyVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="32cb2-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="32cb2-149">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="32cb2-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="32cb2-150">W tym artykule opisano, jak środowisko wykonawcze określa, które zestawu do używania w celu spełnienia żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="32cb2-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="32cb2-151">Odbicie</span><span class="sxs-lookup"><span data-stu-id="32cb2-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="32cb2-152">Opisuje sposób używania **odbicia** klasy, aby uzyskać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="32cb2-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
