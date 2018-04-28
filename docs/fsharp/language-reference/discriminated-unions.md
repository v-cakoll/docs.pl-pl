---
title: Sumy rozłączne (F#)
description: 'Dowiedz się, jak używać F # Suma rozłączna Unii.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 64c91410e284ee16036c4f51bd2247475a202a45
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="discriminated-unions"></a><span data-ttu-id="0d7e3-103">Sumy rozłączne</span><span class="sxs-lookup"><span data-stu-id="0d7e3-103">Discriminated Unions</span></span>

<span data-ttu-id="0d7e3-104">Sumy rozłączne zapewniają obsługę wartości, które może być jedną z liczbą przypadków, prawdopodobnie każde z nich różne wartości i typy.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-104">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="0d7e3-105">Sumy rozłączne są przydatne w przypadku danych heterogenicznych; dane, które mogą mieć szczególnych przypadkach, w tym nieprawidłowy i w przypadku wystąpienia błędów; dane, które może być różna w typie z jednego wystąpienia i jako alternatywę dla małego obiektu hierarchii.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-105">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="0d7e3-106">Ponadto suma rozłączna cykliczne unie są używane do reprezentowania struktur danych drzewa.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-106">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d7e3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d7e3-107">Syntax</span></span>

```fsharp
[ attributes ]
type type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a><span data-ttu-id="0d7e3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d7e3-108">Remarks</span></span>
<span data-ttu-id="0d7e3-109">Sumy rozłączne są podobne do typów złożenia w innych językach, ale różnią się.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-109">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="0d7e3-110">Jako typ union w języku C++ lub typ wariantu w języku Visual Basic danych przechowywanych w wartości nie jest stały; może być jedną z kilku różne opcje.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-110">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="0d7e3-111">W przeciwieństwie do złożenia w tych językach, jednak wszystkich możliwych opcji podano *identyfikator przypadku*.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-111">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="0d7e3-112">Identyfikatory przypadku są nazwy dla różnych rodzajów wartości, które mogą być obiekty tego typu; wartości są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-112">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="0d7e3-113">Jeśli nie podano wartości, że wielkość liter jest odpowiednikiem wariant wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-113">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="0d7e3-114">Jeśli istnieją wartości, każda wartość albo może być pojedynczą wartość określonego typu lub spójnej kolekcji, który agreguje wiele pól w tych samych lub różnych typów.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-114">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="0d7e3-115">Począwszy od F # 3.1 pojedyncze pole można podać nazwę, ale nazwa jest opcjonalny, nawet jeśli są nazywane innych pól w przypadku tego samego.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-115">As of F# 3.1, you can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="0d7e3-116">Na przykład należy wziąć pod uwagę następujące deklaracji typu kształtu.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-116">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="0d7e3-117">Poprzedni kod deklaruje rozróżnianą Unię kształtu, który może mieć wartości dowolnej z trzech przypadkach: prostokąt, okrąg i biblioteki Prism.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-117">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="0d7e3-118">Każdej sprawy ma inny zestaw pól.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-118">Each case has a different set of fields.</span></span> <span data-ttu-id="0d7e3-119">Prostokąt przypadek ma dwa o nazwie pola, zarówno typu `float`, które mają nazwy szerokości i długości.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-119">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="0d7e3-120">W przypadku okrąg ma tylko jedno pole o nazwie, usługi radius.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-120">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="0d7e3-121">W przypadku biblioteki Prism ma trzy pola są dwa (szerokość i wysokość) o nazwie pola.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-121">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="0d7e3-122">Nazwy pól są określane jako pola anonimowego.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-122">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="0d7e3-123">Podając wartości w polach nazwane i anonimowe zgodnie z poniższych przykładach utworzymy obiektów.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-123">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="0d7e3-124">Ten kod pokazuje, że możesz użyć pola o nazwie inicjowania lub mogą polegać na kolejność pól w deklaracji i z kolei wystarczy podać wartości dla każdego pola.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-124">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="0d7e3-125">Wywołanie konstruktora dla `rect` w poprzednim kodzie używa pola o nazwie, ale wywołanie konstruktora dla `circ` używa kolejność.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-125">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="0d7e3-126">Można mieszać uporządkowanych pól i o nazwie pola, tak jak konstrukcji `prism`.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-126">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="0d7e3-127">`option` Typ jest proste rozróżnianą Unię biblioteki podstawowej F #.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-127">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="0d7e3-128">`option` Typ został zadeklarowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-128">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="0d7e3-129">Poprzedni kod określa, że typ `Option` jest rozróżnianą Unię z dwóch przypadków `Some` i `None`.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-129">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="0d7e3-130">`Some` Przypadek ma skojarzoną wartość, która składa się z co najmniej dwa pola anonimowego, którego typ jest reprezentowana przez parametr typu `'a`.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-130">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="0d7e3-131">`None` Case nie ma skojarzonej wartości.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-131">The `None` case has no associated value.</span></span> <span data-ttu-id="0d7e3-132">W związku z tym `option` typ określa typu ogólnego, który ma wartość pewien typ lub brak wartości.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-132">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="0d7e3-133">Typ `Option` ma również alias typu małych `option`, to znaczy więcej często używane.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-133">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="0d7e3-134">Identyfikatory przypadku może służyć jako konstruktorów typu Unii rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-134">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="0d7e3-135">Na przykład poniższy kod służy do tworzenia wartości `option` typu.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-135">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="0d7e3-136">Identyfikatory przypadku są również używane w wyrażeniach dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-136">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="0d7e3-137">We wzorcu zgodnego wyrażeniem identyfikatory są dostępne dla wartości skojarzone z poszczególnych przypadków.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-137">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="0d7e3-138">Na przykład w poniższym kodzie `x` identyfikator znajduje się wartość, z którym skojarzony jest `Some` przypadku `option` typu.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-138">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="0d7e3-139">We wzorcu pasujące wyrażeń pola o nazwie służy do określenia dopasowań Unii rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-139">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="0d7e3-140">Typu, który został wcześniej zadeklarowany jako można użyć pola o nazwie, jak poniższy kod przedstawia wyodrębnianie wartości pól.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-140">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="0d7e3-141">Identyfikatory przypadku można zwykle bez zakwalifikowanie ich nazwą Unii.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-141">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="0d7e3-142">Jeśli nazwa zawsze być kwalifikowane nazwą Unii, można zastosować [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atrybutu do definicji typu union.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-142">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="0d7e3-143">Odkodowywanie rozłączne</span><span class="sxs-lookup"><span data-stu-id="0d7e3-143">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="0d7e3-144">W F # Suma rozłączna unie są często używane w domenie modelowania zawijania jednego typu.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-144">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="0d7e3-145">Jest łatwy do wyodrębnienia odpowiednia wartość za pomocą, jak również dopasowanie wzorca.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-145">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="0d7e3-146">Nie trzeba używać wyrażenie dopasowania dla pojedynczego przypadku:</span><span class="sxs-lookup"><span data-stu-id="0d7e3-146">You don't need to use a match expression for a single case:</span></span>
```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="0d7e3-147">W poniższym przykładzie pokazano to:</span><span class="sxs-lookup"><span data-stu-id="0d7e3-147">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="0d7e3-148">Unie Suma rozłączna — struktura</span><span class="sxs-lookup"><span data-stu-id="0d7e3-148">Struct Discriminated Unions</span></span>

<span data-ttu-id="0d7e3-149">Począwszy od 4.1 F #, może także reprezentować Suma rozłączna unie jako struktury.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-149">Starting with F# 4.1, you can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="0d7e3-150">Jest to zrobić za pomocą `[<Struct>]` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-150">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of Case1 : string
    | Case2 of Case2 : int
    | Case3 of Case3 : double
```

<span data-ttu-id="0d7e3-151">Ponieważ te są typy wartości i typy referencyjne nie istnieją dodatkowe zagadnienia, w porównaniu z odwołaniem Suma rozłączna unie:</span><span class="sxs-lookup"><span data-stu-id="0d7e3-151">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="0d7e3-152">Są kopiowane jako typów wartości i mogą wywoływać semantyka typów wartości.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-152">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="0d7e3-153">Definicja typu rekursywnego nie można używać struktury multicase Discriminated Union.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-153">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="0d7e3-154">Podaj unikatowe nazwy multicase struktury Discriminated Unii.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-154">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="0d7e3-155">Za pomocą rozłączne zamiast hierarchie obiektów</span><span class="sxs-lookup"><span data-stu-id="0d7e3-155">Using Discriminated Unions Instead of Object Hierarchies</span></span>
<span data-ttu-id="0d7e3-156">Często służą rozróżnianą Unię prostsze alternatywę do hierarchii małego obiektu.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-156">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="0d7e3-157">Na przykład można użyć następujących rozróżnianą Unię zamiast `Shape` podstawowa klasa, która ma pochodnych typów koło, kwadratowa itd.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-157">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="0d7e3-158">Zamiast tego metody wirtualnej można obliczyć obszar lub obwód, możesz mogą używać w implementację zorientowany obiektowo, możesz użyć wzorzec dopasowany do gałęzi odpowiednie formuły można obliczyć ilości te.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-158">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="0d7e3-159">W poniższym przykładzie różne formuły są używane do obliczenia obszaru, w zależności od kształtu.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-159">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="0d7e3-160">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="0d7e3-160">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="0d7e3-161">Za pomocą rozłączne dla struktur danych drzewa</span><span class="sxs-lookup"><span data-stu-id="0d7e3-161">Using Discriminated Unions for Tree Data Structures</span></span>
<span data-ttu-id="0d7e3-162">Sumy rozłączne można cyklicznej, co oznacza, że sam Unii można dołączyć do typu jeden lub więcej przypadków.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-162">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="0d7e3-163">Cykliczne rozłączne może służyć do tworzenia struktury drzewa, które są używane do wyrażenia modelu w językach programowania.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-163">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="0d7e3-164">W poniższym kodzie Suma rozłączna cyklicznej union jest używana do tworzenia struktury danych binarnych drzewa.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-164">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="0d7e3-165">Unia składa się z dwóch przypadków `Node`, który jest węzłem z wartością całkowitą i lewy i prawy poddrzewa, i `Tip`, która kończy drzewa.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-165">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="0d7e3-166">W poprzednim kodzie `resultSumTree` ma wartość 10.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-166">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="0d7e3-167">Na poniższej ilustracji przedstawiono struktury drzewa `myTree`.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-167">The following illustration shows the tree structure for `myTree`.</span></span>

![Struktura drzewa myTree](../media/TreeStructureDiagram.png)

<span data-ttu-id="0d7e3-169">Sumy rozłączne działa również w przypadku węzłów w drzewie heterogenicznych.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-169">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="0d7e3-170">W poniższym kodzie typ `Expression` reprezentuje drzewa składni abstrakcyjnej wyrażenia w prosty język programowania, który obsługuje dodawanie i mnożenia zmiennych i cyfry.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-170">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="0d7e3-171">Niektóre przypadków Unii nie są cykliczne i liczby albo (`Number`) lub zmiennych (`Variable`).</span><span class="sxs-lookup"><span data-stu-id="0d7e3-171">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="0d7e3-172">Zdarza się to cykliczne, stanowiące operacji (`Add` i `Multiply`), gdzie argumenty operacji są również wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-172">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="0d7e3-173">`Evaluate` Funkcja korzysta z wyrażenia dopasowania do procesu rekursywnie drzewa składni.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-173">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="0d7e3-174">Po wykonaniu tego kodu, wartość `result` wynosi 5.</span><span class="sxs-lookup"><span data-stu-id="0d7e3-174">When this code is executed, the value of `result` is 5.</span></span>

## <a name="common-attributes"></a><span data-ttu-id="0d7e3-175">Atrybuty wspólne</span><span class="sxs-lookup"><span data-stu-id="0d7e3-175">Common Attributes</span></span>

<span data-ttu-id="0d7e3-176">Następujące atrybuty są zwykle widoczne w rozłączne:</span><span class="sxs-lookup"><span data-stu-id="0d7e3-176">The following attributes are commonly seen in discriminated unions:</span></span>

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* <span data-ttu-id="0d7e3-177">`[Struct]` (F # 4.1 i nowsze)</span><span class="sxs-lookup"><span data-stu-id="0d7e3-177">`[Struct]` (F# 4.1 and higher)</span></span>

## <a name="see-also"></a><span data-ttu-id="0d7e3-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d7e3-178">See Also</span></span>
[<span data-ttu-id="0d7e3-179">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="0d7e3-179">F# Language Reference</span></span>](index.md)
