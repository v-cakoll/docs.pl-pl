---
title: x:Arguments — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5bcd629e306169c1f7a61a316d76203827a2d0fe
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364269"
---
# <a name="xarguments-directive"></a><span data-ttu-id="f86b2-102">x:Arguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="f86b2-102">x:Arguments Directive</span></span>
<span data-ttu-id="f86b2-103">Argumenty konstrukcji pakietów dla deklaracji elementu obiektu konstruktora bez parametrów w języku XAML lub dla deklaracji obiektu metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="f86b2-103">Packages construction arguments for a non-parameterless constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a><span data-ttu-id="f86b2-104">Użycie elementu XAML (Konstruktor bez parametrów)</span><span class="sxs-lookup"><span data-stu-id="f86b2-104">XAML Element Usage (Nonparameterless constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="f86b2-105">Użycie elementu XAML (Metoda Factory)</span><span class="sxs-lookup"><span data-stu-id="f86b2-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f86b2-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="f86b2-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="f86b2-107">Co najmniej jeden element obiektu, który określa argumenty, które mają być przekazane do tworzenia kopii zapasowej konstruktora bez parametrów lub metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="f86b2-107">One or more object elements that specify arguments to be passed to the backing non-parameterless constructor or factory method.</span></span><br /><br /> <span data-ttu-id="f86b2-108">Typowym zastosowaniem jest użycie tekstu inicjującego wewnątrz elementów obiektów w celu określenia rzeczywistych wartości argumentów.</span><span class="sxs-lookup"><span data-stu-id="f86b2-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="f86b2-109">Zobacz sekcję przykłady.</span><span class="sxs-lookup"><span data-stu-id="f86b2-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="f86b2-110">Kolejność elementów jest istotna.</span><span class="sxs-lookup"><span data-stu-id="f86b2-110">The order of the elements is significant.</span></span> <span data-ttu-id="f86b2-111">Typy XAML w kolejności muszą być zgodne z typami i kolejnością typu w konstruktorze zapasowym lub przeciążenia metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="f86b2-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="f86b2-112">Nazwa metody fabryki, która powinna przetwarzać wszystkie `x:Arguments` argumenty.</span><span class="sxs-lookup"><span data-stu-id="f86b2-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="f86b2-113">Zależności</span><span class="sxs-lookup"><span data-stu-id="f86b2-113">Dependencies</span></span>  
 <span data-ttu-id="f86b2-114">`x:FactoryMethod`może zmodyfikować zakres i zachowanie, jeśli `x:Arguments` ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="f86b2-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="f86b2-115">Jeśli nie `x:FactoryMethod` jest określony, `x:Arguments` ma zastosowanie do alternatywnych podpisów (innych niż domyślne) konstruktorów zapasowych.</span><span class="sxs-lookup"><span data-stu-id="f86b2-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="f86b2-116">Jeśli `x:FactoryMethod` jest określony, `x:Arguments` ma zastosowanie do przeciążenia nazwanej metody.</span><span class="sxs-lookup"><span data-stu-id="f86b2-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f86b2-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f86b2-117">Remarks</span></span>  
 <span data-ttu-id="f86b2-118">KOD XAML 2006 może obsługiwać inicjalizację niedomyślną za pomocą tekstu inicjującego.</span><span class="sxs-lookup"><span data-stu-id="f86b2-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="f86b2-119">Jednak praktyczne zastosowania techniki tworzenia tekstu inicjującego są ograniczone.</span><span class="sxs-lookup"><span data-stu-id="f86b2-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="f86b2-120">Tekst inicjujący jest traktowany jako pojedynczy ciąg tekstowy. w związku z tym tylko dodaje możliwość inicjowania jednego parametru, chyba że konwerter typu jest zdefiniowany dla zachowania konstrukcji, które może analizować niestandardowe elementy informacji i niestandardowe ograniczniki z ciągu.</span><span class="sxs-lookup"><span data-stu-id="f86b2-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="f86b2-121">Ponadto ciąg tekstowy do logiki obiektu jest potencjalnie oddzielnym domyślnym konwerterem typu analizatora XAML do obsługi elementów pierwotnych innych niż ciąg prawdziwy.</span><span class="sxs-lookup"><span data-stu-id="f86b2-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="f86b2-122">Użycie `x:Arguments` XAML nie jest użyciem elementu właściwości w typowym sensie, ponieważ znacznik dyrektywy nie odwołuje się do typu elementu obiektu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="f86b2-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="f86b2-123">Jest więcej zbliżone do innych dyrektyw, takich jak `x:Code` element demarkuje zakres, w którym Adiustacja powinna być interpretowana jako inna niż domyślna dla zawartości podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f86b2-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="f86b2-124">W takim przypadku typ XAML każdego elementu obiektu komunikuje informacje o typach argumentów, które są używane przez analizatory języka XAML w celu ustalenia, która konkretna metoda `x:Arguments` fabryki konstruktorów próbuje odwołać użycie.</span><span class="sxs-lookup"><span data-stu-id="f86b2-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="f86b2-125">`x:Arguments`dla elementu obiektu, który jest konstruowany, musi poprzedzać wszystkie inne elementy właściwości, zawartość, tekst wewnętrzny lub ciągi inicjujące elementu Object.</span><span class="sxs-lookup"><span data-stu-id="f86b2-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="f86b2-126">Elementy obiektu w `x:Arguments` mogą zawierać atrybuty i ciągi inicjujące, które są dozwolone przez ten typ XAML i jego Konstruktor zapasowy lub metodę fabryki.</span><span class="sxs-lookup"><span data-stu-id="f86b2-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="f86b2-127">Dla obiektu lub argumentów można określić niestandardowe typy XAML lub typy XAML, które w przeciwnym wypadku poza domyślną przestrzenią nazw XAML przez odwołanie się do ustanowionych mapowań prefiksów.</span><span class="sxs-lookup"><span data-stu-id="f86b2-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="f86b2-128">Procesory XAML wykorzystują następujące wytyczne, aby określić, jak argumenty określone `x:Arguments` w elemencie powinny być używane do konstruowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="f86b2-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="f86b2-129">Jeśli `x:FactoryMethod` jest określony, informacje są porównywane z określoną `x:FactoryMethod` ( `x:FactoryMethod` należy zauważyć, że wartość jest nazwą metody, a nazwana Metoda może mieć przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="f86b2-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="f86b2-130">Jeśli `x:FactoryMethod` nie jest określony, informacje są porównywane z zestawem wszystkich przeciążeń konstruktora publicznego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f86b2-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="f86b2-131">Logika przetwarzania XAML następnie porównuje liczbę parametrów i wybiera przeciążenia z pasującymi liczbami argumentów.</span><span class="sxs-lookup"><span data-stu-id="f86b2-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="f86b2-132">Jeśli istnieje więcej niż jedno dopasowanie, procesor XAML powinien porównać typy parametrów na podstawie typów XAML podanych elementów obiektu.</span><span class="sxs-lookup"><span data-stu-id="f86b2-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="f86b2-133">Jeśli nadal istnieje więcej niż jedno dopasowanie, zachowanie procesora XAML jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="f86b2-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="f86b2-134">`x:FactoryMethod` Jeśli jest określony, ale nie można rozpoznać metody, procesor XAML powinien zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f86b2-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="f86b2-135">Użycie `<x:Arguments>string</x:Arguments>` atrybutu języka XAML jest technicznie możliwe.</span><span class="sxs-lookup"><span data-stu-id="f86b2-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="f86b2-136">Nie ma jednak możliwości wykraczających poza to, co można zrobić za pomocą tekstu inicjującego i konwerterów typów, a korzystanie z tej składni nie jest zamiarem projektu dla funkcji metody fabryki języka XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="f86b2-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f86b2-137">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f86b2-137">Examples</span></span>  
 <span data-ttu-id="f86b2-138">Poniższy przykład przedstawia sygnaturę konstruktora bez parametrów, a następnie użycie `x:Arguments` kodu XAML, który uzyskuje dostęp do tej sygnatury.</span><span class="sxs-lookup"><span data-stu-id="f86b2-138">The following example shows a non-parameterless constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="f86b2-139">Poniższy przykład przedstawia sygnaturę docelowej metody fabryki, a następnie użycie `x:Arguments` języka XAML, który uzyskuje dostęp do tej sygnatury.</span><span class="sxs-lookup"><span data-stu-id="f86b2-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f86b2-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f86b2-140">See also</span></span>

- [<span data-ttu-id="f86b2-141">Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML</span><span class="sxs-lookup"><span data-stu-id="f86b2-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="f86b2-142">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="f86b2-142">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
