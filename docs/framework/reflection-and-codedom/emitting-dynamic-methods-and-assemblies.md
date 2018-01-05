---
title: "Emitowanie dynamicznych metod i zestawów"
ms.custom: 
ms.date: 08/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c724620c987b2ee871dc282bca0dd3da1a5031bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="c70f6-102">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="c70f6-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="c70f6-103">W tej sekcji opisano zestaw typy zarządzane w <xref:System.Reflection.Emit> przestrzeni nazw, która umożliwia kompilatora lub narzędziu emitowanie metadanych i Microsoft języku pośrednim (MSIL) w czasie wykonywania i opcjonalnie Generowanie pliku przenośny plik wykonywalny (PE) na dysku.</span><span class="sxs-lookup"><span data-stu-id="c70f6-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="c70f6-104">Liczba aparatów skryptów i kompilatory są użytkowników podstawowych tego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="c70f6-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="c70f6-105">W tej sekcji funkcje udostępniane przez <xref:System.Reflection.Emit> przestrzeni nazw jest określana jako odbicia emisji.</span><span class="sxs-lookup"><span data-stu-id="c70f6-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="c70f6-106">Emisja odbicia oferuje następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="c70f6-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="c70f6-107">Zdefiniuj lekkie metody globalne wykonywania czasu, przy użyciu <xref:System.Reflection.Emit.DynamicMethod> klasy, a następnie wykonać ich używanie delegatów.</span><span class="sxs-lookup"><span data-stu-id="c70f6-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="c70f6-108">Zdefiniuj zestawów w czasie wykonywania i uruchamiać je lub Zapisz je na dysku.</span><span class="sxs-lookup"><span data-stu-id="c70f6-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="c70f6-109">Zdefiniuj zestawów w czasie wykonywania, uruchom, a następnie zwolnij je i Zezwalaj na wyrzucanie elementów bezużytecznych odzyskać ich zasobów.</span><span class="sxs-lookup"><span data-stu-id="c70f6-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="c70f6-110">Zdefiniuj modułów w nowych zestawach w czasie wykonywania i uruchom lub zapisać je na dysku.</span><span class="sxs-lookup"><span data-stu-id="c70f6-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="c70f6-111">Definiowanie typów modułów w czasie wykonywania, tworzenie wystąpień typów i wywołania metod.</span><span class="sxs-lookup"><span data-stu-id="c70f6-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="c70f6-112">Zdefiniuj informacje symboliczne dla określonych modułów, które mogą być używane przez narzędzia, takie jak debugery i profilery kodu.</span><span class="sxs-lookup"><span data-stu-id="c70f6-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="c70f6-113">Oprócz typy zarządzane w <xref:System.Reflection.Emit> przestrzeni nazw, istnieją interfejsy niezarządzane metadanych, które zostały opisane w [interfejsy metadanych](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) odwołania dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="c70f6-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="c70f6-114">Emisja odbicia zarządzanych zapewnia silniejsze sprawdzanie błędów semantycznych i wyższym poziomie abstrakcji metadanych niż interfejsy niezarządzane metadanych.</span><span class="sxs-lookup"><span data-stu-id="c70f6-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="c70f6-115">Inne przydatne zasoby do pracy z metadanych i MSIL jest dokumentacji infrastruktury języka wspólnego (CLI), szczególnie "Partycji II: metadane definicji i semantyki" i "Partycji III: CIL instrukcji Set".</span><span class="sxs-lookup"><span data-stu-id="c70f6-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="c70f6-116">Dokumentacja jest dostępna online na [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) i [witryny sieci Ecma Web](http://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="c70f6-116">The documentation is available online on [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](http://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c70f6-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c70f6-117">In This Section</span></span>
  
[<span data-ttu-id="c70f6-118">Emituj problemy z zabezpieczeniami w odbicia</span><span class="sxs-lookup"><span data-stu-id="c70f6-118">Security issues in reflection emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
<span data-ttu-id="c70f6-119">W tym artykule opisano zabezpieczeń, które Emituj problemów dotyczących tworzenia dynamicznych zestawach za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="c70f6-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="c70f6-120">[Porady: definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="c70f6-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="c70f6-121">Pokazuje, jak wykonać prostą metodę dynamicznego i dynamiczna metoda powiązany z wystąpieniem klasy.</span><span class="sxs-lookup"><span data-stu-id="c70f6-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="c70f6-122">[Porady: Definiowanie typu ogólnego z odbiciem emisji](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="c70f6-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="c70f6-123">Przedstawia sposób tworzenia prostego typu ogólnego z parametrami typu dwa, jak dotyczą parametrów typu klasy interfejsu i ograniczeń specjalnych oraz sposobu tworzenia memers, które używają parametrów typu klasy jako typy parametrów i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="c70f6-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create memers that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="c70f6-124">[Porady: definiowanie metody ogólnej za pomocą odbicia emisji](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="c70f6-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="c70f6-125">Przedstawia sposób tworzenia, emisji, a następnie wywołaj proste metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="c70f6-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="c70f6-126">[Zestawów kolekcjonowanych generacji typu dynamicznego](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="c70f6-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="c70f6-127">Wprowadza zestawów kolekcjonowanych, które są dynamiczne zestawy, które może być zwolniony bez zwalniania domeny aplikacji, w którym zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="c70f6-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="c70f6-128">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="c70f6-128">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="c70f6-129">Tworzy wykaz kodów instrukcja MSIL, używanej do tworzenia treści metody.</span><span class="sxs-lookup"><span data-stu-id="c70f6-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="c70f6-130">Zawiera klasy zarządzane używane na emitowanie metod dynamicznych, zestawy i typów.</span><span class="sxs-lookup"><span data-stu-id="c70f6-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="c70f6-131">W tym artykule opisano <xref:System.Type> klasy, która reprezentuje typów w zarządzanych odbicia emisja odbicia i która jest kluczem do używania tych technologii.</span><span class="sxs-lookup"><span data-stu-id="c70f6-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="c70f6-132">Zawiera klasy zarządzane używane do eksplorowania metadanych i kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="c70f6-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c70f6-133">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c70f6-133">Related Sections</span></span>  
 [<span data-ttu-id="c70f6-134">Odbicie</span><span class="sxs-lookup"><span data-stu-id="c70f6-134">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="c70f6-135">Wyjaśniono, jak metadanych i kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="c70f6-135">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="c70f6-136">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="c70f6-136">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="c70f6-137">Zawiera omówienie zestawów w implementacjach .NET.</span><span class="sxs-lookup"><span data-stu-id="c70f6-137">Provides an overview of assemblies in .NET implementations.</span></span>
