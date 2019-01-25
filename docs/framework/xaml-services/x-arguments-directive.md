---
title: x:Arguments — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: d4cff4c2f95d1418371921a3ac992a3b243d1c07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490820"
---
# <a name="xarguments-directive"></a><span data-ttu-id="60cf8-102">x:Arguments — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="60cf8-102">x:Arguments Directive</span></span>
<span data-ttu-id="60cf8-103">Pakiety argumentów deklaracji elementu innego niż domyślny konstruktor obiektu w XAML lub dla deklaracji obiektu metody fabryki.</span><span class="sxs-lookup"><span data-stu-id="60cf8-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="60cf8-104">Użycie elementu XAML (inny niż domyślny konstruktor)</span><span class="sxs-lookup"><span data-stu-id="60cf8-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="60cf8-105">Użycie elementu XAML (metoda fabryki)</span><span class="sxs-lookup"><span data-stu-id="60cf8-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="60cf8-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="60cf8-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="60cf8-107">Co najmniej jeden element obiektu, które określają argumenty, które mają być przekazane do metody konstruktora lub fabryki innych niż domyślne tworzenie kopii.</span><span class="sxs-lookup"><span data-stu-id="60cf8-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="60cf8-108">Typowy jest Użyj tekstu inicjowanie elementów obiektu, aby określić wartości rzeczywistych argumentów.</span><span class="sxs-lookup"><span data-stu-id="60cf8-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="60cf8-109">Zobacz sekcję przykłady.</span><span class="sxs-lookup"><span data-stu-id="60cf8-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="60cf8-110">Kolejność elementów jest znaczący.</span><span class="sxs-lookup"><span data-stu-id="60cf8-110">The order of the elements is significant.</span></span> <span data-ttu-id="60cf8-111">Typy XAML w kolejności musi pasują do typów, a następnie wpisz kolejność przeciążenia metody konstruktora lub fabryki zapasowy.</span><span class="sxs-lookup"><span data-stu-id="60cf8-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="60cf8-112">Nazwa metody fabryka, która ma być przetwarzana dowolne `x:Arguments` argumentów.</span><span class="sxs-lookup"><span data-stu-id="60cf8-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="60cf8-113">Zależności</span><span class="sxs-lookup"><span data-stu-id="60cf8-113">Dependencies</span></span>  
 <span data-ttu-id="60cf8-114">`x:FactoryMethod` można zmodyfikować zakres i zachowanie gdzie `x:Arguments` ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="60cf8-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="60cf8-115">Jeśli nie `x:FactoryMethod` jest określony, `x:Arguments` stosuje się do alternatywnego podpisy (innych niż domyślne) konstruktorów zapasowy.</span><span class="sxs-lookup"><span data-stu-id="60cf8-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="60cf8-116">Jeśli `x:FactoryMethod` jest określony, `x:Arguments` ma zastosowanie do przeciążenia metody o nazwie.</span><span class="sxs-lookup"><span data-stu-id="60cf8-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60cf8-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60cf8-117">Remarks</span></span>  
 <span data-ttu-id="60cf8-118">XAML 2006 może obsługiwać inicjowania inny niż domyślny za pomocą inicjowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="60cf8-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="60cf8-119">Praktyczne zastosowanie technikę konstrukcji tekstu inicjowania jest jednak ograniczona.</span><span class="sxs-lookup"><span data-stu-id="60cf8-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="60cf8-120">Inicjowanie tekst jest traktowany jako jeden ciąg tekstowy; w związku z tym tylko dodaje możliwość inicjowania jeden parametr, chyba że konwertera typów jest zdefiniowany dla zachowanie konstrukcji, które mogą przeanalizować elementów niestandardowych informacji oraz niestandardowego ograniczników z ciągu.</span><span class="sxs-lookup"><span data-stu-id="60cf8-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="60cf8-121">Ciąg tekstowy do logiki obiektu jest również potencjalnie konwertera typów natywnych domyślną danego analizatora XAML do obsługi podstawowych innych niż ciąg wartość true.</span><span class="sxs-lookup"><span data-stu-id="60cf8-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="60cf8-122">`x:Arguments` Użycia XAML nie jest użycie elementu właściwości w sensie typowe, ponieważ znaczników dyrektywy nie odwołuje się do typu elementu obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="60cf8-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="60cf8-123">Więcej podobnie inne dyrektywy to taki jak `x:Code` gdzie element demarks zakresu, w którym znaczniki powinny być interpretowane jako inny niż domyślny dla podrzędnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="60cf8-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="60cf8-124">W tym przypadku typ XAML każdego elementu obiektu komunikuje się informacji na temat typów argumentu, używany przez analizatory składni XAML, aby określić, które podpis metody fabryka konstruktora określonego `x:Arguments` próbuje odwoływać się do użycia.</span><span class="sxs-lookup"><span data-stu-id="60cf8-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="60cf8-125">`x:Arguments` elementu obiektu budowany musi poprzedzać wszystkie inne elementy właściwości, zawartości, tekst wewnętrzny lub inicjowania ciągi elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="60cf8-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="60cf8-126">Elementy obiektu w ramach `x:Arguments` mogą one obejmować atrybuty i parametry inicjowania dozwolonym przez tego typu XAML oraz sposób jej zapasowy konstruktora lub fabryki.</span><span class="sxs-lookup"><span data-stu-id="60cf8-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="60cf8-127">Dla obiektu lub argumenty można określić niestandardowe typy XAML lub XAML znajdujących się w przeciwnym razie poza domyślna przestrzeń nazw XAML, odwołując się do mapowania prefiksów ustalonych.</span><span class="sxs-lookup"><span data-stu-id="60cf8-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="60cf8-128">Procesory XAML skorzystaj z poniższych wskazówek, aby określić, jak argumenty określone w `x:Arguments` powinien zostać użyty do utworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="60cf8-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="60cf8-129">Jeśli `x:FactoryMethod` jest określony, są porównywane do określonego `x:FactoryMethod` (należy pamiętać, że wartość `x:FactoryMethod` jest nazwa metody, a metody nazwanej, mogą mieć przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="60cf8-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="60cf8-130">Jeśli `x:FactoryMethod` nie zostanie określony, są porównywane do zestawu wszystkich przeciążeń konstruktora publicznego obiektu.</span><span class="sxs-lookup"><span data-stu-id="60cf8-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="60cf8-131">Logika przetwarzania XAML następnie porównuje liczbę parametrów i wybiera przeciążenia za pomocą dopasowywania argumentów.</span><span class="sxs-lookup"><span data-stu-id="60cf8-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="60cf8-132">Jeśli istnieje więcej niż jedno dopasowanie, procesor XAML należy porównać typy parametrów na podstawie typów XAML elementów udostępnionego obiektu.</span><span class="sxs-lookup"><span data-stu-id="60cf8-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="60cf8-133">W przypadku nadal więcej niż jedno dopasowanie zachowanie procesora XAML jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="60cf8-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="60cf8-134">Jeśli `x:FactoryMethod` jest określony, ale metoda nie można rozwiązać, procesor XAML powinien zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="60cf8-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="60cf8-135">Użycie atrybutu XAML `<x:Arguments>string</x:Arguments>` jest technicznie możliwa.</span><span class="sxs-lookup"><span data-stu-id="60cf8-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="60cf8-136">Zapewnia to nie możliwości poza co można zrobić w przeciwnym razie za pomocą inicjowania tekst i wpisać konwerterów i przy użyciu tej składni nie jest zamiar projektu funkcji metoda fabryki XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="60cf8-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="60cf8-137">Przykłady</span><span class="sxs-lookup"><span data-stu-id="60cf8-137">Examples</span></span>  
 <span data-ttu-id="60cf8-138">W poniższym przykładzie pokazano bez domyślnego konstruktora podpisu, a następnie użycie XAML `x:Arguments` , uzyskuje dostęp ten podpis.</span><span class="sxs-lookup"><span data-stu-id="60cf8-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
 <span data-ttu-id="60cf8-139">W poniższym przykładzie pokazano podpis metody fabryki docelowego, a następnie użycie XAML `x:Arguments` , uzyskuje dostęp ten podpis.</span><span class="sxs-lookup"><span data-stu-id="60cf8-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60cf8-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60cf8-140">See also</span></span>
- [<span data-ttu-id="60cf8-141">Definiowanie typów niestandardowych do użytku z usługami .NET Framework XAML</span><span class="sxs-lookup"><span data-stu-id="60cf8-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [<span data-ttu-id="60cf8-142">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="60cf8-142">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
