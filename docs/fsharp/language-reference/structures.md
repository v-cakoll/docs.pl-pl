---
title: Struktury
description: Dowiedz się więcej o Strukturze F#, typ obiektu kompaktowego często bardziej wydajne niż klasy dla typów z niewielką ilością danych i proste zachowanie.
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400282"
---
# <a name="structures"></a><span data-ttu-id="a59db-103">Struktury</span><span class="sxs-lookup"><span data-stu-id="a59db-103">Structures</span></span>

<span data-ttu-id="a59db-104">*Struktura* jest typem obiektu kompaktowego, który może być bardziej efektywne niż klasy dla typów, które mają niewielką ilość danych i proste zachowanie.</span><span class="sxs-lookup"><span data-stu-id="a59db-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="a59db-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a59db-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="a59db-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a59db-106">Remarks</span></span>

<span data-ttu-id="a59db-107">Struktury są *typy wartości*, co oznacza, że są one przechowywane bezpośrednio na stosie lub, gdy są one używane jako pola lub elementy tablicy, w wierszu typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a59db-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="a59db-108">W przeciwieństwie do klas i rekordów struktury mają semantykę przekazywania według wartości.</span><span class="sxs-lookup"><span data-stu-id="a59db-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="a59db-109">Oznacza to, że są one przydatne głównie dla małych agregatów danych, które są często dostępne i kopiowane.</span><span class="sxs-lookup"><span data-stu-id="a59db-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="a59db-110">W poprzedniej składni wyświetlane są dwie formy.</span><span class="sxs-lookup"><span data-stu-id="a59db-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="a59db-111">Pierwszym z nich nie jest składnia lekka, ale mimo `struct` to `end` jest często używany, `StructAttribute` ponieważ podczas korzystania z i słów kluczowych, można pominąć atrybut, który pojawia się w drugim formularzu.</span><span class="sxs-lookup"><span data-stu-id="a59db-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="a59db-112">Możesz `StructAttribute` skrócić do po `Struct`prostu .</span><span class="sxs-lookup"><span data-stu-id="a59db-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="a59db-113">*Typ-definition-elements-and-members* w poprzedniej składni reprezentuje deklaracje elementów członkowskich i definicje.</span><span class="sxs-lookup"><span data-stu-id="a59db-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="a59db-114">Struktury mogą mieć konstruktorów i pola zmienne i niezmienne i mogą deklarować implementacje członków i interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a59db-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="a59db-115">Aby uzyskać więcej informacji, zobacz [Członkowie](./members/index.md).</span><span class="sxs-lookup"><span data-stu-id="a59db-115">For more information, see [Members](./members/index.md).</span></span>

<span data-ttu-id="a59db-116">Struktury nie mogą uczestniczyć w `let` `do` dziedziczeniu, nie mogą zawierać ani powiązać i nie mogą zawierać cyklicznie pól własnego typu (chociaż mogą zawierać komórki referencyjne, które odwołują się do własnego typu).</span><span class="sxs-lookup"><span data-stu-id="a59db-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="a59db-117">Ponieważ struktury nie `let` zezwalają na powiązania, należy zadeklarować `val` pola w strukturach przy użyciu słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="a59db-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="a59db-118">Słowo `val` kluczowe definiuje pole i jego typ, ale nie zezwala na inicjowanie.</span><span class="sxs-lookup"><span data-stu-id="a59db-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="a59db-119">Zamiast `val` tego deklaracje są inicjowane do zera lub null.</span><span class="sxs-lookup"><span data-stu-id="a59db-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="a59db-120">Z tego powodu struktury, które mają niejawny konstruktor (czyli parametry, które są podane `val` bezpośrednio po nazwie struktury w `DefaultValue` deklaracji) wymagają, aby deklaracje były adnotowane z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="a59db-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="a59db-121">Struktury, które mają zdefiniowany konstruktor nadal obsługują zero-inicjowania.</span><span class="sxs-lookup"><span data-stu-id="a59db-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="a59db-122">W związku `DefaultValue` z tym atrybut jest deklaracją, że taka wartość zero jest prawidłowa dla pola.</span><span class="sxs-lookup"><span data-stu-id="a59db-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="a59db-123">Niejawnych konstruktorów dla struktur nie `let` `do` wykonują żadnych akcji, ponieważ i powiązania nie są dozwolone na typ, ale niejawne wartości parametrów konstruktora przekazywane są dostępne jako pola prywatne.</span><span class="sxs-lookup"><span data-stu-id="a59db-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="a59db-124">Jawne konstruktory mogą obejmować inicjowanie wartości pól.</span><span class="sxs-lookup"><span data-stu-id="a59db-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="a59db-125">Gdy masz strukturę, która ma jawny konstruktora, nadal obsługuje zero-inicjowania; jednak nie należy używać `DefaultValue` atrybutu `val` na deklaracje, ponieważ jest w konflikcie z konstruktora jawnego.</span><span class="sxs-lookup"><span data-stu-id="a59db-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="a59db-126">Aby uzyskać `val` więcej informacji o deklaracjach, zobacz [Jawne pola: `val` Słowo kluczowe](./members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="a59db-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="a59db-127">Atrybuty i modyfikatory ułatwień dostępu są dozwolone w strukturach i postępuj zgodnie z tymi samymi regułami, co w przypadku innych typów.</span><span class="sxs-lookup"><span data-stu-id="a59db-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="a59db-128">Aby uzyskać więcej informacji, zobacz [Atrybuty](attributes.md) i [kontrola dostępu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="a59db-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="a59db-129">Poniższe przykłady kodu ilustrują definicje struktury.</span><span class="sxs-lookup"><span data-stu-id="a59db-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="a59db-130">Struktury ByRefLike</span><span class="sxs-lookup"><span data-stu-id="a59db-130">ByRefLike structs</span></span>

<span data-ttu-id="a59db-131">Można zdefiniować własne struktury, które mogą `byref`przylegać do semantyki -like: zobacz [Byrefs](byrefs.md) aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="a59db-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="a59db-132">Odbywa się to <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> za pomocą atrybutu:</span><span class="sxs-lookup"><span data-stu-id="a59db-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="a59db-133">`IsByRefLike`nie oznacza `Struct`.</span><span class="sxs-lookup"><span data-stu-id="a59db-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="a59db-134">Oba muszą być obecne na typie.</span><span class="sxs-lookup"><span data-stu-id="a59db-134">Both must be present on the type.</span></span>

<span data-ttu-id="a59db-135">Struktura`byref`"-like" w języku F# jest typem wartości powiązanym ze stosem.</span><span class="sxs-lookup"><span data-stu-id="a59db-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="a59db-136">Nigdy nie jest przydzielany na zarządzanym stercie.</span><span class="sxs-lookup"><span data-stu-id="a59db-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="a59db-137">Struktura `byref`-like jest przydatna w programowaniu o wysokiej wydajności, ponieważ jest wymuszana z zestawem silnych kontroli dotyczących okresu istnienia i braku przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="a59db-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="a59db-138">Zasady są następujące:</span><span class="sxs-lookup"><span data-stu-id="a59db-138">The rules are:</span></span>

- <span data-ttu-id="a59db-139">Mogą być używane jako parametry funkcji, parametry metody, zmienne lokalne, zwraca metoda.</span><span class="sxs-lookup"><span data-stu-id="a59db-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
- <span data-ttu-id="a59db-140">Nie mogą być statyczne lub wystąpienia elementów członkowskich klasy lub normalnej struktury.</span><span class="sxs-lookup"><span data-stu-id="a59db-140">They cannot be static or instance members of a class or normal struct.</span></span>
- <span data-ttu-id="a59db-141">Nie mogą być przechwytywane`async` przez dowolną konstrukcję zamknięcia (metody lub wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="a59db-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
- <span data-ttu-id="a59db-142">Nie można ich używać jako parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="a59db-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="a59db-143">Chociaż te reguły bardzo silnie ograniczają użycie, robią to, aby spełnić obietnicę obliczeń o wysokiej wydajności w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="a59db-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="a59db-144">Struktury tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a59db-144">ReadOnly structs</span></span>

<span data-ttu-id="a59db-145">Można adnotować struktury z <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="a59db-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="a59db-146">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a59db-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="a59db-147">`IsReadOnly`nie oznacza `Struct`.</span><span class="sxs-lookup"><span data-stu-id="a59db-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="a59db-148">Należy dodać oba, `IsReadOnly` aby mieć strukturę.</span><span class="sxs-lookup"><span data-stu-id="a59db-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="a59db-149">Użycie tego atrybutu emituje metadane pozwalając F# i `inref<'T>` C# wiedzieć, aby traktować go jako i `in ref`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="a59db-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="a59db-150">Definiowanie wartości zmiennej wewnątrz struktury tylko do odczytu powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="a59db-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="a59db-151">Ewidencja struktur i związki dyskryminowane</span><span class="sxs-lookup"><span data-stu-id="a59db-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="a59db-152">Można reprezentować [rekordy](records.md) i [związki dyskryminowane](discriminated-unions.md) jako struktury z atrybutem. `[<Struct>]`</span><span class="sxs-lookup"><span data-stu-id="a59db-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="a59db-153">Zobacz każdy artykuł, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="a59db-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="a59db-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a59db-154">See also</span></span>

- [<span data-ttu-id="a59db-155">Odwołanie do języka F#</span><span class="sxs-lookup"><span data-stu-id="a59db-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a59db-156">Klasy</span><span class="sxs-lookup"><span data-stu-id="a59db-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="a59db-157">Rekordy</span><span class="sxs-lookup"><span data-stu-id="a59db-157">Records</span></span>](records.md)
- [<span data-ttu-id="a59db-158">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a59db-158">Members</span></span>](./members/index.md)
