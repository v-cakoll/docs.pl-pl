---
title: Niezależność od języka i składniki niezależne od języka
description: Dowiedz się, jak można opracowywać w jednym z wielu obsługiwanych języków w programie .NET C#, C++takich jak F#/CLI,, IronPython, VB, Visual COBOL i PowerShell.
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: e1f419dd57c1e90d7ebb57ef572f338a34d1c509
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423635"
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="d0ac8-103">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="d0ac8-103">Language independence and language-independent components</span></span>

<span data-ttu-id="d0ac8-104">.NET jest niezależny od języka.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-104">.NET is language independent.</span></span> <span data-ttu-id="d0ac8-105">Oznacza to, że jako programista można opracowywać w jednym z wielu języków, które są przeznaczone dla implementacji platformy .NET, takich C#jak F#, i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="d0ac8-106">Można uzyskać dostęp do typów i elementów członkowskich bibliotek klas opracowanych dla implementacji platformy .NET bez konieczności znajomości języka, w którym zostały pierwotnie napisane, i bez konieczności przestrzegania jakichkolwiek Konwencji języka oryginalnego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="d0ac8-107">Jeśli jesteś deweloperem składnika, możesz uzyskać dostęp do składnika przez dowolną aplikację platformy .NET niezależnie od jego języka.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-107">If you are a component developer, your component can be accessed by any .NET app regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="d0ac8-108">W pierwszej części tego artykułu omówiono Tworzenie składników niezależnych od języka — czyli składników, które mogą być używane przez aplikacje, które są zapisywane w dowolnym języku.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-108">This first part of this article discusses creating language-independent components - that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="d0ac8-109">Możesz również utworzyć pojedynczy składnik lub aplikację z kodu źródłowego zapisaną w wielu językach. Zobacz [współdziałanie między językami](#cross-language-interoperability) w drugiej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span>

<span data-ttu-id="d0ac8-110">Aby w pełni współistnieć z innymi obiektami zapisanymi w dowolnym języku, obiekty muszą uwidocznić wywołujących tylko te funkcje, które są wspólne dla wszystkich języków.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="d0ac8-111">Ten wspólny zestaw funkcji jest definiowany przez Common Language Specification (CLS), który jest zestawem reguł, które są stosowane do wygenerowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="d0ac8-112">Common Language Specification jest zdefiniowany w partycji I, klauzule od 7 do 11 w [standardzie ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

<span data-ttu-id="d0ac8-113">Jeśli składnik jest zgodny z Common Language Specification, gwarantowany jest zgodność ze specyfikacją CLS i można uzyskać do niego dostęp z kodu w zestawach pisanych w dowolnym języku programowania, który obsługuje specyfikację CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="d0ac8-114">Można określić, czy składnik jest zgodny z Common Language Specification w czasie kompilacji, stosując atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="d0ac8-115">Aby uzyskać więcej informacji, zobacz [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-115">For more information, see The [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

<span data-ttu-id="d0ac8-116">W tym artykule:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-116">In this article:</span></span>

* [<span data-ttu-id="d0ac8-117">Reguły zgodności ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="d0ac8-117">CLS compliance rules</span></span>](#cls-compliance-rules)

  * [<span data-ttu-id="d0ac8-118">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-118">Types and type member signatures</span></span>](#types-and-type-member-signatures)

  * [<span data-ttu-id="d0ac8-119">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d0ac8-119">Naming conventions</span></span>](#naming-conventions)

  * [<span data-ttu-id="d0ac8-120">Konwersja typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-120">Type conversion</span></span>](#type-conversion)

  * [<span data-ttu-id="d0ac8-121">Tablice</span><span class="sxs-lookup"><span data-stu-id="d0ac8-121">Arrays</span></span>](#arrays)

  * [<span data-ttu-id="d0ac8-122">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d0ac8-122">Interfaces</span></span>](#interfaces)

  * [<span data-ttu-id="d0ac8-123">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-123">Enumerations</span></span>](#enumerations)

  * [<span data-ttu-id="d0ac8-124">Ogólnie wpisz składowe</span><span class="sxs-lookup"><span data-stu-id="d0ac8-124">Type members in general</span></span>](#type-members-in-general)

  * [<span data-ttu-id="d0ac8-125">Ułatwienia dostępu członków</span><span class="sxs-lookup"><span data-stu-id="d0ac8-125">Member accessibility</span></span>](#member-accessibility)

  * [<span data-ttu-id="d0ac8-126">Typy ogólne i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-126">Generic types and members</span></span>](#generic-types-and-members)

  * [<span data-ttu-id="d0ac8-127">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d0ac8-127">Constructors</span></span>](#constructors)

  * [<span data-ttu-id="d0ac8-128">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-128">Properties</span></span>](#properties)

  * [<span data-ttu-id="d0ac8-129">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-129">Events</span></span>](#events)

  * [<span data-ttu-id="d0ac8-130">Overloads</span><span class="sxs-lookup"><span data-stu-id="d0ac8-130">Overloads</span></span>](#overloads)

  * [<span data-ttu-id="d0ac8-131">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d0ac8-131">Exceptions</span></span>](#exceptions)

  * [<span data-ttu-id="d0ac8-132">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0ac8-132">Attributes</span></span>](#attributes)

* [<span data-ttu-id="d0ac8-133">CLSCompliantAttribute — atrybut</span><span class="sxs-lookup"><span data-stu-id="d0ac8-133">CLSCompliantAttribute attribute</span></span>](#the-clscompliantattribute-attribute)

* [<span data-ttu-id="d0ac8-134">Współdziałanie między językami</span><span class="sxs-lookup"><span data-stu-id="d0ac8-134">Cross-Language Interoperability</span></span>](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a><span data-ttu-id="d0ac8-135">Reguły zgodności ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="d0ac8-135">CLS compliance rules</span></span>

<span data-ttu-id="d0ac8-136">W tej sekcji omówiono reguły tworzenia składnika zgodnego ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-136">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="d0ac8-137">Aby uzyskać pełną listę reguł, zobacz partycja I, klauzula 11 [wzorca ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-137">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

> [!NOTE]
> <span data-ttu-id="d0ac8-138">Common Language Specification omawia każdą zasadę zgodności ze specyfikacją CLS, która ma zastosowanie do konsumentów (deweloperzy, którzy korzystają z programistycznego dostępu do składnika, który jest zgodny ze specyfikacją CLS), platformy (deweloperzy używający kompilatora języka do tworzenia Biblioteki zgodne ze specyfikacją CLS) i rozszerzeń (deweloperzy tworzący narzędzie, takie jak kompilator języka lub parser kodu, który tworzy składniki zgodne ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-138">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="d0ac8-139">Ten artykuł koncentruje się na regułach, które mają zastosowanie do struktur.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-139">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="d0ac8-140">Należy zauważyć, że niektóre reguły, które mają zastosowanie do rozszerzeń, mogą również być stosowane do zestawów, które są tworzone za pomocą [odbicia. Emituj](xref:System.Reflection.Emit).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-140">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span>

<span data-ttu-id="d0ac8-141">Aby zaprojektować składnik niezależny od języka, należy zastosować reguły zgodności ze specyfikacją CLS dla interfejsu publicznego składnika.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-141">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="d0ac8-142">Twoja prywatna implementacja nie musi być zgodna ze specyfikacją.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-142">Your private implementation does not have to conform to the specification.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0ac8-143">Reguły zgodności ze specyfikacją CLS mają zastosowanie tylko do interfejsu publicznego składnika, a nie do prywatnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-143">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span>

<span data-ttu-id="d0ac8-144">Na przykład liczby całkowite bez znaku inne niż [Byte](xref:System.Byte) nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-144">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="d0ac8-145">Ponieważ Klasa `Person` w poniższym przykładzie uwidacznia Właściwość `Age` typu [UInt16](xref:System.UInt16), poniższy kod wyświetla ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-145">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

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

<span data-ttu-id="d0ac8-146">Można sprawić, aby Klasa osoby była zgodna ze specyfikacją CLS, zmieniając typ właściwości `Age` z `UInt16` na [Int16](xref:System.Int16), która jest zgodna ze specyfikacją CLS, 16-bitową liczbą całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-146">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="d0ac8-147">Nie musisz zmieniać typu pola `personAge` prywatnego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-147">You do not have to change the type of the private `personAge` field.</span></span>

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

<span data-ttu-id="d0ac8-148">Interfejs publiczny biblioteki składa się z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-148">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="d0ac8-149">Definicje klas publicznych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-149">Definitions of public classes.</span></span>

* <span data-ttu-id="d0ac8-150">Definicje publicznych członków klas publicznych oraz definicje członków dostępnych dla klas pochodnych (czyli chronionych elementów członkowskich).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-150">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span>

* <span data-ttu-id="d0ac8-151">Parametry i zwracane typy metod publicznych klas publicznych oraz parametry i zwracane typy metod dostępnych dla klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-151">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span>

<span data-ttu-id="d0ac8-152">Reguły zgodności ze specyfikacją CLS są wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-152">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="d0ac8-153">Tekst reguł jest pobierany Verbatim z [standardu ECMA-335: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), czyli Copyright 2012 przez Ecma International.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-153">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="d0ac8-154">Bardziej szczegółowe informacje o tych regułach znajdują się w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-154">More detailed information about these rules is found in the following sections.</span></span>

<span data-ttu-id="d0ac8-155">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d0ac8-155">Category</span></span> | <span data-ttu-id="d0ac8-156">Zobacz</span><span class="sxs-lookup"><span data-stu-id="d0ac8-156">See</span></span> | <span data-ttu-id="d0ac8-157">Reguła</span><span class="sxs-lookup"><span data-stu-id="d0ac8-157">Rule</span></span> | <span data-ttu-id="d0ac8-158">Numer reguły</span><span class="sxs-lookup"><span data-stu-id="d0ac8-158">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="d0ac8-159">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-159">Accessibility</span></span> | [<span data-ttu-id="d0ac8-160">Ułatwienia dostępu członków</span><span class="sxs-lookup"><span data-stu-id="d0ac8-160">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="d0ac8-161">Dostępność nie jest zmieniana podczas zastępowania metod dziedziczonych, z wyjątkiem tego, że w przypadku przesłania metody dziedziczonej z innego zestawu z `family-or-assembly`ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-161">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="d0ac8-162">W takim przypadku zastąpienie ma `family`ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-162">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="d0ac8-163">10</span><span class="sxs-lookup"><span data-stu-id="d0ac8-163">10</span></span>
<span data-ttu-id="d0ac8-164">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-164">Accessibility</span></span> | [<span data-ttu-id="d0ac8-165">Ułatwienia dostępu członków</span><span class="sxs-lookup"><span data-stu-id="d0ac8-165">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="d0ac8-166">Widoczność i dostępność typów i członków jest taka, że typy w podpisie każdego elementu członkowskiego są widoczne i dostępne za każdym razem, gdy sam element członkowski jest widoczny i dostępny.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-166">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="d0ac8-167">Na przykład metoda publiczna widoczna poza jej zestawem nie ma argumentu, którego typ jest widoczny tylko w obrębie zestawu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-167">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="d0ac8-168">Widoczność i dostępność typów tworzących typ ogólny, używany w podpisie dowolnego elementu członkowskiego, są widoczne i dostępne za każdym razem, gdy element członkowski jest widoczny i dostępny.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-168">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="d0ac8-169">Na przykład typ generyczny skonkretyzowany obecny w sygnaturze elementu członkowskiego, który jest widoczny poza jego zestawem, nie powinien mieć argumentu ogólnego, którego typ jest widoczny tylko w obrębie zestawu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-169">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="d0ac8-170">12</span><span class="sxs-lookup"><span data-stu-id="d0ac8-170">12</span></span>
<span data-ttu-id="d0ac8-171">Tablice</span><span class="sxs-lookup"><span data-stu-id="d0ac8-171">Arrays</span></span> | [<span data-ttu-id="d0ac8-172">Tablice</span><span class="sxs-lookup"><span data-stu-id="d0ac8-172">Arrays</span></span>](#arrays) | <span data-ttu-id="d0ac8-173">Tablice powinny mieć elementy z typem zgodnym ze specyfikacją CLS, a wszystkie wymiary tablicy mają dolne granice równe zero.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-173">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="d0ac8-174">Tylko fakt, że element jest tablicą, a typ elementu tablicy musi być wymagany do rozróżnienia między przeciążeniami.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-174">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="d0ac8-175">W przypadku przeciążania opartego na co najmniej dwóch typach tablic typy elementów muszą być nazwanymi typami.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-175">When overloading is based on two or more array types the element types shall be named types.</span></span> | <span data-ttu-id="d0ac8-176">16</span><span class="sxs-lookup"><span data-stu-id="d0ac8-176">16</span></span>
<span data-ttu-id="d0ac8-177">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0ac8-177">Attributes</span></span> | [<span data-ttu-id="d0ac8-178">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0ac8-178">Attributes</span></span>](#attributes) | <span data-ttu-id="d0ac8-179">Atrybuty muszą być typu [System. Attribute](xref:System.Attribute)lub dziedziczyć po nim.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-179">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="d0ac8-180">41</span><span class="sxs-lookup"><span data-stu-id="d0ac8-180">41</span></span>
<span data-ttu-id="d0ac8-181">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0ac8-181">Attributes</span></span> | [<span data-ttu-id="d0ac8-182">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0ac8-182">Attributes</span></span>](#attributes) | <span data-ttu-id="d0ac8-183">CLS zezwala tylko na podzbiór kodowań atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-183">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="d0ac8-184">Jedyne typy, które są wyświetlane w tych kodowaniach, to (zobacz partycja IV): [System. Type](xref:System.Type), [System. String](xref:System.String), [System. Char](xref:System.Char), [System. Boolean](xref:System.Boolean), [System. Byte](xref:System.Byte), system. [Int16](xref:System.Int16), [System. Int32](xref:System.Int32), [ System. Int64](xref:System.Int64), [System. Single](xref:System.Single), [System. Double](xref:System.Double)i dowolny typ wyliczeniowy na podstawie typu liczby całkowitej zgodnej ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-184">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="d0ac8-185">34</span><span class="sxs-lookup"><span data-stu-id="d0ac8-185">34</span></span>
<span data-ttu-id="d0ac8-186">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0ac8-186">Attributes</span></span> | [<span data-ttu-id="d0ac8-187">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0ac8-187">Attributes</span></span>](#attributes) | <span data-ttu-id="d0ac8-188">Specyfikacja CLS nie zezwala na publicznie widoczne wymagane Modyfikatory (`modreq`, zobacz partycja II), ale zezwala na Modyfikatory opcjonalne (`modopt`, zobacz partycja II), które nie są zrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-188">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="d0ac8-189">35</span><span class="sxs-lookup"><span data-stu-id="d0ac8-189">35</span></span>
<span data-ttu-id="d0ac8-190">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="d0ac8-190">Constructors</span></span> | [<span data-ttu-id="d0ac8-191">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d0ac8-191">Constructors</span></span>](#constructors) | <span data-ttu-id="d0ac8-192">Konstruktor obiektu wywołuje niektórych konstruktorów wystąpień swojej klasy podstawowej przed wszelkimi dostępami do dziedziczonych danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-192">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="d0ac8-193">(Nie dotyczy to typów wartości, które nie muszą mieć konstruktorów).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-193">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="d0ac8-194">43</span><span class="sxs-lookup"><span data-stu-id="d0ac8-194">21</span></span>
<span data-ttu-id="d0ac8-195">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="d0ac8-195">Constructors</span></span> | [<span data-ttu-id="d0ac8-196">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d0ac8-196">Constructors</span></span>](#constructors) | <span data-ttu-id="d0ac8-197">Konstruktor obiektów nie jest wywoływany, chyba że jest częścią tworzenia obiektu, a obiekt nie zostanie dwukrotnie zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-197">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="d0ac8-198">22</span><span class="sxs-lookup"><span data-stu-id="d0ac8-198">22</span></span>
<span data-ttu-id="d0ac8-199">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-199">Enumerations</span></span> | [<span data-ttu-id="d0ac8-200">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-200">Enumerations</span></span>](#enumerations) | <span data-ttu-id="d0ac8-201">Typ podstawowy wyliczenia musi być wbudowanym typem Integer CLS, nazwą pola będzie "value__", a to pole jest oznaczone `RTSpecialName`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-201">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="d0ac8-202">7</span><span class="sxs-lookup"><span data-stu-id="d0ac8-202">7</span></span>
<span data-ttu-id="d0ac8-203">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-203">Enumerations</span></span> | [<span data-ttu-id="d0ac8-204">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-204">Enumerations</span></span>](#enumerations) | <span data-ttu-id="d0ac8-205">Istnieją dwa odrębne rodzaje typów wyliczeniowych, wskazywane przez obecność lub brak elementu [System. FlagsAttribute](xref:System.FlagsAttribute) (zobacz partycja IV Library) atrybut niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-205">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="d0ac8-206">Jeden reprezentuje nazwane wartości całkowite; Druga reprezentuje nazwane flagi bitowe, które można połączyć w celu wygenerowania nienazwanej wartości.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-206">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="d0ac8-207">Wartość `enum` nie jest ograniczona do określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-207">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="d0ac8-208">8</span><span class="sxs-lookup"><span data-stu-id="d0ac8-208">8</span></span>
<span data-ttu-id="d0ac8-209">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-209">Enumerations</span></span> | [<span data-ttu-id="d0ac8-210">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-210">Enumerations</span></span>](#enumerations) | <span data-ttu-id="d0ac8-211">Literałowe pola statyczne typu wyliczeniowego mają typ wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-211">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="d0ac8-212">9</span><span class="sxs-lookup"><span data-stu-id="d0ac8-212">9</span></span>
<span data-ttu-id="d0ac8-213">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-213">Events</span></span> | [<span data-ttu-id="d0ac8-214">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-214">Events</span></span>](#events) | <span data-ttu-id="d0ac8-215">Metody implementujące zdarzenie należy oznaczyć `SpecialName` w metadanych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-215">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="d0ac8-216">dnia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-216">29</span></span>
<span data-ttu-id="d0ac8-217">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-217">Events</span></span> | [<span data-ttu-id="d0ac8-218">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-218">Events</span></span>](#events) | <span data-ttu-id="d0ac8-219">Dostępność zdarzenia i jego metod dostępu powinna być taka sama.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-219">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="d0ac8-220">0,30</span><span class="sxs-lookup"><span data-stu-id="d0ac8-220">30</span></span>
<span data-ttu-id="d0ac8-221">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-221">Events</span></span> | [<span data-ttu-id="d0ac8-222">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-222">Events</span></span>](#events) | <span data-ttu-id="d0ac8-223">Metody `add` i `remove` dla zdarzenia muszą być obecne lub nieobecne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-223">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="d0ac8-224">niż</span><span class="sxs-lookup"><span data-stu-id="d0ac8-224">31</span></span>
<span data-ttu-id="d0ac8-225">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-225">Events</span></span> | [<span data-ttu-id="d0ac8-226">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-226">Events</span></span>](#events) | <span data-ttu-id="d0ac8-227">Metody `add` i `remove` dla zdarzenia muszą mieć jeden parametr, którego typ definiuje typ zdarzenia i który powinien pochodzić od elementu [System. Delegate](xref:System.Delegate).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-227">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="d0ac8-228">32</span><span class="sxs-lookup"><span data-stu-id="d0ac8-228">32</span></span>
<span data-ttu-id="d0ac8-229">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-229">Events</span></span> | [<span data-ttu-id="d0ac8-230">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-230">Events</span></span>](#events) | <span data-ttu-id="d0ac8-231">Zdarzenia muszą być zgodne z określonym wzorcem nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-231">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="d0ac8-232">Atrybut SpecialName, do którego odwołuje się reguła CLS 29, jest ignorowany w odpowiednich porównaniach nazw i stosuje się do reguł identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-232">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="d0ac8-233">33</span><span class="sxs-lookup"><span data-stu-id="d0ac8-233">33</span></span>
<span data-ttu-id="d0ac8-234">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d0ac8-234">Exceptions</span></span> | [<span data-ttu-id="d0ac8-235">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d0ac8-235">Exceptions</span></span>](#exceptions) | <span data-ttu-id="d0ac8-236">Obiekty, które są generowane, są typu [System. Exception](xref:System.Exception) lub dziedziczą z niego typ.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-236">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="d0ac8-237">Niemniej jednak metody zgodne ze specyfikacją CLS nie są wymagane do blokowania propagacji innych typów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-237">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="d0ac8-238">40</span><span class="sxs-lookup"><span data-stu-id="d0ac8-238">40</span></span>
<span data-ttu-id="d0ac8-239">Ogólne</span><span class="sxs-lookup"><span data-stu-id="d0ac8-239">General</span></span> | [<span data-ttu-id="d0ac8-240">Reguły zgodności ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="d0ac8-240">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="d0ac8-241">Reguły CLS stosują się tylko do tych części typu, które są dostępne lub widoczne poza zestawem definiującym.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-241">CLS rules apply only to those parts of a type that are accessible or visible outside of the defining assembly.</span></span> | <span data-ttu-id="d0ac8-242">1</span><span class="sxs-lookup"><span data-stu-id="d0ac8-242">1</span></span>
<span data-ttu-id="d0ac8-243">Ogólne</span><span class="sxs-lookup"><span data-stu-id="d0ac8-243">General</span></span> | [<span data-ttu-id="d0ac8-244">Reguły zgodności ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="d0ac8-244">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="d0ac8-245">Elementy członkowskie typów niezgodnych ze specyfikacją CLS nie mogą być oznaczone jako zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-245">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="d0ac8-246">2</span><span class="sxs-lookup"><span data-stu-id="d0ac8-246">2</span></span>
<span data-ttu-id="d0ac8-247">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d0ac8-247">Generics</span></span> | [<span data-ttu-id="d0ac8-248">Typy ogólne i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-248">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d0ac8-249">Zagnieżdżone typy powinny zawierać co najmniej tyle parametrów ogólnych jak typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-249">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="d0ac8-250">Parametry ogólne w typie zagnieżdżonym odpowiadają pozycjom parametrów ogólnych w jego typie otaczającym.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-250">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="d0ac8-251">42</span><span class="sxs-lookup"><span data-stu-id="d0ac8-251">42</span></span>
<span data-ttu-id="d0ac8-252">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d0ac8-252">Generics</span></span> | [<span data-ttu-id="d0ac8-253">Typy ogólne i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-253">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d0ac8-254">Nazwa typu ogólnego zawiera kodowanie liczby parametrów typu zadeklarowanych w typie niezagnieżdżonym lub nowo wprowadzona do typu, jeśli jest zagnieżdżona, zgodnie z regułami określonymi powyżej.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-254">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="d0ac8-255">43</span><span class="sxs-lookup"><span data-stu-id="d0ac8-255">43</span></span>
<span data-ttu-id="d0ac8-256">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d0ac8-256">Generics</span></span> | [<span data-ttu-id="d0ac8-257">Typy ogólne i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-257">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d0ac8-258">Typ ogólny musi redeklarować wystarczające ograniczenia, aby zagwarantować, że wszystkie ograniczenia dotyczące typu podstawowego lub interfejsów byłyby spełnione przez ograniczenia typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-258">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="d0ac8-259">44</span><span class="sxs-lookup"><span data-stu-id="d0ac8-259">44</span></span>
<span data-ttu-id="d0ac8-260">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d0ac8-260">Generics</span></span> | [<span data-ttu-id="d0ac8-261">Typy ogólne i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-261">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d0ac8-262">Typy używane jako ograniczenia parametrów ogólnych będą same w sobie zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-262">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="d0ac8-263">45</span><span class="sxs-lookup"><span data-stu-id="d0ac8-263">45</span></span>
<span data-ttu-id="d0ac8-264">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d0ac8-264">Generics</span></span> | [<span data-ttu-id="d0ac8-265">Typy ogólne i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-265">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d0ac8-266">Widoczność i dostępność elementów członkowskich (w tym zagnieżdżonych typów) w typie ogólnym, który można utworzyć, jest uznawana za zakres do określonego wystąpienia, a nie jako całości deklaracji typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-266">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="d0ac8-267">Przy założeniu, że nadal mają zastosowanie reguły widoczności i dostępności reguły CLS 12.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-267">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="d0ac8-268">46</span><span class="sxs-lookup"><span data-stu-id="d0ac8-268">46</span></span>
<span data-ttu-id="d0ac8-269">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d0ac8-269">Generics</span></span> | [<span data-ttu-id="d0ac8-270">Typy ogólne i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-270">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="d0ac8-271">Dla każdej abstrakcyjnej lub wirtualnej metody ogólnej należy mieć domyślną implementację specyficzną (nieabstrakcyjną)</span><span class="sxs-lookup"><span data-stu-id="d0ac8-271">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="d0ac8-272">47</span><span class="sxs-lookup"><span data-stu-id="d0ac8-272">47</span></span>
<span data-ttu-id="d0ac8-273">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d0ac8-273">Interfaces</span></span> | [<span data-ttu-id="d0ac8-274">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d0ac8-274">Interfaces</span></span>](#interfaces) | <span data-ttu-id="d0ac8-275">Interfejsy zgodne ze specyfikacją CLS nie wymagają definicji metod niezgodnych ze specyfikacją CLS w celu ich wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-275">CLS-compliant interfaces shall not require the definition of non-CLS compliant methods in order to implement them.</span></span> | <span data-ttu-id="d0ac8-276">postanowienia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-276">18</span></span>
<span data-ttu-id="d0ac8-277">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d0ac8-277">Interfaces</span></span> | [<span data-ttu-id="d0ac8-278">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d0ac8-278">Interfaces</span></span>](#interfaces) | <span data-ttu-id="d0ac8-279">Interfejsy zgodne ze specyfikacją CLS nie definiują metod statycznych ani nie definiują pól.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-279">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="d0ac8-280">19</span><span class="sxs-lookup"><span data-stu-id="d0ac8-280">19</span></span>
<span data-ttu-id="d0ac8-281">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-281">Members</span></span> | [<span data-ttu-id="d0ac8-282">Ogólnie wpisz składowe</span><span class="sxs-lookup"><span data-stu-id="d0ac8-282">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="d0ac8-283">Globalne pola statyczne i metody nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-283">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="d0ac8-284">36</span><span class="sxs-lookup"><span data-stu-id="d0ac8-284">36</span></span>
<span data-ttu-id="d0ac8-285">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-285">Members</span></span> | -- | <span data-ttu-id="d0ac8-286">Wartość literału statycznego jest określana za pomocą metadanych inicjacji pola.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-286">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="d0ac8-287">Literał zgodny ze specyfikacją CLS musi mieć wartość określoną w metadanych inicjowania pola, która jest identyczna z tym samym typem co literał (lub typ podstawowy, jeśli ten literał jest `enum`).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-287">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="d0ac8-288">13</span><span class="sxs-lookup"><span data-stu-id="d0ac8-288">13</span></span>
<span data-ttu-id="d0ac8-289">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-289">Members</span></span> | [<span data-ttu-id="d0ac8-290">Ogólnie wpisz składowe</span><span class="sxs-lookup"><span data-stu-id="d0ac8-290">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="d0ac8-291">Ograniczenie vararg nie jest częścią specyfikacji CLS, a jedyną konwencją wywoływania obsługiwaną przez specyfikację CLS jest standardowa zarządzana Konwencja wywoływania.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-291">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="d0ac8-292">15000</span><span class="sxs-lookup"><span data-stu-id="d0ac8-292">15</span></span>
<span data-ttu-id="d0ac8-293">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d0ac8-293">Naming conventions</span></span> | [<span data-ttu-id="d0ac8-294">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d0ac8-294">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="d0ac8-295">Zespoły muszą przestrzegać załącznika 7 raportu technicznego 15 standardu Unicode 3.0 w celu określenia zestawu znaków dozwolonego do uruchomienia i dołączenia do identyfikatorów, dostępne online w [formularzach normalizacji Unicode](https://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-295">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](https://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="d0ac8-296">Identyfikatory powinny znajdować się w formacie kanonicznym zdefiniowanym przez normalizację Unicode w postaci C. W celach CLS dwa identyfikatory są takie same, jeśli ich mapowania małymi literami (zgodnie z ustawieniami regionalnymi Unicode, które różnią się od liter, jeden do jednego) są takie same.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-296">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiers are the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="d0ac8-297">Oznacza to, że w przypadku dwóch identyfikatorów, które mają być uznawane za różne pod względem CLS, różnią się w więcej niż w ich przypadku.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-297">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="d0ac8-298">Jednak w celu zastąpienia definicji dziedziczonej, interfejs wiersza polecenia wymaga dokładnego kodowania oryginalnej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-298">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="d0ac8-299">4</span><span class="sxs-lookup"><span data-stu-id="d0ac8-299">4</span></span>
<span data-ttu-id="d0ac8-300">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-300">Overloading</span></span> | [<span data-ttu-id="d0ac8-301">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d0ac8-301">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="d0ac8-302">Wszystkie nazwy wprowadzone w zakresie zgodnym ze specyfikacją CLS powinny być odrębne niezależnie od rodzaju, z wyjątkiem sytuacji, gdy nazwy są identyczne i rozwiązywane przez przeciążanie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-302">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="d0ac8-303">Oznacza to, że podczas gdy CTS zezwala na pojedynczy typ do używania tej samej nazwy dla metody i pola, CLS nie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-303">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="d0ac8-304">5</span><span class="sxs-lookup"><span data-stu-id="d0ac8-304">5</span></span>
<span data-ttu-id="d0ac8-305">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-305">Overloading</span></span> | [<span data-ttu-id="d0ac8-306">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d0ac8-306">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="d0ac8-307">Pola i zagnieżdżone typy powinny różnić się odrębnie przez porównanie identyfikatorów, nawet jeśli CTS zezwala na rozróżnianie unikatowych podpisów.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-307">Fields and nested types shall be distinct by identifier comparison alone, even though the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="d0ac8-308">Metody, właściwości i zdarzenia, które mają taką samą nazwę (za pomocą porównania identyfikatorów), różnią się więcej niż tylko zwracanym typem, z wyjątkiem określonych w regule CLS 39</span><span class="sxs-lookup"><span data-stu-id="d0ac8-308">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type,except as specified in CLS Rule 39</span></span> | <span data-ttu-id="d0ac8-309">6</span><span class="sxs-lookup"><span data-stu-id="d0ac8-309">6</span></span>
<span data-ttu-id="d0ac8-310">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-310">Overloading</span></span> | [<span data-ttu-id="d0ac8-311">Overloads</span><span class="sxs-lookup"><span data-stu-id="d0ac8-311">Overloads</span></span>](#overloads) | <span data-ttu-id="d0ac8-312">Tylko właściwości i metody mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-312">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="d0ac8-313">37</span><span class="sxs-lookup"><span data-stu-id="d0ac8-313">37</span></span>
<span data-ttu-id="d0ac8-314">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-314">Overloading</span></span> | [<span data-ttu-id="d0ac8-315">Overloads</span><span class="sxs-lookup"><span data-stu-id="d0ac8-315">Overloads</span></span>](#overloads) |<span data-ttu-id="d0ac8-316">Właściwości i metody mogą być przeciążone na podstawie liczby i typów ich parametrów, z wyjątkiem operatorów konwersji o nazwie `op_Implicit` i `op_Explicit`, które mogą być również przeciążone na podstawie ich typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-316">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="d0ac8-317">38</span><span class="sxs-lookup"><span data-stu-id="d0ac8-317">38</span></span>
<span data-ttu-id="d0ac8-318">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-318">Overloading</span></span> | -- | <span data-ttu-id="d0ac8-319">Jeśli dwie lub więcej metod zgodnych ze specyfikacją CLS zadeklarowanych w typie ma taką samą nazwę i, dla określonego zestawu wystąpień typu, mają one te same parametry i zwracane typy, wówczas wszystkie te metody są semantycznie równoważne w tych wystąpieniach typu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-319">If two or more CLS-compliant methods declared in a type have the same name and, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="d0ac8-320">48</span><span class="sxs-lookup"><span data-stu-id="d0ac8-320">48</span></span>
<span data-ttu-id="d0ac8-321">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-321">Properties</span></span> | [<span data-ttu-id="d0ac8-322">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-322">Properties</span></span>](#properties) | <span data-ttu-id="d0ac8-323">Metody, które implementują metody pobierającej i ustawiającej właściwość, są oznaczone `SpecialName` w metadanych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-323">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="d0ac8-324">codzienne</span><span class="sxs-lookup"><span data-stu-id="d0ac8-324">24</span></span>
<span data-ttu-id="d0ac8-325">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-325">Properties</span></span> | [<span data-ttu-id="d0ac8-326">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-326">Properties</span></span>](#properties) | <span data-ttu-id="d0ac8-327">Metody dostępu do właściwości muszą być statyczne, wszystkie być wirtualne lub być wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-327">A property’s accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="d0ac8-328">25</span><span class="sxs-lookup"><span data-stu-id="d0ac8-328">26</span></span>
<span data-ttu-id="d0ac8-329">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-329">Properties</span></span> | [<span data-ttu-id="d0ac8-330">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-330">Properties</span></span>](#properties) | <span data-ttu-id="d0ac8-331">Typ właściwości musi być typem zwracanym metody pobierającej i typem ostatniego argumentu metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-331">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="d0ac8-332">Typy parametrów właściwości są typami parametrów do metody pobierającej i typami wszystkich oprócz końcowych parametrów metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-332">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="d0ac8-333">Wszystkie te typy muszą być zgodne ze specyfikacją CLS i nie mogą być zarządzanymi wskaźnikami (czyli nie są przesyłane przez odwołanie).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-333">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="d0ac8-334">27</span><span class="sxs-lookup"><span data-stu-id="d0ac8-334">27</span></span>
<span data-ttu-id="d0ac8-335">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-335">Properties</span></span> | [<span data-ttu-id="d0ac8-336">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-336">Properties</span></span>](#properties) | <span data-ttu-id="d0ac8-337">Właściwości muszą być zgodne z określonym wzorcem nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-337">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="d0ac8-338">Atrybut `SpecialName`, do którego odwołuje się reguła CLS, jest ignorowany w odpowiednich porównaniach nazw i stosuje się do reguł identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-338">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="d0ac8-339">Właściwość ma metodę pobierającą, metodę ustawiającą lub obie te metody.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-339">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="d0ac8-340">28</span><span class="sxs-lookup"><span data-stu-id="d0ac8-340">28</span></span>
<span data-ttu-id="d0ac8-341">Konwersja typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-341">Type conversion</span></span> | [<span data-ttu-id="d0ac8-342">Konwersja typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-342">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="d0ac8-343">Jeśli podano parametr op_Implicit lub op_Explicit, należy podać alternatywną metodę zapewniania przekształcenie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-343">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="d0ac8-344">39</span><span class="sxs-lookup"><span data-stu-id="d0ac8-344">39</span></span>
<span data-ttu-id="d0ac8-345">Types</span><span class="sxs-lookup"><span data-stu-id="d0ac8-345">Types</span></span> | [<span data-ttu-id="d0ac8-346">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-346">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d0ac8-347">Opakowane typy wartości nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-347">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="d0ac8-348">3</span><span class="sxs-lookup"><span data-stu-id="d0ac8-348">3</span></span>
<span data-ttu-id="d0ac8-349">Types</span><span class="sxs-lookup"><span data-stu-id="d0ac8-349">Types</span></span> | [<span data-ttu-id="d0ac8-350">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-350">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d0ac8-351">Wszystkie typy występujące w podpisie muszą być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-351">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="d0ac8-352">Wszystkie typy tworzące typ ogólny, który tworzy wystąpienie, są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-352">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="d0ac8-353">11</span><span class="sxs-lookup"><span data-stu-id="d0ac8-353">11</span></span>
<span data-ttu-id="d0ac8-354">Types</span><span class="sxs-lookup"><span data-stu-id="d0ac8-354">Types</span></span> | [<span data-ttu-id="d0ac8-355">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-355">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d0ac8-356">Wpisane odwołania nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-356">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="d0ac8-357">14,5</span><span class="sxs-lookup"><span data-stu-id="d0ac8-357">14</span></span>
<span data-ttu-id="d0ac8-358">Types</span><span class="sxs-lookup"><span data-stu-id="d0ac8-358">Types</span></span> | [<span data-ttu-id="d0ac8-359">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-359">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d0ac8-360">Niezarządzane typy wskaźnika nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-360">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="d0ac8-361">7</span><span class="sxs-lookup"><span data-stu-id="d0ac8-361">17</span></span>
<span data-ttu-id="d0ac8-362">Types</span><span class="sxs-lookup"><span data-stu-id="d0ac8-362">Types</span></span> | [<span data-ttu-id="d0ac8-363">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-363">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d0ac8-364">Klasy zgodne ze specyfikacją CLS, typy wartości i interfejsy nie wymagają implementacji członków niezgodnych ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="d0ac8-364">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="d0ac8-365">20</span><span class="sxs-lookup"><span data-stu-id="d0ac8-365">20</span></span>
<span data-ttu-id="d0ac8-366">Types</span><span class="sxs-lookup"><span data-stu-id="d0ac8-366">Types</span></span> | [<span data-ttu-id="d0ac8-367">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-367">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="d0ac8-368">Element [System. Object](xref:System.Object) jest zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-368">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="d0ac8-369">Wszystkie inne klasy zgodne ze specyfikacją CLS są dziedziczone z klasy zgodnej ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-369">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="d0ac8-370">233</span><span class="sxs-lookup"><span data-stu-id="d0ac8-370">23</span></span>

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="d0ac8-371">Typy i podpisy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-371">Types and type member signatures</span></span>

<span data-ttu-id="d0ac8-372">Typ [System. Object](xref:System.Object) jest zgodny ze specyfikacją CLS i jest typem podstawowym wszystkich typów obiektów w systemie .NET Framework typu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-372">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET Framework type system.</span></span> <span data-ttu-id="d0ac8-373">Dziedziczenie w .NET Framework jest niejawne (na przykład Klasa [String](xref:System.String) niejawnie dziedziczy z klasy `Object`) lub explicit (na przykład Klasa [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) jawnie dziedziczy z [ Klasa ArgumentException](xref:System.ArgumentException) , która jawnie dziedziczy z klasy [Exception](xref:System.Exception) .</span><span class="sxs-lookup"><span data-stu-id="d0ac8-373">Inheritance in the .NET Framework is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="d0ac8-374">Aby typ pochodny był zgodny ze specyfikacją CLS, jego typ podstawowy również musi być zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-374">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span>

<span data-ttu-id="d0ac8-375">Poniższy przykład przedstawia typ pochodny, którego typ podstawowy nie jest zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-375">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="d0ac8-376">Definiuje on klasę bazową `Counter`, która używa niepodpisanej 32-bitowej liczby całkowitej jako licznika.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-376">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="d0ac8-377">Ponieważ Klasa udostępnia funkcje licznika przez Zawijanie liczby całkowitej bez znaku, Klasa jest oznaczona jako niezgodna ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-377">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="d0ac8-378">W związku z tym Klasa pochodna, `NonZeroCounter`, również nie jest zgodna ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-378">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span>

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
      return $"{ctr}). ";
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
      Return $"{ctr}). "
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

<span data-ttu-id="d0ac8-379">Wszystkie typy, które pojawiają się w sygnaturach składowych, łącznie z typem zwracanym metody lub typem właściwości, muszą być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-379">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="d0ac8-380">Ponadto dla typów ogólnych:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-380">In addition, for generic types:</span></span>

* <span data-ttu-id="d0ac8-381">Wszystkie typy tworzące typ ogólny wystąpienia muszą być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-381">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="d0ac8-382">Wszystkie typy używane jako ograniczenia parametrów ogólnych muszą być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-382">All types used as constraints on generic parameters must be CLS-compliant.</span></span>

<span data-ttu-id="d0ac8-383">[Wspólny system typów](common-type-system.md) .NET zawiera wiele wbudowanych typów, które są obsługiwane bezpośrednio przez środowisko uruchomieniowe języka wspólnego i są specjalnie zakodowane w metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-383">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="d0ac8-384">Z tych typów wewnętrznych typy wymienione w poniższej tabeli są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-384">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span>

<span data-ttu-id="d0ac8-385">Typ zgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="d0ac8-385">CLS-compliant type</span></span> | <span data-ttu-id="d0ac8-386">Opis</span><span class="sxs-lookup"><span data-stu-id="d0ac8-386">Description</span></span>
------------------ | -----------
[<span data-ttu-id="d0ac8-387">Bajc</span><span class="sxs-lookup"><span data-stu-id="d0ac8-387">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="d0ac8-388">8-bitowa liczba całkowita bez znaku</span><span class="sxs-lookup"><span data-stu-id="d0ac8-388">8-bit unsigned integer</span></span>
[<span data-ttu-id="d0ac8-389">Int16</span><span class="sxs-lookup"><span data-stu-id="d0ac8-389">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="d0ac8-390">16-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="d0ac8-390">16-bit signed integer</span></span>
[<span data-ttu-id="d0ac8-391">Elementem</span><span class="sxs-lookup"><span data-stu-id="d0ac8-391">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="d0ac8-392">32-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="d0ac8-392">32-bit signed integer</span></span>
[<span data-ttu-id="d0ac8-393">Int64</span><span class="sxs-lookup"><span data-stu-id="d0ac8-393">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="d0ac8-394">64-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="d0ac8-394">64-bit signed integer</span></span>
[<span data-ttu-id="d0ac8-395">Wiersz</span><span class="sxs-lookup"><span data-stu-id="d0ac8-395">Single</span></span>](xref:System.Single) | <span data-ttu-id="d0ac8-396">Wartość zmiennoprzecinkowa o pojedynczej precyzji</span><span class="sxs-lookup"><span data-stu-id="d0ac8-396">Single-precision floating-point value</span></span>
[<span data-ttu-id="d0ac8-397">Double</span><span class="sxs-lookup"><span data-stu-id="d0ac8-397">Double</span></span>](xref:System.Double) | <span data-ttu-id="d0ac8-398">Wartość zmiennoprzecinkowa o podwójnej precyzji</span><span class="sxs-lookup"><span data-stu-id="d0ac8-398">Double-precision floating-point value</span></span>
[<span data-ttu-id="d0ac8-399">Typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-399">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="d0ac8-400">Typ wartości true lub false</span><span class="sxs-lookup"><span data-stu-id="d0ac8-400">true or false value type</span></span>
[<span data-ttu-id="d0ac8-401">Delikatn</span><span class="sxs-lookup"><span data-stu-id="d0ac8-401">Char</span></span>](xref:System.Char) | <span data-ttu-id="d0ac8-402">Jednostka kodu zakodowana w formacie UTF-16</span><span class="sxs-lookup"><span data-stu-id="d0ac8-402">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="d0ac8-403">Dokładności</span><span class="sxs-lookup"><span data-stu-id="d0ac8-403">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="d0ac8-404">Liczba dziesiętna liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="d0ac8-404">Non-floating-point decimal number</span></span>
[<span data-ttu-id="d0ac8-405">IntPtr</span><span class="sxs-lookup"><span data-stu-id="d0ac8-405">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="d0ac8-406">Wskaźnik lub uchwyt rozmiaru zdefiniowanego przez platformę</span><span class="sxs-lookup"><span data-stu-id="d0ac8-406">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="d0ac8-407">Ciąg</span><span class="sxs-lookup"><span data-stu-id="d0ac8-407">String</span></span>](xref:System.String) | <span data-ttu-id="d0ac8-408">Kolekcja zero, jeden lub więcej obiektów char</span><span class="sxs-lookup"><span data-stu-id="d0ac8-408">Collection of zero, one, or more Char objects</span></span>

<span data-ttu-id="d0ac8-409">Typy wewnętrzne wymienione w poniższej tabeli są niezgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-409">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>

<span data-ttu-id="d0ac8-410">Niezgodny typ</span><span class="sxs-lookup"><span data-stu-id="d0ac8-410">Non-compliant type</span></span> | <span data-ttu-id="d0ac8-411">Opis</span><span class="sxs-lookup"><span data-stu-id="d0ac8-411">Description</span></span> | <span data-ttu-id="d0ac8-412">Alternatywa zgodna ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="d0ac8-412">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="d0ac8-413">SByte</span><span class="sxs-lookup"><span data-stu-id="d0ac8-413">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="d0ac8-414">8-bitowy typ danych ze znakiem liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="d0ac8-414">8-bit signed integer data type</span></span> | [<span data-ttu-id="d0ac8-415">Int16</span><span class="sxs-lookup"><span data-stu-id="d0ac8-415">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="d0ac8-416">UInt16</span><span class="sxs-lookup"><span data-stu-id="d0ac8-416">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="d0ac8-417">16-bitowa liczba całkowita bez znaku</span><span class="sxs-lookup"><span data-stu-id="d0ac8-417">16-bit unsigned integer</span></span> | [<span data-ttu-id="d0ac8-418">Elementem</span><span class="sxs-lookup"><span data-stu-id="d0ac8-418">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="d0ac8-419">Równ</span><span class="sxs-lookup"><span data-stu-id="d0ac8-419">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="d0ac8-420">32-bitowa liczba całkowita bez znaku</span><span class="sxs-lookup"><span data-stu-id="d0ac8-420">32-bit unsigned integer</span></span> | [<span data-ttu-id="d0ac8-421">Int64</span><span class="sxs-lookup"><span data-stu-id="d0ac8-421">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="d0ac8-422">UInt64</span><span class="sxs-lookup"><span data-stu-id="d0ac8-422">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="d0ac8-423">64-bitowa liczba całkowita bez znaku</span><span class="sxs-lookup"><span data-stu-id="d0ac8-423">64-bit unsigned integer</span></span> | <span data-ttu-id="d0ac8-424">[Int64](xref:System.Int64) (może przepełnić się), [BigInteger](xref:System.Numerics.BigInteger)lub [Double](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="d0ac8-424">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="d0ac8-425">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="d0ac8-425">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="d0ac8-426">Niepodpisany wskaźnik lub dojście</span><span class="sxs-lookup"><span data-stu-id="d0ac8-426">Unsigned pointer or handle</span></span> | [<span data-ttu-id="d0ac8-427">IntPtr</span><span class="sxs-lookup"><span data-stu-id="d0ac8-427">IntPtr</span></span>](xref:System.IntPtr)

<span data-ttu-id="d0ac8-428">Biblioteka klas .NET Framework lub jakakolwiek inna Biblioteka klas może zawierać inne typy, które nie są zgodne ze specyfikacją CLS; na przykład:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-428">The .NET Framework Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span>

* <span data-ttu-id="d0ac8-429">Opakowane typy wartości.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-429">Boxed value types.</span></span> <span data-ttu-id="d0ac8-430">Poniższy C# przykład tworzy klasę, która ma właściwość publiczną typu `int`\* o nazwie `Value`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-430">The following C# example creates a class that has a public property of type `int`\* named `Value`.</span></span> <span data-ttu-id="d0ac8-431">Ponieważ `int`\* jest opakowanym typem wartościowym, kompilator flaguje go jako niezgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-431">Because an `int`\* is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

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

* <span data-ttu-id="d0ac8-432">Typy odwołań, które są specjalnymi konstrukcjami, które zawierają odwołanie do obiektu i odwołanie do typu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-432">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="d0ac8-433">Jeśli typ nie jest zgodny ze specyfikacją CLS, należy zastosować atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) z parametrem *iszgodna* z wartością `false`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-433">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="d0ac8-434">Aby uzyskać więcej informacji, zobacz sekcję [atrybut CLSCompliantAttribute](#the-clscompliantattribute-attribute) .</span><span class="sxs-lookup"><span data-stu-id="d0ac8-434">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>

<span data-ttu-id="d0ac8-435">Poniższy przykład ilustruje problem zgodności ze specyfikacją CLS w sygnaturze metody i w tworzeniu wystąpienia typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-435">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="d0ac8-436">Definiuje klasę `InvoiceItem` z właściwością typu [UInt32](xref:System.UInt32), właściwością typu [Nullable (UInt32)](xref:System.Nullable%601)i konstruktorem z parametrami typu `UInt32` i `Nullable(Of UInt32)`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-436">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="d0ac8-437">Podczas próby skompilowania tego przykładu uzyskasz cztery ostrzeżenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-437">You get four compiler warnings when you try to compile this example.</span></span>

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

<span data-ttu-id="d0ac8-438">Aby wyeliminować ostrzeżenia kompilatora, Zastąp typy niezgodne ze specyfikacją CLS w `InvoiceItem` publicznym interfejsie z zgodnymi typami:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-438">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

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

<span data-ttu-id="d0ac8-439">Oprócz określonych typów wymienionych niektóre kategorie typów nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-439">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="d0ac8-440">Są to między innymi typy wskaźników niezarządzanych i typy wskaźników funkcji.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-440">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="d0ac8-441">Poniższy przykład generuje ostrzeżenie kompilatora, ponieważ używa wskaźnika do liczby całkowitej, aby utworzyć tablicę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-441">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span>

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

<span data-ttu-id="d0ac8-442">Dla klas abstrakcyjnych zgodnych ze specyfikacją CLS (czyli klas oznaczonych C#jako `abstract` w) wszystkie elementy członkowskie klasy muszą również być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-442">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="d0ac8-443">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d0ac8-443">Naming conventions</span></span>

<span data-ttu-id="d0ac8-444">Ponieważ w niektórych językach programowania nie jest rozróżniana wielkość liter, identyfikatory (takie jak nazwy przestrzeni nazw, typy i składowe) muszą różnić się więcej niż wielkością liter.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-444">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="d0ac8-445">Dwa identyfikatory są uważane za równoważne, jeśli ich mapowania małych liter są takie same.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-445">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="d0ac8-446">W poniższym C# przykładzie zdefiniowano dwie klasy publiczne, `Person` i `person`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-446">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="d0ac8-447">Ponieważ różnią się tylko wielkością liter C# , kompilator flaguje je jako niezgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-447">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span>

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

<span data-ttu-id="d0ac8-448">Identyfikatory języków programowania, takie jak nazwy przestrzeni nazw, typy i elementy członkowskie, muszą być zgodne ze [standardem Unicode 3,0, sprawozdanie techniczne 15, załącznik 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-448">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard 3.0, Technical Report 15, Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="d0ac8-449">Oznacza to, że:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-449">This means that:</span></span>

* <span data-ttu-id="d0ac8-450">Pierwszy znak identyfikatora może być dowolną wielką literą Unicode, małą literą, literą litery tytułu, literą modyfikującą, inną literą lub cyfrą.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-450">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="d0ac8-451">Aby uzyskać informacje dotyczące kategorii znaków Unicode, zobacz Wyliczenie [System. globalizacja. UnicodeCategory](xref:System.Globalization.UnicodeCategory) .</span><span class="sxs-lookup"><span data-stu-id="d0ac8-451">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span>

* <span data-ttu-id="d0ac8-452">Kolejne znaki mogą pochodzić z dowolnej kategorii jako pierwszy znak i mogą również zawierać znaczniki niebędące odstępami, odstępy łączące znaczniki, liczby dziesiętne, interpunkcji łącznika i kody formatowania.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-452">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuations, and formatting codes.</span></span>

<span data-ttu-id="d0ac8-453">Przed porównaniem identyfikatorów należy odfiltrować kody formatowania i przekonwertować identyfikatory na postać normalizacji Unicode, ponieważ pojedynczy znak może być reprezentowany przez wiele jednostek kodu zakodowanych w formacie UTF-16.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-453">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="d0ac8-454">Sekwencje znaków tworzące te same jednostki kodu w formularzu normalizacji Unicode nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-454">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="d0ac8-455">W poniższym przykładzie zdefiniowano właściwość o nazwie `Å`, która składa się ze znaku ANGSTROM (U + 212B), a druga właściwość o nazwie `Å`, która składa się z znaku Wielka litera A z PIERŚCIENIem powyżej (U + 00C5).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-455">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å` which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="d0ac8-456">C# Kompilator oflagowuje kod źródłowy jako niezgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-456">The C# compiler flags the source code as non-CLS-compliant.</span></span>

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

<span data-ttu-id="d0ac8-457">Nazwy elementów członkowskich w ramach określonego zakresu (takie jak przestrzenie nazw w obrębie zestawu, typy w przestrzeni nazw lub elementy członkowskie w ramach typu) muszą być unikatowe, z wyjątkiem nazw, które są rozpoznawane za pomocą przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-457">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="d0ac8-458">To wymaganie jest bardziej rygorystyczne niż w przypadku systemu wspólnego typu, który umożliwia wielu członkom w zakresie posiadanie identycznych nazw, o ile są one różnymi rodzajami elementów członkowskich (na przykład jest to metoda, a jedna to pole).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-458">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="d0ac8-459">W szczególności dla elementów członkowskich typu:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-459">In particular, for type members:</span></span>

* <span data-ttu-id="d0ac8-460">Pola i zagnieżdżone typy są rozróżniane wyłącznie nazwami.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-460">Fields and nested types are distinguished by name alone.</span></span>

* <span data-ttu-id="d0ac8-461">Metody, właściwości i zdarzenia, które mają taką samą nazwę, muszą różnić się więcej niż tylko zwracanym typem.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-461">Methods, properties, and events that have the same name must differ by more than just return type.</span></span>

<span data-ttu-id="d0ac8-462">Poniższy przykład ilustruje wymaganie, aby nazwy elementów członkowskich muszą być unikatowe w ramach zakresu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-462">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="d0ac8-463">Definiuje klasę o nazwie `Converter`, która zawiera cztery składowe o nazwie `Conversion`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-463">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="d0ac8-464">Trzy to metody, a jedna jest właściwością.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-464">Three are methods, and one is a property.</span></span> <span data-ttu-id="d0ac8-465">Metoda, która zawiera parametr `Int64`, ma unikatową nazwę, ale dwie metody z parametrem `Int32` nie są, ponieważ wartość zwracana nie jest uważana za część podpisu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-465">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="d0ac8-466">Właściwość `Conversion` również narusza to wymaganie, ponieważ właściwości nie mogą mieć takiej samej nazwy jak przeciążone metody.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-466">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span>

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

<span data-ttu-id="d0ac8-467">Poszczególne języki zawierają unikatowe słowa kluczowe, dlatego Języki przeznaczone dla środowiska uruchomieniowego języka wspólnego muszą również zawierać mechanizm odwołujący się do identyfikatorów (takich jak nazwy typów), które pokrywają się ze słowami kluczowymi.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-467">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="d0ac8-468">Na przykład `case` jest słowem kluczowym w C# obu i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-468">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="d0ac8-469">Jednak poniższy Visual Basic przykład jest w stanie odróżnić klasę o nazwie `case` od słowa kluczowego `case` przy użyciu otwierającego i zamykającego nawiasu klamrowego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-469">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="d0ac8-470">W przeciwnym razie przykład zostanie wyświetlony komunikat o błędzie "słowo kluczowe nie jest prawidłowe jako identyfikator" i nie można go skompilować.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-470">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span>

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

<span data-ttu-id="d0ac8-471">Poniższy C# przykład jest w stanie utworzyć wystąpienie klasy `case` za pomocą @ symbol, aby odróżnić identyfikator od słowa kluczowego języka.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-471">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="d0ac8-472">Bez niej, C# kompilator wyświetli dwa komunikaty o błędach, "Oczekiwano typu" i "wyrażenie dotyczące nieprawidłowego terminu". "</span><span class="sxs-lookup"><span data-stu-id="d0ac8-472">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span>

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

### <a name="type-conversion"></a><span data-ttu-id="d0ac8-473">Konwersja typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-473">Type conversion</span></span>

<span data-ttu-id="d0ac8-474">Common Language Specification definiuje dwa operatory konwersji:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-474">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="d0ac8-475">`op_Implicit`, który jest używany do rozszerzania konwersji, które nie powodują utraty danych lub dokładności.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-475">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="d0ac8-476">Na przykład struktura [dziesiętna](xref:System.Decimal) zawiera przeciążony operator `op_Implicit`, aby konwertować wartości typów całkowitych i wartości [Char](xref:System.Char) na wartości `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-476">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span>

* <span data-ttu-id="d0ac8-477">`op_Explicit`, który jest używany na potrzeby konwersji zawężających, które mogą spowodować utratę wielkości (wartość jest konwertowana na wartość, która ma mniejszy zakres) lub precyzję.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-477">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="d0ac8-478">Na przykład struktura `Decimal` zawiera przeciążony operator `op_Explicit` do konwersji [podwójnych](xref:System.Double) i [pojedynczych](xref:System.Single) wartości na `Decimal` oraz do konwersji wartości `Decimal` na wartości całkowite, `Double`, `Single`i `Char`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-478">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span>

<span data-ttu-id="d0ac8-479">Jednak nie wszystkie języki obsługują przeciążanie operatora lub definicję operatorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-479">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="d0ac8-480">Jeśli zdecydujesz się zaimplementować te operatory konwersji, należy również podać alternatywny sposób wykonywania konwersji.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-480">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="d0ac8-481">Zalecamy dostarczenie metod `From`XXX i `To`xxx.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-481">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span>

<span data-ttu-id="d0ac8-482">W poniższym przykładzie zdefiniowano Konwersje jawne zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-482">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="d0ac8-483">Tworzy klasę `UDouble`, która reprezentuje podpisaną liczbę zmiennoprzecinkową o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-483">It creates a `UDouble` class that represents an signed double-precision, floating-point number.</span></span> <span data-ttu-id="d0ac8-484">Zapewnia to niejawne konwersje z `UDouble` do `Double` i dla jawnych konwersji z `UDouble` do `Single`, `Double` `UDouble`i `Single` `UDouble`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-484">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="d0ac8-485">Definiuje również metodę `ToDouble` jako alternatywę dla operatora niejawnej konwersji, metody `ToSingle`, `FromDouble`i `FromSingle` jako alternatywy dla operatorów jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-485">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span>

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

### <a name="arrays"></a><span data-ttu-id="d0ac8-486">Tablice</span><span class="sxs-lookup"><span data-stu-id="d0ac8-486">Arrays</span></span>

<span data-ttu-id="d0ac8-487">Tablice zgodne ze specyfikacją CLS są zgodne z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-487">CLS-compliant arrays conform to the following rules:</span></span>

* <span data-ttu-id="d0ac8-488">Wszystkie wymiary tablicy muszą mieć dolną granicę równą zero.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-488">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="d0ac8-489">Poniższy przykład tworzy tablicę niezgodną ze specyfikacją CLS z dolną granicą.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-489">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="d0ac8-490">Należy pamiętać, że pomimo obecności atrybutu [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) kompilator nie wykrywa, że tablica zwracana przez metodę `Numbers.GetTenPrimes` nie jest zgodna ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-490">Note that, despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span>

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

* <span data-ttu-id="d0ac8-491">Wszystkie elementy tablicy muszą zawierać typy zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-491">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="d0ac8-492">W poniższym przykładzie zdefiniowano dwie metody, które zwracają tablice niezgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-492">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="d0ac8-493">Pierwszy zwraca tablicę wartości [UInt32](xref:System.UInt32) .</span><span class="sxs-lookup"><span data-stu-id="d0ac8-493">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="d0ac8-494">Druga zwraca tablicę [obiektów](xref:System.Object) , która zawiera wartości [Int32](xref:System.Int32) i `UInt32`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-494">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="d0ac8-495">Chociaż kompilator identyfikuje pierwszą tablicę jako niezgodną ze względu na typ `UInt32`, nie rozpozna, że druga tablica zawiera elementy niezgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-495">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span>

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

* <span data-ttu-id="d0ac8-496">Rozpoznawanie przeciążenia dla metod, które mają parametry tablicowe, jest oparte na faktach, że są tablicami i według ich typu elementu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-496">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="d0ac8-497">Z tego powodu następująca definicja przeciążonej metody `GetSquares` jest zgodna ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-497">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span>

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

### <a name="interfaces"></a><span data-ttu-id="d0ac8-498">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d0ac8-498">Interfaces</span></span>

<span data-ttu-id="d0ac8-499">Interfejsy zgodne ze specyfikacją CLS mogą definiować właściwości, zdarzenia i metody wirtualne (metody bez implementacji).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-499">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="d0ac8-500">Interfejs zgodny ze specyfikacją CLS nie może mieć następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-500">A CLS-compliant interface cannot have any of the following:</span></span>

* <span data-ttu-id="d0ac8-501">Metody statyczne lub pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-501">Static methods or static fields.</span></span> <span data-ttu-id="d0ac8-502">C# Kompilator generuje błędy kompilatora, jeśli zdefiniujesz statyczną składową w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-502">The C# compiler generates compiler errors if you define a static member in an interface.</span></span>

* <span data-ttu-id="d0ac8-503">Pola.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-503">Fields.</span></span> <span data-ttu-id="d0ac8-504">C# Kompilator generuje błędy kompilatora, jeśli zdefiniujesz pole w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-504">The C# a compiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="d0ac8-505">Metody, które nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-505">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="d0ac8-506">Na przykład następująca definicja interfejsu zawiera metodę `INumber.GetUnsigned`, która jest oznaczona jako niezgodna ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-506">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="d0ac8-507">Ten przykład generuje ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-507">This example generates a compiler warning.</span></span>

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

  <span data-ttu-id="d0ac8-508">Ze względu na tę regułę typy zgodne ze specyfikacją CLS nie są wymagane do implementacji członków niezgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-508">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="d0ac8-509">Jeśli struktura zgodna ze specyfikacją CLS uwidacznia klasę, która implementuje interfejs niezgodny ze specyfikacją CLS, powinien również udostępnić konkretne implementacje wszystkich członków niezgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-509">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span>

<span data-ttu-id="d0ac8-510">Kompilatory języka zgodne ze specyfikacją CLS muszą również zezwalać klasie na udostępnianie oddzielnych implementacji elementów członkowskich o tej samej nazwie i podpisie w wielu interfejsach.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-510">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="d0ac8-511">C#obsługuje jawne implementacje interfejsu w celu zapewnienia różnych implementacji identycznie nazwanych metod.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-511">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="d0ac8-512">Poniższy przykład ilustruje ten scenariusz, definiując klasę `Temperature` implementującą interfejsy `ICelsius` i `IFahrenheit` jako jawne implementacje interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-512">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span>

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

### <a name="enumerations"></a><span data-ttu-id="d0ac8-513">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-513">Enumerations</span></span>

<span data-ttu-id="d0ac8-514">Wyliczenia zgodne ze specyfikacją CLS muszą być zgodne z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-514">CLS-compliant enumerations must follow these rules:</span></span>

* <span data-ttu-id="d0ac8-515">Podstawowym typem wyliczenia musi być wewnętrzna liczba całkowita zgodna ze specyfikacją CLS ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32)lub [Int64](xref:System.Int64)).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-515">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="d0ac8-516">Na przykład poniższy kod próbuje zdefiniować Wyliczenie, którego typem podstawowym jest [UInt32](xref:System.UInt32) i generuje ostrzeżenie kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-516">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span>

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

* <span data-ttu-id="d0ac8-517">Typ wyliczeniowy musi mieć pole pojedynczego wystąpienia o nazwie `Value__`, które jest oznaczone atrybutem `FieldAttributes.RTSpecialName`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-517">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="d0ac8-518">Dzięki temu można odwołać się do wartości pola niejawnie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-518">This enables you to reference the field value implicitly.</span></span>

* <span data-ttu-id="d0ac8-519">Wyliczenie zawiera literał pól statycznych, których typy pasują do typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-519">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="d0ac8-520">Na przykład, jeśli zdefiniujesz `State` Wyliczenie z wartościami `State.On` i `State.Off`, `State.On` i `State.Off` są polami literałów statycznych, których typ to `State`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-520">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span>

* <span data-ttu-id="d0ac8-521">Istnieją dwa rodzaje wyliczeń:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-521">There are two kinds of enumerations:</span></span>

  * <span data-ttu-id="d0ac8-522">Wyliczenie, które reprezentuje zestaw wzajemnie wykluczających się wartości o nazwach całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-522">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="d0ac8-523">Ten typ wyliczenia jest wskazywany przez brak atrybutu niestandardowego [System. FlagsAttribute](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="d0ac8-523">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

  * <span data-ttu-id="d0ac8-524">Wyliczenie, które reprezentuje zestaw flag bitowych, które można połączyć w celu wygenerowania nienazwanej wartości.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-524">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="d0ac8-525">Ten typ wyliczenia jest wskazywany przez obecność atrybutu niestandardowego [System. FlagsAttribute](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="d0ac8-525">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

<span data-ttu-id="d0ac8-526">Aby uzyskać więcej informacji, zapoznaj się z dokumentacją struktury [enum](xref:System.Enum) .</span><span class="sxs-lookup"><span data-stu-id="d0ac8-526">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span>

* <span data-ttu-id="d0ac8-527">Wartość wyliczenia nie jest ograniczona do zakresu określonych wartości.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-527">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="d0ac8-528">Innymi słowy, zakres wartości w wyliczeniu jest zakresem jego wartości źródłowej.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-528">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="d0ac8-529">Można użyć metody `Enum.IsDefined`, aby określić, czy określona wartość jest elementem członkowskim wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-529">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span>

### <a name="type-members-in-general"></a><span data-ttu-id="d0ac8-530">Ogólnie wpisz składowe</span><span class="sxs-lookup"><span data-stu-id="d0ac8-530">Type members in general</span></span>

<span data-ttu-id="d0ac8-531">Common Language Specification wymaga, aby wszystkie pola i metody były dostępne jako elementy członkowskie konkretnej klasy.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-531">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="d0ac8-532">W związku z tym globalne pola i metody statyczne (czyli pola statyczne lub metody, które są zdefiniowane niezależnie od typu) nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-532">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="d0ac8-533">Jeśli spróbujesz dołączyć pole globalne lub metodę w kodzie źródłowym, C# kompilator generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-533">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span>

<span data-ttu-id="d0ac8-534">Common Language Specification obsługuje tylko standardową konwencję wywoływania zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-534">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="d0ac8-535">Nie obsługuje ona niezarządzanych konwencji wywoływania i metod z listami zmiennych argumentów oznaczonych za pomocą słowa kluczowego `varargs`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-535">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="d0ac8-536">W przypadku list zmiennych argumentów, które są zgodne ze standardową konwencją wywoływania zarządzanego, Użyj atrybutu [ParamArrayAttribute](xref:System.ParamArrayAttribute) lub implementacji poszczególnych języków, takich jak słowo kluczowe `params` w C# i słowa kluczowego `ParamArray` w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-536">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span>

### <a name="member-accessibility"></a><span data-ttu-id="d0ac8-537">Ułatwienia dostępu członków</span><span class="sxs-lookup"><span data-stu-id="d0ac8-537">Member accessibility</span></span>

<span data-ttu-id="d0ac8-538">Zastępowanie dziedziczonego elementu członkowskiego nie może zmienić dostępności tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-538">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="d0ac8-539">Na przykład metoda publiczna w klasie bazowej nie może zostać zastąpiona przez prywatną metodę w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-539">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="d0ac8-540">Istnieje jeden wyjątek: `protected internal` (in C#) lub `Protected Friend` (w Visual Basic) składowej w jednym zestawie, który jest zastępowany przez typ w innym zestawie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-540">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="d0ac8-541">W takim przypadku dostępność przesłonięcia jest `Protected`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-541">In that case, the accessibility of the override is `Protected`.</span></span>

<span data-ttu-id="d0ac8-542">Poniższy przykład ilustruje błąd generowany, gdy atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) jest ustawiony na `true`i `Person`, który jest klasą pochodną `Animal`, próbuje zmienić dostępność właściwości `Species` z publicznego do prywatnego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-542">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="d0ac8-543">Przykład został pomyślnie skompilowany, jeśli jego dostępność została zmieniona na publiczną.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-543">The example compiles successfully if its accessibility is changed to public.</span></span>

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

<span data-ttu-id="d0ac8-544">Typy w podpisie składowej muszą być dostępne za każdym razem, gdy ten element członkowski jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-544">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="d0ac8-545">Na przykład oznacza to, że publiczna składowa nie może zawierać parametru, którego typem jest Private, protected lub internal.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-545">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="d0ac8-546">Poniższy przykład ilustruje błąd kompilatora, który powstaje, gdy Konstruktor klasy `StringWrapper` uwidacznia `StringOperationType` wewnętrzną wartość wyliczenia, która określa, w jaki sposób wartość ciągu powinna być opakowana.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-546">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span>

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

### <a name="generic-types-and-members"></a><span data-ttu-id="d0ac8-547">Typy ogólne i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0ac8-547">Generic types and members</span></span>

<span data-ttu-id="d0ac8-548">Zagnieżdżone typy zawsze mają co najmniej tyle parametrów ogólnych jak ich typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-548">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="d0ac8-549">Odnoszą się one do parametrów ogólnych w typie otaczającym.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-549">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="d0ac8-550">Typ ogólny może również zawierać nowe parametry ogólne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-550">The generic type can also include new generic parameters.</span></span>

<span data-ttu-id="d0ac8-551">Relacja między parametrami typu ogólnego typu zawierającego i jego zagnieżdżonymi typami może być ukryta przez składnię poszczególnych języków.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-551">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="d0ac8-552">W poniższym przykładzie typ ogólny `Outer<T>` zawiera dwie klasy zagnieżdżone, `Inner1A` i `Inner1B<U>`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-552">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="d0ac8-553">Wywołania metody `ToString`, którą każda klasa dziedziczy z `Object.ToString`, pokazują, że każda klasa zagnieżdżona zawiera parametry typu klasy zawierającej.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-553">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span>

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

<span data-ttu-id="d0ac8-554">Nazwy typów ogólnych są zakodowane w postaci *nazwy*"*n*, gdzie *name* jest nazwą typu, *\`* jest literałem znaku, a *n* to liczba parametrów zadeklarowanych w typie, lub dla zagnieżdżonych typów ogólnych, liczba nowych wprowadzono parametry typu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-554">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="d0ac8-555">To kodowanie nazw typów ogólnych jest szczególnie przydatne dla deweloperów korzystających z odbicia w celu uzyskania dostępu do typów ogólnych z aspektami CLS w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-555">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span>

<span data-ttu-id="d0ac8-556">Jeśli ograniczenia są stosowane do typu generycznego, wszystkie typy używane jako ograniczenia muszą również być zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-556">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="d0ac8-557">W poniższym przykładzie zdefiniowano klasę o nazwie `BaseClass`, która jest niezgodna ze specyfikacją CLS, i klasy generycznej o nazwie `BaseCollection` której parametr typu musi pochodzić od `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-557">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="d0ac8-558">Ale ponieważ `BaseClass` nie jest zgodny ze specyfikacją CLS, kompilator emituje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-558">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span>

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

<span data-ttu-id="d0ac8-559">Jeśli typ ogólny pochodzi od generycznego typu podstawowego, musi ponownie zadeklarować wszelkie ograniczenia, aby można było zagwarantować, że ograniczenia dotyczące typu podstawowego również są spełnione.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-559">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="d0ac8-560">W poniższym przykładzie zdefiniowano `Number<T>`, która może reprezentować dowolny typ liczbowy.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-560">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="d0ac8-561">Definiuje również klasę `FloatingPoint<T>`, która reprezentuje wartość zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-561">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="d0ac8-562">Jednak kod źródłowy nie zostanie skompilowany, ponieważ nie ma zastosowania ograniczenia dotyczącego `Number<T>` (to T musi być typem wartości), aby `FloatingPoint<T>`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-562">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

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
// The attempt to compile the example displays the following output:
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
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="d0ac8-563">Przykład zostanie skompilowany pomyślnie, jeśli ograniczenie zostanie dodane do klasy `FloatingPoint<T>`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-563">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

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

<span data-ttu-id="d0ac8-564">Common Language Specification nakładają się na model tworzenia wystąpień dla zagnieżdżonych typów i chronionych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-564">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="d0ac8-565">Otwarte typy ogólne nie mogą ujawniać pól ani członków z podpisami zawierającymi określone wystąpienie zagnieżdżonego, chronionego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-565">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="d0ac8-566">Typy nieogólne, które zwiększają wystąpienie określonego wystąpienia generycznej klasy podstawowej lub interfejsu, nie mogą ujawniać pól ani elementów członkowskich z podpisami zawierającymi różne wystąpienia zagnieżdżonego, chronionego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-566">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="d0ac8-567">W poniższym przykładzie zdefiniowano typ ogólny, `C1<T>`i chronioną klasę `C1<T>.N`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-567">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="d0ac8-568">`C1<T>` ma dwie metody, `M1` i `M2`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-568">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="d0ac8-569">Jednakże `M1` nie jest zgodny ze specyfikacją CLS, ponieważ próbuje zwrócić obiekt `C1<int>.N` z `C1<T>`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-569">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="d0ac8-570">Druga klasa, `C2`, pochodzi od `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-570">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="d0ac8-571">Ma dwie metody, `M3` i `M4`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-571">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="d0ac8-572">`M3` jest niezgodna ze specyfikacją CLS, ponieważ próbuje zwrócić obiekt `C1<int>.N` z podklasy `C1<long>`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-572">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="d0ac8-573">Należy zauważyć, że kompilatory języka mogą być jeszcze bardziej restrykcyjne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-573">Note that language compilers can be even more restrictive.</span></span> <span data-ttu-id="d0ac8-574">W tym przykładzie Visual Basic wyświetla błąd podczas próby skompilowania `M4`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-574">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span>

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

### <a name="constructors"></a><span data-ttu-id="d0ac8-575">Konstruktorów</span><span class="sxs-lookup"><span data-stu-id="d0ac8-575">Constructors</span></span>

<span data-ttu-id="d0ac8-576">Konstruktory w klasach i strukturach zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-576">Constructors in CLS-compliant classes and structures must follow these rules:</span></span>

* <span data-ttu-id="d0ac8-577">Konstruktor klasy pochodnej musi wywoływać konstruktora wystąpienia swojej klasy bazowej przed uzyskaniem dostępu do danych dziedziczonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-577">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="d0ac8-578">To wymaganie wynika z faktu, że konstruktory klasy bazowej nie są dziedziczone przez ich klasy pochodne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-578">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="d0ac8-579">Ta zasada nie ma zastosowania do struktur, które nie obsługują bezpośredniego dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-579">This rule does not apply to structures, which do not support direct inheritance.</span></span>

  <span data-ttu-id="d0ac8-580">Zazwyczaj kompilatory wymuszają tę regułę niezależnie od zgodności ze specyfikacją CLS, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-580">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="d0ac8-581">Tworzy klasę `Doctor`, która jest pochodną klasy `Person`, ale Klasa `Doctor` nie może wywołać konstruktora klasy `Person` w celu zainicjowania pól dziedziczonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-581">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span>

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

* <span data-ttu-id="d0ac8-582">Konstruktor obiektów nie może zostać wywołany z wyjątkiem tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-582">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="d0ac8-583">Ponadto nie można dwukrotnie zainicjować obiektu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-583">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="d0ac8-584">Na przykład oznacza to, że `Object.MemberwiseClone` nie może wywoływać konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-584">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>

### <a name="properties"></a><span data-ttu-id="d0ac8-585">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0ac8-585">Properties</span></span>

<span data-ttu-id="d0ac8-586">Właściwości typów zgodnych ze specyfikacją CLS muszą być zgodne z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-586">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="d0ac8-587">Właściwość musi mieć metody ustawiającej, pobierającej lub obu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-587">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="d0ac8-588">W zestawie są one implementowane jako metody specjalne, co oznacza, że będą wyświetlane jako oddzielne metody (metoda pobierająca ma nazwę `get`\_*PropertyName* , a Metoda ustawiająca jest `set`\_*PropertyName*) oznaczona jako `SpecialName` w metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-588">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set`\_*propertyname*) marked as `SpecialName` in the assembly's metadata.</span></span> <span data-ttu-id="d0ac8-589">C# Kompilator wymusza tę regułę automatycznie bez konieczności stosowania atrybutu <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-589">The C# compiler enforces this rule automatically without the need to apply the <xref:System.CLSCompliantAttribute> attribute.</span></span>

* <span data-ttu-id="d0ac8-590">Typ właściwości jest typem zwracanym metody pobierającej właściwości i ostatnim argumentem metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-590">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="d0ac8-591">Te typy muszą być zgodne ze specyfikacją CLS, a argumenty nie mogą być przypisywane do właściwości przez odwołanie (oznacza to, że nie mogą być wskaźnikami zarządzanymi).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-591">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span>

* <span data-ttu-id="d0ac8-592">Jeśli właściwość ma zarówno metodę pobierającą, jak i setter, muszą jednocześnie być wirtualne, zarówno statyczne, jak i oba wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-592">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="d0ac8-593">C# Kompilator automatycznie wymusza tę regułę za pomocą składni definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-593">The C# compiler automatically enforces this rule through property definition syntax.</span></span>

### <a name="events"></a><span data-ttu-id="d0ac8-594">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0ac8-594">Events</span></span>

<span data-ttu-id="d0ac8-595">Zdarzenie jest definiowane przy użyciu jego nazwy i typu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-595">An event is defined by its name and its type.</span></span> <span data-ttu-id="d0ac8-596">Typ zdarzenia jest delegatem, który jest używany do wskazania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-596">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="d0ac8-597">Na przykład zdarzenie `DbConnection.StateChange` jest typu `StateChangeEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-597">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="d0ac8-598">Oprócz samego zdarzenia trzy metody z nazwami na podstawie nazwy zdarzenia dostarczają implementację zdarzenia i są oznaczone jako `SpecialName` w metadanych zestawu:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-598">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span>

* <span data-ttu-id="d0ac8-599">Metoda dodawania programu obsługi zdarzeń o nazwie `add`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-599">A method for adding an event handler, named `add`_*EventName*.</span></span> <span data-ttu-id="d0ac8-600">Na przykład Metoda subskrypcji zdarzeń dla zdarzenia `DbConnection.StateChange` ma nazwę `add_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-600">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span>

* <span data-ttu-id="d0ac8-601">Metoda usuwania programu obsługi zdarzeń o nazwie `remove`_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-601">A method for removing an event handler, named `remove`_*EventName*.</span></span> <span data-ttu-id="d0ac8-602">Na przykład metoda usuwania dla zdarzenia `DbConnection.StateChange` ma nazwę `remove_StateChange`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-602">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="d0ac8-603">Metoda wskazująca, że wystąpiło zdarzenie o nazwie `raise`\_*EventName*.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-603">A method for indicating that the event has occurred, named `raise`\_*EventName*.</span></span>

> [!NOTE]
> <span data-ttu-id="d0ac8-604">Większość reguł Common Language Specification dotyczących zdarzeń jest implementowanych przez kompilatory języka i są przezroczyste dla deweloperów składników.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-604">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span>

<span data-ttu-id="d0ac8-605">Metody dodawania, usuwania i wywoływania zdarzenia muszą mieć taki sam dostęp.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-605">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="d0ac8-606">Muszą one również być statyczne, wystąpienia lub wirtualne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-606">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="d0ac8-607">Metody dodawania i usuwania zdarzenia mają jeden parametr, którego typem jest typ delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-607">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="d0ac8-608">Metody Add i Remove muszą być obecne lub być nieobecne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-608">The add and remove methods must both be present or both be absent.</span></span>

<span data-ttu-id="d0ac8-609">W poniższym przykładzie zdefiniowano klasę zgodną ze specyfikacją CLS o nazwie `Temperature`, która wywołuje zdarzenie `TemperatureChanged`, jeśli zmiana temperatury między dwoma odczytami jest równa lub przekracza wartość progową.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-609">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="d0ac8-610">Klasa `Temperature` jawnie definiuje metodę `raise_TemperatureChanged`, aby umożliwić selektywne wykonywanie programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-610">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

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

### <a name="overloads"></a><span data-ttu-id="d0ac8-611">Overloads</span><span class="sxs-lookup"><span data-stu-id="d0ac8-611">Overloads</span></span>

<span data-ttu-id="d0ac8-612">Common Language Specification nakładają następujące wymagania dotyczące przeciążonych elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-612">The Common Language Specification imposes the following requirements on overloaded members:</span></span>

* <span data-ttu-id="d0ac8-613">Elementy członkowskie mogą być przeciążone na podstawie liczby parametrów i typu każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-613">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="d0ac8-614">Konwencja wywoływania, zwracany typ, Modyfikatory niestandardowe stosowane do metody lub jej parametru oraz czy parametry są przesyłane przez wartość lub przez odwołanie nie są brane pod uwagę podczas różnicowania przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-614">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="d0ac8-615">Aby zapoznać się z przykładem, zobacz kod wymagający, aby nazwy muszą być unikatowe w zakresie w sekcji [konwencji nazewnictwa](#naming-conventions) .</span><span class="sxs-lookup"><span data-stu-id="d0ac8-615">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span>

* <span data-ttu-id="d0ac8-616">Tylko właściwości i metody mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-616">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="d0ac8-617">Pola i zdarzenia nie mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-617">Fields and events cannot be overloaded.</span></span>

* <span data-ttu-id="d0ac8-618">Metody generyczne mogą być przeciążone na podstawie liczby parametrów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-618">Generic methods can be overloaded based on the number of their generic parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="d0ac8-619">Operatory `op_Explicit` i `op_Implicit` są wyjątkami od reguły, która zwraca wartość nie jest uważana za część sygnatury metody w celu rozpoznania przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-619">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="d0ac8-620">Te dwa operatory mogą być przeciążone na podstawie zarówno ich parametrów, jak i ich wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-620">These two operators can be overloaded based on both their parameters and their return value.</span></span>

### <a name="exceptions"></a><span data-ttu-id="d0ac8-621">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d0ac8-621">Exceptions</span></span>

<span data-ttu-id="d0ac8-622">Obiekty wyjątków muszą pochodzić od klasy [System. Exception](xref:System.Exception) lub z innego typu pochodzącego od `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-622">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="d0ac8-623">Poniższy przykład ilustruje błąd kompilatora, który powstaje, gdy Klasa niestandardowa o nazwie `ErrorClass` jest używana do obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-623">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

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

<span data-ttu-id="d0ac8-624">Aby naprawić ten błąd, Klasa `ErrorClass` musi dziedziczyć po `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-624">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="d0ac8-625">Ponadto Właściwość Message musi zostać zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-625">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="d0ac8-626">Poniższy przykład koryguje te błędy w celu zdefiniowania klasy `ErrorClass`, która jest zgodna ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-626">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>

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

### <a name="attributes"></a><span data-ttu-id="d0ac8-627">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0ac8-627">Attributes</span></span>

<span data-ttu-id="d0ac8-628">Zestawy platformy In.NET Framework, atrybuty niestandardowe oferują rozszerzalny mechanizm do przechowywania atrybutów niestandardowych i pobierania metadanych dotyczących obiektów programistycznych, takich jak zestawy, typy, elementy członkowskie i parametry metody.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-628">In.NET Framework assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="d0ac8-629">Atrybuty niestandardowe muszą pochodzić od klasy [System. Attribute](xref:System.Attribute) lub z typu pochodnego od `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-629">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="d0ac8-630">Poniższy przykład narusza tę regułę.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-630">The following example violates this rule.</span></span> <span data-ttu-id="d0ac8-631">Definiuje klasę `NumericAttribute`, która nie pochodzi z `System.Attribute`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-631">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="d0ac8-632">Należy zauważyć, że błąd kompilatora występuje tylko wtedy, gdy jest stosowany atrybut niezgodny ze specyfikacją CLS, nie gdy Klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-632">Note that a compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span>

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

<span data-ttu-id="d0ac8-633">Konstruktor lub właściwości atrybutu zgodnego ze specyfikacją CLS mogą uwidaczniać tylko następujące typy:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-633">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="d0ac8-634">Typu</span><span class="sxs-lookup"><span data-stu-id="d0ac8-634">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="d0ac8-635">Bajc</span><span class="sxs-lookup"><span data-stu-id="d0ac8-635">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="d0ac8-636">Delikatn</span><span class="sxs-lookup"><span data-stu-id="d0ac8-636">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="d0ac8-637">Double</span><span class="sxs-lookup"><span data-stu-id="d0ac8-637">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="d0ac8-638">Int16</span><span class="sxs-lookup"><span data-stu-id="d0ac8-638">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="d0ac8-639">Elementem</span><span class="sxs-lookup"><span data-stu-id="d0ac8-639">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="d0ac8-640">Int64</span><span class="sxs-lookup"><span data-stu-id="d0ac8-640">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="d0ac8-641">Wiersz</span><span class="sxs-lookup"><span data-stu-id="d0ac8-641">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="d0ac8-642">Ciąg</span><span class="sxs-lookup"><span data-stu-id="d0ac8-642">String</span></span>](xref:System.String)

* [<span data-ttu-id="d0ac8-643">Wprowadź</span><span class="sxs-lookup"><span data-stu-id="d0ac8-643">Type</span></span>](xref:System.Type)

* <span data-ttu-id="d0ac8-644">Każdy typ wyliczeniowy, którego typ podstawowy to `Byte`, `Int16`, `Int32`lub `Int64`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-644">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span>

<span data-ttu-id="d0ac8-645">W poniższym przykładzie zdefiniowano klasę `DescriptionAttribute`, która pochodzi od [atrybutu](xref:System.Attribute).</span><span class="sxs-lookup"><span data-stu-id="d0ac8-645">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="d0ac8-646">Konstruktor klasy ma parametr typu `Descriptor`, więc Klasa nie jest zgodna ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-646">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="d0ac8-647">Należy zauważyć, C# że kompilator emituje ostrzeżenie, ale kompiluje się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-647">Note that the C# compiler emits a warning but compiles successfully.</span></span>

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

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="d0ac8-648">Atrybut CLSCompliantAttribute</span><span class="sxs-lookup"><span data-stu-id="d0ac8-648">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="d0ac8-649">Atrybut [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) służy do wskazywania, czy element programu jest zgodny z Common Language Specification.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-649">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="d0ac8-650">Konstruktor `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` zawiera jeden wymagany parametr, *iszgodna*, który wskazuje, czy element programu jest zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-650">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span>

<span data-ttu-id="d0ac8-651">W czasie kompilacji kompilator wykrywa niezgodne elementy, które są zgodne ze specyfikacją CLS, i emituje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-651">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="d0ac8-652">Kompilator nie emituje ostrzeżeń dla typów lub elementów członkowskich, które są jawnie zadeklarowane jako niezgodne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-652">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span>

<span data-ttu-id="d0ac8-653">Deweloperzy składników mogą używać atrybutu `CLSCompliantAttribute` na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-653">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span>

* <span data-ttu-id="d0ac8-654">Do definiowania części interfejsu publicznego uwidocznionych przez składnik, który jest zgodny ze specyfikacją CLS, i części, które nie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-654">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="d0ac8-655">Gdy atrybut jest używany do oznaczania określonych elementów programu jako zgodnych ze specyfikacją CLS, jego użycie gwarantuje, że te elementy są dostępne we wszystkich językach i narzędziach przeznaczonych dla .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-655">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target the .NET Framework.</span></span>

* <span data-ttu-id="d0ac8-656">Aby zapewnić, że interfejs publiczny biblioteki składników uwidacznia tylko elementy programu, które są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-656">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="d0ac8-657">Jeśli elementy nie są zgodne ze specyfikacją CLS, kompilatory zwykle wygenerują ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-657">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="d0ac8-658">W niektórych przypadkach kompilatory języka wymuszają reguły zgodne ze specyfikacją CLS niezależnie od tego, czy atrybut `CLSCompliantAttribute` jest używany.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-658">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="d0ac8-659">Na przykład Definiowanie elementu członkowskiego `*static` w interfejsie narusza regułę CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-659">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="d0ac8-660">Jeśli jednak zdefiniujesz element członkowski `*static` w interfejsie, C# kompilator wyświetli komunikat o błędzie i nie będzie mógł skompilować aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-660">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="d0ac8-661">Atrybut `CLSCompliantAttribute` jest oznaczony atrybutem [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) o wartości `AttributeTargets.All`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-661">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="d0ac8-662">Ta wartość pozwala zastosować atrybut `CLSCompliantAttribute` do dowolnego elementu programu, w tym zestawów, modułów, typów (klasy, struktury, wyliczenia, interfejsy i delegatów), składowych typu (konstruktory, metody, właściwości, pola i zdarzenia), parametry, parametry ogólne i wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-662">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="d0ac8-663">Jednakże, w przypadku, należy zastosować atrybut tylko do zestawów, typów i elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-663">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="d0ac8-664">W przeciwnym razie kompilatory ignorują atrybut i kontynuuje generowanie ostrzeżeń kompilatora zawsze wtedy, gdy napotkają niezgodny parametr, parametr ogólny lub wartość zwracaną w interfejsie publicznym biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-664">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>

<span data-ttu-id="d0ac8-665">Wartość atrybutu `CLSCompliantAttribute` jest dziedziczona przez zawarte elementy programu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-665">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="d0ac8-666">Na przykład, jeśli zestaw jest oznaczony jako zgodny ze specyfikacją CLS, jego typy są również zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-666">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="d0ac8-667">Jeśli typ jest oznaczony jako zgodny ze specyfikacją CLS, jego zagnieżdżone typy i elementy członkowskie są również zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-667">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span>

<span data-ttu-id="d0ac8-668">Dziedziczonej zgodności można jawnie zastąpić, stosując atrybut `CLSCompliantAttribute` do zawartego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-668">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="d0ac8-669">Na przykład można użyć atrybutu `CLSCompliantAttribute` z wartością *Iszgodną* `false` do zdefiniowania niezgodnego typu w zgodnym zestawie i można użyć atrybutu z wartością *iszgodnej* `true` w celu zdefiniowania zgodnego typu w niezgodny zestaw.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-669">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isCompliant* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="d0ac8-670">Istnieje również możliwość zdefiniowania niezgodnych elementów członkowskich w typie zgodnym.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-670">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="d0ac8-671">Niezgodny typ nie może jednak mieć zgodnych elementów członkowskich, dlatego nie można użyć atrybutu z wartością *Iszgodnej* `true`, aby zastąpić dziedziczenie z niezgodnego typu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-671">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span>

<span data-ttu-id="d0ac8-672">Podczas tworzenia składników należy zawsze używać atrybutu `CLSCompliantAttribute`, aby wskazać, czy zestaw, jego typy i jego elementy członkowskie są zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-672">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span>

<span data-ttu-id="d0ac8-673">Aby utworzyć składniki zgodne ze specyfikacją CLS:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-673">To create CLS-compliant components:</span></span>

1. <span data-ttu-id="d0ac8-674">Użyj `CLSCompliantAttribute`, aby oznaczyć zestaw jako zgodny ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-674">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="d0ac8-675">Oznacz wszystkie publicznie uwidocznione typy w zestawie, które nie są zgodne ze specyfikacją CLS jako niezgodne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-675">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span>

3. <span data-ttu-id="d0ac8-676">Oznacz wszystkie publicznie uwidocznionych członków w typach zgodnych ze specyfikacją CLS jako niezgodne.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-676">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span>

4. <span data-ttu-id="d0ac8-677">Podaj alternatywę zgodną ze specyfikacją CLS dla członków niezgodnych ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-677">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span>

<span data-ttu-id="d0ac8-678">Jeśli wszystkie niezgodne typy i elementy członkowskie zostały oznaczone pomyślnie, kompilator nie powinien emitować ostrzeżeń o braku zgodności.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-678">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="d0ac8-679">Należy jednak wskazać, które elementy członkowskie nie są zgodne ze specyfikacją CLS, i wyświetlić ich alternatywy zgodne ze specyfikacją CLS w dokumentacji produktu.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-679">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span>

<span data-ttu-id="d0ac8-680">Poniższy przykład używa atrybutu `CLSCompliantAttribute`, aby zdefiniować zestaw zgodny ze specyfikacją CLS i typ `CharacterUtilities`, który ma dwie składowe niezgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-680">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="d0ac8-681">Ponieważ oba elementy członkowskie są oznaczone atrybutem `CLSCompliant(false)`, kompilator nie generuje ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-681">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="d0ac8-682">Klasa zawiera również alternatywę zgodną ze specyfikacją CLS dla obu tych metod.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-682">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="d0ac8-683">Zwykle dodaliśmy dwa przeciążenia do metody `ToUTF16`, aby zapewnić alternatywy zgodne ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-683">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="d0ac8-684">Jednak ponieważ metody nie mogą być przeciążone w oparciu o wartość zwracaną, nazwy metod zgodnych ze specyfikacją CLS różnią się od nazw metod niezgodnych.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-684">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>

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

<span data-ttu-id="d0ac8-685">Jeśli tworzysz aplikację, a nie bibliotekę (czyli jeśli nie ujawniasz typów lub elementów członkowskich, które mogą być używane przez innych deweloperów aplikacji), zgodność ze specyfikacją CLS elementów programu, których używa aplikacja, jest interesująca tylko wtedy, gdy język ich nie obsługuje .</span><span class="sxs-lookup"><span data-stu-id="d0ac8-685">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="d0ac8-686">W takim przypadku kompilator języka wygeneruje błąd podczas próby użycia elementu niezgodnego ze specyfikacją CLS.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-686">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span>

## <a name="cross-language-interoperability"></a><span data-ttu-id="d0ac8-687">Współdziałanie między językami</span><span class="sxs-lookup"><span data-stu-id="d0ac8-687">Cross-Language Interoperability</span></span>

<span data-ttu-id="d0ac8-688">Niezależność od języka ma wiele możliwych znaczenia.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-688">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="d0ac8-689">Jedno z tych problemów obejmuje bezproblemowe zużywanie typów pisanych w jednym języku z aplikacji w innym języku.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-689">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="d0ac8-690">Drugie znaczenie, które jest fokusem tego artykułu, obejmuje łączenie kodu pisanego w wielu językach w jeden zestaw .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-690">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET Framework assembly.</span></span>

<span data-ttu-id="d0ac8-691">Poniższy przykład ilustruje współdziałanie między językami przez utworzenie biblioteki klas o nazwie Utilities. dll zawierającej dwie klasy, `NumericLib` i `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-691">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="d0ac8-692">Klasa `NumericLib` jest zapisywana C#, a Klasa `StringLib` jest zapisywana w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-692">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="d0ac8-693">Oto kod źródłowy dla `StringUtil.vb`, który zawiera pojedynczy element członkowski, `ToTitleCase`, w swojej klasie `StringLib`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-693">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

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

<span data-ttu-id="d0ac8-694">Oto kod źródłowy dla NumberUtil.cs, który definiuje klasę `NumericLib`, która ma dwa elementy członkowskie, `IsEven` i `NearZero`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-694">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

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

<span data-ttu-id="d0ac8-695">Aby spakować dwie klasy w jednym zestawie, należy skompilować je do modułów.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-695">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="d0ac8-696">Aby skompilować plik kodu źródłowego Visual Basic do modułu, użyj tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-696">To compile the Visual Basic source code file into a module, use this command:</span></span>

```console
vbc /t:module StringUtil.vb
```

<span data-ttu-id="d0ac8-697">Aby skompilować plik C# kodu źródłowego do modułu, użyj tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-697">To compile the C# source code file into a module, use this command:</span></span>

```console
csc /t:module NumberUtil.cs
```

<span data-ttu-id="d0ac8-698">Następnie użyj narzędzia link (link. exe), aby skompilować dwa moduły do zestawu:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-698">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span>

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="d0ac8-699">Poniższy przykład wywołuje metody `NumericLib.NearZero` i `StringLib.ToTitleCase`.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-699">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="d0ac8-700">Należy zauważyć, że zarówno kod Visual Basic, C# jak i kod mogą uzyskać dostęp do metod w obu klasach.</span><span class="sxs-lookup"><span data-stu-id="d0ac8-700">Note that both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

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

<span data-ttu-id="d0ac8-701">Aby skompilować kod Visual Basic, użyj tego polecenia:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-701">To compile the Visual Basic code, use this command:</span></span>

```console
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="d0ac8-702">Aby skompilować przy C#użyciu, Zmień nazwę kompilatora z VBC na CSC i Zmień rozszerzenie pliku z. vb na. cs:</span><span class="sxs-lookup"><span data-stu-id="d0ac8-702">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```console
csc example.cs /r:UtilityLib.dll
```
