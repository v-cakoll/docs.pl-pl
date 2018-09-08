---
title: Emitowanie dynamicznych metod i zestawów
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0ed1d02fd40a94d4ae63deea3c09b04bfc9bd8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183135"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="3d08d-102">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="3d08d-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="3d08d-103">W tej sekcji opisano zestaw typów zarządzanych w <xref:System.Reflection.Emit> przestrzeni nazw, dzięki czemu kompilator lub narzędziu emitowanie metadanych oraz języka Microsoft intermediate language (MSIL) w czasie wykonywania i opcjonalnie generowania przenośnych plików wykonywalnych (PE) pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="3d08d-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="3d08d-104">Kompilatory i aparatów skryptów są użytkownicy podstawowi tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3d08d-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="3d08d-105">W tej sekcji funkcje udostępniane przez <xref:System.Reflection.Emit> przestrzeni nazw jest określany jako odbicia emisji.</span><span class="sxs-lookup"><span data-stu-id="3d08d-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="3d08d-106">Emisji odbicia zapewnia następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="3d08d-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="3d08d-107">Zdefiniuj uproszczone globalnych metod wykonywania użycie <xref:System.Reflection.Emit.DynamicMethod> klasy i wykonać je przy użyciu delegatów.</span><span class="sxs-lookup"><span data-stu-id="3d08d-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="3d08d-108">Definiowanie zestawów w czasie wykonywania i uruchamiać je lub zapisać je na dysku.</span><span class="sxs-lookup"><span data-stu-id="3d08d-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="3d08d-109">Definiowanie zestawów w czasie wykonywania, uruchamiaj je, a następnie zwolnij je i Zezwalaj na wyrzucanie elementów bezużytecznych odzyskać ich zasobów.</span><span class="sxs-lookup"><span data-stu-id="3d08d-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="3d08d-110">Zdefiniuj modułów w nowych zestawów w czasie wykonywania i uruchomić lub zapisać je na dysku.</span><span class="sxs-lookup"><span data-stu-id="3d08d-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="3d08d-111">Definiowanie typów modułów w czasie wykonywania, tworzenie wystąpień typów i wywołania ich metod.</span><span class="sxs-lookup"><span data-stu-id="3d08d-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="3d08d-112">Zdefiniuj informacje o symbolach dla określonych modułów, które mogą być używane przez narzędzi, takich jak debugery i profilery kodu.</span><span class="sxs-lookup"><span data-stu-id="3d08d-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="3d08d-113">Oprócz typów zarządzanych w <xref:System.Reflection.Emit> przestrzeni nazw, istnieją interfejsy niezarządzane metadanych, które są opisane w [interfejsy metadanych](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="3d08d-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="3d08d-114">Emisji odbicia zarządzanych zapewnia lepsze sprawdzanie błędów semantycznego i wyższym poziomie abstrakcji metadanych niż interfejsy niezarządzane metadanych.</span><span class="sxs-lookup"><span data-stu-id="3d08d-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="3d08d-115">Innym zasobem przydatne do pracy z MSIL i metadanych znajduje się dokumentacja Common Language Infrastructure (CLI), szczególnie "Partycja II: metadane definicji i semantyka" oraz "Partition III: CIL instrukcji Set".</span><span class="sxs-lookup"><span data-stu-id="3d08d-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="3d08d-116">Dokumentacja jest dostępna online na [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) i [witryny sieci Ecma Web](https://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="3d08d-116">The documentation is available online on [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](https://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d08d-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3d08d-117">In This Section</span></span>
  
[<span data-ttu-id="3d08d-118">Problemy związane z zabezpieczeniami, w odbiciu emisji</span><span class="sxs-lookup"><span data-stu-id="3d08d-118">Security issues in reflection emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
<span data-ttu-id="3d08d-119">W tym artykule opisano zabezpieczeń, które emitują problemy związane z tworzenie dynamicznych zestawów przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="3d08d-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="3d08d-120">[Porady: definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="3d08d-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="3d08d-121">Pokazuje, jak wykonać prostą metodę dynamiczną i metodę dynamiczną, która jest powiązana z wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="3d08d-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="3d08d-122">[Porady: Definiowanie typu ogólnego przy użyciu odbicia emisji](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="3d08d-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="3d08d-123">Pokazuje, jak utworzyć prosty typ ogólny z dwoma parametrami typu, instrukcje dotyczą parametrów typu klasy, interfejsu i ograniczeń specjalnych i tworzenie elementów członkowskich, które używać parametrów typu klasy jako typy parametrów i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="3d08d-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="3d08d-124">[Porady: definiowanie metody ogólnej przy użyciu odbicia emisji](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="3d08d-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="3d08d-125">Pokazuje, jak utworzyć, emisji i wywołania proste metody rodzajowej.</span><span class="sxs-lookup"><span data-stu-id="3d08d-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="3d08d-126">[Zestawy kolekcjonowane dla dynamicznego generowania typów](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="3d08d-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="3d08d-127">Wprowadza kolekcjonowane zestawów, które są dynamicznych zestawów, które może być rozładowany bez rozładowywania domeny aplikacji, w którym zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="3d08d-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="3d08d-128">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="3d08d-128">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="3d08d-129">Skatalogowano kody instrukcji MSIL, służących do tworzenia treści metod.</span><span class="sxs-lookup"><span data-stu-id="3d08d-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="3d08d-130">Zawiera klasy zarządzanej, używany do emitowania metody dynamicznej, zespoły i typów.</span><span class="sxs-lookup"><span data-stu-id="3d08d-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="3d08d-131">W tym artykule opisano <xref:System.Type> klasy, która reprezentuje typy w zarządzanych odbicia emisji odbicia i który ma kluczowe znaczenie dla korzystania z tych technologii.</span><span class="sxs-lookup"><span data-stu-id="3d08d-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="3d08d-132">Zawiera klasy zarządzane używane do eksplorowania metadanych i kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="3d08d-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3d08d-133">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3d08d-133">Related Sections</span></span>  
 [<span data-ttu-id="3d08d-134">Odbicie</span><span class="sxs-lookup"><span data-stu-id="3d08d-134">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="3d08d-135">Wyjaśnia, jak eksplorować metadanych i kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="3d08d-135">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="3d08d-136">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="3d08d-136">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="3d08d-137">Omówienie zestawów w implementacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3d08d-137">Provides an overview of assemblies in .NET implementations.</span></span>
