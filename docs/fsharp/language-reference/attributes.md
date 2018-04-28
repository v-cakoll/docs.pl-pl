---
title: Atrybuty (F#)
description: 'Dowiedz się, jak włączyć metadanych ma być stosowany do konstrukcji programującej przez atrybuty F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: b8efc0cdc14e690bbc5c24456d0b1eaa3d55988e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="attributes"></a><span data-ttu-id="0ad97-103">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0ad97-103">Attributes</span></span>

<span data-ttu-id="0ad97-104">Atrybuty Włącz metadanych ma być stosowany do programowania konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="0ad97-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ad97-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ad97-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="0ad97-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ad97-106">Remarks</span></span>

<span data-ttu-id="0ad97-107">W poprzednich składni *docelowej* jest opcjonalna i, jeśli jest obecny, określa typ jednostki program, którego dotyczy ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="0ad97-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="0ad97-108">Prawidłowymi wartościami dla *docelowej* są wyświetlane w tabeli, która pojawia się w dalszej części tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="0ad97-109">*Nazwa atrybutu* odwołuje się do nazwy (prawdopodobnie kwalifikowany za pomocą przestrzeni nazw) z prawidłowego typu atrybutu, lub bez sufiks `Attribute` zwykle używany w nazwach typu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="0ad97-110">Na przykład typ `ObsoleteAttribute` może zostać skrócony nieco `Obsolete` w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="0ad97-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="0ad97-111">*Argumenty* argumentów konstruktora dla typu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="0ad97-112">Jeśli atrybut ma domyślny konstruktor, można pominąć listy argumentów i nawiasy.</span><span class="sxs-lookup"><span data-stu-id="0ad97-112">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="0ad97-113">Atrybuty obsługują argumenty pozycyjne i nazwanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="0ad97-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="0ad97-114">*Argumenty pozycyjne* są argumenty, które są używane w kolejności ich występowania.</span><span class="sxs-lookup"><span data-stu-id="0ad97-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="0ad97-115">Jeśli ten atrybut ma właściwości publiczne można nazwanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="0ad97-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="0ad97-116">Można ustawić przy użyciu następującej składni w liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="0ad97-116">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="0ad97-117">Takie inicjowania właściwości można w dowolnej kolejności, ale muszą wykonać żadnych argumentów pozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="0ad97-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="0ad97-118">Poniżej przedstawiono przykład atrybut, który używa argumentów pozycyjnych i inicjowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="0ad97-118">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="0ad97-119">W tym przykładzie ten atrybut jest `DllImportAttribute`, w tym miejscu są używane w formie skróconej.</span><span class="sxs-lookup"><span data-stu-id="0ad97-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="0ad97-120">Pierwszy argument jest parametrów pozycyjnych, a drugą jest wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="0ad97-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="0ad97-121">Atrybuty są konstrukcję programowania .NET umożliwia obiektu znanego jako *atrybut* ma zostać skojarzony z typem lub innego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="0ad97-122">Element programu, do którego zastosowano atrybut nosi nazwę *element docelowy atrybutu*.</span><span class="sxs-lookup"><span data-stu-id="0ad97-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="0ad97-123">Ten atrybut zawiera zwykle metadane dotyczące elementem docelowym.</span><span class="sxs-lookup"><span data-stu-id="0ad97-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="0ad97-124">W tym kontekście metadanych można żadnych danych o typie innym niż jego pola i elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="0ad97-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="0ad97-125">Atrybuty w języku F # można zastosować do następujących narzędzi programistycznych: funkcje metod, zestawy, moduły, typów (klas, rekordów, struktury, interfejsy, delegatów, wyliczeń, Unii i tak dalej), konstruktorów, właściwości, pola, parametrów, Parametry typu i wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="0ad97-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="0ad97-126">Atrybuty są niedozwolone w `let` powiązania wewnątrz klasy, wyrażenia lub wyrażeń przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0ad97-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="0ad97-127">Zazwyczaj deklaracji atrybutu pojawia się bezpośrednio przed deklaracją elementu docelowego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="0ad97-128">Wiele deklaracji atrybutu można ze sobą w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="0ad97-128">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="0ad97-129">Atrybuty w czasie wykonywania można badać przy użyciu odbicia .NET.</span><span class="sxs-lookup"><span data-stu-id="0ad97-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="0ad97-130">Można zadeklarować wiele atrybutów indywidualnie, co w poprzednim przykładzie kodu lub mogą zadeklarować ich w jednym zestawie nawiasów Jeśli Użyj średnika do oddzielenia poszczególnych atrybutów i konstruktorów, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="0ad97-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="0ad97-131">Atrybuty najczęściej spotykanych obejmują `Obsolete` atrybutu, atrybuty zagadnienia dotyczące zabezpieczeń, atrybuty do obsługi modelu COM, atrybuty, które odnoszą się do właściciela kodu i atrybuty wskazującą, czy można zserializować typu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="0ad97-132">W poniższym przykładzie pokazano użycie `Obsolete` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="0ad97-133">Dla celów atrybutu `assembly` i `module`, zastosować atrybutów do najwyższego poziomu `do` powiązania w tym zestawem.</span><span class="sxs-lookup"><span data-stu-id="0ad97-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="0ad97-134">Może zawierać słowo `assembly` lub `module` w deklaracji atrybutu w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="0ad97-134">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="0ad97-135">Jeśli pominięto element docelowy atrybutu dla atrybutu dotyczą `do` powiązanie, kompilator języka F # spróbuje określić element docelowy atrybutu, który ma sens dla tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="0ad97-136">Wiele klas atrybut ma atrybut typu `System.AttributeUsageAttribute` zawierającą informacje o możliwych elementy docelowe obsługiwane dla tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="0ad97-137">Jeśli `System.AttributeUsageAttribute` wskazuje, czy ten atrybut obsługuje funkcje jako miejsca docelowe, ten atrybut jest przełączany do zastosowania do główny punkt wejścia programu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="0ad97-138">Jeśli `System.AttributeUsageAttribute` wskazuje, że ten atrybut obsługuje zestawy jako miejsca docelowe, kompilator ma atrybut do zastosowania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="0ad97-139">Większość atrybutów nie dotyczą zarówno funkcje i zestawy, ale w przypadkach, gdy robią, ten atrybut pochodzi do zastosowania do głównych funkcji programu.</span><span class="sxs-lookup"><span data-stu-id="0ad97-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="0ad97-140">Jeśli element docelowy atrybutu jest jawnie określony, atrybut jest stosowany do określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0ad97-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="0ad97-141">Chociaż zazwyczaj zbędna, nie można określić atrybutu target jawnie, prawidłowe wartości *docelowej* w atrybucie przedstawiono w poniższej tabeli, wraz z przykładem użycia.</span><span class="sxs-lookup"><span data-stu-id="0ad97-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="0ad97-142">Element docelowy atrybutu</span><span class="sxs-lookup"><span data-stu-id="0ad97-142">Attribute target</span></span></td>
    <th><span data-ttu-id="0ad97-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ad97-143">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="0ad97-144">zestaw</span><span class="sxs-lookup"><span data-stu-id="0ad97-144">assembly</span></span></td>
    <td><span data-ttu-id="0ad97-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="0ad97-145">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="0ad97-146">return</span><span class="sxs-lookup"><span data-stu-id="0ad97-146">return</span></span></td>
    <td><span data-ttu-id="0ad97-147">"let function1 x: [<return: Obsolete>] int = x + 1'</span><span class="sxs-lookup"><span data-stu-id="0ad97-147">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="0ad97-148">pole</span><span class="sxs-lookup"><span data-stu-id="0ad97-148">field</span></span></td>
    <td><span data-ttu-id="0ad97-149">"[<field: DefaultValue>] val mutable x: int"</span><span class="sxs-lookup"><span data-stu-id="0ad97-149">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="0ad97-150">property</span><span class="sxs-lookup"><span data-stu-id="0ad97-150">property</span></span></td>
    <td><span data-ttu-id="0ad97-151">"[<property: Obsolete>] to. MyProperty = x'</span><span class="sxs-lookup"><span data-stu-id="0ad97-151">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="0ad97-152">Param</span><span class="sxs-lookup"><span data-stu-id="0ad97-152">param</span></span></td>
    <td><span data-ttu-id="0ad97-153">"elementu członkowskiego to. MyMethod ([<param: Out>] x: ref<int>) = x: = 10'.</span><span class="sxs-lookup"><span data-stu-id="0ad97-153">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="0ad97-154">— typ</span><span class="sxs-lookup"><span data-stu-id="0ad97-154">type</span></span></td>
    <td><span data-ttu-id="0ad97-155">
        ```
        [<type: StructLayout(Sequential)>] wpisz MyStruct = struct x: byte y: int zakończenia ```
    </span><span class="sxs-lookup"><span data-stu-id="0ad97-155">
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : int end ```
    </span></span></td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="0ad97-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ad97-156">See Also</span></span>

[<span data-ttu-id="0ad97-157">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="0ad97-157">F# Language Reference</span></span>](index.md)
