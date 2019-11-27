---
title: Emitowanie dynamicznych metod i zestawów
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 578851bed188921324e3c25e533b3466068dee3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446783"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="07b9d-102">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="07b9d-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="07b9d-103">W tej sekcji opisano zestaw typów zarządzanych w przestrzeni nazw <xref:System.Reflection.Emit>, które umożliwiają kompilatorowi lub narzędziu emitowanie metadanych i języka pośredniego firmy Microsoft (MSIL) w czasie wykonywania i opcjonalnie generowanie przenośnego pliku wykonywalnego (PE) na dysku.</span><span class="sxs-lookup"><span data-stu-id="07b9d-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="07b9d-104">Aparaty skryptów i kompilatory są podstawowymi użytkownikami tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="07b9d-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="07b9d-105">W tej sekcji funkcje zapewniane przez przestrzeń nazw <xref:System.Reflection.Emit> są określane jako emisja odbicia.</span><span class="sxs-lookup"><span data-stu-id="07b9d-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="07b9d-106">Emisja odbicia zapewnia następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="07b9d-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="07b9d-107">Zdefiniuj lekkie metody globalne w czasie wykonywania przy użyciu klasy <xref:System.Reflection.Emit.DynamicMethod> i wykonuj je za pomocą delegatów.</span><span class="sxs-lookup"><span data-stu-id="07b9d-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="07b9d-108">Zdefiniuj zestawy w czasie wykonywania, a następnie uruchom je i/lub Zapisz na dysku.</span><span class="sxs-lookup"><span data-stu-id="07b9d-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="07b9d-109">Zdefiniuj zestawy w czasie wykonywania, uruchom je, a następnie zwolnij i zezwól na odzyskiwanie elementów bezużytecznych w celu odtworzenia zasobów.</span><span class="sxs-lookup"><span data-stu-id="07b9d-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="07b9d-110">Zdefiniuj moduły w nowych zestawach w czasie wykonywania, a następnie uruchom i/lub Zapisz je na dysku.</span><span class="sxs-lookup"><span data-stu-id="07b9d-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="07b9d-111">Zdefiniuj typy w modułach w czasie wykonywania, twórz wystąpienia tych typów i Wywołaj ich metody.</span><span class="sxs-lookup"><span data-stu-id="07b9d-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="07b9d-112">Zdefiniuj informacje symboliczne dla zdefiniowanych modułów, które mogą być używane przez narzędzia, takie jak debugery i program do tworzenia kodu.</span><span class="sxs-lookup"><span data-stu-id="07b9d-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="07b9d-113">Oprócz typów zarządzanych w przestrzeni nazw <xref:System.Reflection.Emit> istnieją niezarządzane interfejsy metadanych, które opisano w dokumentacji dotyczącej [interfejsów metadanych](../unmanaged-api/metadata/metadata-interfaces.md) .</span><span class="sxs-lookup"><span data-stu-id="07b9d-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="07b9d-114">Emitowane emisje odbicia udostępniają silniejsze sprawdzanie błędów semantycznych i wyższy poziom abstrakcji metadanych niż niezarządzane interfejsy metadanych.</span><span class="sxs-lookup"><span data-stu-id="07b9d-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="07b9d-115">Innym przydatnym zasobem do pracy z metadanymi i MSIL jest dokumentacja Common Language Infrastructure (CLI), szczególnie "partycja II: definicja metadanych i semantyka" i "partycja III: zestaw instrukcji CIL".</span><span class="sxs-lookup"><span data-stu-id="07b9d-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="07b9d-116">Dokumentacja jest dostępna w trybie online w [witrynie sieci Web ECMA](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="07b9d-116">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="07b9d-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="07b9d-117">In This Section</span></span>
  
[<span data-ttu-id="07b9d-118">Problemy z zabezpieczeniami w emisji odbicia</span><span class="sxs-lookup"><span data-stu-id="07b9d-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="07b9d-119">Opisuje problemy z zabezpieczeniami związane z tworzeniem zestawów dynamicznych przy użyciu emisji odbicia.</span><span class="sxs-lookup"><span data-stu-id="07b9d-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="07b9d-120">[Instrukcje: Definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="07b9d-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="07b9d-121">Pokazuje, jak wykonać prostą metodę dynamiczną i metodę dynamiczną powiązaną z wystąpieniem klasy.</span><span class="sxs-lookup"><span data-stu-id="07b9d-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="07b9d-122">[Instrukcje: Definiowanie typu ogólnego przy użyciu emisji odbicia](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="07b9d-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="07b9d-123">Pokazuje, jak utworzyć prosty typ ogólny z dwoma parametrami typu, jak zastosować klasę, interfejs i ograniczenia specjalne do parametrów typu oraz jak tworzyć składowe, które używają parametrów typu klasy jako typów parametrów i zwracanych typów.</span><span class="sxs-lookup"><span data-stu-id="07b9d-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="07b9d-124">[Instrukcje: Definiowanie metody ogólnej przy użyciu emisji odbicia](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="07b9d-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="07b9d-125">Pokazuje, jak tworzyć, emitować i wywoływać prostą metodę rodzajową.</span><span class="sxs-lookup"><span data-stu-id="07b9d-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="07b9d-126">[Zestawy kolekcjonowane do generowania typów dynamicznych](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="07b9d-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="07b9d-127">Wprowadza zestawy kolekcjonowane, które są dynamicznymi zestawami, które można zwolnić bez zwalniania domeny aplikacji, w której zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="07b9d-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="07b9d-128">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="07b9d-128">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="07b9d-129">Kataloguje kody instrukcji MSIL, których można użyć do kompilowania treści metody.</span><span class="sxs-lookup"><span data-stu-id="07b9d-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="07b9d-130">Zawiera klasy zarządzane używane do emitowania metod, zestawów i typów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="07b9d-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="07b9d-131">Opisuje klasę <xref:System.Type>, która reprezentuje typy w zarządzanym zakresie odbicia i emisji odbicia, która jest kluczem do korzystania z tych technologii.</span><span class="sxs-lookup"><span data-stu-id="07b9d-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="07b9d-132">Zawiera zarządzane klasy służące do eksplorowania metadanych i kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="07b9d-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="07b9d-133">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="07b9d-133">Related Sections</span></span>  

[<span data-ttu-id="07b9d-134">Odbicie</span><span class="sxs-lookup"><span data-stu-id="07b9d-134">Reflection</span></span>](reflection.md)  
<span data-ttu-id="07b9d-135">Wyjaśnia, jak eksplorować metadane i kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="07b9d-135">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="07b9d-136">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="07b9d-136">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="07b9d-137">Zawiera omówienie zestawów w implementacjach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="07b9d-137">Provides an overview of assemblies in .NET implementations.</span></span>
