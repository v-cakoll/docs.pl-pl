---
title: Atrybuty (F#)
description: 'Dowiedz się, jak włączyć metadanych ma być stosowany do konstrukcji programującej przez atrybuty F #.'
keywords: 'Visual f #, f #, funkcjonalności programowania'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 95c001e6-3708-4d04-a850-d855f78eb51e
ms.openlocfilehash: 88098e51d19a86f501c35abe3408524378f147b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="attributes"></a><span data-ttu-id="96661-104">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="96661-104">Attributes</span></span>

<span data-ttu-id="96661-105">Atrybuty Włącz metadanych ma być stosowany do programowania konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="96661-105">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="96661-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="96661-106">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="96661-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96661-107">Remarks</span></span>

<span data-ttu-id="96661-108">W poprzednich składni *docelowej* jest opcjonalna i, jeśli jest obecny, określa typ jednostki program, którego dotyczy ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="96661-108">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="96661-109">Prawidłowymi wartościami dla *docelowej* są wyświetlane w tabeli, która pojawia się w dalszej części tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="96661-109">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="96661-110">*Nazwa atrybutu* odwołuje się do nazwy (prawdopodobnie kwalifikowany za pomocą przestrzeni nazw) z prawidłowego typu atrybutu, lub bez sufiks `Attribute` zwykle używany w nazwach typu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="96661-110">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="96661-111">Na przykład typ `ObsoleteAttribute` może zostać skrócony nieco `Obsolete` w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="96661-111">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="96661-112">*Argumenty* argumentów konstruktora dla typu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="96661-112">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="96661-113">Jeśli atrybut ma domyślny konstruktor, można pominąć listy argumentów i nawiasy.</span><span class="sxs-lookup"><span data-stu-id="96661-113">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="96661-114">Atrybuty obsługują argumenty pozycyjne i nazwanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="96661-114">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="96661-115">*Argumenty pozycyjne* są argumenty, które są używane w kolejności ich występowania.</span><span class="sxs-lookup"><span data-stu-id="96661-115">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="96661-116">Jeśli ten atrybut ma właściwości publiczne można nazwanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="96661-116">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="96661-117">Można ustawić przy użyciu następującej składni w liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="96661-117">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="96661-118">Takie inicjowania właściwości można w dowolnej kolejności, ale muszą wykonać żadnych argumentów pozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="96661-118">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="96661-119">Poniżej przedstawiono przykład atrybut, który używa argumentów pozycyjnych i inicjowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="96661-119">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="96661-120">W tym przykładzie ten atrybut jest `DllImportAttribute`, w tym miejscu są używane w formie skróconej.</span><span class="sxs-lookup"><span data-stu-id="96661-120">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="96661-121">Pierwszy argument jest parametrów pozycyjnych, a drugą jest wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="96661-121">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="96661-122">Atrybuty są konstrukcję programowania .NET umożliwia obiektu znanego jako *atrybut* ma zostać skojarzony z typem lub innego elementu programu.</span><span class="sxs-lookup"><span data-stu-id="96661-122">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="96661-123">Element programu, do którego zastosowano atrybut nosi nazwę *element docelowy atrybutu*.</span><span class="sxs-lookup"><span data-stu-id="96661-123">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="96661-124">Ten atrybut zawiera zwykle metadane dotyczące elementem docelowym.</span><span class="sxs-lookup"><span data-stu-id="96661-124">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="96661-125">W tym kontekście metadanych można żadnych danych o typie innym niż jego pola i elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="96661-125">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="96661-126">Atrybuty w języku F # można zastosować do następujących narzędzi programistycznych: funkcje metod, zestawy, moduły, typów (klas, rekordów, struktury, interfejsy, delegatów, wyliczeń, Unii i tak dalej), konstruktorów, właściwości, pola, parametrów, Parametry typu i wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="96661-126">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="96661-127">Atrybuty są niedozwolone w `let` powiązania wewnątrz klasy, wyrażenia lub wyrażeń przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96661-127">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="96661-128">Zazwyczaj deklaracji atrybutu pojawia się bezpośrednio przed deklaracją elementu docelowego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="96661-128">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="96661-129">Wiele deklaracji atrybutu można ze sobą w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="96661-129">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="96661-130">Atrybuty w czasie wykonywania można badać przy użyciu odbicia .NET.</span><span class="sxs-lookup"><span data-stu-id="96661-130">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="96661-131">Można zadeklarować wiele atrybutów indywidualnie, co w poprzednim przykładzie kodu lub mogą zadeklarować ich w jednym zestawie nawiasów Jeśli Użyj średnika do oddzielenia poszczególnych atrybutów i konstruktorów, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="96661-131">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="96661-132">Atrybuty najczęściej spotykanych obejmują `Obsolete` atrybutu, atrybuty zagadnienia dotyczące zabezpieczeń, atrybuty do obsługi modelu COM, atrybuty, które odnoszą się do właściciela kodu i atrybuty wskazującą, czy można zserializować typu.</span><span class="sxs-lookup"><span data-stu-id="96661-132">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="96661-133">W poniższym przykładzie pokazano użycie `Obsolete` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="96661-133">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="96661-134">Dla celów atrybutu `assembly` i `module`, zastosować atrybutów do najwyższego poziomu `do` powiązania w tym zestawem.</span><span class="sxs-lookup"><span data-stu-id="96661-134">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="96661-135">Może zawierać słowo `assembly` lub `module` w deklaracji atrybutu w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="96661-135">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="96661-136">Jeśli pominięto element docelowy atrybutu dla atrybutu dotyczą `do` powiązanie, kompilator języka F # spróbuje określić element docelowy atrybutu, który ma sens dla tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="96661-136">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="96661-137">Wiele klas atrybut ma atrybut typu `System.AttributeUsageAttribute` zawierającą informacje o możliwych elementy docelowe obsługiwane dla tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="96661-137">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="96661-138">Jeśli `System.AttributeUsageAttribute` wskazuje, czy ten atrybut obsługuje funkcje jako miejsca docelowe, ten atrybut jest przełączany do zastosowania do główny punkt wejścia programu.</span><span class="sxs-lookup"><span data-stu-id="96661-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="96661-139">Jeśli `System.AttributeUsageAttribute` wskazuje, że ten atrybut obsługuje zestawy jako miejsca docelowe, kompilator ma atrybut do zastosowania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="96661-139">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="96661-140">Większość atrybutów nie dotyczą zarówno funkcje i zestawy, ale w przypadkach, gdy robią, ten atrybut pochodzi do zastosowania do głównych funkcji programu.</span><span class="sxs-lookup"><span data-stu-id="96661-140">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="96661-141">Jeśli element docelowy atrybutu jest jawnie określony, atrybut jest stosowany do określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="96661-141">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="96661-142">Chociaż zazwyczaj zbędna, nie można określić atrybutu target jawnie, prawidłowe wartości *docelowej* w atrybucie przedstawiono w poniższej tabeli, wraz z przykładem użycia.</span><span class="sxs-lookup"><span data-stu-id="96661-142">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="96661-143">Element docelowy atrybutu</span><span class="sxs-lookup"><span data-stu-id="96661-143">Attribute target</span></span></td>
    <th><span data-ttu-id="96661-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="96661-144">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="96661-145">zestaw</span><span class="sxs-lookup"><span data-stu-id="96661-145">assembly</span></span></td>
    <td><span data-ttu-id="96661-146">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="96661-146">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="96661-147">return</span><span class="sxs-lookup"><span data-stu-id="96661-147">return</span></span></td>
    <td><span data-ttu-id="96661-148">"let function1 x: [<return: Obsolete>] int = x + 1'</span><span class="sxs-lookup"><span data-stu-id="96661-148">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="96661-149">pole</span><span class="sxs-lookup"><span data-stu-id="96661-149">field</span></span></td>
    <td><span data-ttu-id="96661-150">"[<field: DefaultValue>] val mutable x: int"</span><span class="sxs-lookup"><span data-stu-id="96661-150">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="96661-151">property</span><span class="sxs-lookup"><span data-stu-id="96661-151">property</span></span></td>
    <td><span data-ttu-id="96661-152">"[<property: Obsolete>] to. MyProperty = x'</span><span class="sxs-lookup"><span data-stu-id="96661-152">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="96661-153">Param</span><span class="sxs-lookup"><span data-stu-id="96661-153">param</span></span></td>
    <td><span data-ttu-id="96661-154">"elementu członkowskiego to. MyMethod ([<param: Out>] x: ref<int>) = x: = 10'.</span><span class="sxs-lookup"><span data-stu-id="96661-154">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="96661-155">— typ</span><span class="sxs-lookup"><span data-stu-id="96661-155">type</span></span></td>
    <td><span data-ttu-id="96661-156">
        ```
        [<type: StructLayout(Sequential)>] wpisz MyStruct = struct x: byte y: int zakończenia```
    </span><span class="sxs-lookup"><span data-stu-id="96661-156">
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : int end ```
    </span></span></td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="96661-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96661-157">See Also</span></span>

[<span data-ttu-id="96661-158">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="96661-158">F# Language Reference</span></span>](index.md)
