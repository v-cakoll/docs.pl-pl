---
title: "Niezależność od języka i elementy niezależne od języka"
description: "Dowiedz się, jak można tworzyć w jednym z wielu języków w programie .NET, takich jak C#, C + +/ CLI, F # IronPython, VB, Visual COBOL i programu PowerShell."
keywords: .NET, .NET core
author: dotnet-bot
ms.author: dotnetcontent
ms.date: 07/22/2016
ms.topic: article
dev_langs:
- csharp
- vb
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: ed48191ee397bb5f892a7afba6dfbfa2d06e1045
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="c3394-104">Niezależność od języka i elementy niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="c3394-104">Language independence and language-independent components</span></span>

<span data-ttu-id="c3394-105">.NET jest niezależny od języka.</span><span class="sxs-lookup"><span data-stu-id="c3394-105">.NET is language independent.</span></span> <span data-ttu-id="c3394-106">Oznacza to, że deweloper, można tworzyć w jednym z wielu języków, które odnoszą się do implementacji .NET, takich jak C#, F # i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3394-106">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="c3394-107">Dostępne typy i składniki bibliotek klas utworzonych dla implementacji .NET bez konieczności znajomości języka, w którym pierwotnie zostały zapisane i bez konieczności postępuj zgodnie z oryginalnego języka Konwencji.</span><span class="sxs-lookup"><span data-stu-id="c3394-107">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="c3394-108">Jeśli jesteś deweloperem składnika składnika jest dostępna przez dowolną aplikację .NET, niezależnie od języka.</span><span class="sxs-lookup"><span data-stu-id="c3394-108">If you are a component developer, your component can be accessed by any .NET app regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="c3394-109">To pierwsza część w tym artykule omówiono tworzenie niezależny od języka składników — czyli składników, które mogą być używane przez aplikacje, które są zapisywane w dowolnym języku.</span><span class="sxs-lookup"><span data-stu-id="c3394-109">This first part of this article discusses creating language-independent components - that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="c3394-110">Można również utworzyć pojedynczy składnik lub aplikacji z kodu źródłowego w wielu językach; zobacz [współdziałanie między językami](#cross-language-interoperability) w drugiej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="c3394-110">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span> 

<span data-ttu-id="c3394-111">Pełni interakcję z innymi obiektami w dowolnym języku, obiektów musi ujawniać dotyczące obiektów wywołujących te funkcje, które są wspólne dla wszystkich języków.</span><span class="sxs-lookup"><span data-stu-id="c3394-111">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="c3394-112">Ten zestaw typowych funkcji jest zdefiniowany przez wspólnej specyfikacji języka (CLS), który jest zestaw reguł stosowanych do zestawów wygenerowanych.</span><span class="sxs-lookup"><span data-stu-id="c3394-112">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="c3394-113">Specyfikacja języka wspólnego jest zdefiniowany w partycji I klauzule 7 do 11 [ECMA-335 standardowe: wspólną infrastrukturę języka](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="c3394-113">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span> 

<span data-ttu-id="c3394-114">Jeśli składnik spełnia specyfikacja języka wspólnego, może być zgodne ze specyfikacją CLS i są dostępne z kodu w zestawach napisane w języku programowania, który obsługuje ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-114">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="c3394-115">Można określić, czy składnik jest zgodny ze specyfikacja języka wspólnego w czasie kompilacji, stosując [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutu do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="c3394-115">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="c3394-116">Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="c3394-116">For more information, see The [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

<span data-ttu-id="c3394-117">W tym artykule:</span><span class="sxs-lookup"><span data-stu-id="c3394-117">In this article:</span></span>

* [<span data-ttu-id="c3394-118">Zasady zgodności ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="c3394-118">CLS compliance rules</span></span>](#cls-compliance-rules)

    * [<span data-ttu-id="c3394-119">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="c3394-119">Types and type member signatures</span></span>](#types-and-type-member-signatures)

    * [<span data-ttu-id="c3394-120">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="c3394-120">Naming conventions</span></span>](#naming-conventions)
    
    * [<span data-ttu-id="c3394-121">Konwersja typów</span><span class="sxs-lookup"><span data-stu-id="c3394-121">Type conversion</span></span>](#type-conversion)
    
    * [<span data-ttu-id="c3394-122">Tablice</span><span class="sxs-lookup"><span data-stu-id="c3394-122">Arrays</span></span>](#arrays)
    
    * [<span data-ttu-id="c3394-123">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3394-123">Interfaces</span></span>](#interfaces)
    
    * [<span data-ttu-id="c3394-124">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c3394-124">Enumerations</span></span>](#enumerations)
    
    * [<span data-ttu-id="c3394-125">Ogólnie rzecz biorąc wpisz elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c3394-125">Type members in general</span></span>](#type-members-in-general)
    
    * [<span data-ttu-id="c3394-126">Dostępność elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c3394-126">Member accessibility</span></span>](#member-accessibility)
    
    * [<span data-ttu-id="c3394-127">Typy ogólne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="c3394-127">Generic types and members</span></span>](#generic-types-and-members)
    
    * [<span data-ttu-id="c3394-128">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="c3394-128">Constructors</span></span>](#constructors)
    
    * [<span data-ttu-id="c3394-129">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-129">Properties</span></span>](#properties)
    
    * [<span data-ttu-id="c3394-130">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-130">Events</span></span>](#events)
    
    * [<span data-ttu-id="c3394-131">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="c3394-131">Overloads</span></span>](#overloads)
    
    * [<span data-ttu-id="c3394-132">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c3394-132">Exceptions</span></span>](#exceptions)
    
    * [<span data-ttu-id="c3394-133">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3394-133">Attributes</span></span>](#attributes)
    
* [<span data-ttu-id="c3394-134">Atrybut CLSCompliant</span><span class="sxs-lookup"><span data-stu-id="c3394-134">CLSCompliantAttribute attribute</span></span>](#the-clscompliantattribute-attribute)

* [<span data-ttu-id="c3394-135">Współdziałanie między językami</span><span class="sxs-lookup"><span data-stu-id="c3394-135">Cross-Language Interoperability</span></span>](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a><span data-ttu-id="c3394-136">Zasady zgodności ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="c3394-136">CLS compliance rules</span></span>

<span data-ttu-id="c3394-137">W tej sekcji omówiono reguł do tworzenia składnika zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-137">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="c3394-138">Pełną listę zasad, zobacz partycji I 11 klauzuli [ECMA-335 standardowe: wspólną infrastrukturę języka](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="c3394-138">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

> [!NOTE]
> <span data-ttu-id="c3394-139">Specyfikacja języka wspólnego omówiono każdej reguły zgodności ze specyfikacją CLS, zastosowanie w przypadku użytkowników (deweloperów, którzy są uzyskiwania dostępu do składnika, który jest zgodny ze specyfikacją CLS), platformy (deweloperów, którzy korzystają z kompilatora języka Aby utworzyć CLS-compliant biblioteki) i rozszerzeń (deweloperów, którzy tworzą narzędzia, takiego jak kompilatora języka lub analizator kodu tworzącego składniki zgodne ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="c3394-139">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="c3394-140">Ten artykuł dotyczy reguł odnoszących się do struktur.</span><span class="sxs-lookup"><span data-stu-id="c3394-140">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="c3394-141">Należy pamiętać, że niektóre reguły, które dotyczą Extender mogą również dotyczyć zestawy, które są tworzone przy użyciu [Reflection.Emit](xref:System.Reflection.Emit).</span><span class="sxs-lookup"><span data-stu-id="c3394-141">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span> 

<span data-ttu-id="c3394-142">Projektowanie składnik, który jest niezależny od języka, wystarczy dotyczą zasady zgodności ze specyfikacją CLS interfejs publiczny danego składnika.</span><span class="sxs-lookup"><span data-stu-id="c3394-142">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="c3394-143">Prywatnej implementacji nie ma być zgodny ze specyfikacją.</span><span class="sxs-lookup"><span data-stu-id="c3394-143">Your private implementation does not have to conform to the specification.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="c3394-144">Zasady zgodności ze specyfikacją CLS dotyczą tylko interfejs publiczny składnika, nie można jej prywatna implementacja.</span><span class="sxs-lookup"><span data-stu-id="c3394-144">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span> 

<span data-ttu-id="c3394-145">Na przykład innych niż podpisane liczby całkowite [bajtów](xref:System.Byte) nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-145">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="c3394-146">Ponieważ `Person` udostępnia klasy w poniższym przykładzie `Age` właściwości typu [UInt16](xref:System.UInt16), poniższy kod wyświetla ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c3394-146">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age 
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)> 

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge      
      End Get   
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'    
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

<span data-ttu-id="c3394-147">Możesz wprowadzić klasy osoby zgodne ze specyfikacją CLS, zmieniając typ `Age` właściwość z `UInt16` do [Int16](xref:System.Int16), który jest zgodny ze specyfikacją CLS, 16-bitową liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="c3394-147">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="c3394-148">Nie trzeba zmienić typ prywatna `personAge` pola.</span><span class="sxs-lookup"><span data-stu-id="c3394-148">You do not have to change the type of the private `personAge` field.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age 
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)> 

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)      
      End Get   
   End Property
End Class
```

<span data-ttu-id="c3394-149">Interfejs publiczny biblioteki składa się z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c3394-149">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="c3394-150">Definicje klas publicznych.</span><span class="sxs-lookup"><span data-stu-id="c3394-150">Definitions of public classes.</span></span>

* <span data-ttu-id="c3394-151">Definicje publiczne elementy członkowskie publicznych klas i definicje członków dostępne dla klas pochodnych (elementy chronione).</span><span class="sxs-lookup"><span data-stu-id="c3394-151">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span> 

* <span data-ttu-id="c3394-152">Parametry i zwracane typy metod publicznych klas publicznych i parametrów i zwracanych typów metod dostępne dla klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="c3394-152">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span> 

<span data-ttu-id="c3394-153">W poniższej tabeli wymieniono zasady zgodności ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-153">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="c3394-154">Tekst reguły jest zajęta dosłownego wyrażenia z [ECMA-335 standardowe: wspólną infrastrukturę języka](http://www.ecma-international.org/publications/standards/Ecma-335.htm), czyli Copyright 2012 międzynarodowej Ecma.</span><span class="sxs-lookup"><span data-stu-id="c3394-154">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](http://www.ecma-international.org/publications/standards/Ecma-335.htm), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="c3394-155">W poniższych sekcjach znajduje się bardziej szczegółowe informacje o tych reguł.</span><span class="sxs-lookup"><span data-stu-id="c3394-155">More detailed information about these rules is found in the following sections.</span></span> 

<span data-ttu-id="c3394-156">Kategoria</span><span class="sxs-lookup"><span data-stu-id="c3394-156">Category</span></span> | <span data-ttu-id="c3394-157">Zobacz</span><span class="sxs-lookup"><span data-stu-id="c3394-157">See</span></span> | <span data-ttu-id="c3394-158">Reguła</span><span class="sxs-lookup"><span data-stu-id="c3394-158">Rule</span></span> | <span data-ttu-id="c3394-159">Numer reguły</span><span class="sxs-lookup"><span data-stu-id="c3394-159">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="c3394-160">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="c3394-160">Accessibility</span></span> | [<span data-ttu-id="c3394-161">Dostępność elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c3394-161">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="c3394-162">Ułatwienia dostępu nie zmienia się w przypadku zastępowanie dziedziczonych metod, z wyjątkiem podczas przesłaniania metody dziedziczone z innego zestawu z ułatwieniami dostępu `family-or-assembly`.</span><span class="sxs-lookup"><span data-stu-id="c3394-162">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="c3394-163">W takim przypadku zastąpienie ma ułatwień dostępu `family`.</span><span class="sxs-lookup"><span data-stu-id="c3394-163">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="c3394-164">10</span><span class="sxs-lookup"><span data-stu-id="c3394-164">10</span></span>
<span data-ttu-id="c3394-165">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="c3394-165">Accessibility</span></span> | [<span data-ttu-id="c3394-166">Dostępność elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c3394-166">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="c3394-167">Widoczność i dostępności typów i członków się typy w podpisie dowolnego elementu członkowskiego jest widoczny i jest dostępny zawsze, gdy ten element członkowski jest widoczny i jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="c3394-167">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="c3394-168">Na przykład metodę publiczną, która jest widoczny spoza jej zestawu nie ma argument o typie jest widoczna tylko w zestawie.</span><span class="sxs-lookup"><span data-stu-id="c3394-168">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="c3394-169">Widoczność i dostępności typów tworzenia wystąpień typu ogólnego używane w podpisie dowolnego elementu członkowskiego jest widoczny i jest dostępny zawsze, gdy ten element członkowski jest widoczny i jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="c3394-169">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="c3394-170">Na przykład wystąpień typu ogólnego w podpisie elementu członkowskiego, który jest widoczny spoza jej zestawu nie posiada argumentów ogólnych, którego typ jest widoczna tylko w zestawie.</span><span class="sxs-lookup"><span data-stu-id="c3394-170">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="c3394-171">12</span><span class="sxs-lookup"><span data-stu-id="c3394-171">12</span></span>
<span data-ttu-id="c3394-172">Tablice</span><span class="sxs-lookup"><span data-stu-id="c3394-172">Arrays</span></span> | [<span data-ttu-id="c3394-173">Tablice</span><span class="sxs-lookup"><span data-stu-id="c3394-173">Arrays</span></span>](#arrays) | <span data-ttu-id="c3394-174">Tablice mają elementy o typie zgodnym ze specyfikacją CLS, oraz wszystkie wymiary tablicy posiada dolne granice tablicy o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="c3394-174">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="c3394-175">Fakt, że element jest tablicą i typ elementu tablicy wymaga aby odróżnić przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-175">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="c3394-176">Gdy przeładowanie opiera się na dwóch lub więcej tablicy typów typów elementów są nazw typów.</span><span class="sxs-lookup"><span data-stu-id="c3394-176">When overloading is based on two or more array types the element types shall be named types.</span></span> | <span data-ttu-id="c3394-177">16</span><span class="sxs-lookup"><span data-stu-id="c3394-177">16</span></span>
<span data-ttu-id="c3394-178">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3394-178">Attributes</span></span> | [<span data-ttu-id="c3394-179">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3394-179">Attributes</span></span>](#attributes) | <span data-ttu-id="c3394-180">Atrybuty powinny być typu [System.Attribute](xref:System.Attribute), lub dziedziczenie z tego typu.</span><span class="sxs-lookup"><span data-stu-id="c3394-180">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="c3394-181">41</span><span class="sxs-lookup"><span data-stu-id="c3394-181">41</span></span>
<span data-ttu-id="c3394-182">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3394-182">Attributes</span></span> | [<span data-ttu-id="c3394-183">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3394-183">Attributes</span></span>](#attributes) | <span data-ttu-id="c3394-184">Ze specyfikacją CLS umożliwia tylko podzbiór kodowania atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c3394-184">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="c3394-185">Są tylko typy, które pojawia się w tych kodowania (patrz partycji IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [ System.Single](xref:System.Single), [System.Double](xref:System.Double), i dowolnego typu wyliczenie oparte na zgodne ze specyfikacją CLS typu podstawowego liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="c3394-185">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="c3394-186">34</span><span class="sxs-lookup"><span data-stu-id="c3394-186">34</span></span>
<span data-ttu-id="c3394-187">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3394-187">Attributes</span></span> | [<span data-ttu-id="c3394-188">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3394-188">Attributes</span></span>](#attributes) | <span data-ttu-id="c3394-189">Ze specyfikacją CLS nie zezwala na Modyfikatory wymagane widocznego publicznie (`modreq`, zobacz II partycji), ale zezwala na Modyfikatory opcjonalne (`modopt`, zobacz II partycji) nie rozpoznaje.</span><span class="sxs-lookup"><span data-stu-id="c3394-189">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="c3394-190">35</span><span class="sxs-lookup"><span data-stu-id="c3394-190">35</span></span>
<span data-ttu-id="c3394-191">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="c3394-191">Constructors</span></span> | [<span data-ttu-id="c3394-192">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="c3394-192">Constructors</span></span>](#constructors) | <span data-ttu-id="c3394-193">Konstruktor obiektu są wywołać niektórych konstruktora wystąpienia klasy podstawowej przed wystąpieniem dostęp do danych odziedziczone wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="c3394-193">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="c3394-194">(To nie dotyczą typów wartości, które nie muszą mieć konstruktorów.)</span><span class="sxs-lookup"><span data-stu-id="c3394-194">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="c3394-195">21</span><span class="sxs-lookup"><span data-stu-id="c3394-195">21</span></span>
<span data-ttu-id="c3394-196">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="c3394-196">Constructors</span></span> | [<span data-ttu-id="c3394-197">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="c3394-197">Constructors</span></span>](#constructors) | <span data-ttu-id="c3394-198">Nie jest wymagany Konstruktor obiektów z wyjątkiem w ramach tworzenia obiektu, a jest nie można zainicjować obiektu dwa razy.</span><span class="sxs-lookup"><span data-stu-id="c3394-198">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="c3394-199">22</span><span class="sxs-lookup"><span data-stu-id="c3394-199">22</span></span>
<span data-ttu-id="c3394-200">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c3394-200">Enumerations</span></span> | [<span data-ttu-id="c3394-201">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c3394-201">Enumerations</span></span>](#enumerations) | <span data-ttu-id="c3394-202">Podstawowy typ wyliczeniowy powinien być typem wbudowanym liczby całkowitej ze specyfikacją CLS, nazwy pola są "value__" i to pole jest oznaczone jako `RTSpecialName`.</span><span class="sxs-lookup"><span data-stu-id="c3394-202">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="c3394-203">7</span><span class="sxs-lookup"><span data-stu-id="c3394-203">7</span></span>
<span data-ttu-id="c3394-204">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c3394-204">Enumerations</span></span> | [<span data-ttu-id="c3394-205">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c3394-205">Enumerations</span></span>](#enumerations) | <span data-ttu-id="c3394-206">Istnieją dwa różne rodzaje wyliczenia wskazywanym przez obecności lub braku [System.FlagsAttribute](xref:System.FlagsAttribute) atrybutu niestandardowego (zobacz Biblioteka IV partycji).</span><span class="sxs-lookup"><span data-stu-id="c3394-206">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="c3394-207">Reprezentuje jedną o nazwie liczby całkowite; inne reprezentuje nazwę flagi bitów, które można łączyć do generowania wartości bez nazwy.</span><span class="sxs-lookup"><span data-stu-id="c3394-207">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="c3394-208">Wartość `enum` nie jest ograniczony do określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="c3394-208">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="c3394-209">8</span><span class="sxs-lookup"><span data-stu-id="c3394-209">8</span></span>
<span data-ttu-id="c3394-210">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c3394-210">Enumerations</span></span> | [<span data-ttu-id="c3394-211">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c3394-211">Enumerations</span></span>](#enumerations) | <span data-ttu-id="c3394-212">Literał pola statyczne typu wyliczeniowego ma typ wyliczenia samej siebie.</span><span class="sxs-lookup"><span data-stu-id="c3394-212">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="c3394-213">9</span><span class="sxs-lookup"><span data-stu-id="c3394-213">9</span></span>
<span data-ttu-id="c3394-214">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-214">Events</span></span> | [<span data-ttu-id="c3394-215">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-215">Events</span></span>](#events) | <span data-ttu-id="c3394-216">Metody, które implementują zdarzenia są oznaczane `SpecialName` w metadanych.</span><span class="sxs-lookup"><span data-stu-id="c3394-216">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="c3394-217">29</span><span class="sxs-lookup"><span data-stu-id="c3394-217">29</span></span>
<span data-ttu-id="c3394-218">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-218">Events</span></span> | [<span data-ttu-id="c3394-219">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-219">Events</span></span>](#events) | <span data-ttu-id="c3394-220">Dostępność zdarzenia i jego metody dostępu muszą być identyczne.</span><span class="sxs-lookup"><span data-stu-id="c3394-220">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="c3394-221">30</span><span class="sxs-lookup"><span data-stu-id="c3394-221">30</span></span>
<span data-ttu-id="c3394-222">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-222">Events</span></span> | [<span data-ttu-id="c3394-223">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-223">Events</span></span>](#events) | <span data-ttu-id="c3394-224">`add` i `remove` metody dla zdarzenia są oba albo być obecny lub nieobecny.</span><span class="sxs-lookup"><span data-stu-id="c3394-224">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="c3394-225">31</span><span class="sxs-lookup"><span data-stu-id="c3394-225">31</span></span>
<span data-ttu-id="c3394-226">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-226">Events</span></span> | [<span data-ttu-id="c3394-227">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-227">Events</span></span>](#events) | <span data-ttu-id="c3394-228">`add` i `remove` metody zdarzenia przyjmują jeden parametr o typie definiuje typ zdarzenia i która pochodzi z [System.Delegate](xref:System.Delegate).</span><span class="sxs-lookup"><span data-stu-id="c3394-228">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="c3394-229">32</span><span class="sxs-lookup"><span data-stu-id="c3394-229">32</span></span>
<span data-ttu-id="c3394-230">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-230">Events</span></span> | [<span data-ttu-id="c3394-231">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-231">Events</span></span>](#events) | <span data-ttu-id="c3394-232">Zdarzenia będzie stosować się do określonego wzorca nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="c3394-232">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="c3394-233">Atrybut jako SpecialName określone w regule ze specyfikacją CLS 29 nie są uwzględniane w porównania odpowiednią nazwę i są oparte na identyfikator reguły.</span><span class="sxs-lookup"><span data-stu-id="c3394-233">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="c3394-234">33</span><span class="sxs-lookup"><span data-stu-id="c3394-234">33</span></span>
<span data-ttu-id="c3394-235">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c3394-235">Exceptions</span></span> | [<span data-ttu-id="c3394-236">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c3394-236">Exceptions</span></span>](#exceptions) | <span data-ttu-id="c3394-237">Obiekty, które są generowane jest typu [System.Exception](xref:System.Exception) lub dziedziczenie z tego typu.</span><span class="sxs-lookup"><span data-stu-id="c3394-237">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="c3394-238">Niemniej jednak metody zgodne ze specyfikacją CLS nie są wymagane do blokowania propagacji innych typów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="c3394-238">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="c3394-239">40</span><span class="sxs-lookup"><span data-stu-id="c3394-239">40</span></span>
<span data-ttu-id="c3394-240">Ogólne</span><span class="sxs-lookup"><span data-stu-id="c3394-240">General</span></span> | [<span data-ttu-id="c3394-241">Zasady zgodności ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="c3394-241">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="c3394-242">Reguły ze specyfikacją CLS mają zastosowanie tylko do tych elementów typu, które są dostępne lub widoczne outsideof zestawu definiującego.</span><span class="sxs-lookup"><span data-stu-id="c3394-242">CLS rules apply only to those parts of a type that are accessible or visible outsideof the defining assembly.</span></span> | <span data-ttu-id="c3394-243">1</span><span class="sxs-lookup"><span data-stu-id="c3394-243">1</span></span>
<span data-ttu-id="c3394-244">Ogólne</span><span class="sxs-lookup"><span data-stu-id="c3394-244">General</span></span> | [<span data-ttu-id="c3394-245">Zasady zgodności ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="c3394-245">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="c3394-246">Elementy członkowskie typów zgodnych ze specyfikacją CLS nie jest oznaczony zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-246">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="c3394-247">2</span><span class="sxs-lookup"><span data-stu-id="c3394-247">2</span></span>
<span data-ttu-id="c3394-248">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="c3394-248">Generics</span></span> | [<span data-ttu-id="c3394-249">Typy ogólne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="c3394-249">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="c3394-250">Typy zagnieżdżone mają co najmniej tyle parametry ogólne, jak typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="c3394-250">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="c3394-251">Parametry ogólne w typu zagnieżdżonego odpowiada za pomocą pozycji do parametrów ogólnych w jego typie otaczającym.</span><span class="sxs-lookup"><span data-stu-id="c3394-251">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="c3394-252">42</span><span class="sxs-lookup"><span data-stu-id="c3394-252">42</span></span>
<span data-ttu-id="c3394-253">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="c3394-253">Generics</span></span> | [<span data-ttu-id="c3394-254">Typy ogólne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="c3394-254">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="c3394-255">Nazwa typu ogólnego jest zakodowania liczba parametrów typu dla typu niezagnieżdżonego lub nowo wprowadzonych do typu, jeśli zagnieżdżony, zgodnie z regułami zdefiniowanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="c3394-255">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="c3394-256">43</span><span class="sxs-lookup"><span data-stu-id="c3394-256">43</span></span>
<span data-ttu-id="c3394-257">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="c3394-257">Generics</span></span> | [<span data-ttu-id="c3394-258">Typy ogólne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="c3394-258">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="c3394-259">Typ ogólny jest ponownie zadeklarować ograniczenia wystarczające, aby zagwarantować, że wszystkie ograniczenia dotyczące typu podstawowego lub interfejsy będzie spełniony przez ograniczeń typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="c3394-259">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="c3394-260">44</span><span class="sxs-lookup"><span data-stu-id="c3394-260">44</span></span>
<span data-ttu-id="c3394-261">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="c3394-261">Generics</span></span> | [<span data-ttu-id="c3394-262">Typy ogólne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="c3394-262">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="c3394-263">Typy używane jako ograniczenia dotyczące parametrów ogólnych są się zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-263">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="c3394-264">45</span><span class="sxs-lookup"><span data-stu-id="c3394-264">45</span></span>
<span data-ttu-id="c3394-265">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="c3394-265">Generics</span></span> | [<span data-ttu-id="c3394-266">Typy ogólne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="c3394-266">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="c3394-267">Widoczność i dostępności elementów członkowskich (w tym typy zagnieżdżone) w ogólnym typem skonkretyzowanym uznaje się ograniczyć zakres konkretnego wystąpienia zamiast deklaracji typu ogólnego jako całość.</span><span class="sxs-lookup"><span data-stu-id="c3394-267">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="c3394-268">Zakładając, że to, widoczność i dostępności reguły ze specyfikacją CLS 12 nadal zastosowanie zasady.</span><span class="sxs-lookup"><span data-stu-id="c3394-268">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="c3394-269">46</span><span class="sxs-lookup"><span data-stu-id="c3394-269">46</span></span>
<span data-ttu-id="c3394-270">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="c3394-270">Generics</span></span> | [<span data-ttu-id="c3394-271">Typy ogólne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="c3394-271">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="c3394-272">Dla każdej metodzie abstrakcyjnej ani wirtualnej ogólny jest domyślną konkretną implementację (nieabstrakcyjnej)</span><span class="sxs-lookup"><span data-stu-id="c3394-272">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="c3394-273">47</span><span class="sxs-lookup"><span data-stu-id="c3394-273">47</span></span>
<span data-ttu-id="c3394-274">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3394-274">Interfaces</span></span> | [<span data-ttu-id="c3394-275">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3394-275">Interfaces</span></span>](#interfaces) | <span data-ttu-id="c3394-276">Interfejsy zgodne ze specyfikacją CLS nie wymagają definicji compliantmethods niezgodny ze specyfikacją CLS w celu ich wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-276">CLS-compliant interfaces shall not require the definition of non-CLS compliantmethods in order to implement them.</span></span> | <span data-ttu-id="c3394-277">18</span><span class="sxs-lookup"><span data-stu-id="c3394-277">18</span></span>
<span data-ttu-id="c3394-278">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3394-278">Interfaces</span></span> | [<span data-ttu-id="c3394-279">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3394-279">Interfaces</span></span>](#interfaces) | <span data-ttu-id="c3394-280">Interfejsy zgodne ze specyfikacją CLS nie określają metody statyczne nie są one Definiowanie pól.</span><span class="sxs-lookup"><span data-stu-id="c3394-280">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="c3394-281">19</span><span class="sxs-lookup"><span data-stu-id="c3394-281">19</span></span>
<span data-ttu-id="c3394-282">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c3394-282">Members</span></span> | [<span data-ttu-id="c3394-283">Ogólnie rzecz biorąc wpisz elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c3394-283">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="c3394-284">Globalne pola statyczne i metod nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-284">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="c3394-285">36</span><span class="sxs-lookup"><span data-stu-id="c3394-285">36</span></span>
<span data-ttu-id="c3394-286">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c3394-286">Members</span></span> | -- | <span data-ttu-id="c3394-287">Przy użyciu metadanych inicjowania pola określona jest wartość literału statycznego.</span><span class="sxs-lookup"><span data-stu-id="c3394-287">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="c3394-288">Literał zgodne ze specyfikacją CLS muszą mieć określoną wartość w polu inicjowania metadanych, które jest taki sam typ, jak literał (lub podstawowego typu, jeśli ten literał `enum`).</span><span class="sxs-lookup"><span data-stu-id="c3394-288">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="c3394-289">13</span><span class="sxs-lookup"><span data-stu-id="c3394-289">13</span></span>
<span data-ttu-id="c3394-290">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c3394-290">Members</span></span> | [<span data-ttu-id="c3394-291">Ogólnie rzecz biorąc wpisz elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c3394-291">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="c3394-292">Ograniczenie vararg nie jest częścią ze specyfikacją CLS, a tylko Konwencja wywoływania obsługiwane przez ze specyfikacją CLS jest standardowego zarządzanych konwencję wywołania.</span><span class="sxs-lookup"><span data-stu-id="c3394-292">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="c3394-293">15</span><span class="sxs-lookup"><span data-stu-id="c3394-293">15</span></span>
<span data-ttu-id="c3394-294">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="c3394-294">Naming conventions</span></span> | [<span data-ttu-id="c3394-295">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="c3394-295">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="c3394-296">Zestawy postępuje zgodnie z załącznikiem 7 z techniczne raportu 15 Unicode Standard3.0 regulujące zestaw znaków mogą uruchomić i zawarte w identyfikatorach dostępnych online w [formuły normalizacji Unicode](http://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="c3394-296">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](http://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="c3394-297">Identyfikatory jest w formacie canonical zdefiniowane przez Unicode normalizacji formularza C. Do celów ze specyfikacją CLS, identifiersare dwa takie same, jeśli ich mapowania małe litery (zgodnie z instrukcjami w Unicode niezależne od ustawień regionalnych, jeden do jednego małe mapowania) są takie same.</span><span class="sxs-lookup"><span data-stu-id="c3394-297">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiersare the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="c3394-298">Oznacza to, że dla dwóch identyfikatorów wziąć pod uwagę różne zgodnie ze specyfikacją CLS są różnią się tylko w ich przypadku.</span><span class="sxs-lookup"><span data-stu-id="c3394-298">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="c3394-299">Jednak aby można było zastąpić dziedziczone definicji interfejsu wiersza polecenia wymaga dokładne kodowanie oryginalnej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="c3394-299">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="c3394-300">4</span><span class="sxs-lookup"><span data-stu-id="c3394-300">4</span></span>
<span data-ttu-id="c3394-301">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="c3394-301">Overloading</span></span> | [<span data-ttu-id="c3394-302">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="c3394-302">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="c3394-303">Nazwy wszystkich wprowadzonych w zakresie zgodne ze specyfikacją CLS są różne niezależnie od rodzaju, z wyjątkiem przypadków, w których nazwy są identyczne i rozwiązane za pomocą przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-303">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="c3394-304">Oznacza to, że chociaż CTS pozwala na jednym typie, do korzystania z tej samej nazwy dla metody i pole, ze specyfikacją CLS nie.</span><span class="sxs-lookup"><span data-stu-id="c3394-304">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="c3394-305">5</span><span class="sxs-lookup"><span data-stu-id="c3394-305">5</span></span>
<span data-ttu-id="c3394-306">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="c3394-306">Overloading</span></span> | [<span data-ttu-id="c3394-307">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="c3394-307">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="c3394-308">Pola i typy zagnieżdżone powinna różnić się przez porównanie identyfikator samodzielnie, eventhough CTS pozwala odrębnych podpisów rozróżnienie.</span><span class="sxs-lookup"><span data-stu-id="c3394-308">Fields and nested types shall be distinct by identifier comparison alone, eventhough the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="c3394-309">Metody, właściwości i zdarzenia, które mają taką samą nazwę (przez porównanie identyfikator) może różnić się nie tylko typem zwracanym, z wyjątkiem określonych w 39 reguły ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="c3394-309">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type,except as specified in CLS Rule 39</span></span> | <span data-ttu-id="c3394-310">6</span><span class="sxs-lookup"><span data-stu-id="c3394-310">6</span></span>
<span data-ttu-id="c3394-311">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="c3394-311">Overloading</span></span> | [<span data-ttu-id="c3394-312">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="c3394-312">Overloads</span></span>](#overloads) | <span data-ttu-id="c3394-313">Tylko właściwości i metody może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="c3394-313">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="c3394-314">37</span><span class="sxs-lookup"><span data-stu-id="c3394-314">37</span></span>
<span data-ttu-id="c3394-315">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="c3394-315">Overloading</span></span> | [<span data-ttu-id="c3394-316">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="c3394-316">Overloads</span></span>](#overloads) |<span data-ttu-id="c3394-317">Właściwości i metody mogą być przeciążone tylko na podstawie liczby i typów ich parametrów, z wyjątkiem operatory konwersji o nazwie `op_Implicit` i `op_Explicit`, które również można przeciążać na podstawie ich zwracanego typu.</span><span class="sxs-lookup"><span data-stu-id="c3394-317">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="c3394-318">38</span><span class="sxs-lookup"><span data-stu-id="c3394-318">38</span></span>
<span data-ttu-id="c3394-319">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="c3394-319">Overloading</span></span> | -- | <span data-ttu-id="c3394-320">Co najmniej dwie metody zgodne ze specyfikacją CLS zadeklarowana w typie ma tego samego nameand, dla określonej grupy wystąpień typu mają ten sam parametr i typy zwracane, a następnie tych metod jest semantycznie równoważne w tych wystąpień typu.</span><span class="sxs-lookup"><span data-stu-id="c3394-320">If two or more CLS-compliant methods declared in a type have the same nameand, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="c3394-321">48</span><span class="sxs-lookup"><span data-stu-id="c3394-321">48</span></span>
<span data-ttu-id="c3394-322">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-322">Properties</span></span> | [<span data-ttu-id="c3394-323">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-323">Properties</span></span>](#properties) | <span data-ttu-id="c3394-324">Metody, które implementują metody pobierającej i ustawiającej właściwość jest oznaczona jako `SpecialName` w metadanych.</span><span class="sxs-lookup"><span data-stu-id="c3394-324">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="c3394-325">24</span><span class="sxs-lookup"><span data-stu-id="c3394-325">24</span></span>
<span data-ttu-id="c3394-326">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-326">Properties</span></span> | [<span data-ttu-id="c3394-327">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-327">Properties</span></span>](#properties) | <span data-ttu-id="c3394-328">Metody dostępu właściwości zostaje być wszystkie statyczne, wszystkie wirtualne lub wszystkie można instancji.</span><span class="sxs-lookup"><span data-stu-id="c3394-328">A property’s accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="c3394-329">26</span><span class="sxs-lookup"><span data-stu-id="c3394-329">26</span></span>
<span data-ttu-id="c3394-330">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-330">Properties</span></span> | [<span data-ttu-id="c3394-331">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-331">Properties</span></span>](#properties) | <span data-ttu-id="c3394-332">Typ właściwości jest zwracany typ metody pobierającej i typ ostatni argument metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="c3394-332">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="c3394-333">Typy parametrów właściwości są typy parametrów metody pobierającej i wszystkie typy, ale ostatni parametr metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="c3394-333">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="c3394-334">Wszystkie te typy są zgodne ze specyfikacją CLS, a nie są zarządzane wskaźników (to znaczy nie mogą być przekazywane przez odwołanie).</span><span class="sxs-lookup"><span data-stu-id="c3394-334">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="c3394-335">27</span><span class="sxs-lookup"><span data-stu-id="c3394-335">27</span></span>
<span data-ttu-id="c3394-336">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-336">Properties</span></span> | [<span data-ttu-id="c3394-337">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-337">Properties</span></span>](#properties) | <span data-ttu-id="c3394-338">Właściwości będzie stosować się do określonego wzorca nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="c3394-338">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="c3394-339">`SpecialName` Atrybut określone w regule ze specyfikacją CLS 24 nie będą uwzględniane w porównania odpowiednią nazwę i będzie stosować się do identyfikatora reguły.</span><span class="sxs-lookup"><span data-stu-id="c3394-339">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="c3394-340">Właściwość ma metodę metody pobierającej i/lub metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="c3394-340">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="c3394-341">28</span><span class="sxs-lookup"><span data-stu-id="c3394-341">28</span></span>
<span data-ttu-id="c3394-342">Konwersja typów</span><span class="sxs-lookup"><span data-stu-id="c3394-342">Type conversion</span></span> | [<span data-ttu-id="c3394-343">Konwersja typów</span><span class="sxs-lookup"><span data-stu-id="c3394-343">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="c3394-344">Jeśli podano op_Implicit lub op_Explicit dostarcza alternatywne metody udostępniania wymuszenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-344">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="c3394-345">39</span><span class="sxs-lookup"><span data-stu-id="c3394-345">39</span></span>
<span data-ttu-id="c3394-346">Types</span><span class="sxs-lookup"><span data-stu-id="c3394-346">Types</span></span> | [<span data-ttu-id="c3394-347">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="c3394-347">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="c3394-348">Spakowane typy wartości nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-348">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="c3394-349">3</span><span class="sxs-lookup"><span data-stu-id="c3394-349">3</span></span>
<span data-ttu-id="c3394-350">Types</span><span class="sxs-lookup"><span data-stu-id="c3394-350">Types</span></span> | [<span data-ttu-id="c3394-351">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="c3394-351">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="c3394-352">Wszystkie typy w podpis jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-352">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="c3394-353">Wszystkie typy tworzenia wystąpień typu ogólnego jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-353">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="c3394-354">11</span><span class="sxs-lookup"><span data-stu-id="c3394-354">11</span></span>
<span data-ttu-id="c3394-355">Types</span><span class="sxs-lookup"><span data-stu-id="c3394-355">Types</span></span> | [<span data-ttu-id="c3394-356">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="c3394-356">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="c3394-357">Odwołania do typu nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-357">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="c3394-358">14</span><span class="sxs-lookup"><span data-stu-id="c3394-358">14</span></span>
<span data-ttu-id="c3394-359">Types</span><span class="sxs-lookup"><span data-stu-id="c3394-359">Types</span></span> | [<span data-ttu-id="c3394-360">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="c3394-360">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="c3394-361">Typy wskaźników niezarządzanych nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-361">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="c3394-362">17</span><span class="sxs-lookup"><span data-stu-id="c3394-362">17</span></span>
<span data-ttu-id="c3394-363">Types</span><span class="sxs-lookup"><span data-stu-id="c3394-363">Types</span></span> | [<span data-ttu-id="c3394-364">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="c3394-364">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="c3394-365">Klasy zgodne ze specyfikacją CLS, typy wartości i interfejsy nie wymagają wykonania elementy członkowskie z systemem innym niż zgodne-ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="c3394-365">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="c3394-366">20</span><span class="sxs-lookup"><span data-stu-id="c3394-366">20</span></span>
<span data-ttu-id="c3394-367">Types</span><span class="sxs-lookup"><span data-stu-id="c3394-367">Types</span></span> | [<span data-ttu-id="c3394-368">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="c3394-368">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="c3394-369">[System.Object](xref:System.Object) jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-369">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="c3394-370">Inne klasy zgodne ze specyfikacją CLS są dziedziczy z klasy, zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-370">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="c3394-371">23</span><span class="sxs-lookup"><span data-stu-id="c3394-371">23</span></span>

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="c3394-372">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="c3394-372">Types and type member signatures</span></span>

<span data-ttu-id="c3394-373">[System.Object](xref:System.Object) typ jest zgodny ze specyfikacją CLS i jest podstawowym typem wszystkie typy obiektów w systemie typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3394-373">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET Framework type system.</span></span> <span data-ttu-id="c3394-374">Dziedziczenia w programie .NET Framework jest albo niejawne (na przykład [ciąg](xref:System.String) klasy niejawnie dziedziczy `Object` klasy) bezpośredniego lub pośredniego (na przykład [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) Klasa jawnie dziedziczy [ArgumentException](xref:System.ArgumentException) klasy, która dziedziczy po jawnie [wyjątek](xref:System.Exception) klasy.</span><span class="sxs-lookup"><span data-stu-id="c3394-374">Inheritance in the .NET Framework is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="c3394-375">Typ pochodny być zgodne ze specyfikacją CLS jego typ podstawowy również musi być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-375">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span> 

<span data-ttu-id="c3394-376">W poniższym przykładzie przedstawiono typem pochodnym, którego typ podstawowy nie jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-376">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="c3394-377">Definiuje podstawowej `Counter` klasy, która używa jako licznik całkowitą bez znaku 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="c3394-377">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="c3394-378">Ponieważ ta klasa dostarcza funkcje licznika zawijania całkowitą bez znaku, klasa jest oznaczona jako niezgodne-ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-378">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="c3394-379">W rezultacie Klasa pochodna `NonZeroCounter`, również jest niezgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-379">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)] 
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return String.Format("{0}). ", ctr);
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment() 
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _ 
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return String.Format("{0}). ", ctr)
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant 
'    because it derives from 'Counter', which is not CLS-compliant.
'    
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

<span data-ttu-id="c3394-380">Wszystkie typy, które pojawiają się w podpisach elementu członkowskiego, w tym zwracany typ metody lub typ właściwości musi być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-380">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="c3394-381">Ponadto dla typów ogólnych:</span><span class="sxs-lookup"><span data-stu-id="c3394-381">In addition, for generic types:</span></span> 

* <span data-ttu-id="c3394-382">Wszystkie typy, które tworzą ogólnego typu musi być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-382">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="c3394-383">Wszystkie typy używane jako ograniczenia dotyczące parametrów ogólnych musi być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-383">All types used as constraints on generic parameters must be CLS-compliant.</span></span> 

<span data-ttu-id="c3394-384">.NET [wspólny system typów](common-type-system.md) zawiera kilka wbudowanych typów, które są obsługiwane bezpośrednio przez środowisko uruchomieniowe języka wspólnego i specjalnie są zakodowane w metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="c3394-384">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="c3394-385">Te typy wewnętrzne typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-385">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span> 


<span data-ttu-id="c3394-386">Typie zgodnym ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="c3394-386">CLS-compliant type</span></span> | <span data-ttu-id="c3394-387">Opis</span><span class="sxs-lookup"><span data-stu-id="c3394-387">Description</span></span>
------------------ | -----------
[<span data-ttu-id="c3394-388">Bajtów</span><span class="sxs-lookup"><span data-stu-id="c3394-388">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="c3394-389">8-bitową liczbę całkowitą bez znaku</span><span class="sxs-lookup"><span data-stu-id="c3394-389">8-bit unsigned integer</span></span> 
[<span data-ttu-id="c3394-390">Int16</span><span class="sxs-lookup"><span data-stu-id="c3394-390">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="c3394-391">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="c3394-391">16-bit signed integer</span></span> 
[<span data-ttu-id="c3394-392">Int32</span><span class="sxs-lookup"><span data-stu-id="c3394-392">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="c3394-393">32-bitowej liczby całkowitej ze znakiem</span><span class="sxs-lookup"><span data-stu-id="c3394-393">32-bit signed integer</span></span> 
[<span data-ttu-id="c3394-394">Int64</span><span class="sxs-lookup"><span data-stu-id="c3394-394">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="c3394-395">64-bitowej liczby całkowitej ze znakiem</span><span class="sxs-lookup"><span data-stu-id="c3394-395">64-bit signed integer</span></span>
[<span data-ttu-id="c3394-396">Pojedynczy</span><span class="sxs-lookup"><span data-stu-id="c3394-396">Single</span></span>](xref:System.Single) | <span data-ttu-id="c3394-397">Wartość zmiennoprzecinkową o pojedynczej dokładności</span><span class="sxs-lookup"><span data-stu-id="c3394-397">Single-precision floating-point value</span></span>
[<span data-ttu-id="c3394-398">O podwójnej precyzji</span><span class="sxs-lookup"><span data-stu-id="c3394-398">Double</span></span>](xref:System.Double) | <span data-ttu-id="c3394-399">Wartość zmiennoprzecinkową podwójnej precyzji</span><span class="sxs-lookup"><span data-stu-id="c3394-399">Double-precision floating-point value</span></span>
[<span data-ttu-id="c3394-400">Wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="c3394-400">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="c3394-401">Typ wartości PRAWDA lub FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="c3394-401">true or false value type</span></span> 
[<span data-ttu-id="c3394-402">Char</span><span class="sxs-lookup"><span data-stu-id="c3394-402">Char</span></span>](xref:System.Char) | <span data-ttu-id="c3394-403">Jednostka zakodowanego kodu UTF-16</span><span class="sxs-lookup"><span data-stu-id="c3394-403">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="c3394-404">Decimal</span><span class="sxs-lookup"><span data-stu-id="c3394-404">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="c3394-405">Liczba dziesiętna non--zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="c3394-405">Non-floating-point decimal number</span></span>
[<span data-ttu-id="c3394-406">IntPtr</span><span class="sxs-lookup"><span data-stu-id="c3394-406">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="c3394-407">Wskaźnika lub dojścia o rozmiarze określone platformy</span><span class="sxs-lookup"><span data-stu-id="c3394-407">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="c3394-408">Ciąg</span><span class="sxs-lookup"><span data-stu-id="c3394-408">String</span></span>](xref:System.String) | <span data-ttu-id="c3394-409">Kolekcja zero, co najmniej jeden obiekt Char</span><span class="sxs-lookup"><span data-stu-id="c3394-409">Collection of zero, one, or more Char objects</span></span> 
 
<span data-ttu-id="c3394-410">Typy wewnętrzne wymienione w poniższej tabeli nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-410">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>


<span data-ttu-id="c3394-411">Niezgodny typ</span><span class="sxs-lookup"><span data-stu-id="c3394-411">Non-compliant type</span></span> | <span data-ttu-id="c3394-412">Opis</span><span class="sxs-lookup"><span data-stu-id="c3394-412">Description</span></span> | <span data-ttu-id="c3394-413">Alternatywnym, zgodnym ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="c3394-413">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="c3394-414">Sbyte —</span><span class="sxs-lookup"><span data-stu-id="c3394-414">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="c3394-415">Typ danych 8-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="c3394-415">8-bit signed integer data type</span></span> | [<span data-ttu-id="c3394-416">Int16</span><span class="sxs-lookup"><span data-stu-id="c3394-416">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="c3394-417">UInt16</span><span class="sxs-lookup"><span data-stu-id="c3394-417">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="c3394-418">16-bitową liczbę całkowitą bez znaku</span><span class="sxs-lookup"><span data-stu-id="c3394-418">16-bit unsigned integer</span></span> | [<span data-ttu-id="c3394-419">Int32</span><span class="sxs-lookup"><span data-stu-id="c3394-419">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="c3394-420">UInt32</span><span class="sxs-lookup"><span data-stu-id="c3394-420">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="c3394-421">32-bitowa liczba całkowita bez znaku</span><span class="sxs-lookup"><span data-stu-id="c3394-421">32-bit unsigned integer</span></span> | [<span data-ttu-id="c3394-422">Int64</span><span class="sxs-lookup"><span data-stu-id="c3394-422">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="c3394-423">UInt64 —</span><span class="sxs-lookup"><span data-stu-id="c3394-423">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="c3394-424">64-bitowej liczby całkowitej bez znaku</span><span class="sxs-lookup"><span data-stu-id="c3394-424">64-bit unsigned integer</span></span> | <span data-ttu-id="c3394-425">[Int64](xref:System.Int64) (może przepełnienie), [BigInteger](xref:System.Numerics.BigInteger), lub [podwójne](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="c3394-425">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="c3394-426">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="c3394-426">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="c3394-427">Niepodpisane wskaźnika lub dojścia</span><span class="sxs-lookup"><span data-stu-id="c3394-427">Unsigned pointer or handle</span></span> | [<span data-ttu-id="c3394-428">IntPtr</span><span class="sxs-lookup"><span data-stu-id="c3394-428">IntPtr</span></span>](xref:System.IntPtr)
 
 <span data-ttu-id="c3394-429">Biblioteka klas programu .NET Framework lub inne biblioteki klas może zawierać innych typów, które nie są zgodne z CLS; na przykład:</span><span class="sxs-lookup"><span data-stu-id="c3394-429">The .NET Framework Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span> 
 
 * <span data-ttu-id="c3394-430">Spakowanymi typami wartości.</span><span class="sxs-lookup"><span data-stu-id="c3394-430">Boxed value types.</span></span> <span data-ttu-id="c3394-431">W poniższym przykładzie C# tworzy klasę, która ma właściwości publicznej typu `int`* o nazwie `Value`.</span><span class="sxs-lookup"><span data-stu-id="c3394-431">The following C# example creates a class that has a public property of type `int`* named `Value`.</span></span> <span data-ttu-id="c3394-432">Ponieważ `int`* jest opakowanym typem wartościowym, kompilator flagi go jako niezgodne-ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-432">Because an `int`* is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public unsafe class TestClass
  {
     private int* val;

     public TestClass(int number)
     {
        val = (int*) number;
     }

     public int* Value {
        get { return val; }        
     }
  }
  // The compiler generates the following output when compiling this example:
  //        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
  ```

* <span data-ttu-id="c3394-433">Odwołania typu, które są specjalne konstrukcje, które zawierają odwołania do obiektu i odwołania do typu.</span><span class="sxs-lookup"><span data-stu-id="c3394-433">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="c3394-434">Jeśli typ nie jest zgodne ze specyfikacją CLS, należy zastosować [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutem *isCompliant* parametru z wartością `false` do niego.</span><span class="sxs-lookup"><span data-stu-id="c3394-434">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="c3394-435">Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute) sekcji.</span><span class="sxs-lookup"><span data-stu-id="c3394-435">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>  

<span data-ttu-id="c3394-436">Poniższy przykład przedstawia problem zgodności ze specyfikacją CLS w podpisie metody i podczas tworzenia wystąpienia typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="c3394-436">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="c3394-437">Definiuje `InvoiceItem` z właściwością typu [UInt32](xref:System.UInt32), właściwość typu [Nullable (z UInt32)](xref:System.Nullable%601)ani konstruktora z parametrami typu `UInt32` i `Nullable(Of UInt32)`.</span><span class="sxs-lookup"><span data-stu-id="c3394-437">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="c3394-438">Otrzymasz cztery ostrzeżeń kompilatora podczas kompilowania w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c3394-438">You get four compiler warnings when you try to compile this example.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get   
      Set 
         qty = value
      End Set   
   End Property

   Public Property InvoiceId As UInteger
      Get   
         Return invId
      End Get
      Set 
         invId = value
      End Set   
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'    
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'    
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'    
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'    
'       Public Property InvoiceId As UInteger
```

<span data-ttu-id="c3394-439">Aby wyeliminować ostrzeżeń kompilatora, Zastąp ze specyfikacją CLS-niezgodnych typów w `InvoiceItem` interfejs publiczny z typów zgodnych:</span><span class="sxs-lookup"><span data-stu-id="c3394-439">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set { 
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get   
      Set 
         qty = value
      End Set   
   End Property

   Public Property InvoiceId As Integer
      Get   
         Return CInt(invId)
      End Get
      Set 
         invId = CUInt(value)
      End Set   
   End Property
End Class
```

<span data-ttu-id="c3394-440">Oprócz folderów dla określonych typów wymienionych niektóre kategorie typów nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-440">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="c3394-441">Obejmują one typy niezarządzanych wskaźników i typów wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="c3394-441">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="c3394-442">Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej w celu utworzenia tablicy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="c3394-442">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}   
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```vb
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}   
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

<span data-ttu-id="c3394-443">Klasy abstrakcyjne dla zgodne ze specyfikacją CLS (czyli oznaczenie klasy `abstract` w języku C#), wszystkie elementy członkowskie klasy również musi być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-443">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span> 

### <a name="naming-conventions"></a><span data-ttu-id="c3394-444">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="c3394-444">Naming conventions</span></span>

<span data-ttu-id="c3394-445">Ponieważ niektóre języki programowania jest rozróżniana wielkość liter, identyfikatory (takich jak nazwy przestrzeni nazw, typy i składniki) musi się różnić tylko wielkością liter.</span><span class="sxs-lookup"><span data-stu-id="c3394-445">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="c3394-446">Dwa identyfikatory są traktowane jako równoważne, jeśli ich małe mapowania są takie same.</span><span class="sxs-lookup"><span data-stu-id="c3394-446">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="c3394-447">W poniższym przykładzie C# definiuje dwie klasy publicznej, `Person` i `person`.</span><span class="sxs-lookup"><span data-stu-id="c3394-447">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="c3394-448">Ponieważ różnią się tylko wielkością liter, kompilator języka C# flagi je jako nie zgodne z CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-448">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing 
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

<span data-ttu-id="c3394-449">Programowanie identyfikatorów języka, takich jak nazwy przestrzeni nazw, typów i członków, musi być zgodna z [Unicode Standard 3.0, techniczne 15 raportu, załącznik 7](http://www.unicode.org/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="c3394-449">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard 3.0, Technical Report 15, Annex 7](http://www.unicode.org/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="c3394-450">Oznacza to, że:</span><span class="sxs-lookup"><span data-stu-id="c3394-450">This means that:</span></span>

* <span data-ttu-id="c3394-451">Pierwszy znak identyfikatora mogą być dowolnej Unicode wielkie litery, małe litery, tytuł wielkość list, litera modyfikatora, innego litery lub list numer.</span><span class="sxs-lookup"><span data-stu-id="c3394-451">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="c3394-452">Aby uzyskać informacje na kategorie znaków Unicode, zobacz [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-452">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span> 

* <span data-ttu-id="c3394-453">Kolejne znaki mogą pochodzić z jednej z kategorii jako pierwszy znak i mogą również obejmować znaczniki bez spacji, odstępy łączenie znaki, liczby dziesiętne, łączące znaki interpunkcyjne i kody formatowania.</span><span class="sxs-lookup"><span data-stu-id="c3394-453">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuations, and formatting codes.</span></span> 

<span data-ttu-id="c3394-454">Przed porównywania identyfikatorów, należy odfiltrować kody formatowania i dokonać konwersji identyfikatory C formularza normalizacji Unicode, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu algorytmem UTF-16.</span><span class="sxs-lookup"><span data-stu-id="c3394-454">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="c3394-455">Sekwencje znaków, które powodują powstanie tej samej jednostki kodu w języku C formularza normalizacji Unicode nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-455">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="c3394-456">W poniższym przykładzie zdefiniowano właściwość o nazwie `Å`, który składa się z znaku ANGSTROM znak (U + 212B) i drugi właściwość o nazwie `Å` składające się z znak LATIN litera A z PIERŚCIEŃ powyżej (U + 00 C 5).</span><span class="sxs-lookup"><span data-stu-id="c3394-456">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å` which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="c3394-457">Kompilator języka C# flagi kodu źródłowego jako niezgodne-ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-457">The C# compiler flags the source code as non-CLS-compliant.</span></span>

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }         

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set 
          a1 = value
       End Set
   End Property         

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set   
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'    
'       Public Property Å As Double
'                       ~
```

<span data-ttu-id="c3394-458">Nazwy elementów członkowskich z określonego zakresu (na przykład przestrzeni nazw w zestawie, typy w przestrzeni nazw lub elementy członkowskie w określonym typie) musi być unikatowa, z wyjątkiem nazw, które są rozpoznawane za pomocą przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-458">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="c3394-459">To wymaganie jest bardziej rygorystyczne niż wspólny system typów, dzięki czemu wiele elementów członkowskich w zakresie mają identyczne nazwy tak długo, jak są one różne rodzaje elementów członkowskich (na przykład, jeden to metoda i jedna jest polem).</span><span class="sxs-lookup"><span data-stu-id="c3394-459">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="c3394-460">W szczególności dla elementów członkowskich typu:</span><span class="sxs-lookup"><span data-stu-id="c3394-460">In particular, for type members:</span></span> 

* <span data-ttu-id="c3394-461">Pola i typy zagnieżdżone są rozróżnianych na podstawie samej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c3394-461">Fields and nested types are distinguished by name alone.</span></span> 

* <span data-ttu-id="c3394-462">Metody, właściwości i zdarzenia, które mają taką samą nazwę musi się różnić się bardziej niż tylko typem zwracanym.</span><span class="sxs-lookup"><span data-stu-id="c3394-462">Methods, properties, and events that have the same name must differ by more than just return type.</span></span> 

<span data-ttu-id="c3394-463">Poniższy przykład przedstawia wymaganie, że nazwy składników muszą być unikatowe w ich zakresie.</span><span class="sxs-lookup"><span data-stu-id="c3394-463">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="c3394-464">Definiuje klasę o nazwie `Converter` który obejmuje cztery elementy członkowskie o nazwie `Conversion`.</span><span class="sxs-lookup"><span data-stu-id="c3394-464">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="c3394-465">Są trzy metody, a jeden z nich jest właściwością.</span><span class="sxs-lookup"><span data-stu-id="c3394-465">Three are methods, and one is a property.</span></span> <span data-ttu-id="c3394-466">Metoda, która obejmuje `Int64` parametru jest unikatowo o nazwie, ale te dwie metody z `Int32` parametru są, ponieważ wartość zwrotna nie jest uznawany za część podpisu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c3394-466">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="c3394-467">`Conversion` Właściwość również narusza to wymaganie, ponieważ właściwości nie mogą mieć taką samą nazwę jak przeciążonej metody.</span><span class="sxs-lookup"><span data-stu-id="c3394-467">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }     
}  
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get   
   End Property     
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double' 
'                    and 'Public Function Conversion(number As Integer) As Single' cannot 
'                    overload each other because they differ only by return types.
'    
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function 
'                     Conversion(number As Integer) As Single' in this class.
'    
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

<span data-ttu-id="c3394-468">Poszczególne języki unikatowych słów kluczowych, więc języków przeznaczonych środowisko uruchomieniowe języka wspólnego należy również podać mechanizmu dla odwołania do identyfikatorów (na przykład wpisz nazwy), które pokrywają się z słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="c3394-468">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="c3394-469">Na przykład `case` jest słowem kluczowym w języku C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3394-469">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="c3394-470">Jednak w poniższym przykładzie w języku Visual Basic jest w stanie odróżnić klasę o nazwie `case` z `case` — słowo kluczowe przy użyciu otwierające i zamykające nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="c3394-470">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="c3394-471">W przeciwnym razie przykładzie tworzy komunikat o błędzie, "— słowo kluczowe nie jest prawidłowe jako identyfikator" i nie można skompilować.</span><span class="sxs-lookup"><span data-stu-id="c3394-471">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span> 

```vb
Public Class [case]
   Private _id As Guid
   Private name As String  

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name 
   End Sub   

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

<span data-ttu-id="c3394-472">W poniższym przykładzie C# jest w stanie utworzyć wystąpienia `case` przy użyciu symbolu, aby usunąć niejednoznaczność identyfikator ze słowem kluczowym języka @.</span><span class="sxs-lookup"><span data-stu-id="c3394-472">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="c3394-473">Bez tego kompilatora C# będzie wyświetlane dwa komunikaty o błędach, "Oczekiwano typu" i "nieprawidłowe wyrażenie termin"case"."</span><span class="sxs-lookup"><span data-stu-id="c3394-473">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span> 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a><span data-ttu-id="c3394-474">Konwersja typów</span><span class="sxs-lookup"><span data-stu-id="c3394-474">Type conversion</span></span>

<span data-ttu-id="c3394-475">Specyfikacja języka wspólnego definiuje dwa operatory konwersji:</span><span class="sxs-lookup"><span data-stu-id="c3394-475">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="c3394-476">`op_Implicit`, używany dla rozszerzanie konwersji, które nie powodują utratę danych lub dokładności.</span><span class="sxs-lookup"><span data-stu-id="c3394-476">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="c3394-477">Na przykład [dziesiętną](xref:System.Decimal) struktura zawiera przeciążone `op_Implicit` operator do konwersji wartości typów całkowitych i [Char](xref:System.Char) wartości do `Decimal` wartości.</span><span class="sxs-lookup"><span data-stu-id="c3394-477">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span> 

* <span data-ttu-id="c3394-478">`op_Explicit`, używany dla zawężanie konwersji, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub dokładności.</span><span class="sxs-lookup"><span data-stu-id="c3394-478">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="c3394-479">Na przykład `Decimal` struktura zawiera przeciążone `op_Explicit` operatora, aby przekonwertować [podwójne](xref:System.Double) i [pojedynczego](xref:System.Single) wartości do `Decimal` i konwertowania `Decimal` wartości do wartości całkowite `Double`, `Single`, i `Char`.</span><span class="sxs-lookup"><span data-stu-id="c3394-479">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span> 

<span data-ttu-id="c3394-480">Jednak nie obsługuje wszystkich języków przeładowania operatora lub definicję operatorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c3394-480">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="c3394-481">Jeśli wybierzesz do wdrożenia tych operatorów konwersji, musisz także podać innym sposobem wykonania konwersji.</span><span class="sxs-lookup"><span data-stu-id="c3394-481">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="c3394-482">Firma Microsoft zaleca, aby podać `From`Xxx i `To`metody Xxx.</span><span class="sxs-lookup"><span data-stu-id="c3394-482">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span> 

<span data-ttu-id="c3394-483">W poniższym przykładzie zdefiniowano zgodne ze specyfikacją CLS Konwersje jawne i niejawne.</span><span class="sxs-lookup"><span data-stu-id="c3394-483">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="c3394-484">Tworzy `UDouble` klasa, która reprezentuje numer podpisem podwójnej precyzji, zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="c3394-484">It creates a `UDouble` class that represents an signed double-precision, floating-point number.</span></span> <span data-ttu-id="c3394-485">Zapewnia niejawną konwersję z `UDouble` do `Double` i jawne konwersje z `UDouble` do `Single`, `Double` do `UDouble`, i `Single` do `UDouble`.</span><span class="sxs-lookup"><span data-stu-id="c3394-485">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="c3394-486">Definiuje również `ToDouble` metody zamiast operatora niejawnej konwersji i `ToSingle`, `FromDouble`, i `FromSingle` metod jako alternatywy dla operatory jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="c3394-486">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span> 

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue) 
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;         
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   } 

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   } 

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }   

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }   

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }   
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)         
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator 

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator 

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function   

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function   

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function   
End Structure
```

### <a name="arrays"></a><span data-ttu-id="c3394-487">Tablice</span><span class="sxs-lookup"><span data-stu-id="c3394-487">Arrays</span></span>

<span data-ttu-id="c3394-488">Tablice zgodne ze specyfikacją CLS spełniać następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="c3394-488">CLS-compliant arrays conform to the following rules:</span></span> 

* <span data-ttu-id="c3394-489">Wszystkie wymiary tablicy muszą mieć dolna granica zero.</span><span class="sxs-lookup"><span data-stu-id="c3394-489">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="c3394-490">Poniższy przykład tworzy specyfikacją CLS tablicy z dolną granicą jednego.</span><span class="sxs-lookup"><span data-stu-id="c3394-490">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="c3394-491">Należy zauważyć, że mimo występowania [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutu, kompilator nie wykrywa czy tablica zwrócona przez `Numbers.GetTenPrimes` metody nie jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-491">Note that, despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span> 

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6); 
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr; 
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* <span data-ttu-id="c3394-492">Wszystkie elementy tablicy muszą składać się z typów zgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-492">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="c3394-493">W poniższym przykładzie zdefiniowano dwie metody zwracające tablice niezgodnym-ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-493">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="c3394-494">Pierwszy zwraca tablicę [UInt32](xref:System.UInt32) wartości.</span><span class="sxs-lookup"><span data-stu-id="c3394-494">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="c3394-495">Zwraca drugie [obiektu](xref:System.Object) tablicy, która obejmuje [Int32](xref:System.Int32) i `UInt32` wartości.</span><span class="sxs-lookup"><span data-stu-id="c3394-495">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="c3394-496">Mimo że kompilator identyfikuje pierwszy tablicy jako niezgodne z powodu jego `UInt32` typu, nie rozpoznaje, że druga tablica zawiera elementy niezgodnym-ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-496">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span> 

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```                             

* <span data-ttu-id="c3394-497">Rozpoznanie przeciążenia dla metod, które mają tablicy parametrów jest opiera się na fakt, że są one tablicami i na ich typ elementu.</span><span class="sxs-lookup"><span data-stu-id="c3394-497">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="c3394-498">Z tego powodu definicji następujące przeciążone `GetSquares` metody jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-498">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span> 

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]); 
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding 
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr]; 

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr))) 
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding 
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If   
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr) 
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a><span data-ttu-id="c3394-499">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c3394-499">Interfaces</span></span>

<span data-ttu-id="c3394-500">Interfejsy zgodne ze specyfikacją CLS można określić właściwości, zdarzeń i metody wirtualne (metody z żadnej implementacji).</span><span class="sxs-lookup"><span data-stu-id="c3394-500">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="c3394-501">Interfejsie zgodnym ze specyfikacją CLS nie może mieć jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c3394-501">A CLS-compliant interface cannot have any of the following:</span></span> 

* <span data-ttu-id="c3394-502">Metody statycznej lub pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="c3394-502">Static methods or static fields.</span></span> <span data-ttu-id="c3394-503">Błędy kompilatora C# generatse kompilatora w przypadku definiowania statycznego elementu członkowskiego w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="c3394-503">The C# compiler generatse compiler errors if you define a static member in an interface.</span></span> 

* <span data-ttu-id="c3394-504">Pola.</span><span class="sxs-lookup"><span data-stu-id="c3394-504">Fields.</span></span> <span data-ttu-id="c3394-505">C# acompiler generuje błędy kompilatora w przypadku definiowania pola w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="c3394-505">The C# acompiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="c3394-506">Metody, które nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-506">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="c3394-507">Na przykład następujący definicji interfejsu zawiera metodę, `INumber.GetUnsigned`, która jest oznaczona jako specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-507">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="c3394-508">W tym przykładzie generuje ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c3394-508">This example generates a compiler warning.</span></span> 

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong   
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a 
    '    CLS-compliant interface.
    '    
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  <span data-ttu-id="c3394-509">Z powodu działania tej reguły typów zgodnych ze specyfikacją CLS nie są wymagane do zaimplementowania elementy członkowskie z systemem innym niż zgodne-ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-509">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="c3394-510">Jeśli zgodne ze specyfikacją CLS framework ujawnia klasy, która implementuje interfejsie zgodnym ze specyfikacją CLS, on również zawierał konkretnych implementacje wszystkich członków z systemem innym niż — zgodne z CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-510">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span> 

<span data-ttu-id="c3394-511">Kompilatory języka zgodne ze specyfikacją CLS, należy także zezwolić klasę, aby zapewnić oddzielne implementacje elementów członkowskich, które mają taką samą nazwę i sygnaturę w wielu interfejsach.</span><span class="sxs-lookup"><span data-stu-id="c3394-511">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="c3394-512">C# obsługuje jawne implementacje interfejsu zapewnienie różnych implementacji metody o identycznej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c3394-512">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="c3394-513">Poniższy przykład przedstawia tego scenariusza, definiując `Temperature` klasa implementująca `ICelsius` i `IFahrenheit` interfejsy jako jawne implementacje interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c3394-513">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   } 

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   } 
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees", 
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees", 
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub 

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function 
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees", 
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees", 
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a><span data-ttu-id="c3394-514">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c3394-514">Enumerations</span></span>

<span data-ttu-id="c3394-515">Wyliczenia zgodne ze specyfikacją CLS, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c3394-515">CLS-compliant enumerations must follow these rules:</span></span> 

* <span data-ttu-id="c3394-516">Podstawowy typ wyliczenia musi być całkowitą wewnętrzne zgodne ze specyfikacją CLS ([bajtów](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), lub [Int64](xref:System.Int64)).</span><span class="sxs-lookup"><span data-stu-id="c3394-516">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="c3394-517">Na przykład następujący kod próbuje zdefiniowanie wyliczenia o typie podstawowym [UInt32](xref:System.UInt32) i generuje ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c3394-517">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span> 

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint { 
        Unspecified = 0, 
        XSmall = 1, 
        Small = 2, 
        Medium = 3, 
        Large = 4, 
        XLarge = 5 
    };

    public class Clothing
    {
        public string Name; 
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '    
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* <span data-ttu-id="c3394-518">Typ wyliczenia musi mieć pojedynczego wystąpienia pola o nazwie `Value__` który jest oznaczony atrybutem `FieldAttributes.RTSpecialName` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c3394-518">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="c3394-519">Dzięki temu można jawnie odwoływać wartość pola.</span><span class="sxs-lookup"><span data-stu-id="c3394-519">This enables you to reference the field value implicitly.</span></span> 

* <span data-ttu-id="c3394-520">Wyliczenie zawiera literału pól statycznych, których typ zgodny z typem wyliczenia samej siebie.</span><span class="sxs-lookup"><span data-stu-id="c3394-520">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="c3394-521">Na przykład w przypadku definiowania `State` wyliczenie z wartościami `State.On` i `State.Off`, `State.On` i `State.Off` to statycznego pola literału typu `State`.</span><span class="sxs-lookup"><span data-stu-id="c3394-521">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span> 

* <span data-ttu-id="c3394-522">Istnieją dwa rodzaje wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="c3394-522">There are two kinds of enumerations:</span></span> 
    
    * <span data-ttu-id="c3394-523">Reprezentuje zestaw wykluczają się wzajemnie, wyliczenie o nazwie wartości będące liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="c3394-523">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="c3394-524">Ten typ wyliczenia jest określane przez braku [System.FlagsAttribute](xref:System.FlagsAttribute) atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="c3394-524">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>
    
    * <span data-ttu-id="c3394-525">Wyliczenie reprezentuje zestaw flagi bitów, które można łączyć do generowania wartości bez nazwy.</span><span class="sxs-lookup"><span data-stu-id="c3394-525">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="c3394-526">Ten typ wyliczenia jest określane przez obecności [System.FlagsAttribute](xref:System.FlagsAttribute) atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="c3394-526">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>
    
 <span data-ttu-id="c3394-527">Aby uzyskać więcej informacji, zobacz dokumentację [wyliczenia](xref:System.Enum) struktury.</span><span class="sxs-lookup"><span data-stu-id="c3394-527">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span> 

* <span data-ttu-id="c3394-528">Wartość wyliczenia nie jest ograniczona do jego określonej wartości z zakresu.</span><span class="sxs-lookup"><span data-stu-id="c3394-528">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="c3394-529">Innymi słowy zakres wartości podstawowej jest zakres wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-529">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="c3394-530">Można użyć `Enum.IsDefined` metodę, aby ustalić, czy określona wartość elementu członkowskiego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-530">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span> 

### <a name="type-members-in-general"></a><span data-ttu-id="c3394-531">Ogólnie rzecz biorąc wpisz elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c3394-531">Type members in general</span></span>

<span data-ttu-id="c3394-532">Specyfikacja języka wspólnego wymaga wszystkich pól i metod można uzyskać dostępu do jako członków konkretnej klasy.</span><span class="sxs-lookup"><span data-stu-id="c3394-532">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="c3394-533">W związku z tym globalnych pola statyczne i metody (czyli pola statyczne lub metody, które są zdefiniowane oprócz typu) nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-533">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="c3394-534">Jeśli spróbujesz obejmują pole lub metoda globalna w kodzie źródłowym kompilatora C# generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c3394-534">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span> 

<span data-ttu-id="c3394-535">Specyfikacja języka wspólnego obsługuje tylko standardowe zarządzanych konwencję wywołania.</span><span class="sxs-lookup"><span data-stu-id="c3394-535">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="c3394-536">Nie obsługuje niezarządzane konwencji wywoływania i metody z listami zmiennych argumentów oznaczony atrybutem `varargs` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c3394-536">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="c3394-537">Listy zmiennych argumentów, które są zgodne z standardowej konwencji wywoływania zarządzanych, można użyć [ParamArrayAttribute](xref:System.ParamArrayAttribute) lub atrybutu implementacji poszczególnych języków, takich jak `params` — słowo kluczowe języka C# i `ParamArray` słów kluczowych w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3394-537">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span> 

### <a name="member-accessibility"></a><span data-ttu-id="c3394-538">Dostępność elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="c3394-538">Member accessibility</span></span>

<span data-ttu-id="c3394-539">Zastępowanie dziedziczonego elementu członkowskiego nie można zmienić dostępności tego członka.</span><span class="sxs-lookup"><span data-stu-id="c3394-539">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="c3394-540">Na przykład publiczną metodę w klasie podstawowej nie mogą zostać zastąpione przez prywatnej metody w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c3394-540">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="c3394-541">Istnieje jeden wyjątek: `protected internal` (w języku C#) lub `Protected Friend` (w języku Visual Basic) elementu członkowskiego w jednym zestawie, który jest zastępowany przez typ w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="c3394-541">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="c3394-542">W takim przypadku jest dostępność zastąpienie `Protected`.</span><span class="sxs-lookup"><span data-stu-id="c3394-542">In that case, the accessibility of the override is `Protected`.</span></span> 

<span data-ttu-id="c3394-543">Poniższy przykład pokazuje błąd, który jest generowany, gdy [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybut ma ustawioną `true`, i `Person`, które jest klasą pochodną `Animal`, próbuje zmienić dostępność `Species` właściwości z publicznej, prywatnej.</span><span class="sxs-lookup"><span data-stu-id="c3394-543">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="c3394-544">Przykład pomyślnie kompiluje zmiana jego dostępność publiczną.</span><span class="sxs-lookup"><span data-stu-id="c3394-544">The example compiles successfully if its accessibility is changed to public.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species 
   {    
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;   
   } 
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species 
   {
      get { return base.Species; }
   }

   public override string ToString() 
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species   
   End Function 
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get   
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override 
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
' 
'         Private Overrides ReadOnly Property Species As String
```

<span data-ttu-id="c3394-545">Typy w podpisie elementu członkowskiego musi być dostępny zawsze, gdy ten element członkowski jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="c3394-545">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="c3394-546">Na przykład oznacza to, że publicznego elementu członkowskiego nie może zawierać parametru, którego typ jest prywatny, chronionych lub wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="c3394-546">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="c3394-547">Poniższy przykład przedstawia błąd kompilatora, która powoduje podczas `StringWrapper` konstruktora klasy uwidacznia wewnętrzny `StringOperationType` wartość wyliczenia, która określa, jak powinien być zawijany wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="c3394-547">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span> 

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {   
      if (type == StringOperationType.Normal) {
         useSB = false;
      }   
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }    
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)   
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder() 
         useSB = True
      End If    
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'    
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a><span data-ttu-id="c3394-548">Typy ogólne i elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="c3394-548">Generic types and members</span></span>

<span data-ttu-id="c3394-549">Zagnieżdżone typy zawsze mieć co najmniej tyle parametrów ogólnych jak ich typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="c3394-549">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="c3394-550">Te odpowiada za pomocą pozycji do parametrów ogólnych w typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="c3394-550">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="c3394-551">Typ ogólny mogą również obejmować nowe parametry ogólne.</span><span class="sxs-lookup"><span data-stu-id="c3394-551">The generic type can also include new generic parameters.</span></span> 

<span data-ttu-id="c3394-552">Relacja między typ zawierający parametry typu ogólnego i jego zagnieżdżone typy mogą być ukryte przez składnię poszczególnych języków.</span><span class="sxs-lookup"><span data-stu-id="c3394-552">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="c3394-553">W poniższym przykładzie typu ogólnego `Outer<T>` zawiera dwie klasy zagnieżdżonej `Inner1A` i `Inner1B<U>`.</span><span class="sxs-lookup"><span data-stu-id="c3394-553">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="c3394-554">Wywołania `ToString` metodę, która dziedziczy po każdej klasy `Object.ToString`, Pokaż, że każda klasa zagnieżdżona zawiera parametry typu zawierająca go klasa.</span><span class="sxs-lookup"><span data-stu-id="c3394-554">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span> 

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

<span data-ttu-id="c3394-555">Nazwy typów ogólnych są zakodowane w postaci *nazwa*"*n*, gdzie *nazwa* jest nazwą typu  *\`*  jest literał znaku i  *n*  jest liczba parametrów zadeklarowana w typie lub dla zagnieżdżone ogólnych typów, liczba parametrów typu nowo wprowadzonych.</span><span class="sxs-lookup"><span data-stu-id="c3394-555">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="c3394-556">To kodowanie nazwy typu ogólnego jest głównie deweloperom, którzy zgodne ze specyfikacją CLS typy ogólne w bibliotece dostęp do za pomocą odbicia.</span><span class="sxs-lookup"><span data-stu-id="c3394-556">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span> 

<span data-ttu-id="c3394-557">Jeśli ograniczenia są stosowane do ogólnego typu żadnych typów, używany jako ograniczenia również musi być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-557">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="c3394-558">W poniższym przykładzie zdefiniowano klasę o nazwie `BaseClass` czyli nie zgodne ze specyfikacją CLS i rodzajowy klasę o nazwie `BaseCollection` których parametru typu muszą pochodzić od `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="c3394-558">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="c3394-559">Jednak ponieważ `BaseClass` nie jest zgodny z CLS, kompilator emituje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c3394-559">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span> 

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}


public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class


Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not 
'    CLS-compliant.
'    
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

<span data-ttu-id="c3394-560">Jeśli typem ogólnym pochodzi od typu podstawowego ogólny, go ponownie zadeklarować żadnych ograniczeń, dzięki czemu można zagwarantować, że spełnione są również ograniczenia dotyczące typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="c3394-560">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="c3394-561">W poniższym przykładzie zdefiniowano `Number<T>` reprezentujące dowolnego typu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="c3394-561">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="c3394-562">Definiuje również `FloatingPoint<T>` klasa, która reprezentuje zmiennoprzecinkową wartości.</span><span class="sxs-lookup"><span data-stu-id="c3394-562">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="c3394-563">Jednak kod źródłowy nie powiedzie się do kompilacji, ponieważ nie ma zastosowania ograniczenie na `Number<T>` (czy T musi być typem wartości) do `FloatingPoint<T>`.</span><span class="sxs-lookup"><span data-stu-id="c3394-563">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }  
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> 
{
   public FloatingPoint(T number) : base(number) 
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() || 
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else   
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }       
}           
// The attempt to comple the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T) 
   Public Sub New(number As T)
      MyBase.New(number) 
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then 
         Me.number = Convert.ToDouble(number)
      Else   
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If   
   End Sub       
End Class           
' The attempt to comple the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'    
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="c3394-564">Przykład kompiluje pomyślnie dodany do ograniczenia `FloatingPoint<T>` klasy.</span><span class="sxs-lookup"><span data-stu-id="c3394-564">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]


public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }  
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct 
{
   public FloatingPoint(T number) : base(number) 
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() || 
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else   
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }       
}      
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T) 
   Public Sub New(number As T)
      MyBase.New(number) 
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then 
         Me.number = Convert.ToDouble(number)
      Else   
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If   
   End Sub       
End Class
```

<span data-ttu-id="c3394-565">Specyfikacja języka wspólnego nakłada model wystąpienia zachowawcze zagnieżdżone typy i chronione elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="c3394-565">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="c3394-566">Otwórz typy ogólne nie może ujawnić pól lub elementy członkowskie o podpisy zawierające konkretnego wystąpienia typu ogólnego zagnieżdżone, chronionych.</span><span class="sxs-lookup"><span data-stu-id="c3394-566">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="c3394-567">Inne niż ogólne typy, które rozszerzają konkretnego wystąpienia metody rodzajowe klasy podstawowej lub interfejsu nie może ujawnić pól lub elementy członkowskie o podpisy zawierające inną podczas tworzenia wystąpienia typu ogólnego zagnieżdżone, chronionych.</span><span class="sxs-lookup"><span data-stu-id="c3394-567">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="c3394-568">W poniższym przykładzie zdefiniowano typu ogólnego, `C1<T>`i Klasa chroniona, `C1<T>.N`.</span><span class="sxs-lookup"><span data-stu-id="c3394-568">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="c3394-569">`C1<T>`ma dwie metody `M1` i `M2`.</span><span class="sxs-lookup"><span data-stu-id="c3394-569">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="c3394-570">Jednak `M1` nie jest zgodne ze specyfikacją CLS, ponieważ próbuje przywrócić `C1<int>.N` obiekt z `C1<T>`.</span><span class="sxs-lookup"><span data-stu-id="c3394-570">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="c3394-571">W drugiej klasy `C2`, jest określana na podstawie `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="c3394-571">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="c3394-572">Składa się z dwóch metod `M3` i `M4`.</span><span class="sxs-lookup"><span data-stu-id="c3394-572">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="c3394-573">`M3`nie jest zgodne ze specyfikacją CLS, ponieważ próbuje przywrócić `C1<int>.N` obiektu z podklasą `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="c3394-573">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="c3394-574">Należy pamiętać, że Kompilatory języka można jeszcze bardziej restrykcyjne.</span><span class="sxs-lookup"><span data-stu-id="c3394-574">Note that language compilers can be even more restrictive.</span></span> <span data-ttu-id="c3394-575">W tym przykładzie Visual Basic jest wyświetlany błąd przy próbie skompilować `M4`.</span><span class="sxs-lookup"><span data-stu-id="c3394-575">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span> 

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T> 
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long> 
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T) 
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages


   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long) 
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)   
   End Sub                                
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace 
'    '<Default>' through class 'C1'.
'    
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because 
'    it is 'Protected'.
'    
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'    
'                             ~~~~~~~~~~~~~~~~
'    
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'    
'       Protected Sub M4(n As C1(Of Long).N)  
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a><span data-ttu-id="c3394-576">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="c3394-576">Constructors</span></span>

<span data-ttu-id="c3394-577">Konstruktory zgodne ze specyfikacją CLS klas i struktur muszą wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c3394-577">Constructors in CLS-compliant classes and structures must follow these rules:</span></span> 

* <span data-ttu-id="c3394-578">Konstruktora klasy pochodnej musi wywołać konstruktora wystąpień klasy podstawowej, zanim uzyskuje dostęp do danych wystąpienia dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="c3394-578">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="c3394-579">To wymaganie dotyczy faktu, że konstruktorów klasy podstawowej nie są dziedziczone przez ich klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="c3394-579">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="c3394-580">Ta zasada dotyczy struktur, które nie obsługują bezpośredniego dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-580">This rule does not apply to structures, which do not support direct inheritance.</span></span> 

  <span data-ttu-id="c3394-581">Zazwyczaj kompilatory wymuszania tej reguły, niezależnie od zgodności ze specyfikacją CLS, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c3394-581">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="c3394-582">Tworzy `Doctor` klasy, która jest pochodną `Person` klasy, ale `Doctor` klasa nie może wywołać `Person` konstruktora klasy w celu zainicjowania pól wystąpień dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="c3394-582">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span> 

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");    

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName 
    {
        get { return fName; }
    }

    public string LastName 
    {
        get { return lName; }
    }

    public string Id 
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName, 
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)> 

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")    
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName, 
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call 
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does 
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '    
    '       Public Sub New()
    '                  ~~~
    ````
    
* <span data-ttu-id="c3394-583">Nie można wywołać konstruktora obiektów z wyjątkiem tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="c3394-583">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="c3394-584">Ponadto nie można zainicjować obiektu dwa razy.</span><span class="sxs-lookup"><span data-stu-id="c3394-584">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="c3394-585">Oznacza to, że na przykład `Object.MemberwiseClone` nie mogą wywoływać konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="c3394-585">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>  

### <a name="properties"></a><span data-ttu-id="c3394-586">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3394-586">Properties</span></span>

<span data-ttu-id="c3394-587">Właściwości typów zgodnych ze specyfikacją CLS, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c3394-587">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="c3394-588">Właściwość musi mieć metody ustawiającej i/lub metody pobierającej.</span><span class="sxs-lookup"><span data-stu-id="c3394-588">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="c3394-589">W zestawie te są zaimplementowane jako specjalnych metod, co oznacza, że będą wyświetlane jako osobne metody (nosi nazwę metody pobierającej `get` \_ *propertyname* i metodę ustawiającą `set*\_*propertyname*) marked as `jako SpecialName "w metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="c3394-589">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set*\_*propertyname*) marked as `SpecialName\` in the assembly's metadata.</span></span> <span data-ttu-id="c3394-590">Ta reguła automatycznie bez konieczności zastosowania wymusza kompilatora C# [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c3394-590">The C# compiler enforces this rule automatically without the need to apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute.</span></span> 

* <span data-ttu-id="c3394-591">Typ właściwości jest zwracany typ metody pobierającej właściwości i ostatni argument metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="c3394-591">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="c3394-592">Te typy muszą być zgodne ze specyfikacją CLS, oraz argumentów nie można przypisać do właściwości przez odwołanie (oznacza to, nie może być wskaźniki zarządzanych).</span><span class="sxs-lookup"><span data-stu-id="c3394-592">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span> 

* <span data-ttu-id="c3394-593">Jeśli właściwość ma metodę pobierającą i metody ustawiającej, oba muszą być wirtualny, statycznym lub oba wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c3394-593">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="c3394-594">Kompilator języka C# wymusza automatycznie tej reguły za pomocą składni definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="c3394-594">The C# compiler automatically enforces this rule through property definition syntax.</span></span> 

### <a name="events"></a><span data-ttu-id="c3394-595">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c3394-595">Events</span></span>

<span data-ttu-id="c3394-596">Zdarzenie jest definiowane przez jego nazwa i jej typie.</span><span class="sxs-lookup"><span data-stu-id="c3394-596">An event is defined by its name and its type.</span></span> <span data-ttu-id="c3394-597">Typ zdarzenia jest delegata, który służy do wskazywania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-597">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="c3394-598">Na przykład `DbConnection.StateChange` zdarzenie jest typu `StateChangeEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="c3394-598">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="c3394-599">Oprócz samym zdarzeniu trzy metody z nazw na podstawie nazwy zdarzenia implementacji zdarzeń i są oznaczone jako `SpecialName` w metadanych zestawu:</span><span class="sxs-lookup"><span data-stu-id="c3394-599">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span> 

* <span data-ttu-id="c3394-600">Dodawanie obsługi zdarzeń, o nazwie metodę `add`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="c3394-600">A method for adding an event handler, named `add`_*EventName*.</span></span> <span data-ttu-id="c3394-601">Na przykład metoda subskrypcji zdarzeń dla `DbConnection.StateChange` nosi nazwę zdarzenia `add_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="c3394-601">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span> 

* <span data-ttu-id="c3394-602">Metoda usuwania program obsługi zdarzeń o nazwie `remove`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="c3394-602">A method for removing an event handler, named `remove`_*EventName*.</span></span> <span data-ttu-id="c3394-603">Na przykład metoda usuwania dla `DbConnection.StateChange` nosi nazwę zdarzenia `remove_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="c3394-603">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="c3394-604">Metoda wskazującą, w której wystąpiło zdarzenie, o nazwie `raise`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="c3394-604">A method for indicating that the event has occurred, named `raise`_*EventName*.</span></span> 

> [!NOTE]
> <span data-ttu-id="c3394-605">Większość specyfikacja języka wspólnego zasady dotyczące zdarzenia są implementowane przez Kompilatory języka i są niewidoczne dla deweloperów składnika.</span><span class="sxs-lookup"><span data-stu-id="c3394-605">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span> 

<span data-ttu-id="c3394-606">Metody dodawania, usuwania i wywoływanie zdarzeń musi mieć tą samą dostępnością.</span><span class="sxs-lookup"><span data-stu-id="c3394-606">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="c3394-607">One również wszystkie muszą być statyczne, wystąpienie, lub wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="c3394-607">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="c3394-608">Metody do dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-608">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="c3394-609">Dodawanie i usuwanie metody muszą być obecne jednocześnie lub nieobecne.</span><span class="sxs-lookup"><span data-stu-id="c3394-609">The add and remove methods must both be present or both be absent.</span></span> 

<span data-ttu-id="c3394-610">W poniższym przykładzie zdefiniowano klasę zgodne ze specyfikacją CLS o nazwie `Temperature` który zgłasza `TemperatureChanged` zdarzeń, jeśli zmiana temperatury między dwa odczyty jest równa lub przekracza wartość progową.</span><span class="sxs-lookup"><span data-stu-id="c3394-610">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="c3394-611">`Temperature` Klasa jawnie definiuje `raise_TemperatureChanged` metodę, tak aby selektywnie można wykonać procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c3394-611">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp; 
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }   

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   } 

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   } 

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance) 
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return; 

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e) 
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);   
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   { 
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);   
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal 
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub   

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property 

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property 

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)   
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)   
   End Sub
End Class
```

### <a name="overloads"></a><span data-ttu-id="c3394-612">Overloads</span><span class="sxs-lookup"><span data-stu-id="c3394-612">Overloads</span></span>

<span data-ttu-id="c3394-613">Specyfikacja języka wspólnego nakłada się na przeciążone elementy członkowskie następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="c3394-613">The Common Language Specification imposes the following requirements on overloaded members:</span></span> 

* <span data-ttu-id="c3394-614">Elementy członkowskie można przeciążać, na podstawie liczby parametrów i typ żadnego parametru.</span><span class="sxs-lookup"><span data-stu-id="c3394-614">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="c3394-615">Wywoływanie Konwencji, zwracany typ niestandardowy Modyfikatory stosowane do metody lub jej parametr i określa, czy parametry są przekazywane przez wartości lub według odwołania nie są uznawane za podczas rozróżnianie między przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-615">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="c3394-616">Na przykład, zobacz kod z wymaganiem, aby nazwy musi być unikatowa w zakresie w [konwencje nazewnictwa](#naming-conventions) sekcji.</span><span class="sxs-lookup"><span data-stu-id="c3394-616">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span> 

* <span data-ttu-id="c3394-617">Tylko właściwości i metody może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="c3394-617">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="c3394-618">Pola i zdarzenia nie może być przeciążony.</span><span class="sxs-lookup"><span data-stu-id="c3394-618">Fields and events cannot be overloaded.</span></span> 

* <span data-ttu-id="c3394-619">Metody ogólne można przeciążać, na podstawie liczby ich parametry ogólne.</span><span class="sxs-lookup"><span data-stu-id="c3394-619">Generic methods can be overloaded based on the number of their generic parameters.</span></span> 

> [!NOTE]
><span data-ttu-id="c3394-620">`op_Explicit` i `op_Implicit` operatory są wyjątki od reguły, które zwracają wartość nie jest uznawany za część sygnatury metody Rozpoznanie przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="c3394-620">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="c3394-621">Te dwa operatory można przeciążać, na podstawie zarówno ich parametrów i ich wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="c3394-621">These two operators can be overloaded based on both their parameters and their return value.</span></span> 

### <a name="exceptions"></a><span data-ttu-id="c3394-622">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c3394-622">Exceptions</span></span>

<span data-ttu-id="c3394-623">Obiekty wyjątków muszą pochodzić od [System.Exception](xref:System.Exception) lub inny typ pochodny typu `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="c3394-623">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="c3394-624">Poniższy przykład przedstawia błąd kompilatora, która powoduje podczas niestandardowej klasy o nazwie `ErrorClass` służy do obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="c3394-624">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{ 
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1), 
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass 
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get   
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1), 
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'    
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

<span data-ttu-id="c3394-625">Aby rozwiązać ten problem, `ErrorClass` musi dziedziczyć po klasie `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="c3394-625">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="c3394-626">Ponadto właściwości wiadomości musi zostać zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="c3394-626">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="c3394-627">Poniższy przykład poprawia te błędy, aby zdefiniować `ErrorClass` klasy, która jest zgodna ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-627">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>  

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{ 
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1), 
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get   
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1), 
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a><span data-ttu-id="c3394-628">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3394-628">Attributes</span></span>

<span data-ttu-id="c3394-629">Zestawy struktury In.NET, atrybuty niestandardowe udostępnić extensible mechanizm do przechowywania niestandardowych atrybutów i pobierania metadanych dotyczących programowania obiekty, takie jak zestawy, typy elementów członkowskich i parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="c3394-629">In.NET Framework assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="c3394-630">Atrybuty niestandardowe musi pochodzić od [System.Attribute](xref:System.Attribute) lub typ pochodny typu `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="c3394-630">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="c3394-631">Poniższy przykład narusza tę regułę.</span><span class="sxs-lookup"><span data-stu-id="c3394-631">The following example violates this rule.</span></span> <span data-ttu-id="c3394-632">Definiuje `NumericAttribute` klasy, która nie pochodzi od `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="c3394-632">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="c3394-633">Należy pamiętać, że wystąpi błąd kompilatora wyniki, tylko gdy specyfikacją CLS atrybut jest stosowany, nie, jeśli klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="c3394-633">Note that a compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span> 

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)] 
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric 
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it 
'    does not inherit from 'System.Attribute'.
'    
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

<span data-ttu-id="c3394-634">Konstruktor lub właściwości atrybutu zgodne ze specyfikacją CLS mogą uwidaczniać tylko następujących typów:</span><span class="sxs-lookup"><span data-stu-id="c3394-634">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="c3394-635">Wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="c3394-635">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="c3394-636">Bajtów</span><span class="sxs-lookup"><span data-stu-id="c3394-636">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="c3394-637">Char</span><span class="sxs-lookup"><span data-stu-id="c3394-637">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="c3394-638">O podwójnej precyzji</span><span class="sxs-lookup"><span data-stu-id="c3394-638">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="c3394-639">Int16</span><span class="sxs-lookup"><span data-stu-id="c3394-639">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="c3394-640">Int32</span><span class="sxs-lookup"><span data-stu-id="c3394-640">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="c3394-641">Int64</span><span class="sxs-lookup"><span data-stu-id="c3394-641">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="c3394-642">Pojedynczy</span><span class="sxs-lookup"><span data-stu-id="c3394-642">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="c3394-643">Ciąg</span><span class="sxs-lookup"><span data-stu-id="c3394-643">String</span></span>](xref:System.String)

* [<span data-ttu-id="c3394-644">Typ</span><span class="sxs-lookup"><span data-stu-id="c3394-644">Type</span></span>](xref:System.Type)

* <span data-ttu-id="c3394-645">Dowolnego typu wyliczenia o typie podstawowym `Byte`, `Int16`, `Int32`, lub `Int64`.</span><span class="sxs-lookup"><span data-stu-id="c3394-645">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span> 

<span data-ttu-id="c3394-646">W poniższym przykładzie zdefiniowano `DescriptionAttribute` klasą pochodzącą z [atrybutu](xref:System.Attribute).</span><span class="sxs-lookup"><span data-stu-id="c3394-646">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="c3394-647">Konstruktor klasy ma parametr typu `Descriptor`, więc klasa nie jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-647">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="c3394-648">Zauważ, że kompilator języka C# emituje ostrzeżenie, który kompiluje się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c3394-648">Note that the C# compiler emits a warning but compiles successfully.</span></span> 

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description; 
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d; 
   }

   public Descriptor Descriptor
   { get { return desc; } } 
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType 
   Public Description As String 
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d 
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get 
         Return desc
      End Get    
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="c3394-649">Atrybut CLSCompliant</span><span class="sxs-lookup"><span data-stu-id="c3394-649">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="c3394-650">[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) atrybut używany do określenia, czy program element spełnia specyfikacja języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="c3394-650">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="c3394-651">`CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` Konstruktor zawiera jeden wymagany parametr *isCompliant*, który wskazuje, czy program element jest zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-651">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span> 

<span data-ttu-id="c3394-652">W czasie kompilacji kompilatorowi wykrywa niezgodne elementy, które są uważane za zgodne ze specyfikacją CLS i emituje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c3394-652">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="c3394-653">Kompilator nie Emituj ostrzeżenia dla typów albo elementów członkowskich, które są jawnie uznane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="c3394-653">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span> 

<span data-ttu-id="c3394-654">Składnik deweloperzy mogą używać `CLSCompliantAttribute` atrybutu na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="c3394-654">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span> 

* <span data-ttu-id="c3394-655">Aby zdefiniować części interfejs publiczny udostępnianych przez składnik, które są zgodne ze specyfikacją CLS i części, które nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-655">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="c3394-656">W przypadku atrybutu można oznaczyć jako zgodnego ze specyfikacją CLS elementy określonego programu użytkowania gwarantuje, że te elementy są dostępne ze wszystkich języków i narzędzi przeznaczonych dla platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3394-656">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target the .NET Framework.</span></span> 

* <span data-ttu-id="c3394-657">Aby upewnić się, że biblioteka składnik publiczny interfejs przedstawia tylko elementy programu, które są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-657">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="c3394-658">Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory będzie zazwyczaj ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c3394-658">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="c3394-659">W niektórych przypadkach Kompilatory języka wymuszania reguł zgodne ze specyfikacją CLS, niezależnie od tego, czy `CLSCompliantAttribute` atrybut jest używany.</span><span class="sxs-lookup"><span data-stu-id="c3394-659">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="c3394-660">Na przykład definiowanie `*static` elementu członkowskiego w interfejsie narusza regułę ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-660">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="c3394-661">Jednak w przypadku definiowania `*static` elementu członkowskiego w interfejsie, kompilator języka C# Wyświetla komunikat o błędzie i kończy się niepowodzeniem, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="c3394-661">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="c3394-662">`CLSCompliantAttribute` Atrybut jest oznaczony atrybutem [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) atrybut, który ma wartość `AttributeTargets.All`.</span><span class="sxs-lookup"><span data-stu-id="c3394-662">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="c3394-663">Ta wartość umożliwia stosowanie `CLSCompliantAttribute` atrybut do dowolnych programów, zestawy, moduły, w tym typów (klasy, struktury, wyliczenia, interfejsów i delegatów), typy elementów członkowskich (konstruktorów, metod, właściwości, pól i zdarzenia), Parametry, parametry ogólne i wartości zwracanych.</span><span class="sxs-lookup"><span data-stu-id="c3394-663">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="c3394-664">Jednak w praktyce, powinien zastosować atrybut tylko do zestawów, typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="c3394-664">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="c3394-665">W przeciwnym razie kompilatory Ignoruj ten atrybut i nadal generować ostrzeżenia kompilatora zawsze, gdy wystąpi parametrem niezgodnych parametru ogólnego lub zwróć wartość interfejs publiczny biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c3394-665">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>  

<span data-ttu-id="c3394-666">Wartość `CLSCompliantAttribute` atrybutu jest dziedziczona przez program zawartych w niej elementów.</span><span class="sxs-lookup"><span data-stu-id="c3394-666">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="c3394-667">Na przykład jeśli zestaw jest oznaczony jako zgodnego ze specyfikacją CLS, jego typów także są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-667">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="c3394-668">Typ jest oznaczony jako zgodnego ze specyfikacją CLS, jego zagnieżdżone typy i elementy członkowskie nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-668">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span> 

<span data-ttu-id="c3394-669">Można jawnie przesłonić odziedziczonego zgodności, stosując `CLSCompliantAttribute` atrybutu element zawartych w niej program.</span><span class="sxs-lookup"><span data-stu-id="c3394-669">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="c3394-670">Na przykład można użyć `CLSCompliantAttribute` atrybutem *isCompliant* wartość `false` można użyć do definiowania niezgodnych typów w zestawie zgodne, a atrybut o *isComplian*wartość `true` do definiowania zgodny typ w zestawie niezgodnych.</span><span class="sxs-lookup"><span data-stu-id="c3394-670">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isComplian* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="c3394-671">Można również zdefiniować niezgodnych elementów członkowskich w typie zgodnym.</span><span class="sxs-lookup"><span data-stu-id="c3394-671">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="c3394-672">Jednak niezgodnych typów nie może mieć elementy członkowskie zgodne, więc nie można użyć atrybutu o *isCompliant* wartość `true` do przesłonięcia dziedziczenia z typem niezgodnych.</span><span class="sxs-lookup"><span data-stu-id="c3394-672">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span> 

<span data-ttu-id="c3394-673">Gdy tworzysz składników, zawsze należy używać `CLSCompliantAttribute` atrybutu, aby wskazać, czy używanemu zestawowi, jego typów i jej elementów członkowskich są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-673">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span> 

<span data-ttu-id="c3394-674">Aby utworzyć zgodny z CLS składniki:</span><span class="sxs-lookup"><span data-stu-id="c3394-674">To create CLS-compliant components:</span></span> 

1. <span data-ttu-id="c3394-675">Użyj `CLSCompliantAttribute` aby oznaczyć możesz zestawu jako zgodnego ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-675">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="c3394-676">Oznacz publicznie ujawnionych typów w zestawie, które nie są zgodne z CLS jako niezgodne.</span><span class="sxs-lookup"><span data-stu-id="c3394-676">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span> 

3. <span data-ttu-id="c3394-677">Oznacz żadnych publicznie ujawnionych elementów członkowskich w typach zgodne ze specyfikacją CLS jako niezgodne.</span><span class="sxs-lookup"><span data-stu-id="c3394-677">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span> 

4. <span data-ttu-id="c3394-678">Podaj alternatywnym, zgodnym ze specyfikacją CLS elementy członkowskie z systemem innym niż zgodne-ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-678">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span> 

<span data-ttu-id="c3394-679">Jeśli pomyślnie zostały oznaczone jako niezgodne typy i elementy członkowskie, kompilujący powinien nie Emituj wszelkie ostrzeżenia o braku zgodności.</span><span class="sxs-lookup"><span data-stu-id="c3394-679">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="c3394-680">Jednak należy wskazać elementów członkowskich, które nie są zgodne ze specyfikacją CLS i wyświetlać ich zgodne ze specyfikacją CLS alternatyw w dokumentacji produktu.</span><span class="sxs-lookup"><span data-stu-id="c3394-680">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span> 

<span data-ttu-id="c3394-681">W poniższym przykładzie użyto `CLSCompliantAttribute` atrybut do definiowania zgodne ze specyfikacją CLS zestawu i typu `CharacterUtilities`, która ma dwa elementy członkowskie z systemem innym niż — zgodne z CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-681">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="c3394-682">Ponieważ oba elementy są oznaczane `CLSCompliant(false)` atrybutu, kompilator generuje żadnych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="c3394-682">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="c3394-683">Ta klasa dostarcza również alternatywnym, zgodnym ze specyfikacją CLS dla obu metod.</span><span class="sxs-lookup"><span data-stu-id="c3394-683">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="c3394-684">Zwykle po prostu dodamy dwa przeciążenia do `ToUTF16` metodę w celu zapewnienia alternatywnych zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-684">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="c3394-685">Jednak ponieważ metody nie może zostać przeciążony oparte na wartości zwracanej, nazwy metody zgodne ze specyfikacją CLS różnią się od nazwy metod niezgodnych.</span><span class="sxs-lookup"><span data-stu-id="c3394-685">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>  

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch); 
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);   
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);   
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      } 
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch) 
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)   
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)   
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If 
   End Function            
End Class
```

<span data-ttu-id="c3394-686">Jeśli opracowujesz aplikację, a nie w bibliotece (Jeśli nie są udostępnianie typów albo elementów członkowskich, które mogą być używane przez innych aplikacji), zgodności ze specyfikacją CLS elementów programu, które korzysta z aplikacji mogą być przydatne tylko wtedy, gdy język nie obsługuje ich .</span><span class="sxs-lookup"><span data-stu-id="c3394-686">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="c3394-687">W takim przypadku kompilujący języka zostanie wygenerowany błąd podczas próby użycia elementu niezgodnym-ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="c3394-687">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span> 

## <a name="cross-language-interoperability"></a><span data-ttu-id="c3394-688">Współdziałanie między językami</span><span class="sxs-lookup"><span data-stu-id="c3394-688">Cross-Language Interoperability</span></span>

<span data-ttu-id="c3394-689">Niezależność od języka ma liczbę możliwych znaczenie.</span><span class="sxs-lookup"><span data-stu-id="c3394-689">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="c3394-690">Znaczenie co obejmuje bezproblemowo używające typów napisane w języku jednej z aplikacji w języku innym.</span><span class="sxs-lookup"><span data-stu-id="c3394-690">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="c3394-691">Drugi znaczenie, które ma fokus w tym artykule, polega na połączeniu kod napisany w wielu językach w ramach jednego zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3394-691">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET Framework assembly.</span></span> 

<span data-ttu-id="c3394-692">Poniższy przykład przedstawia współdziałanie między językami przez tworzenia biblioteki klas o nazwie Utilities.dll, który zawiera dwie klasy `NumericLib` i `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="c3394-692">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="c3394-693">`NumericLib` Klasy jest napisany w języku C# i `StringLib` klasy jest napisany w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c3394-693">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="c3394-694">Oto kod źródłowy `StringUtil.vb`, zawierające jeden element członkowski `ToTitleCase`w jego `StringLib` klasy.</span><span class="sxs-lookup"><span data-stu-id="c3394-694">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String) 

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split() 
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "             
         End If   
      Next 
      Return result 
   End Function
End Module
```

<span data-ttu-id="c3394-695">Oto kod źródłowy NumberUtil.cs, który definiuje `NumericLib` klasy, która ma dwa elementy członkowskie, `IsEven` i `NearZero`.</span><span class="sxs-lookup"><span data-stu-id="c3394-695">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

```csharp
using System;

public static class NumericLib 
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 || 
          number is Int32 || 
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001; 
   }
}
```

<span data-ttu-id="c3394-696">Aby pakiet dwóch klas w jednym zestawie, należy skompilować je w modułach.</span><span class="sxs-lookup"><span data-stu-id="c3394-696">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="c3394-697">Aby skompilować pliku kodu źródłowego języka Visual Basic w module, użyj tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c3394-697">To compile the Visual Basic source code file into a module, use this command:</span></span> 

```
vbc /t:module StringUtil.vb 
```

<span data-ttu-id="c3394-698">Aby skompilować pliku kodu źródłowego C# w module, użyj tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c3394-698">To compile the C# source code file into a module, use this command:</span></span>

```
csc /t:module NumberUtil.cs
```

<span data-ttu-id="c3394-699">Następnie skompilować dwa moduły do zestawu jest używane narzędzie łącza (Link.exe):</span><span class="sxs-lookup"><span data-stu-id="c3394-699">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span> 

```
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="c3394-700">Poniższy przykład wywołuje `NumericLib.NearZero` i `StringLib.ToTitleCase` metody.</span><span class="sxs-lookup"><span data-stu-id="c3394-700">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="c3394-701">Należy zauważyć, że zarówno kod Visual Basic, jak i kodu C# możliwość dostępu metody w obu klasach.</span><span class="sxs-lookup"><span data-stu-id="c3394-701">Note that both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

<span data-ttu-id="c3394-702">Aby skompilować kod Visual Basic, użyj tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c3394-702">To compile the Visual Basic code, use this command:</span></span>

```
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="c3394-703">Aby skompilować w języku C#, Zmień nazwę kompilatora z vbc do csc i zmień rozszerzenie pliku z .vb CS:</span><span class="sxs-lookup"><span data-stu-id="c3394-703">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```
csc example.cs /r:UtilityLib.dll
```

