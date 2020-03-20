---
title: Emitowanie dynamicznych metod i zestawów
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180525"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="31190-102">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="31190-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="31190-103">W tej sekcji opisano zestaw <xref:System.Reflection.Emit> typów zarządzanych w obszarze nazw, które umożliwiają kompilatorowi lub narzędziu emitowanie metadanych i języka pośredniego firmy Microsoft (MSIL) w czasie wykonywania i opcjonalnie generowanie przenośnego pliku wykonywalnego (PE) na dysku.</span><span class="sxs-lookup"><span data-stu-id="31190-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="31190-104">Aparaty skryptów i kompilatory są podstawowymi użytkownikami tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="31190-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="31190-105">W tej sekcji funkcje udostępniane <xref:System.Reflection.Emit> przez obszar nazw jest określany jako emitować odbicia.</span><span class="sxs-lookup"><span data-stu-id="31190-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="31190-106">Emitowanie odbicia zapewnia następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="31190-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="31190-107">Zdefiniuj lekkie metody <xref:System.Reflection.Emit.DynamicMethod> globalne w czasie wykonywania, przy użyciu klasy i wykonaj je przy użyciu pełnomocników.</span><span class="sxs-lookup"><span data-stu-id="31190-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="31190-108">Zdefiniuj zestawy w czasie wykonywania, a następnie uruchom je i/lub zapisz na dysku.</span><span class="sxs-lookup"><span data-stu-id="31190-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="31190-109">Zdefiniuj zestawy w czasie wykonywania, uruchom je, a następnie zwolnij je i pozwól wyrzucaniu elementów bezużytecznych odzyskać swoje zasoby.</span><span class="sxs-lookup"><span data-stu-id="31190-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="31190-110">Zdefiniuj moduły w nowych złożeniach w czasie wykonywania, a następnie uruchom i/lub zapisz je na dysku.</span><span class="sxs-lookup"><span data-stu-id="31190-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="31190-111">Zdefiniuj typy w modułach w czasie wykonywania, utwórz wystąpienia tych typów i wywołaj ich metody.</span><span class="sxs-lookup"><span data-stu-id="31190-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="31190-112">Zdefiniuj informacje symboliczne dla zdefiniowanych modułów, które mogą być używane przez narzędzia, takie jak debugery i profileery kodu.</span><span class="sxs-lookup"><span data-stu-id="31190-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="31190-113">Oprócz typów zarządzanych w <xref:System.Reflection.Emit> obszarze nazw istnieją niezarządzane interfejsy metadanych, które są opisane w dokumentacji odwołania [do interfejsów metadanych.](../unmanaged-api/metadata/metadata-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="31190-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="31190-114">Emitowane odbicie zarządzane zapewnia silniejsze sprawdzanie błędów semantycznych i wyższy poziom abstrakcji metadanych niż interfejsy metadanych niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="31190-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="31190-115">Innym użytecznym zasobem do pracy z metadanymi i MSIL jest dokumentacja wspólnej infrastruktury języka (CLI), w szczególności "Partition II: Definicja metadanych i semantyka" i "Partycja III: Zestaw instrukcji CIL".</span><span class="sxs-lookup"><span data-stu-id="31190-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="31190-116">Dokumentacja jest dostępna online w [witrynie ecma w sieci Web](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="31190-116">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31190-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="31190-117">In This Section</span></span>
  
[<span data-ttu-id="31190-118">Problemy z bezpieczeństwem w refleksji emitują</span><span class="sxs-lookup"><span data-stu-id="31190-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="31190-119">W tym artykule opisano problemy z zabezpieczeniami związane z tworzeniem zestawów dynamicznych przy użyciu emisji odbicia.</span><span class="sxs-lookup"><span data-stu-id="31190-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="31190-120">[Jak: Definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md) Pokazuje, jak wykonać prostą metodę dynamiczną i metodę dynamiczną powiązaną z wystąpieniem klasy.</span><span class="sxs-lookup"><span data-stu-id="31190-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="31190-121">[Jak: Definiowanie typu ogólnego z emitować odbicie](how-to-define-a-generic-type-with-reflection-emit.md) Pokazuje, jak utworzyć prosty typ ogólny z dwoma parametrami typu, jak zastosować klasę, interfejs i ograniczenia specjalne do parametrów typu oraz jak utworzyć elementy członkowskie, które używają parametrów typu klasy jako typów parametrów i typów zwracanych.</span><span class="sxs-lookup"><span data-stu-id="31190-121">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="31190-122">[Jak: Zdefiniuj metodę rodzajową z emitować odbicie](how-to-define-a-generic-method-with-reflection-emit.md) Pokazuje, jak tworzyć, emitować i wywoływać prostą metodę rodzajową.</span><span class="sxs-lookup"><span data-stu-id="31190-122">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="31190-123">[Zespoły kolekcjonerskie do generowania typów dynamicznych](collectible-assemblies.md) Wprowadza zestawy kolekcjonerskie, które są zestawami dynamicznymi, które można zwolnić bez zwalniania domeny aplikacji, w której zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="31190-123">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="31190-124">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="31190-124">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="31190-125">Kataloguje kody instrukcji MSIL, których można użyć do tworzenia obiektów metody.</span><span class="sxs-lookup"><span data-stu-id="31190-125">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="31190-126">Zawiera klasy zarządzane używane do emitowania metod dynamicznych, zestawów i typów.</span><span class="sxs-lookup"><span data-stu-id="31190-126">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="31190-127">Opisuje <xref:System.Type> klasę, która reprezentuje typy w zarządzanych odbicia i odbicia emitują i który jest kluczem do korzystania z tych technologii.</span><span class="sxs-lookup"><span data-stu-id="31190-127">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="31190-128">Zawiera klasy zarządzane używane do eksplorowania metadanych i kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="31190-128">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="31190-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="31190-129">Related Sections</span></span>  

[<span data-ttu-id="31190-130">Odbicie</span><span class="sxs-lookup"><span data-stu-id="31190-130">Reflection</span></span>](reflection.md)  
<span data-ttu-id="31190-131">W tym artykule wyjaśniono, jak eksplorować metadane i kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="31190-131">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="31190-132">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="31190-132">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="31190-133">Zawiera omówienie zestawów w implementacjach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="31190-133">Provides an overview of assemblies in .NET implementations.</span></span>
