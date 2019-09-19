---
title: Atrybuty
description: Dowiedz F# się, jak atrybuty umożliwiają stosowanie metadanych do konstrukcji programistycznej.
ms.date: 05/16/2016
ms.openlocfilehash: 08d50f7f57b6c0a81221e8f635f77f67750d0ff9
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082943"
---
# <a name="attributes"></a><span data-ttu-id="c73f7-103">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c73f7-103">Attributes</span></span>

<span data-ttu-id="c73f7-104">Atrybuty umożliwiają stosowanie metadanych do konstrukcji programistycznej.</span><span class="sxs-lookup"><span data-stu-id="c73f7-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="c73f7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c73f7-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="c73f7-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c73f7-106">Remarks</span></span>

<span data-ttu-id="c73f7-107">W poprzedniej składni *obiekt docelowy* jest opcjonalny i, jeśli jest obecny, określa rodzaj jednostki programu, do której odnosi się ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="c73f7-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="c73f7-108">W tabeli, która pojawia się w dalszej części tego dokumentu, są wyświetlane prawidłowe wartości dla *elementu docelowego* .</span><span class="sxs-lookup"><span data-stu-id="c73f7-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="c73f7-109">*Atrybut-name* odnosi się do nazwy (możliwej do zakwalifikowania z przestrzenią nazw) prawidłowego typu atrybutu, z `Attribute` lub bez sufiksu, który jest zazwyczaj używany w nazwach typu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="c73f7-110">Na przykład typ `ObsoleteAttribute` może być skrócony do tylko `Obsolete` w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="c73f7-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="c73f7-111">*Argumenty* są argumentami konstruktora dla typu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="c73f7-112">Jeśli atrybut ma konstruktora domyślnego, lista argumentów i nawiasy mogą być pominięte.</span><span class="sxs-lookup"><span data-stu-id="c73f7-112">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="c73f7-113">Atrybuty obsługują zarówno argumenty pozycyjne, jak i nazwane argumenty.</span><span class="sxs-lookup"><span data-stu-id="c73f7-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="c73f7-114">*Argumenty pozycyjne* są argumentami, które są używane w kolejności, w jakiej są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="c73f7-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="c73f7-115">Nazwanych argumentów można użyć, jeśli atrybut ma właściwości publiczne.</span><span class="sxs-lookup"><span data-stu-id="c73f7-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="c73f7-116">Można je ustawić przy użyciu następującej składni na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="c73f7-116">You can set these by using the following syntax in the argument list.</span></span>

```fsharp
property-name = property-value
```

<span data-ttu-id="c73f7-117">Takie inicjalizacje właściwości mogą być w dowolnej kolejności, ale muszą być zgodne z dowolnymi argumentami pozycyjnymi.</span><span class="sxs-lookup"><span data-stu-id="c73f7-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="c73f7-118">Poniżej znajduje się przykład atrybutu, który używa argumentów pozycyjnych i inicjalizacji właściwości.</span><span class="sxs-lookup"><span data-stu-id="c73f7-118">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="c73f7-119">W tym przykładzie atrybut jest `DllImportAttribute`używany w skróconej postaci.</span><span class="sxs-lookup"><span data-stu-id="c73f7-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="c73f7-120">Pierwszy argument jest parametrem pozycyjnym, a drugi jest właściwością.</span><span class="sxs-lookup"><span data-stu-id="c73f7-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="c73f7-121">Atrybuty to konstrukcja programistyczna platformy .NET, która umożliwia obiektowi znanemu jako *atrybut* , który ma być skojarzony z typem lub innym elementem programu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="c73f7-122">Element programu, do którego zastosowano atrybut, jest określany jako *element docelowy atrybutu*.</span><span class="sxs-lookup"><span data-stu-id="c73f7-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="c73f7-123">Ten atrybut zwykle zawiera metadane dotyczące jego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c73f7-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="c73f7-124">W tym kontekście metadane mogą zawierać dowolne dane dotyczące typu innego niż jego pola i elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="c73f7-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="c73f7-125">Atrybuty w F# programie można stosować do następujących konstrukcji programistycznych: funkcji, metod, zestawów, modułów, typów (klas, rekordów, struktur, interfejsów, delegatów, wyliczeń, Unii itd.), konstruktorów, właściwości, pól parametry, parametry typu i wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="c73f7-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="c73f7-126">Atrybuty są niedozwolone w `let` powiązaniach wewnątrz klas, wyrażeń lub wyrażeń przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c73f7-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="c73f7-127">Zwykle deklaracja atrybutu pojawia się bezpośrednio przed deklaracją obiektu docelowego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="c73f7-128">Deklaracje wielu atrybutów mogą być używane razem w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="c73f7-128">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="c73f7-129">Można badać atrybuty w czasie wykonywania przy użyciu odbicia platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c73f7-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="c73f7-130">Można zadeklarować wiele atrybutów pojedynczo, jak w poprzednim przykładzie kodu lub można je zadeklarować w jednym zestawie nawiasów, jeśli używasz średnika do oddzielenia poszczególnych atrybutów i konstruktorów, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="c73f7-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="c73f7-131">Zazwyczaj napotkane atrybuty obejmują `Obsolete` atrybut, atrybuty dla zagadnień związanych z bezpieczeństwem, atrybuty obsługi modelu COM, atrybuty, które odnoszą się do własności kodu, oraz atrybuty wskazujące, czy typ może być serializowany.</span><span class="sxs-lookup"><span data-stu-id="c73f7-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="c73f7-132">Poniższy przykład demonstruje użycie `Obsolete` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="c73f7-133">Dla elementów docelowych `assembly` atrybutu i `module`należy zastosować atrybuty do powiązania najwyższego poziomu `do` w zestawie.</span><span class="sxs-lookup"><span data-stu-id="c73f7-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="c73f7-134">Można uwzględnić słowo `assembly` lub `module` w deklaracji atrybutu w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="c73f7-134">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="c73f7-135">Jeśli pominięto element docelowy atrybutu dla atrybutu zastosowanego do `do` powiązania, F# kompilator próbuje określić obiekt docelowy atrybutu, który jest zrozumiały dla tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="c73f7-136">Wiele klas atrybutów ma atrybut typu `System.AttributeUsageAttribute` , który zawiera informacje o możliwych celach obsługiwanych przez ten atrybut.</span><span class="sxs-lookup"><span data-stu-id="c73f7-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="c73f7-137">`System.AttributeUsageAttribute` Jeśli wskazuje, że atrybut obsługuje funkcje jako elementy docelowe, atrybut jest stosowany do głównego punktu wejścia programu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="c73f7-138">`System.AttributeUsageAttribute` Jeśli wskazuje, że atrybut obsługuje zestawy jako elementy docelowe, kompilator Pobiera atrybut, który ma zostać zastosowany do zestawu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="c73f7-139">Większość atrybutów nie ma zastosowania do obu funkcji i zestawów, ale w przypadkach, w których są one wykonywane, atrybut jest stosowany do funkcji Main programu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="c73f7-140">Jeśli obiekt docelowy atrybutu jest jawnie określony, atrybut jest stosowany do określonego celu.</span><span class="sxs-lookup"><span data-stu-id="c73f7-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="c73f7-141">Mimo że zwykle nie trzeba określać obiektu docelowego atrybutu, w poniższej tabeli podano prawidłowe wartości dla *elementu Target* , a także przykłady użycia.</span><span class="sxs-lookup"><span data-stu-id="c73f7-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="c73f7-142">Obiekt docelowy atrybutu</span><span class="sxs-lookup"><span data-stu-id="c73f7-142">Attribute target</span></span></td>
    <th><span data-ttu-id="c73f7-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="c73f7-143">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="c73f7-144">zestaw</span><span class="sxs-lookup"><span data-stu-id="c73f7-144">assembly</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="c73f7-145">return</span><span class="sxs-lookup"><span data-stu-id="c73f7-145">return</span></span></td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="c73f7-146">pole</span><span class="sxs-lookup"><span data-stu-id="c73f7-146">field</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="c73f7-147">property</span><span class="sxs-lookup"><span data-stu-id="c73f7-147">property</span></span></td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="c73f7-148">Param</span><span class="sxs-lookup"><span data-stu-id="c73f7-148">param</span></span></td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="c73f7-149">— typ</span><span class="sxs-lookup"><span data-stu-id="c73f7-149">type</span></span></td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(Sequential)&gt;] 
type MyStruct = 
struct 
x : byte
y : int
end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="c73f7-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c73f7-150">See also</span></span>

- [<span data-ttu-id="c73f7-151">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="c73f7-151">F# Language Reference</span></span>](index.md)
