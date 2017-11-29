---
title: "Programowanie za pomocą zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 368021062a3ad49d2c63f92797c59b8c0f1cddfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="d8108-102">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="d8108-102">Programming with Assemblies</span></span>
<span data-ttu-id="d8108-103">Zestawy są blokami konstrukcyjnymi programu .NET Framework; stanowią podstawową jednostkę wdrożenia, kontroli wersji, ponownemu, zakresu aktywacji i uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d8108-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="d8108-104">Zestaw zawiera środowisko uruchomieniowe języka wspólnego o informacje, które należy znać typ implementacji.</span><span class="sxs-lookup"><span data-stu-id="d8108-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="d8108-105">Jest kolekcją typów i zasobów, które są przeznaczone do współpracują ze sobą i utworzenia jednostki logicznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8108-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="d8108-106">Do środowiska wykonawczego typ nie istnieje poza kontekstem zestawu.</span><span class="sxs-lookup"><span data-stu-id="d8108-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="d8108-107">Ta sekcja zawiera opis sposobu tworzenia modułów, tworzenie zestawów z modułów utworzyć pary kluczy i podpisać zestaw o silnej nazwie i Instalowanie zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="d8108-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="d8108-108">Ponadto w tej sekcji opisano sposób użycia [dezasembler MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) do wyświetlania informacji manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="d8108-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8108-109">W programie .NET Framework w wersji 2.0, środowisko uruchomieniowe nie zostanie załadowany zestaw, który został skompilowany przy użyciu wersji programu .NET Framework, która ma wyższy numer wersji niż aktualnie załadowany.</span><span class="sxs-lookup"><span data-stu-id="d8108-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="d8108-110">Dotyczy to kombinacja główne i pomocnicze składniki numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="d8108-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8108-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d8108-111">In This Section</span></span>  
 [<span data-ttu-id="d8108-112">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="d8108-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="d8108-113">Zawiera omówienie zestawy jednoplikowe i wiele plików.</span><span class="sxs-lookup"><span data-stu-id="d8108-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="d8108-114">Nazw zestawów</span><span class="sxs-lookup"><span data-stu-id="d8108-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="d8108-115">Omówienie zestawu nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="d8108-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="d8108-116">Porady: ustalić w pełni kwalifikowana nazwa zestawu</span><span class="sxs-lookup"><span data-stu-id="d8108-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="d8108-117">Opisuje sposób ustalić w pełni kwalifikowana nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="d8108-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="d8108-118">Uruchamianie aplikacji intranetowych w trybie pełnego zaufania</span><span class="sxs-lookup"><span data-stu-id="d8108-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="d8108-119">Opisuje sposób określenia zasady zabezpieczeń starsze dla zestawów pełnego zaufania w udziale sieci intranet.</span><span class="sxs-lookup"><span data-stu-id="d8108-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="d8108-120">Lokalizacja zestawu</span><span class="sxs-lookup"><span data-stu-id="d8108-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="d8108-121">Zawiera omówienie gdzie umieścić zestawy.</span><span class="sxs-lookup"><span data-stu-id="d8108-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="d8108-122">Porady: tworzenie zestawów pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="d8108-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="d8108-123">Opisuje sposób tworzenia zestawu pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="d8108-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="d8108-124">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="d8108-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="d8108-125">W tym artykule opisano powodów tworzenia zestawy wieloplikowe.</span><span class="sxs-lookup"><span data-stu-id="d8108-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="d8108-126">Porady: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="d8108-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="d8108-127">Opisuje sposób tworzenia zestawów wieloplikowych.</span><span class="sxs-lookup"><span data-stu-id="d8108-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="d8108-128">Ustawienie atrybutów zestawu</span><span class="sxs-lookup"><span data-stu-id="d8108-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="d8108-129">Zawiera opis atrybutów zestawu i sposobu ich ustawiania.</span><span class="sxs-lookup"><span data-stu-id="d8108-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="d8108-130">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="d8108-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="d8108-131">W tym artykule opisano, jak i dlaczego podpisać zestaw o silnej nazwie i zawiera tematy porad.</span><span class="sxs-lookup"><span data-stu-id="d8108-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="d8108-132">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="d8108-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="d8108-133">Opisuje sposób Podpisz zestaw opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="d8108-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="d8108-134">Praca z zestawami i Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="d8108-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="d8108-135">W tym artykule opisano, jak i dlaczego dodawania zestawów do globalnej pamięci podręcznej zestawów i zawiera tematy porad.</span><span class="sxs-lookup"><span data-stu-id="d8108-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="d8108-136">Porady: wyświetlanie zawartości zestawu</span><span class="sxs-lookup"><span data-stu-id="d8108-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="d8108-137">Informacje dotyczące używania dezasembler MSIL (Ildasm.exe), aby wyświetlić zawartość zestawu.</span><span class="sxs-lookup"><span data-stu-id="d8108-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="d8108-138">Przekazywanie dalej typu w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="d8108-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="d8108-139">Opisuje sposób umożliwia przekazywanie dalej typu przenosić typu w innym zestawie bez przerywania istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8108-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d8108-140">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d8108-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="d8108-141">Klasa .NET Framework, która reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="d8108-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d8108-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d8108-142">Related Sections</span></span>  
 [<span data-ttu-id="d8108-143">Porady: uzyskać informacje dotyczące elementu członkowskiego typu i z zestawu</span><span class="sxs-lookup"><span data-stu-id="d8108-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="d8108-144">Opisuje sposób programowego uzyskać inne informacje dotyczące typu i z zestawu.</span><span class="sxs-lookup"><span data-stu-id="d8108-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="d8108-145">Zestawy w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="d8108-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="d8108-146">Zawiera omówienie języka wspólnego zestawy środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="d8108-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="d8108-147">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="d8108-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="d8108-148">Omówienie powiązań zestawów i z <xref:System.Reflection.AssemblyVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d8108-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="d8108-149">Jak lokalizuje zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d8108-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="d8108-150">W tym artykule opisano, jak środowisko uruchomieniowe Określa, które zestawu do używania w celu spełnienia żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="d8108-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="d8108-151">Odbicie</span><span class="sxs-lookup"><span data-stu-id="d8108-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="d8108-152">Informacje dotyczące używania **odbicia** klasę, aby uzyskać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="d8108-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
