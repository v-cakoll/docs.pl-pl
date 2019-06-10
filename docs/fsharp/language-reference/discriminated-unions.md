---
title: Sumy rozłączne
description: Dowiedz się, jak używać F# związków wyróżniających.
ms.date: 05/16/2016
ms.openlocfilehash: a3958a9ffb021c0c46c24216f17a1e7ee5605dd3
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816247"
---
# <a name="discriminated-unions"></a><span data-ttu-id="92dc3-103">Sumy rozłączne</span><span class="sxs-lookup"><span data-stu-id="92dc3-103">Discriminated Unions</span></span>

<span data-ttu-id="92dc3-104">Połączenia rozróżniane zapewniają obsługę wartości, które mogą być jednym z wielu przypadków nazwanych, prawdopodobnie każdy z różnych wartości i typów.</span><span class="sxs-lookup"><span data-stu-id="92dc3-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="92dc3-105">Połączenia rozróżniane są przydatne w przypadku heterogenicznych danych; dane, które mogą mieć specjalne przypadki, włączając przypadku prawidłowe i błędy; dane, które różni się w typie z jednego wystąpienia i jako alternatywa dla małych obiektów hierarchii.</span><span class="sxs-lookup"><span data-stu-id="92dc3-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="92dc3-106">Ponadto rekursywne sumy rozłączne są używane do reprezentowania struktur drzew danych.</span><span class="sxs-lookup"><span data-stu-id="92dc3-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="92dc3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="92dc3-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]

    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="92dc3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92dc3-108">Remarks</span></span>

<span data-ttu-id="92dc3-109">Połączenia rozróżniane są podobne do typów połączeń w innych językach, ale istnieją różnice.</span><span class="sxs-lookup"><span data-stu-id="92dc3-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="92dc3-110">Jako typ union w języku C++ lub typ wariantu w języku Visual Basic danych przechowywanych w wartości nie zostanie usunięty; może być jednym z kilku opcji distinct.</span><span class="sxs-lookup"><span data-stu-id="92dc3-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="92dc3-111">W przeciwieństwie do złożeń w tych innych językach, jednak każda z możliwych opcji otrzymuje *identyfikator przypadku*.</span><span class="sxs-lookup"><span data-stu-id="92dc3-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="92dc3-112">Identyfikatory przypadków to nazwy dla różnych możliwych typów wartości, które mogą być obiekty tego typu; wartości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="92dc3-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="92dc3-113">Jeśli wartości nie są obecne, wielkość liter jest równoważna do wielkości liter w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="92dc3-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="92dc3-114">Jeśli wartości są obecne, każda wartością może być jedną wartością z określonego typu lub spójną kolekcją, która agreguje wiele pól tych samych lub różnych typów.</span><span class="sxs-lookup"><span data-stu-id="92dc3-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="92dc3-115">Poszczególnym polom można nadać nazwę, ale nazwa jest opcjonalna, nawet wtedy, gdy inne pola, w tym samym przypadku są nazwane.</span><span class="sxs-lookup"><span data-stu-id="92dc3-115">You can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="92dc3-116">Wartością domyślną jest ułatwień dostępu dla sum rozłącznych `public`.</span><span class="sxs-lookup"><span data-stu-id="92dc3-116">Accessibility for discriminated unions defaults to `public`.</span></span>

<span data-ttu-id="92dc3-117">Na przykład rozważmy następującą deklarację typu kształt.</span><span class="sxs-lookup"><span data-stu-id="92dc3-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="92dc3-118">Powyższy kod deklaruje kształt złożenia dyskryminowanego, który może zawierać wartości dowolnego z trzech przypadków: Prostokąt, okrąg i pryzmat.</span><span class="sxs-lookup"><span data-stu-id="92dc3-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="92dc3-119">Każdy przypadek ma inny zestaw pól.</span><span class="sxs-lookup"><span data-stu-id="92dc3-119">Each case has a different set of fields.</span></span> <span data-ttu-id="92dc3-120">Przypadek prostokąt ma dwa o nazwane pola, oba typu `float`, które mają szerokości i długości nazwy.</span><span class="sxs-lookup"><span data-stu-id="92dc3-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="92dc3-121">Przypadek okręg ma tylko jedno nazwane pole, promień.</span><span class="sxs-lookup"><span data-stu-id="92dc3-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="92dc3-122">Przypadek pryzmat ma trzy pola są dwa (szerokość i wysokość) o nazwie pola.</span><span class="sxs-lookup"><span data-stu-id="92dc3-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="92dc3-123">Bez nazwy pól są określane jako pola anonimowe.</span><span class="sxs-lookup"><span data-stu-id="92dc3-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="92dc3-124">Konstruujesz obiekty podając wartości dla pól nazwanych i anonimowych według poniższych przykładów.</span><span class="sxs-lookup"><span data-stu-id="92dc3-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="92dc3-125">Ten kod wskazuje, że możesz użyć nazwanych pól podczas inicjowania lub możesz polegać na określeniu kolejności pól w deklaracji i po prostu Podaj wartości dla każdego pola, z kolei.</span><span class="sxs-lookup"><span data-stu-id="92dc3-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="92dc3-126">Wywołanie konstruktora dla `rect` w poprzednim kodzie używa pól nazwanych, ale wywołanie konstruktora dla `circ` używa kolejności.</span><span class="sxs-lookup"><span data-stu-id="92dc3-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="92dc3-127">Możesz mieszać pola zamówione i pola nazwane, tak jak w konstrukcji `prism`.</span><span class="sxs-lookup"><span data-stu-id="92dc3-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="92dc3-128">`option` Typu jest proste złożeniem dyskryminowanym w F# podstawowej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="92dc3-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="92dc3-129">`option` Typ jest zadeklarowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="92dc3-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="92dc3-130">Powyższy kod określa, że typ `Option` to złożenie dyskryminowane, które posiada dwa przypadki `Some` i `None`.</span><span class="sxs-lookup"><span data-stu-id="92dc3-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="92dc3-131">`Some` Przypadek ma skojarzoną wartość, która składa się z jednego pola anonimowego, którego typ jest reprezentowany przez parametr typu `'a`.</span><span class="sxs-lookup"><span data-stu-id="92dc3-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="92dc3-132">`None` Przypadek nie ma przypisanej wartości.</span><span class="sxs-lookup"><span data-stu-id="92dc3-132">The `None` case has no associated value.</span></span> <span data-ttu-id="92dc3-133">Ten sposób `option` typ Określa typ ogólny, który ma wartość pewnego typu, lub brak wartości.</span><span class="sxs-lookup"><span data-stu-id="92dc3-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="92dc3-134">Typ `Option` ma również alias z małej litery, `option`, czyli więcej często używane.</span><span class="sxs-lookup"><span data-stu-id="92dc3-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="92dc3-135">Identyfikatory przypadków mogą służyć jako konstruktory dla dyskryminowanego typu złożenia.</span><span class="sxs-lookup"><span data-stu-id="92dc3-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="92dc3-136">Na przykład, poniższy kod służy do tworzenia wartości `option` typu.</span><span class="sxs-lookup"><span data-stu-id="92dc3-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="92dc3-137">Identyfikatory przypadków są również używane w wyrażeniach dopasowania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="92dc3-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="92dc3-138">W wyrażeniu dopasowania do wzorca identyfikatory są dostarczane dla wartości skojarzonych z indywidualnych przypadkami.</span><span class="sxs-lookup"><span data-stu-id="92dc3-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="92dc3-139">Na przykład w poniższym kodzie `x` jest identyfikatorem otrzymującym wartość, która jest skojarzona z `Some` przypadku `option` typu.</span><span class="sxs-lookup"><span data-stu-id="92dc3-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="92dc3-140">W wyrażeniach dopasowania do wzorca można użyć nazwanych pól do określenia dopasowań złożenia dyskryminowanego.</span><span class="sxs-lookup"><span data-stu-id="92dc3-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="92dc3-141">Dla typu kształt, który został uprzednio zadeklarowany można użyć nazwanych pól, jak w poniższym kodzie pokazano do wyodrębnienia wartości pól.</span><span class="sxs-lookup"><span data-stu-id="92dc3-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="92dc3-142">Zazwyczaj identyfikatory przypadków mogą służyć bez kwalifikowania ich nazwą Unii.</span><span class="sxs-lookup"><span data-stu-id="92dc3-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="92dc3-143">Jeśli chcesz, aby nazwa zawsze była kwalifikowana nazwą złożenia, można zastosować [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) atrybutu do definicji typu złożenia.</span><span class="sxs-lookup"><span data-stu-id="92dc3-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-[fsharp]) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="92dc3-144">Odkodowywanie sumy rozłączne</span><span class="sxs-lookup"><span data-stu-id="92dc3-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="92dc3-145">W F# sumy rozłączne są często używane w domenie modelowania zawijania jednego typu.</span><span class="sxs-lookup"><span data-stu-id="92dc3-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="92dc3-146">To ułatwia wyodrębnić wartości podstawowej za pomocą także dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="92dc3-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="92dc3-147">Nie należy użyć wyrażenia dopasowania dla jednego przypadku:</span><span class="sxs-lookup"><span data-stu-id="92dc3-147">You don't need to use a match expression for a single case:</span></span>

```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="92dc3-148">Poniższy przykład przedstawia to:</span><span class="sxs-lookup"><span data-stu-id="92dc3-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someFunctionUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ...
```

<span data-ttu-id="92dc3-149">Dopasowywania do wzorca jest też dozwolony bezpośrednio w parametrów funkcji, dzięki czemu można Odkodowywanie jeden przypadek:</span><span class="sxs-lookup"><span data-stu-id="92dc3-149">Pattern matching is also allowed directly in function parameters, so you can unwrap a single case there:</span></span>

```fsharp
let someFunctionUsingShaderProgram (ShaderProgram id) =
    // Use the unwrapped value
    ...
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="92dc3-150">Sumy rozłączne</span><span class="sxs-lookup"><span data-stu-id="92dc3-150">Struct Discriminated Unions</span></span>

<span data-ttu-id="92dc3-151">Sumy rozłączne może również reprezentować jako struktury.</span><span class="sxs-lookup"><span data-stu-id="92dc3-151">You can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="92dc3-152">Jest to zrobić za pomocą `[<Struct>]` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="92dc3-152">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="92dc3-153">Ponieważ te są typami wartości i typy referencyjne nie istnieją dodatkowe zagadnienia dotyczące w porównaniu z odwołaniem rekord z wariantami:</span><span class="sxs-lookup"><span data-stu-id="92dc3-153">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="92dc3-154">Zostaną skopiowane jako typów wartości i mogą wywoływać semantyka typów wartości.</span><span class="sxs-lookup"><span data-stu-id="92dc3-154">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="92dc3-155">Nie można używać definicji typu cyklicznego multicase struktury Discriminated Unii.</span><span class="sxs-lookup"><span data-stu-id="92dc3-155">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="92dc3-156">Należy podać unikatowe nazwy przypadków multicase struktury Discriminated Unii.</span><span class="sxs-lookup"><span data-stu-id="92dc3-156">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="92dc3-157">Używanie dyskryminowanych związków zamiast hierarchii obiektu</span><span class="sxs-lookup"><span data-stu-id="92dc3-157">Using Discriminated Unions Instead of Object Hierarchies</span></span>

<span data-ttu-id="92dc3-158">Często można użyć złożenia dyskryminowanego jako prostszej alternatywy dla hierarchii małych obiektów.</span><span class="sxs-lookup"><span data-stu-id="92dc3-158">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="92dc3-159">Na przykład następującej sumy rozłączonej można użyć zamiast `Shape` podstawowej klasy, która ma pochodne typy dla okręgu, kwadratu, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="92dc3-159">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="92dc3-160">Zamiast tego metody wirtualnej do obliczenia powierzchni lub obwodu, która zostałaby użyta w implementacji zorientowanej, można użyć wzorca dopasowania w celu odgałęzienia odpowiednich formuł do obliczania tych ilości.</span><span class="sxs-lookup"><span data-stu-id="92dc3-160">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="92dc3-161">W poniższym przykładzie różne formuły służą do obliczania powierzchni, w zależności od kształtu.</span><span class="sxs-lookup"><span data-stu-id="92dc3-161">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="92dc3-162">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="92dc3-162">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="92dc3-163">Używanie dyskryminowanych związków dla struktur drzewa danych</span><span class="sxs-lookup"><span data-stu-id="92dc3-163">Using Discriminated Unions for Tree Data Structures</span></span>

<span data-ttu-id="92dc3-164">Połączenia rozróżniane mogą być cykliczne, co oznacza, że samo połączenie mogły zostać uwzględnione w rodzaju jeden lub więcej przypadków.</span><span class="sxs-lookup"><span data-stu-id="92dc3-164">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="92dc3-165">Cykliczne związki dyskryminowane mogą służyć do tworzenia struktur drzewa, które są używane do modelowania wyrażeń w językach programowania.</span><span class="sxs-lookup"><span data-stu-id="92dc3-165">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="92dc3-166">W poniższym kodzie cykliczna Suma rozłączna jest używana do tworzenia struktury drzewa danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="92dc3-166">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="92dc3-167">Złożenie składa się z dwóch przypadków `Node`, który jest węzłem o wartości całkowitej oraz poddrzew lewego i prawego, i `Tip`, który kończy drzewo.</span><span class="sxs-lookup"><span data-stu-id="92dc3-167">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="92dc3-168">W poprzednim kodzie `resultSumTree` ma wartość 10.</span><span class="sxs-lookup"><span data-stu-id="92dc3-168">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="92dc3-169">Poniższa ilustracja przedstawia strukturę drzewa dla `myTree`.</span><span class="sxs-lookup"><span data-stu-id="92dc3-169">The following illustration shows the tree structure for `myTree`.</span></span>

![Diagram przedstawia strukturę drzewa dla myTree.](../media/discriminated-unions/tree-structure-mytree.png)

<span data-ttu-id="92dc3-171">Połączenia rozróżniane działają dobrze, jeśli węzłów w drzewie są heterogeniczne.</span><span class="sxs-lookup"><span data-stu-id="92dc3-171">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="92dc3-172">W poniższym kodzie typ `Expression` reprezentuje drzewo abstrakcyjnej składni wyrażenia w prostym języku programowania, który obsługuje dodawanie i mnożenie liczb i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="92dc3-172">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="92dc3-173">Niektórych przypadki nie są cykliczne i reprezentują liczby (`Number`) lub zmienne (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="92dc3-173">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="92dc3-174">Inne przypadki są cykliczne i reprezentują operacje (`Add` i `Multiply`), gdzie argumenty operacji są również wyrażeniami.</span><span class="sxs-lookup"><span data-stu-id="92dc3-174">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="92dc3-175">`Evaluate` Funkcja używa wyrażenia dopasowania, aby procesu cyklicznie przetwarzać drzewo składni.</span><span class="sxs-lookup"><span data-stu-id="92dc3-175">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="92dc3-176">Kiedy ten kod jest wykonywany, wartość `result` wynosi 5.</span><span class="sxs-lookup"><span data-stu-id="92dc3-176">When this code is executed, the value of `result` is 5.</span></span>

## <a name="members"></a><span data-ttu-id="92dc3-177">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="92dc3-177">Members</span></span>

<span data-ttu-id="92dc3-178">Istnieje możliwość definiowania elementów członkowskich w związki dyskryminowane.</span><span class="sxs-lookup"><span data-stu-id="92dc3-178">It is possible to define members on discriminated unions.</span></span> <span data-ttu-id="92dc3-179">Poniższy przykład pokazuje, jak zdefiniować właściwość i zaimplementować interfejs:</span><span class="sxs-lookup"><span data-stu-id="92dc3-179">The following example shows how to define a property and implement an interface:</span></span>

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

## <a name="common-attributes"></a><span data-ttu-id="92dc3-180">Atrybuty wspólne</span><span class="sxs-lookup"><span data-stu-id="92dc3-180">Common attributes</span></span>

<span data-ttu-id="92dc3-181">Następujące atrybuty są często widoczne w połączenia dyskryminowanych:</span><span class="sxs-lookup"><span data-stu-id="92dc3-181">The following attributes are commonly seen in discriminated unions:</span></span>

* `[<RequireQualifiedAccess>]`
* `[<NoEquality>]`
* `[<NoComparison>]`
* `[<Struct>]`

## <a name="see-also"></a><span data-ttu-id="92dc3-182">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92dc3-182">See also</span></span>

- [<span data-ttu-id="92dc3-183">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="92dc3-183">F# Language Reference</span></span>](index.md)
