---
title: Struktury (F#)
description: 'Dowiedz się więcej o F # struktury, typ obiektu compact, który jest często bardziej efektywne niż klasy dla typów z małą ilością danych i prostego zachowanie.'
ms.date: 05/16/2016
ms.openlocfilehash: 08af88132dda28883e246b94585ff4ed8bd2f16a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086791"
---
# <a name="structures"></a><span data-ttu-id="129c6-103">Struktury</span><span class="sxs-lookup"><span data-stu-id="129c6-103">Structures</span></span>

<span data-ttu-id="129c6-104">A *struktury* jest typem obiektu compact, który może być bardziej efektywne niż klasę dla typów, które mają niewielką ilość danych i prostego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="129c6-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="129c6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="129c6-105">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a><span data-ttu-id="129c6-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="129c6-106">Remarks</span></span>

<span data-ttu-id="129c6-107">Struktury są *typy wartości*, co oznacza, że są one przechowywane bezpośrednio na stosie, lub gdy są one używane jako pola lub typ elementów tablicy, wbudowanego w obiekcie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="129c6-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="129c6-108">W odróżnieniu od klas i rekordy struktury mają semantykę przekazać przez wartość.</span><span class="sxs-lookup"><span data-stu-id="129c6-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="129c6-109">Oznacza to, że są one przydatne głównie dla małych wartości zagregowanych danych, które są dostępne i często kopiowany.</span><span class="sxs-lookup"><span data-stu-id="129c6-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="129c6-110">W poprzedniej składni są wyświetlane dwie formy.</span><span class="sxs-lookup"><span data-stu-id="129c6-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="129c6-111">Pierwszy jest składni lekkiej, ale mimo to często jest używana, ponieważ podczas korzystania `struct` i `end` słów kluczowych, można pominąć `StructAttribute` atrybut, który pojawia się w drugim formularzu.</span><span class="sxs-lookup"><span data-stu-id="129c6-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="129c6-112">Można skrócić `StructAttribute` tylko `Struct`.</span><span class="sxs-lookup"><span data-stu-id="129c6-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="129c6-113">*-Definition elementów i-elementy członkowskie typu* w poprzedniej składni reprezentuje element członkowski deklaracje i definicje.</span><span class="sxs-lookup"><span data-stu-id="129c6-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="129c6-114">Struktury mogą mieć konstruktorów i pola mutable i niezmienne i mogą deklarować elementów członkowskich i implementacje interfejsu.</span><span class="sxs-lookup"><span data-stu-id="129c6-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="129c6-115">Aby uzyskać więcej informacji, zobacz [członków](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="129c6-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="129c6-116">Struktury nie uczestniczą w dziedziczeniu, nie mogą zawierać `let` lub `do` powiązań i nie może rekursywnie zawierać pola własne typu z (mimo że zawierają one komórki odwołań, odwołujące się do ich własnych typu).</span><span class="sxs-lookup"><span data-stu-id="129c6-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="129c6-117">Ponieważ nie zezwalają na struktury `let` powiązania, należy zadeklarować pól w strukturach przy użyciu `val` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="129c6-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="129c6-118">`val` — Słowo kluczowe definiuje pola typu i jego typu, ale nie zezwala na inicjowanie.</span><span class="sxs-lookup"><span data-stu-id="129c6-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="129c6-119">Zamiast tego `val` deklaracje są zainicjowana na zero lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="129c6-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="129c6-120">Z tego powodu struktur, które mają Konstruktor niejawne (czyli parametry, które zawierają zaraz po nazwie struktury w deklaracji) wymagają `val` deklaracje być oznaczona przy użyciu `DefaultValue` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="129c6-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="129c6-121">Struktury, które mają zdefiniowany Konstruktor nadal obsługuje inicjowania zero.</span><span class="sxs-lookup"><span data-stu-id="129c6-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="129c6-122">W związku z tym `DefaultValue` atrybutu jest deklaracją, że takie wartość zero jest prawidłowy dla pola.</span><span class="sxs-lookup"><span data-stu-id="129c6-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="129c6-123">Niejawne konstruktory dla struktury nie wykonuj żadnych akcji, ponieważ `let` i `do` powiązania nie są dozwolone w typie, ale wartości parametru dorozumiany Konstruktor przekazane są dostępne jako pola prywatne.</span><span class="sxs-lookup"><span data-stu-id="129c6-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="129c6-124">Jawnych konstruktorów może obejmować Inicjowanie wartości pól.</span><span class="sxs-lookup"><span data-stu-id="129c6-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="129c6-125">Jeśli masz strukturę, która ma jawny Konstruktor, nadal obsługuje inicjowania zero; jednak nie użyto `DefaultValue` atrybutu na `val` deklaracji, ponieważ powoduje on konflikt z jawny Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="129c6-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="129c6-126">Aby uzyskać więcej informacji na temat `val` deklaracji, zobacz [pola jawne: `val` — słowo kluczowe](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="129c6-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="129c6-127">Atrybuty i modyfikatory dostępności są dozwolone w strukturach, a następnie wykonaj te same zasady, jak w przypadku innych typów.</span><span class="sxs-lookup"><span data-stu-id="129c6-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="129c6-128">Aby uzyskać więcej informacji, zobacz [atrybuty](attributes.md) i [kontroli dostępu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="129c6-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="129c6-129">Poniższe przykłady kodu ilustrują definicji struktury.</span><span class="sxs-lookup"><span data-stu-id="129c6-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="129c6-130">Struktury ByRefLike</span><span class="sxs-lookup"><span data-stu-id="129c6-130">ByRefLike structs</span></span>

<span data-ttu-id="129c6-131">Można zdefiniować własne struktur, które można stosować `byref`— semantyka, takich jak: zobacz [Zkratka](byrefs.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="129c6-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="129c6-132">Jest to zrobić za pomocą <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> atrybutu:</span><span class="sxs-lookup"><span data-stu-id="129c6-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="129c6-133">`IsByRefLike` nie oznacza `Struct`.</span><span class="sxs-lookup"><span data-stu-id="129c6-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="129c6-134">Zarówno musi być obecny w typie.</span><span class="sxs-lookup"><span data-stu-id="129c6-134">Both must be present on the type.</span></span>

<span data-ttu-id="129c6-135">Element "`byref`— takich jak" struct w języku F # to typ wartości powiązanym ze stosu.</span><span class="sxs-lookup"><span data-stu-id="129c6-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="129c6-136">Nigdy nie zostanie przydzielona na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="129c6-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="129c6-137">A `byref`— takie jak struktura jest przydatne w przypadku programowania o wysokiej wydajności, jak są wymuszane za pomocą zestawu silne testów o okresie istnienia i -capture.</span><span class="sxs-lookup"><span data-stu-id="129c6-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="129c6-138">Dostępne są następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="129c6-138">The rules are:</span></span>

* <span data-ttu-id="129c6-139">One może służyć jako parametry funkcji, parametrów metody, zmienne lokalne, metoda zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="129c6-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="129c6-140">Nie mogą one być statyczne lub wystąpieniami elementów członkowskich klasy lub struktury normalne.</span><span class="sxs-lookup"><span data-stu-id="129c6-140">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="129c6-141">Nie można przechwycić według konstrukcji zamknięcia (`async` metod lub wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="129c6-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="129c6-142">Nie mogą one służyć jako parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="129c6-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="129c6-143">Mimo że te reguły ograniczają bardzo silnie użycia, to zrobią do spełnienia obietnicy o wysokiej wydajności obliczeniowej w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="129c6-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="129c6-144">Struktur tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="129c6-144">ReadOnly structs</span></span>

<span data-ttu-id="129c6-145">Możesz dodawać adnotacje do struktury za pomocą <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="129c6-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="129c6-146">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="129c6-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="129c6-147">`IsReadOnly` nie oznacza `Struct`.</span><span class="sxs-lookup"><span data-stu-id="129c6-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="129c6-148">Musisz dodać oba mieć `IsReadOnly` struktury.</span><span class="sxs-lookup"><span data-stu-id="129c6-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="129c6-149">Użyj tego atrybutu emituje metadane, umożliwiając F # i C#, aby traktować jako `inref<'T>` i `in ref`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="129c6-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="129c6-150">Definiowanie wartości modyfikowalne wewnątrz struktury tylko do odczytu powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="129c6-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="129c6-151">Rekordy struktury i związki dyskryminowane</span><span class="sxs-lookup"><span data-stu-id="129c6-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="129c6-152">Może reprezentować [rekordów](records.md) i [sumy rozłączne](discriminated-unions.md) jako struktury za pomocą `[<Struct>]` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="129c6-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="129c6-153">Zobacz poszczególnymi artykułami, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="129c6-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="129c6-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="129c6-154">See also</span></span>

- [<span data-ttu-id="129c6-155">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="129c6-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="129c6-156">Klasy</span><span class="sxs-lookup"><span data-stu-id="129c6-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="129c6-157">Rekordy</span><span class="sxs-lookup"><span data-stu-id="129c6-157">Records</span></span>](records.md)
- [<span data-ttu-id="129c6-158">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="129c6-158">Members</span></span>](members/index.md)
