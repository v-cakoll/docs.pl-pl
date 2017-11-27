---
title: Struktury (F#)
description: "Dowiedz się więcej o F # struktury, typu obiektu compact często bardziej efektywne niż klasa dla typów z małej ilości danych i zachowania proste."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 50819506-3210-418f-9602-0ee1c9a52177
ms.openlocfilehash: 542b69a5aacb8fcfb0e8f6d6c943fe1954c4c59c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="structures"></a><span data-ttu-id="4cc67-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="4cc67-104">Structures</span></span>

<span data-ttu-id="4cc67-105">A *struktury* jest typem obiektu compact, który może być skuteczniejsza niż klasa dla typów, które mają niewielką ilość danych i zachowania proste.</span><span class="sxs-lookup"><span data-stu-id="4cc67-105">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="4cc67-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cc67-106">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a><span data-ttu-id="4cc67-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4cc67-107">Remarks</span></span>
<span data-ttu-id="4cc67-108">Struktury są *typów wartości*, co oznacza, że są przechowywane bezpośrednio na stosie, lub gdy są one używane jako pola lub typ elementów tablicy, wbudowanego w obiekcie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="4cc67-108">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="4cc67-109">W odróżnieniu od klasy i rejestruje struktury ma semantykę przebiegu przez wartość.</span><span class="sxs-lookup"><span data-stu-id="4cc67-109">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="4cc67-110">Oznacza to, że są one przydatne głównie dla małych wartości zagregowanych danych, które są dostępne i często skopiowane.</span><span class="sxs-lookup"><span data-stu-id="4cc67-110">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="4cc67-111">W poprzednich składni są wyświetlane dwa formularze.</span><span class="sxs-lookup"><span data-stu-id="4cc67-111">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="4cc67-112">Pierwszy nie jest lekkie składni, ale mimo to często jest używana, ponieważ, jeśli używasz `struct` i `end` słów kluczowych, można pominąć `StructAttribute` atrybut, który pojawi się w drugim formularzu.</span><span class="sxs-lookup"><span data-stu-id="4cc67-112">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="4cc67-113">Można skrócić `StructAttribute` nieco `Struct`.</span><span class="sxs-lookup"><span data-stu-id="4cc67-113">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="4cc67-114">*Elementy definicji typu* w poprzednim składni reprezentuje element członkowski deklaracje i definicje.</span><span class="sxs-lookup"><span data-stu-id="4cc67-114">The *type-definition-elements* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="4cc67-115">Struktury mogą mieć konstruktorów i modyfikowalne i modyfikować pola, a ich można zadeklarować elementów członkowskich i implementacje interfejsów.</span><span class="sxs-lookup"><span data-stu-id="4cc67-115">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="4cc67-116">Aby uzyskać więcej informacji, zobacz [członków](members/index.md).</span><span class="sxs-lookup"><span data-stu-id="4cc67-116">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="4cc67-117">Struktury nie mogą uczestniczyć w dziedziczeniu, nie może zawierać `let` lub `do` powiązań, i nie można rekursywnie zawierać pola własne typu z (chociaż zawierają odwołanie do komórki, odwołujące się do ich własnych typu).</span><span class="sxs-lookup"><span data-stu-id="4cc67-117">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="4cc67-118">Ponieważ struktur nie zezwalaj na `let` powiązań, musisz zadeklarować pól struktur za pomocą `val` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4cc67-118">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="4cc67-119">`val` — Słowo kluczowe definiuje pola i jego typ, ale nie zezwala na inicjowanie.</span><span class="sxs-lookup"><span data-stu-id="4cc67-119">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="4cc67-120">Zamiast tego `val` deklaracje są zainicjowana na zero lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="4cc67-120">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="4cc67-121">Z tego powodu struktur, które mają niejawnego konstruktora (czyli parametry, które są podane natychmiast po nazwie struktury w deklaracji) wymaga, aby `val` deklaracje być adnotowany przy `DefaultValue` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4cc67-121">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="4cc67-122">Struktury, które mają Konstruktor zdefiniowany nadal obsługuje inicjowania zero.</span><span class="sxs-lookup"><span data-stu-id="4cc67-122">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="4cc67-123">W związku z tym `DefaultValue` atrybutu jest deklaracją nieprawidłowość nieprawidłowy dla pola takie wartość zero.</span><span class="sxs-lookup"><span data-stu-id="4cc67-123">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="4cc67-124">Niejawne konstruktory struktury nie wykonuj żadnych akcji, ponieważ `let` i `do` powiązania nie są dozwolone w typie, ale przekazano wartości parametrów dorozumiany Konstruktor są dostępne jako pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="4cc67-124">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="4cc67-125">Jawne Konstruktory mogą dotyczyć inicjowania wartości pól.</span><span class="sxs-lookup"><span data-stu-id="4cc67-125">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="4cc67-126">Jeśli masz struktury, która ma jawny Konstruktor nadal obsługuje inicjowania zero; jednak nie użyto `DefaultValue` atrybutu `val` deklaracje, ponieważ powoduje on konflikt z jawny Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="4cc67-126">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="4cc67-127">Aby uzyskać więcej informacji na temat `val` deklaracje, zobacz [pola jawne: `val` — słowo kluczowe](members/explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="4cc67-127">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="4cc67-128">Atrybuty i modyfikatory dostępności są dozwolone w struktury i wykonaj te same zasady, jak w przypadku innych typów.</span><span class="sxs-lookup"><span data-stu-id="4cc67-128">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="4cc67-129">Aby uzyskać więcej informacji, zobacz [atrybuty](attributes.md) i [kontroli dostępu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="4cc67-129">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="4cc67-130">Poniższe przykłady kodu przedstawiają definicji struktury.</span><span class="sxs-lookup"><span data-stu-id="4cc67-130">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="4cc67-131">Struktura rekordów i sumy rozłączne</span><span class="sxs-lookup"><span data-stu-id="4cc67-131">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="4cc67-132">Począwszy od 4.1 F #, może reprezentować [rekordów](records.md) i [Suma rozłączna unie](discriminated-unions.md) jako struktury z `[<Struct>]` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4cc67-132">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="4cc67-133">Zobacz każdego artykułu, aby dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="4cc67-133">See each article to learn more.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="4cc67-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cc67-134">See Also</span></span>
[<span data-ttu-id="4cc67-135">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="4cc67-135">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4cc67-136">Klasy</span><span class="sxs-lookup"><span data-stu-id="4cc67-136">Classes</span></span>](classes.md)

[<span data-ttu-id="4cc67-137">Rekordy</span><span class="sxs-lookup"><span data-stu-id="4cc67-137">Records</span></span>](records.md)

[<span data-ttu-id="4cc67-138">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4cc67-138">Members</span></span>](members/index.md)
