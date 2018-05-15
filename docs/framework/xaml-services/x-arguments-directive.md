---
title: x:Arguments — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: e0e7f380ec176e80d2422878a2e676d64985d660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xarguments-directive"></a><span data-ttu-id="beaf1-102">x:Arguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="beaf1-102">x:Arguments Directive</span></span>
<span data-ttu-id="beaf1-103">Argumenty konstrukcji pakietów z systemem innym niż domyślny konstruktor obiektu deklaracji elementu w języku XAML, lub fabryki metody obiektu.</span><span class="sxs-lookup"><span data-stu-id="beaf1-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="beaf1-104">Użycie elementu XAML (inny niż domyślny konstruktor)</span><span class="sxs-lookup"><span data-stu-id="beaf1-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="beaf1-105">Użycie elementu XAML (metoda fabryki)</span><span class="sxs-lookup"><span data-stu-id="beaf1-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="beaf1-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="beaf1-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="beaf1-107">Co najmniej jeden element obiektu określających argumenty do przekazania do tworzenia kopii innych niż domyślne konstruktora lub metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="beaf1-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="beaf1-108">Typowe jest używane do inicjowania tekstu w elementach obiektu umożliwia określenie wartości rzeczywistych argumentów.</span><span class="sxs-lookup"><span data-stu-id="beaf1-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="beaf1-109">Zobacz sekcję dotyczącą przykłady.</span><span class="sxs-lookup"><span data-stu-id="beaf1-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="beaf1-110">Kolejność elementów jest znacząca.</span><span class="sxs-lookup"><span data-stu-id="beaf1-110">The order of the elements is significant.</span></span> <span data-ttu-id="beaf1-111">Typy XAML w kolejności musi pasują do typów, a następnie wpisz kolejność przeciążenie metody konstruktora lub fabryki zapasowego.</span><span class="sxs-lookup"><span data-stu-id="beaf1-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="beaf1-112">Nazwa metody fabryki, która ma być przetwarzana żadnego `x:Arguments` argumentów.</span><span class="sxs-lookup"><span data-stu-id="beaf1-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="beaf1-113">Zależności</span><span class="sxs-lookup"><span data-stu-id="beaf1-113">Dependencies</span></span>  
 <span data-ttu-id="beaf1-114">`x:FactoryMethod` można zmodyfikować zakresu i zachowanie gdzie `x:Arguments` ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="beaf1-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="beaf1-115">Jeśli nie `x:FactoryMethod` jest określony, `x:Arguments` dotyczy alternatywny podpisów (z systemem innym niż domyślny) konstruktorów zapasowego.</span><span class="sxs-lookup"><span data-stu-id="beaf1-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="beaf1-116">Jeśli `x:FactoryMethod` jest określony, `x:Arguments` dotyczy przeciążenia metody o nazwie.</span><span class="sxs-lookup"><span data-stu-id="beaf1-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beaf1-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="beaf1-117">Remarks</span></span>  
 <span data-ttu-id="beaf1-118">XAML 2006 może obsługiwać inicjowania inny niż domyślny za pomocą inicjowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="beaf1-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="beaf1-119">Praktyczne zastosowania technikę konstrukcji tekstu inicjowania jest jednak ograniczona.</span><span class="sxs-lookup"><span data-stu-id="beaf1-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="beaf1-120">Inicjowanie tekst jest traktowany jako jeden ciąg tekstowy; w związku z tym tylko dodaje możliwość inicjowania pojedynczy parametr Jeśli konwerter typów nie jest zdefiniowany dla konstrukcji zachowanie można analizować elementy niestandardowe informacje i niestandardowych ograniczniki z ciągu.</span><span class="sxs-lookup"><span data-stu-id="beaf1-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="beaf1-121">Ciąg tekstowy do obiektu logiki jest również potencjalnie konwerter typów natywnych domyślne danego analizatora XAML do obsługi podstawowych innego niż ciąg wartość true.</span><span class="sxs-lookup"><span data-stu-id="beaf1-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="beaf1-122">`x:Arguments` Użycie języka XAML nie jest użycie elementu właściwości w tym sensie, typowe, ponieważ znacznika dyrektywy nie odwołuje się do typu zawierającego element object.</span><span class="sxs-lookup"><span data-stu-id="beaf1-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="beaf1-123">Jest więcej podobnie dyrektyw takich jak `x:Code` gdzie element demarks zakresu, w którym kod znaczników powinny być rozumiane jako inny niż domyślny dla podrzędnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="beaf1-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="beaf1-124">W takim przypadku typu XAML każdego elementu obiektu komunikuje się informacje o typy argumentów, co jest używany przez analizatory składni języka XAML w celu określenia podpisów metody fabryki określonego konstruktora `x:Arguments` użycia próbuje odwołać.</span><span class="sxs-lookup"><span data-stu-id="beaf1-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="beaf1-125">`x:Arguments` dla obiekt elementu budowany musi poprzedzać inne elementy właściwości, zawartość, tekst wewnętrzny ani ciągi inicjowanie obiektu elementu.</span><span class="sxs-lookup"><span data-stu-id="beaf1-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="beaf1-126">Elementy obiektu wewnątrz `x:Arguments` mogą zawierać atrybuty i ciągi inicjowania dozwolonych przez tego typu XAML i jego zapasowy konstruktora lub metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="beaf1-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="beaf1-127">Dla obiekt lub argumentów można określić niestandardowych typów XAML lub XAML znajdujących się w przeciwnym razie poza domyślnej przestrzeni nazw XAML za pomocą odwołań do mapowania prefiksów ustalonych.</span><span class="sxs-lookup"><span data-stu-id="beaf1-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="beaf1-128">Procesory XAML, skorzystaj z poniższych wskazówek ustalenie sposobu określania argumentów w `x:Arguments` powinien zostać użyty do utworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="beaf1-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="beaf1-129">Jeśli `x:FactoryMethod` określono informacji jest porównywany do określonego `x:FactoryMethod` (należy pamiętać, że wartość `x:FactoryMethod` nazwę metody, a metodę o nazwie mogą mieć przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="beaf1-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="beaf1-130">Jeśli `x:FactoryMethod` nie zostanie określony, informacje są porównywane do zestawu wszystkich przeciążeń konstruktora publicznego obiektu.</span><span class="sxs-lookup"><span data-stu-id="beaf1-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="beaf1-131">Logika przetwarzania XAML następnie porównuje liczbę parametrów i wybiera przeciążenia z dopasowania argumentów.</span><span class="sxs-lookup"><span data-stu-id="beaf1-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="beaf1-132">Jeśli istnieje więcej niż jedno dopasowanie, procesor XAML należy porównać typów parametrów, na podstawie typów XAML elementów udostępnionego obiektu.</span><span class="sxs-lookup"><span data-stu-id="beaf1-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="beaf1-133">W przypadku nadal więcej niż jedno dopasowanie XAML procesora jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="beaf1-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="beaf1-134">Jeśli `x:FactoryMethod` jest określony, ale nie można rozpoznać metody, procesor XAML powinien zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="beaf1-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="beaf1-135">Użycie atrybutu XAML `<x:Arguments>string</x:Arguments>` jest technicznie możliwe.</span><span class="sxs-lookup"><span data-stu-id="beaf1-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="beaf1-136">Zapewnia to nie możliwości poza co można zrobić w przeciwnym razie za pośrednictwem konwertery tekst i typ inicjowania i przy użyciu tej składni nie jest zamiar projektu XAML 2009 funkcji metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="beaf1-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="beaf1-137">Przykłady</span><span class="sxs-lookup"><span data-stu-id="beaf1-137">Examples</span></span>  
 <span data-ttu-id="beaf1-138">W poniższym przykładzie przedstawiono z systemem innym niż domyślny konstruktor podpisu, a następnie użycie XAML `x:Arguments` który uzyskuje dostęp do tego podpisu.</span><span class="sxs-lookup"><span data-stu-id="beaf1-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="beaf1-139">W poniższym przykładzie przedstawiono sygnatury metody fabryki docelowego, a następnie użycie XAML `x:Arguments` który uzyskuje dostęp do tego podpisu.</span><span class="sxs-lookup"><span data-stu-id="beaf1-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="beaf1-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="beaf1-140">See Also</span></span>  
 [<span data-ttu-id="beaf1-141">Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML</span><span class="sxs-lookup"><span data-stu-id="beaf1-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [<span data-ttu-id="beaf1-142">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="beaf1-142">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
