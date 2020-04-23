---
title: x:Arguments — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071592"
---
# <a name="xarguments-directive"></a><span data-ttu-id="885e0-102">x:Arguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="885e0-102">x:Arguments Directive</span></span>

<span data-ttu-id="885e0-103">Pakiety argumenty konstrukcyjne dla nieswęzowej deklaracji elementu obiektu konstruktora w XAML lub dla deklaracji obiektu metody fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="885e0-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>

## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="885e0-104">Użycie elementu XAML (konstruktor bezparametrowy)</span><span class="sxs-lookup"><span data-stu-id="885e0-104">XAML Element Usage (Nonparameterless constructor)</span></span>

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="885e0-105">Użycie elementu XAML (metoda fabryczna)</span><span class="sxs-lookup"><span data-stu-id="885e0-105">XAML Element Usage (factory method)</span></span>

```xaml
<object x:FactoryMethod="methodName"...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="885e0-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="885e0-106">XAML Values</span></span>

|||
|-|-|
|`oneOrMoreObjectElements`|<span data-ttu-id="885e0-107">Jeden lub więcej elementów obiektu, które określają argumenty, które mają być przekazywane do kopii nieparzemetryczne konstruktora lub metody fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="885e0-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="885e0-108">Typowym zastosowaniem jest użycie tekstu inicjowania w elementach obiektu w celu określenia rzeczywistych wartości argumentów.</span><span class="sxs-lookup"><span data-stu-id="885e0-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="885e0-109">Zobacz przykłady sekcji.</span><span class="sxs-lookup"><span data-stu-id="885e0-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="885e0-110">Kolejność elementów jest znacząca.</span><span class="sxs-lookup"><span data-stu-id="885e0-110">The order of the elements is significant.</span></span> <span data-ttu-id="885e0-111">Typy XAML w kolejności musi odpowiadać typy i kolejność typów konstruktora kopii zapasowej lub przeciążenie metody fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="885e0-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|
|`methodName`|<span data-ttu-id="885e0-112">Nazwa metody fabrycznej, która `x:Arguments` powinna przetwarzać wszystkie argumenty.</span><span class="sxs-lookup"><span data-stu-id="885e0-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="885e0-113">Zależności</span><span class="sxs-lookup"><span data-stu-id="885e0-113">Dependencies</span></span>

<span data-ttu-id="885e0-114">`x:FactoryMethod`można zmodyfikować zakres `x:Arguments` i zachowanie, gdzie ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="885e0-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>

<span data-ttu-id="885e0-115">Jeśli `x:FactoryMethod` nie jest `x:Arguments` określony, stosuje się do alternatywnych (nie domyślne) podpisy konstruktorów kopii zapasowej.</span><span class="sxs-lookup"><span data-stu-id="885e0-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>

<span data-ttu-id="885e0-116">Jeśli `x:FactoryMethod` jest `x:Arguments` określony, stosuje się do przeciążenia nazwanej metody.</span><span class="sxs-lookup"><span data-stu-id="885e0-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>

## <a name="remarks"></a><span data-ttu-id="885e0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="885e0-117">Remarks</span></span>

<span data-ttu-id="885e0-118">XAML 2006 może obsługiwać inicjowanie inne niż domyślne za pomocą tekstu inicjowania.</span><span class="sxs-lookup"><span data-stu-id="885e0-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="885e0-119">Jednak praktyczne zastosowanie techniki budowy tekstu inicjowania jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="885e0-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="885e0-120">Tekst inicjowania jest traktowany jako pojedynczy ciąg tekstowy; w związku z tym tylko dodaje możliwości inicjowania pojedynczego parametru, chyba że konwerter typu jest zdefiniowany dla zachowania konstrukcji, które można przeanalizować elementy informacji niestandardowych i niestandardowe ograniczniki z ciągu.</span><span class="sxs-lookup"><span data-stu-id="885e0-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="885e0-121">Ponadto ciąg tekstowy do logiki obiektu jest potencjalnie natywnego konwertera typu domyślnego analizatora analizatora XAML do obsługi podstawowego niż ciąg rzeczywisty.</span><span class="sxs-lookup"><span data-stu-id="885e0-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>

<span data-ttu-id="885e0-122">Użycie `x:Arguments` XAML nie jest użycie elementu właściwości w typowym sensie, ponieważ znaczników dyrektywy nie odwołuje się do typu elementu zawierającego obiekt.</span><span class="sxs-lookup"><span data-stu-id="885e0-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="885e0-123">Jest bardziej zbliżona do innych `x:Code` dyrektyw, takich jak gdzie element demarks zakres, w którym znaczników powinny być interpretowane jako inne niż domyślne dla zawartości podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="885e0-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="885e0-124">W takim przypadku typ XAML każdego elementu obiektu komunikuje informacje o typach argumentów, który jest używany przez `x:Arguments` analizatory XAML do określenia, który podpis metody fabrycznej konstruktora próbuje odwołać.</span><span class="sxs-lookup"><span data-stu-id="885e0-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>

<span data-ttu-id="885e0-125">`x:Arguments`dla elementu obiektu konstruowany musi poprzedzać inne elementy właściwości, zawartość, tekst wewnętrzny lub ciągi inicjowania elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="885e0-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="885e0-126">Elementy obiektu `x:Arguments` wewnątrz mogą zawierać atrybuty i ciągi inicjowania, zgodnie z tym typem XAML i jego konstruktorem zapasowym lub metodą fabryczną.</span><span class="sxs-lookup"><span data-stu-id="885e0-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="885e0-127">Dla obiektu lub argumentów można określić niestandardowe typy XAML lub typy XAML, które w przeciwnym razie znajdują się poza domyślnym obszarem nazw XAML, odwołując się do ustalonych mapowań prefiksów.</span><span class="sxs-lookup"><span data-stu-id="885e0-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>

<span data-ttu-id="885e0-128">Procesory XAML używają następujących wskazówek, aby `x:Arguments` określić, w jaki sposób argumenty określone w powinny być używane do konstruowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="885e0-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="885e0-129">Jeśli `x:FactoryMethod` jest określony, informacje są `x:FactoryMethod` porównywane z `x:FactoryMethod` określonym (należy zauważyć, że wartość jest nazwą metody, a nazwana metoda może mieć przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="885e0-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="885e0-130">Jeśli `x:FactoryMethod` nie jest określony, informacje są porównywane z zestawem wszystkich przeciążeń konstruktora publicznego obiektu.</span><span class="sxs-lookup"><span data-stu-id="885e0-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="885e0-131">Logika przetwarzania XAML następnie porównuje liczbę parametrów i wybiera przeciążenie z pasującymi arity.</span><span class="sxs-lookup"><span data-stu-id="885e0-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="885e0-132">Jeśli istnieje więcej niż jedno dopasowanie, procesor XAML należy porównać typy parametrów na podstawie typów XAML podanych elementów obiektu.</span><span class="sxs-lookup"><span data-stu-id="885e0-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="885e0-133">Jeśli nadal istnieje więcej niż jedno dopasowanie, zachowanie procesora XAML jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="885e0-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="885e0-134">Jeśli `x:FactoryMethod` a jest określony, ale nie można rozpoznać metody, procesor XAML powinien zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="885e0-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>

<span data-ttu-id="885e0-135">Użycie `<x:Arguments>string</x:Arguments>` atrybutu XAML jest technicznie możliwe.</span><span class="sxs-lookup"><span data-stu-id="885e0-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="885e0-136">Zapewnia to jednak żadnych możliwości poza to, co można zrobić w przeciwnym razie za pomocą konwerterów tekstu inicjowania i typu, a użycie tej składni nie jest intencją projektu funkcji metody fabrycznej XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="885e0-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>

## <a name="examples"></a><span data-ttu-id="885e0-137">Przykłady</span><span class="sxs-lookup"><span data-stu-id="885e0-137">Examples</span></span>

<span data-ttu-id="885e0-138">W poniższym przykładzie przedstawiono podpis konstruktora bez `x:Arguments` parametrów, a następnie użycie XAML, który uzyskuje dostęp do tego podpisu.</span><span class="sxs-lookup"><span data-stu-id="885e0-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

```csharp
public class Food {
  private string _name;
  private Int32 _calories;
  public Food(string name, Int32 calories) {
      _name=name;
      _calories=calories;
  }
}
```

```xaml
<my:Food>
  <x:Arguments>
      <x:String>Apple</x:String>
      <x:Int32>150</x:Int32>
  </x:Arguments>
</my:Food>
```

<span data-ttu-id="885e0-139">W poniższym przykładzie pokazano podpis docelowej metody `x:Arguments` fabryki, a następnie użycie XAML, który uzyskuje dostęp do tego podpisu.</span><span class="sxs-lookup"><span data-stu-id="885e0-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>

```csharp
public Food TryLookupFood(string name)
{
switch (name) {
  case "Apple": return new Food("Apple",150);
  case "Chocolate": return new Food("Chocolate",200);
  case "Cheese": return new Food("Cheese", 450);
  default: {return new Food(name,0);
}
}
```

```xaml
<my:Food x:FactoryMethod="TryLookupFood">
  <x:Arguments>
      <x:String>Apple</x:String>
  </x:Arguments>
</my:Food>
```

## <a name="see-also"></a><span data-ttu-id="885e0-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="885e0-140">See also</span></span>

- [<span data-ttu-id="885e0-141">Definiowanie typów niestandardowych do użytku z usługami .NET XAML</span><span class="sxs-lookup"><span data-stu-id="885e0-141">Defining Custom Types for Use with .NET XAML Services</span></span>](define-custom-types.md)
- [<span data-ttu-id="885e0-142">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="885e0-142">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
