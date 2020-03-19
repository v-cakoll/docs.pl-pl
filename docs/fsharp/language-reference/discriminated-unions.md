---
title: Sumy rozłączne
description: Dowiedz się, jak używać związków dyskryminowanych f#.
ms.date: 05/16/2016
ms.openlocfilehash: 539e2843c0bbc8c5ac9c0597ffc5443f8cd127f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400219"
---
# <a name="discriminated-unions"></a><span data-ttu-id="15a04-103">Sumy rozłączne</span><span class="sxs-lookup"><span data-stu-id="15a04-103">Discriminated Unions</span></span>

<span data-ttu-id="15a04-104">Dyskryminowane związki zapewniają obsługę wartości, które mogą być jednym z wielu nazwanych przypadków, ewentualnie każdy z różnych wartości i typów.</span><span class="sxs-lookup"><span data-stu-id="15a04-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="15a04-105">Dyskryminowane związki zawodowe są przydatne w przypadku danych heterogenicznych; dane, które mogą mieć szczególne przypadki, w tym ważne i przypadki błędów; danych, które różnią się w zależności od typu; i jako alternatywa dla hierarchii małych obiektów.</span><span class="sxs-lookup"><span data-stu-id="15a04-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="15a04-106">Ponadto rekurencyjne związki dyskryminowane są używane do reprezentowania struktur danych drzewa.</span><span class="sxs-lookup"><span data-stu-id="15a04-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="15a04-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="15a04-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="15a04-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15a04-108">Remarks</span></span>

<span data-ttu-id="15a04-109">Związki dyskryminowane są podobne do typów związków w innych językach, ale istnieją różnice.</span><span class="sxs-lookup"><span data-stu-id="15a04-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="15a04-110">Podobnie jak w przypadku typu unii w języku C++ lub typu wariantu w języku Visual Basic, dane przechowywane w wartości nie jest ustalona; może to być jedna z kilku różnych opcji.</span><span class="sxs-lookup"><span data-stu-id="15a04-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="15a04-111">W przeciwieństwie do związków zawodowych w tych innych językach, jednak każda z możliwych opcji otrzymuje *identyfikator sprawy*.</span><span class="sxs-lookup"><span data-stu-id="15a04-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="15a04-112">Identyfikatory przypadków są nazwy dla różnych możliwych typów wartości, które mogą być obiekty tego typu; wartości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="15a04-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="15a04-113">Jeśli wartości nie są obecne, sprawa jest równoważna przypadku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="15a04-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="15a04-114">Jeśli wartości są obecne, każda wartość może być pojedynczą wartością określonego typu lub krotką, która agreguje wiele pól tego samego lub różnych typów.</span><span class="sxs-lookup"><span data-stu-id="15a04-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="15a04-115">Można nadać poszczególne pola nazwę, ale nazwa jest opcjonalna, nawet jeśli inne pola w tym samym przypadku są nazwane.</span><span class="sxs-lookup"><span data-stu-id="15a04-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="15a04-116">Dostępność dla związków dyskryminowanych `public`domyślnie .</span><span class="sxs-lookup"><span data-stu-id="15a04-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="15a04-117">Rozważmy na przykład następującą deklarację typu Shape.</span><span class="sxs-lookup"><span data-stu-id="15a04-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="15a04-118">Poprzedni kod deklaruje rozróżniony kształt unii, który może mieć wartości dowolnego z trzech przypadków: Prostokąt, Okrąg i Pryzmat.</span><span class="sxs-lookup"><span data-stu-id="15a04-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="15a04-119">Każdy przypadek ma inny zestaw pól.</span><span class="sxs-lookup"><span data-stu-id="15a04-119">Each case has a different set of fields.</span></span> <span data-ttu-id="15a04-120">Prostokąt ma dwa pola o nazwie, `float`oba typu , które mają szerokość i długość nazw.</span><span class="sxs-lookup"><span data-stu-id="15a04-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="15a04-121">Przypadek Circle ma tylko jedno nazwane pole, promień.</span><span class="sxs-lookup"><span data-stu-id="15a04-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="15a04-122">Przypadek Pryzmat ma trzy pola, z których dwa (szerokość i wysokość) są nazywane polami.</span><span class="sxs-lookup"><span data-stu-id="15a04-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="15a04-123">Pola bez nazwy są nazywane polami anonimowymi.</span><span class="sxs-lookup"><span data-stu-id="15a04-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="15a04-124">Obiekty można konstruować, podając wartości dla nazwanych i anonimowych pól zgodnie z poniższymi przykładami.</span><span class="sxs-lookup"><span data-stu-id="15a04-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="15a04-125">Ten kod pokazuje, że można użyć nazwanych pól w inicjalizacji lub można polegać na kolejności pól w deklaracji i po prostu podać wartości dla każdego pola po kolei.</span><span class="sxs-lookup"><span data-stu-id="15a04-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="15a04-126">Wywołanie konstruktora `rect` w poprzednim kodzie używa nazwanych `circ` pól, ale wywołanie konstruktora używa kolejności.</span><span class="sxs-lookup"><span data-stu-id="15a04-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="15a04-127">Można mieszać uporządkowane pola i pola nazwane, tak `prism`jak w przypadku konstrukcji .</span><span class="sxs-lookup"><span data-stu-id="15a04-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="15a04-128">Typ `option` jest prostą, dyskryminowaną uniią w bibliotece podstawowej F#.</span><span class="sxs-lookup"><span data-stu-id="15a04-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="15a04-129">Typ `option` jest zadeklarowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="15a04-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="15a04-130">Poprzedni kod określa, że `Option` typ jest związkiem dyskryminowanym, `None`który ma dwa przypadki i `Some` .</span><span class="sxs-lookup"><span data-stu-id="15a04-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="15a04-131">Sprawa `Some` ma skojarzoną wartość, która składa się z jednego `'a`pola anonimowego, którego typ jest reprezentowany przez parametr type .</span><span class="sxs-lookup"><span data-stu-id="15a04-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="15a04-132">Sprawa `None` nie ma skojarzonej wartości.</span><span class="sxs-lookup"><span data-stu-id="15a04-132">The `None` case has no associated value.</span></span> <span data-ttu-id="15a04-133">W `option` związku z tym typ określa typ ogólny, który ma wartość pewnego typu lub nie ma wartości.</span><span class="sxs-lookup"><span data-stu-id="15a04-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="15a04-134">Typ `Option` ma również alias typu `option`małych liter, który jest powszechnie używany.</span><span class="sxs-lookup"><span data-stu-id="15a04-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="15a04-135">Identyfikatory przypadków mogą być używane jako konstruktory dla typu unii dyskryminowanych.</span><span class="sxs-lookup"><span data-stu-id="15a04-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="15a04-136">Na przykład następujący kod jest używany do `option` tworzenia wartości typu.</span><span class="sxs-lookup"><span data-stu-id="15a04-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="15a04-137">Identyfikatory przypadków są również używane w wyrażeniach dopasowania wzorca.</span><span class="sxs-lookup"><span data-stu-id="15a04-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="15a04-138">W wyrażeniu dopasowania wzorca identyfikatory są dostarczane dla wartości skojarzonych z poszczególnych przypadków.</span><span class="sxs-lookup"><span data-stu-id="15a04-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="15a04-139">Na przykład w poniższym `x` kodzie jest identyfikator biorąc pod `Some` uwagę wartość, która jest skojarzona ze sprawą `option` typu.</span><span class="sxs-lookup"><span data-stu-id="15a04-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="15a04-140">W wyrażeniach dopasowania wzorca można użyć nazwanych pól do określania dopasowanych dopasowań unii dyskryminowanych.</span><span class="sxs-lookup"><span data-stu-id="15a04-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="15a04-141">Dla typu Kształt, który został zadeklarowany wcześniej, można użyć nazwanych pól, jak pokazano w poniższym kodzie, aby wyodrębnić wartości pól.</span><span class="sxs-lookup"><span data-stu-id="15a04-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeWidth shape =
    match shape with
    | Rectangle(width = w) -> w
    | Circle(radius = r) -> 2. * r
    | Prism(width = w) -> w
```

<span data-ttu-id="15a04-142">Zwykle identyfikatory sprawy mogą być używane bez kwalifikowania ich nazwą związku.</span><span class="sxs-lookup"><span data-stu-id="15a04-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="15a04-143">Jeśli chcesz, aby nazwa była zawsze kwalifikowana przy użyciu nazwy unii, można zastosować [requirequalifiedaccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) atrybut do definicji typu unii.</span><span class="sxs-lookup"><span data-stu-id="15a04-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="15a04-144">Rozpakowywanie dyskryminowanych związków</span><span class="sxs-lookup"><span data-stu-id="15a04-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="15a04-145">W F# Dyskryminowane związki są często używane w modelowaniu domeny do zawijania pojedynczego typu.</span><span class="sxs-lookup"><span data-stu-id="15a04-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="15a04-146">Łatwo jest wyodrębnić wartość podstawową poprzez dopasowanie wzorca, jak również.</span><span class="sxs-lookup"><span data-stu-id="15a04-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="15a04-147">Nie musisz używać wyrażenia dopasowania dla pojedynczego przypadku:</span><span class="sxs-lookup"><span data-stu-id="15a04-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseIdentifier] [values]) = [UnionValue]
```

<span data-ttu-id="15a04-148">Poniższy przykład pokazuje to:</span><span class="sxs-lookup"><span data-stu-id="15a04-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="15a04-149">Dopasowywanie wzorców jest również dozwolone bezpośrednio w parametrach funkcji, dzięki czemu można rozpakować tam pojedynczy przypadek:</span><span class="sxs-lookup"><span data-stu-id="15a04-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="15a04-150">Związki dyskryminowane struct</span><span class="sxs-lookup"><span data-stu-id="15a04-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="15a04-151">Związki dyskryminowane można również reprezentować jako struktury.</span><span class="sxs-lookup"><span data-stu-id="15a04-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="15a04-152">Odbywa się to `[<Struct>]` za pomocą atrybutu.</span><span class="sxs-lookup"><span data-stu-id="15a04-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="15a04-153">Ponieważ są to typy wartości, a nie typy odwołań, istnieją dodatkowe zagadnienia w porównaniu z odwołaniami dyskryminowane związki:</span><span class="sxs-lookup"><span data-stu-id="15a04-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="15a04-154">Są one kopiowane jako typy wartości i mają semantyki typu wartości.</span><span class="sxs-lookup"><span data-stu-id="15a04-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="15a04-155">Nie można użyć definicji typu cyklicznego z wieloliterową strukturą Unii dyskryminowanej.</span><span class="sxs-lookup"><span data-stu-id="15a04-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="15a04-156">Należy podać unikatowe nazwy przypadków dla wieloliterowej struktury Unii dyskryminowanej.</span><span class="sxs-lookup"><span data-stu-id="15a04-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="15a04-157">Używanie związków dyskryminowanych zamiast hierarchii obiektów</span><span class="sxs-lookup"><span data-stu-id="15a04-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="15a04-158">Często można użyć unii dyskryminowanej jako prostszą alternatywę dla hierarchii małych obiektów.</span><span class="sxs-lookup"><span data-stu-id="15a04-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="15a04-159">Na przykład następujące unii dyskryminowanej może służyć `Shape` zamiast klasy podstawowej, która ma pochodne typy dla okręgu, kwadratu i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="15a04-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="15a04-160">Zamiast metody wirtualnej do obliczania obszaru lub obwodu, jak można użyć w implementacji obiektowej, można użyć dopasowania wzorca do gałęzi do odpowiednich formuł do obliczenia tych ilości.</span><span class="sxs-lookup"><span data-stu-id="15a04-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="15a04-161">W poniższym przykładzie różne formuły są używane do obliczania obszaru, w zależności od kształtu.</span><span class="sxs-lookup"><span data-stu-id="15a04-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="15a04-162">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="15a04-162">The output is as follows:</span></span>

```console
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="15a04-163">Używanie zniechęconych związków dla struktur danych drzewa</span><span class="sxs-lookup"><span data-stu-id="15a04-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="15a04-164">Dyskryminowane związki zawodowe mogą być rekurencyjne, co oznacza, że sam związek może zostać włączony do rodzaju jednego lub więcej przypadków.</span><span class="sxs-lookup"><span data-stu-id="15a04-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="15a04-165">Rekurencyjne związki dyskryminowane mogą służyć do tworzenia struktur drzewa, które są używane do modelowania wyrażeń w językach programowania.</span><span class="sxs-lookup"><span data-stu-id="15a04-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="15a04-166">W poniższym kodzie rekurencyjne jednych z unii dyskryminaciajest używany do tworzenia struktury danych drzewa binarnego.</span><span class="sxs-lookup"><span data-stu-id="15a04-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="15a04-167">Unia składa się z `Node`dwóch przypadków, , który jest węzłem z wartością `Tip`całkowitą i lewym i prawym poddrzewa, i , który kończy drzewo.</span><span class="sxs-lookup"><span data-stu-id="15a04-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="15a04-168">W poprzednim kodzie `resultSumTree` ma wartość 10.</span><span class="sxs-lookup"><span data-stu-id="15a04-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="15a04-169">Na poniższej ilustracji `myTree`przedstawiono strukturę drzewa dla .</span><span class="sxs-lookup"><span data-stu-id="15a04-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Diagram, który pokazuje strukturę drzewa dla myTree.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="15a04-171">Dyskryminowane związki działają dobrze, jeśli węzły w drzewie są heterogeniczne.</span><span class="sxs-lookup"><span data-stu-id="15a04-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="15a04-172">W poniższym kodzie `Expression` typ reprezentuje abstrakcyjne drzewo składni wyrażenia w prostym języku programowania, który obsługuje dodawanie i mnożenie liczb i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="15a04-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="15a04-173">Niektóre sprawy związkowe nie są rekurencyjne`Number`i reprezentują liczby`Variable`( ) lub zmienne ( ).</span><span class="sxs-lookup"><span data-stu-id="15a04-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="15a04-174">Inne przypadki są rekurencyjne i`Add` reprezentują `Multiply`operacje ( i ), gdzie operandy są również wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="15a04-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="15a04-175">Funkcja `Evaluate` używa wyrażenia dopasowania do rekurencyjnego przetwarzania drzewa składni.</span><span class="sxs-lookup"><span data-stu-id="15a04-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="15a04-176">Po wykonaniu tego kodu wartość `result` to 5.</span><span class="sxs-lookup"><span data-stu-id="15a04-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="15a04-177">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="15a04-177">Members</span></span>

<span data-ttu-id="15a04-178">Możliwe jest zdefiniowanie członków na dyskryminowanych związkach.</span><span class="sxs-lookup"><span data-stu-id="15a04-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="15a04-179">W poniższym przykładzie pokazano, jak zdefiniować właściwość i zaimplementować interfejs:</span><span class="sxs-lookup"><span data-stu-id="15a04-179">The following example shows how to define a property and implement an interface:</span></span>

```fsharp
open System

type IPrintable =
    abstract Print: unit -> unit

type Shape =
    | Circle of float
    | EquilateralTriangle of float
    | Square of float
    | Rectangle of float * float

    member this.Area =
        match this with
        | Circle r -> 2.0 * Math.PI * r
        | EquilateralTriangle s -> s * s * sqrt 3.0 / 4.0
        | Square s -> s * s
        | Rectangle(l, w) -> l * w

    interface IPrintable with
        member this.Print () =
            match this with
            | Circle r -> printfn "Circle with radius %f" r
            | EquilateralTriangle s -> printfn "Equilateral Triangle of side %f" s
            | Square s -> printfn "Square with side %f" s
            | Rectangle(l, w) -> printfn "Rectangle with length %f and width %f" l w
```

## <a name="common-attributes"></a><span data-ttu-id="15a04-180">Typowe atrybuty</span><span class="sxs-lookup"><span data-stu-id="15a04-180">Common attributes</span></span>

<span data-ttu-id="15a04-181">Następujące atrybuty są powszechnie postrzegane w dyskryminowanych związków:</span><span class="sxs-lookup"><span data-stu-id="15a04-181">The following attributes are commonly seen in discriminated unions:</span></span>

- `[<RequireQualifiedAccess>]`
- `[<NoEquality>]`
- `[<NoComparison>]`
- `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="15a04-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15a04-182">See also</span></span>

- [<span data-ttu-id="15a04-183">Odwołanie do języka F#</span><span class="sxs-lookup"><span data-stu-id="15a04-183">F# Language Reference</span></span>](index.md)
