---
title: Rozszerzenia typu (F#)
description: "Dowiedz się, jak rozszerzenia typu F # zezwala na dodawanie nowych elementów członkowskich do typu wcześniej zdefiniowanego obiektu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c9d7ce27-f5ad-4766-b9e9-34187da5bc24
ms.openlocfilehash: f78f8689e95fc1547f1a2b17c615592c00051f7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="type-extensions"></a><span data-ttu-id="f3b54-104">Rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="f3b54-104">Type Extensions</span></span>

<span data-ttu-id="f3b54-105">Typ rozszerzenia umożliwiają dodawanie nowych elementów członkowskich do typu wcześniej zdefiniowanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f3b54-105">Type extensions let you add new members to a previously defined object type.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3b54-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3b54-106">Syntax</span></span>

```fsharp
// Intrinsic extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]

// Optional extension.
type typename with
    member self-identifier.member-name =
        body
    ...
[ end ]
```

## <a name="remarks"></a><span data-ttu-id="f3b54-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3b54-107">Remarks</span></span>
<span data-ttu-id="f3b54-108">Istnieją dwie formy rozszerzeń typu, które ma nieco inną składnię i zachowania.</span><span class="sxs-lookup"><span data-stu-id="f3b54-108">There are two forms of type extensions that have slightly different syntax and behavior.</span></span> <span data-ttu-id="f3b54-109">*Rozszerzenie wewnętrzne* to rozszerzenie, które pojawia się w tej samej przestrzeni nazw lub modułu, w tym samym pliku źródłowego, a w tym samym zestawie (plik DLL lub plik wykonywalny) jako rozszerzanego typu.</span><span class="sxs-lookup"><span data-stu-id="f3b54-109">An *intrinsic extension* is an extension that appears in the same namespace or module, in the same source file, and in the same assembly (DLL or executable file) as the type being extended.</span></span> <span data-ttu-id="f3b54-110">*Opcjonalne rozszerzenie* to rozszerzenie, które znajduje się poza oryginalnego modułu, przestrzeni nazw lub zestawie rozszerzanego typu.</span><span class="sxs-lookup"><span data-stu-id="f3b54-110">An *optional extension* is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span> <span data-ttu-id="f3b54-111">Wewnętrzne rozszerzenia są wyświetlane na typ po typ się zbadana przez odbicie, ale opcjonalne rozszerzenia nie.</span><span class="sxs-lookup"><span data-stu-id="f3b54-111">Intrinsic extensions appear on the type when the type is examined by reflection, but optional extensions do not.</span></span> <span data-ttu-id="f3b54-112">Opcjonalne rozszerzenia musi być w modułach i są tylko w zakresie po otwarciu moduł, który zawiera rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f3b54-112">Optional extensions must be in modules, and they are only in scope when the module that contains the extension is open.</span></span>

<span data-ttu-id="f3b54-113">W poprzednich składni *typename* reprezentuje typ, który zostanie rozszerzone.</span><span class="sxs-lookup"><span data-stu-id="f3b54-113">In the previous syntax, *typename* represents the type that is being extended.</span></span> <span data-ttu-id="f3b54-114">Można ją rozszerzyć dowolnego typu, który jest dostępny, ale nazwa typu musi być nazwą typu rzeczywistego nie skrót typu.</span><span class="sxs-lookup"><span data-stu-id="f3b54-114">Any type that can be accessed can be extended, but the type name must be an actual type name, not a type abbreviation.</span></span> <span data-ttu-id="f3b54-115">Można zdefiniować wiele elementów członkowskich w jeden typ rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f3b54-115">You can define multiple members in one type extension.</span></span> <span data-ttu-id="f3b54-116">*Własny identyfikator* reprezentuje wystąpienie obiektu wywoływany, tak jak w przypadku zwykłej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f3b54-116">The *self-identifier* represents the instance of the object being invoked, just as in ordinary members.</span></span>

<span data-ttu-id="f3b54-117">`end` — Słowo kluczowe jest opcjonalna w lightweight — składnia.</span><span class="sxs-lookup"><span data-stu-id="f3b54-117">The `end` keyword is optional in lightweight syntax.</span></span>

<span data-ttu-id="f3b54-118">Elementów członkowskich zdefiniowanych w rozszerzenia typu może służyć podobnie jak w innych elementach członkowskich w typie klasy.</span><span class="sxs-lookup"><span data-stu-id="f3b54-118">Members defined in type extensions can be used just like other members on a class type.</span></span> <span data-ttu-id="f3b54-119">Podobnie jak inni członkowie ich być statyczne lub wystąpienia elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f3b54-119">Like other members, they can be static or instance members.</span></span> <span data-ttu-id="f3b54-120">Te metody są również znane jako *metody rozszerzenia*; właściwości są określane jako *właściwości rozszerzenia*i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="f3b54-120">These methods are also known as *extension methods*; properties are known as *extension properties*, and so on.</span></span> <span data-ttu-id="f3b54-121">Rozszerzenie opcjonalne elementy członkowskie są kompilowane do statycznych elementów członkowskich, dla których wystąpienie obiektu jest przekazywany niejawnie jako pierwszym parametrem.</span><span class="sxs-lookup"><span data-stu-id="f3b54-121">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="f3b54-122">Działają one jednak, tak jakby były elementów członkowskich wystąpień lub statycznych elementów członkowskich w zależności od sposobu są zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="f3b54-122">However, they act as if they were instance members or static members according to how they are declared.</span></span> <span data-ttu-id="f3b54-123">Elementy członkowskie rozszerzeń niejawne są uwzględnione jako elementy członkowskie tego typu i można go używać bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="f3b54-123">Implicit extension members are included as members of the type and can be used without restriction.</span></span>

<span data-ttu-id="f3b54-124">Metody rozszerzenia nie może być metody wirtualne lub abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="f3b54-124">Extension methods cannot be virtual or abstract methods.</span></span> <span data-ttu-id="f3b54-125">One przeciążenia innych metod o tej samej nazwie, ale kompilator daje preferencje metody bez rozszerzenia w przypadku niejednoznaczne wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f3b54-125">They can overload other methods of the same name, but the compiler gives preference to non-extension methods in the case of an ambiguous call.</span></span>

<span data-ttu-id="f3b54-126">Jeśli istnieje wiele rozszerzeń typu wewnętrznej dla jednego typu, wszystkie elementy członkowskie muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="f3b54-126">If multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="f3b54-127">Dla typu opcjonalne rozszerzenia elementy członkowskie w rozszerzeniach innego typu na ten sam typ mogą mieć tych samych nazwach.</span><span class="sxs-lookup"><span data-stu-id="f3b54-127">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="f3b54-128">Niejednoznaczności błędów tylko wtedy, gdy kod klienta otwiera dwa różne zakresy, które definiują tej samej nazwy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f3b54-128">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

<span data-ttu-id="f3b54-129">W poniższym przykładzie typu w module ma rozszerzenie typu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="f3b54-129">In the following example, a type in a module has an intrinsic type extension.</span></span> <span data-ttu-id="f3b54-130">Dla kodu klienta poza modułu rozszerzenia typu pojawia się jako zwykły element członkowski typu we wszystkich aspektach.</span><span class="sxs-lookup"><span data-stu-id="f3b54-130">To client code outside the module, the type extension appears as a regular member of the type in all respects.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3701.fs)]

<span data-ttu-id="f3b54-131">Rozszerzenia typu wewnętrznej służy do oddzielnych definicji typu na sekcje.</span><span class="sxs-lookup"><span data-stu-id="f3b54-131">You can use intrinsic type extensions to separate the definition of a type into sections.</span></span> <span data-ttu-id="f3b54-132">Może to być przydatne w zarządzaniu definicje dużego typu, na przykład zachowanie oddzielny kod wygenerowany przez kompilator i napisanego kodu lub zgrupować kodu utworzone przez różne osoby lub skojarzone z różnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="f3b54-132">This can be useful in managing large type definitions, for example, to keep compiler-generated code and authored code separate or to group together code created by different people or associated with different functionality.</span></span>

<span data-ttu-id="f3b54-133">W poniższym przykładzie opcjonalny type — rozszerzenie rozszerza `System.Int32` typ z metody rozszerzenia `FromString` wywołującym statycznego elementu członkowskiego `Parse`.</span><span class="sxs-lookup"><span data-stu-id="f3b54-133">In the following example, an optional type extension extends the `System.Int32` type with an extension method `FromString` that calls the static member `Parse`.</span></span> <span data-ttu-id="f3b54-134">`testFromString` Metody pokazuje, że nowy element członkowski jest nazywany podobnie jak wszystkie wystąpienia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f3b54-134">The `testFromString` method demonstrates that the new member is called just like any instance member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3702.fs)]

<span data-ttu-id="f3b54-135">Podobnie jak wszystkie inne metody pojawi się nowy element członkowski wystąpienia `Int32` typu w funkcji IntelliSense, ale tylko wtedy, gdy moduł, który zawiera rozszerzenie jest otwarte lub w inny sposób w zakresie.</span><span class="sxs-lookup"><span data-stu-id="f3b54-135">The new instance member will appear like any other method of the `Int32` type in IntelliSense, but only when the module that contains the extension is open or otherwise in scope.</span></span>

## <a name="generic-extension-methods"></a><span data-ttu-id="f3b54-136">Metody rozszerzenia w ogólnych</span><span class="sxs-lookup"><span data-stu-id="f3b54-136">Generic Extension Methods</span></span>
<span data-ttu-id="f3b54-137">Przed F # 3.1, kompilator języka F # nie obsługuje języka C# — styl metody rozszerzenia zmienną typu ogólnego, typu tablicy, typ krotki lub typem funkcji języka F # jako parametr "this".</span><span class="sxs-lookup"><span data-stu-id="f3b54-137">Before F# 3.1, the F# compiler didn't support the use of C#-style extension methods with a generic type variable, array type, tuple type, or an F# function type as the "this" parameter.</span></span> <span data-ttu-id="f3b54-138">3.1 F # obsługuje korzystanie z tych elementów członkowskich rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f3b54-138">F# 3.1 supports the use of these extension members.</span></span>

<span data-ttu-id="f3b54-139">Na przykład w kodzie języka F # 3.1, można użyć metody rozszerzenia podpisów, które przypominają następującej składni w języku C#:</span><span class="sxs-lookup"><span data-stu-id="f3b54-139">For example, in F# 3.1 code, you can use extension methods with signatures that resemble the following syntax in C#:</span></span>

```csharp
static member Method<T>(this T input, T other)
```

<span data-ttu-id="f3b54-140">Ta metoda jest szczególnie przydatne, gdy parametr typu ogólnego jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="f3b54-140">This approach is particularly useful when the generic type parameter is constrained.</span></span> <span data-ttu-id="f3b54-141">Ponadto można zadeklarować elementów członkowskich rozszerzenia następująco w kodzie języka F # i zdefiniować dodatkowe, semantycznie bogaty zestaw metod rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f3b54-141">Further, you can now declare extension members like this in F# code and define an additional, semantically rich set of extension methods.</span></span> <span data-ttu-id="f3b54-142">W języku F # zazwyczaj zdefiniowane jako w poniższym przykładzie przedstawiono elementy członkowskie rozszerzeń:</span><span class="sxs-lookup"><span data-stu-id="f3b54-142">In F#, you usually define extension members as the following example shows:</span></span>

```fsharp
open System.Collections.Generic

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq { for x in xs do for i in 1 .. n do yield x }
```

<span data-ttu-id="f3b54-143">Jednak dla typu ogólnego, zmienna typu może nie być ograniczone.</span><span class="sxs-lookup"><span data-stu-id="f3b54-143">However, for a generic type, the type variable may not be constrained.</span></span> <span data-ttu-id="f3b54-144">Teraz można zadeklarować C# — styl Członkowskim rozszerzenia języka F # w celu obejścia tego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="f3b54-144">You can now declare a C#-style extension member in F# to work around this limitation.</span></span> <span data-ttu-id="f3b54-145">Łącząc tego rodzaju deklaracji przy użyciu funkcji wbudowanej języka F # można przedstawić ogólnego algorytmów jako elementy członkowskie rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="f3b54-145">When you combine this kind of declaration with the inline feature of F#, you can present generic algorithms as extension members.</span></span>

<span data-ttu-id="f3b54-146">Należy wziąć pod uwagę następujące oświadczenie:</span><span class="sxs-lookup"><span data-stu-id="f3b54-146">Consider the following declaration:</span></span>

```fsharp
[<Extension>]
type ExtraCSharpStyleExtensionMethodsInFSharp () =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="f3b54-147">Za pomocą tej deklaracji, można napisać kod, podobny do poniższego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f3b54-147">By using this declaration, you can write code that resembles the following sample.</span></span>

```fsharp
let listOfIntegers = [ 1 .. 100 ]
let listOfBigIntegers = [ 1I to 100I ]
let sum1 = listOfIntegers.Sum()
let sum2 = listOfBigIntegers.Sum()
```

<span data-ttu-id="f3b54-148">W tym kodzie ten sam kod arytmetyczne ogólnego jest stosowany do listy dwa typy bez przeładowanie, definiując rozszerzenia jednego członka.</span><span class="sxs-lookup"><span data-stu-id="f3b54-148">In this code, the same generic arithmetic code is applied to lists of two types without overloading, by defining a single extension member.</span></span>


## <a name="see-also"></a><span data-ttu-id="f3b54-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3b54-149">See Also</span></span>
[<span data-ttu-id="f3b54-150">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="f3b54-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f3b54-151">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f3b54-151">Members</span></span>](members/index.md)
