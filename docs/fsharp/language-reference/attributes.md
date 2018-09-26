---
title: Atrybuty (F#)
description: 'Dowiedz się, jak włączyć metadanych, które mają być stosowane do konstrukcji programowania w F # atrybutów.'
ms.date: 05/16/2016
ms.openlocfilehash: 3e7f1d0ff383e1070b3db72e633f80ea37150548
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216490"
---
# <a name="attributes"></a><span data-ttu-id="4aa7a-103">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4aa7a-103">Attributes</span></span>

<span data-ttu-id="4aa7a-104">Atrybuty Włącz metadanych, które mają być stosowane do konstrukcji programowania.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="4aa7a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4aa7a-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="4aa7a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4aa7a-106">Remarks</span></span>

<span data-ttu-id="4aa7a-107">W poprzedniej składni *docelowej* jest opcjonalny, a jeśli jest obecny, określa typ jednostki program, który dotyczy ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="4aa7a-108">Prawidłowe wartości dla *docelowej* są wyświetlane w tabeli, która pojawia się w dalszej części tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="4aa7a-109">*Nazwa atrybutu* odwołuje się do nazwy (prawdopodobnie kwalifikowany za pomocą przestrzeni nazw) prawidłowego atrybutu typu, z lub bez sufiksu `Attribute` zwykle używany w nazwach typu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="4aa7a-110">Na przykład typ `ObsoleteAttribute` może zostać skrócony tylko `Obsolete` w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="4aa7a-111">*Argumenty* argumentów konstruktora dla typu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="4aa7a-112">Jeśli atrybut ma domyślnego konstruktora, można pominąć listy argumentów i nawiasy.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-112">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="4aa7a-113">Atrybuty obsługują argumenty pozycyjne i nazwane argumenty.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="4aa7a-114">*Argumenty pozycyjne* argumentów, które są używane w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="4aa7a-115">Argumenty nazwane może służyć, jeśli atrybut ma właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="4aa7a-116">Możesz ustawić te elementy przy użyciu następującej składni na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-116">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="4aa7a-117">Takie inicjowania właściwości mogą znajdować się w dowolnej kolejności, ale muszą wykonać żadnych argumentów pozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="4aa7a-118">Poniżej przedstawiono przykład atrybutu, który używa argumentów pozycyjnych i inicjowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-118">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="4aa7a-119">W tym przykładzie atrybut jest `DllImportAttribute`, w tym miejscu są używane w formie skróconej.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="4aa7a-120">Pierwszy argument jest parametr pozycyjne, a drugą jest wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="4aa7a-121">Atrybuty są konstrukcja programowania .NET, która umożliwia obiektu, nazywany *atrybut* ma zostać skojarzony z typem lub innego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="4aa7a-122">Element programu, do którego zastosowano atrybut jest znany jako *element docelowy atrybutu*.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="4aa7a-123">Ten atrybut zawiera zazwyczaj metadane dotyczące jego element docelowy.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="4aa7a-124">W tym kontekście metadanych może być żadnych danych o typie innym niż jego pola i elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="4aa7a-125">Atrybuty w języku F # mogą być stosowane do następujące konstrukcje programowania: funkcje, metody, zestawy, moduły, typami (klasy, rekordy, struktury, interfejsy, delegaty, wyliczenia, Unii i tak dalej), konstruktory, właściwości, pola, parametrów, Wpisz parametry i zwracane wartości.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="4aa7a-126">Atrybuty nie są dozwolone w `let` powiązania wewnątrz klasy, wyrażenia lub wyrażeń przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="4aa7a-127">Zazwyczaj deklaracji atrybutu pojawia się bezpośrednio przed deklaracją elementu docelowego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="4aa7a-128">Wiele deklaracji atrybutu można ze sobą, wykonując następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-128">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="4aa7a-129">Atrybuty można badać w czasie wykonywania przy użyciu odbicia .NET.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="4aa7a-130">Można zadeklarować wiele atrybutów pojedynczo, tak jak w poprzednim przykładzie kodu lub można je zadeklarować w jeden zestaw nawiasów Jeśli Użyj średnika do rozdzielenia poszczególne atrybuty i konstruktory, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="4aa7a-131">Atrybuty najczęściej obejmują `Obsolete` atrybutu, atrybuty, które ze względów bezpieczeństwa atrybuty do obsługi COM, atrybuty, które odnoszą się do własności kodu i atrybutów, wskazującą, czy typ może być serializowany.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="4aa7a-132">W poniższym przykładzie pokazano użycie `Obsolete` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="4aa7a-133">Dla celów atrybut `assembly` i `module`, Zastosuj atrybuty do najwyższego poziomu `do` powiązanie w swoim zestawie.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="4aa7a-134">Może zawierać słowa `assembly` lub `module` w deklaracji atrybutu w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-134">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="4aa7a-135">Jeżeli pominięto element docelowy atrybutu dla atrybutu, dotyczy `do` powiązania, kompilator F # próbuje określić element docelowy atrybutu, który ma sens dla tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="4aa7a-136">Wiele klas atrybutów ma atrybut typu `System.AttributeUsageAttribute` zawierającej informacje o możliwych elementów docelowych obsługiwane dla tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="4aa7a-137">Jeśli `System.AttributeUsageAttribute` wskazuje, że ten atrybut obsługuje funkcje jako elementy docelowe, ten atrybut pochodzi dotyczą główny punkt wejścia programu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="4aa7a-138">Jeśli `System.AttributeUsageAttribute` wskazuje, że ten atrybut obsługuje zestawy jako elementy docelowe, kompilator przyjmuje atrybutu do zastosowania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="4aa7a-139">Większość atrybutów nie dotyczą zarówno funkcje, jak i zestawy, ale w przypadkach, gdy robią, ten atrybut jest zajęta do zastosowania do funkcji main tego programu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="4aa7a-140">Jeśli element docelowy atrybutu jest jawnie określona, jest stosowany do określonego celu.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="4aa7a-141">Mimo że nie zwykle należy określić atrybut docelowy jawnie, prawidłowe wartości dla *docelowej* w atrybucie są wyświetlane w poniższej tabeli, a także przykłady użycia.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="4aa7a-142">Element docelowy atrybutu</span><span class="sxs-lookup"><span data-stu-id="4aa7a-142">Attribute target</span></span></td>
    <th><span data-ttu-id="4aa7a-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="4aa7a-143">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4aa7a-144">zestaw</span><span class="sxs-lookup"><span data-stu-id="4aa7a-144">assembly</span></span></td>
    <td><span data-ttu-id="4aa7a-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="4aa7a-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4aa7a-146">return</span><span class="sxs-lookup"><span data-stu-id="4aa7a-146">return</span></span></td>
    <td><span data-ttu-id="4aa7a-147">"let function1 x: [<return: Obsolete>] int = x + 1"</span><span class="sxs-lookup"><span data-stu-id="4aa7a-147">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4aa7a-148">pole</span><span class="sxs-lookup"><span data-stu-id="4aa7a-148">field</span></span></td>
    <td><span data-ttu-id="4aa7a-149">"[<field: DefaultValue>] val mutable x: int"</span><span class="sxs-lookup"><span data-stu-id="4aa7a-149">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4aa7a-150">property</span><span class="sxs-lookup"><span data-stu-id="4aa7a-150">property</span></span></td>
    <td><span data-ttu-id="4aa7a-151">"[<property: Obsolete>] to. MyProperty = x "</span><span class="sxs-lookup"><span data-stu-id="4aa7a-151">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4aa7a-152">param</span><span class="sxs-lookup"><span data-stu-id="4aa7a-152">param</span></span></td>
    <td><span data-ttu-id="4aa7a-153">"element członkowski to. MyMethod ([<param: Out>] x: ref<int>) = x: = 10'.</span><span class="sxs-lookup"><span data-stu-id="4aa7a-153">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="4aa7a-154">— typ</span><span class="sxs-lookup"><span data-stu-id="4aa7a-154">type</span></span></td>
    <td><span data-ttu-id="4aa7a-155">
        ```
        [<type: StructLayout(Sequential)>] wpisz MyStruct = struktury x: byte y: koniec int ```
    </span><span class="sxs-lookup"><span data-stu-id="4aa7a-155">
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : int end ```
    </span></span></td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="4aa7a-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4aa7a-156">See also</span></span>

- [<span data-ttu-id="4aa7a-157">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="4aa7a-157">F# Language Reference</span></span>](index.md)
