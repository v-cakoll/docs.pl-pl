---
title: Rekordy (F#)
description: 'Dowiedz się, jak F # rekordów reprezentują proste agreguje nazwanych wartości, opcjonalnie z elementami członkowskimi.'
ms.date: 05/16/2016
ms.openlocfilehash: 5bd1f76937bf5839b7da5cae7dea578747ec9b99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="records"></a><span data-ttu-id="c49ac-103">Rekordy</span><span class="sxs-lookup"><span data-stu-id="c49ac-103">Records</span></span>

<span data-ttu-id="c49ac-104">Rejestruje reprezentują proste agreguje nazwanych wartości, opcjonalnie z elementami członkowskimi.</span><span class="sxs-lookup"><span data-stu-id="c49ac-104">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="c49ac-105">Począwszy od 4.1 F #, może to być typy struktur lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="c49ac-105">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="c49ac-106">Są one typy referencyjne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="c49ac-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="c49ac-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c49ac-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="c49ac-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c49ac-108">Remarks</span></span>
<span data-ttu-id="c49ac-109">W poprzednich składni *typename* jest nazwa typu rekordu *label1* i *label2* nazwy wartości, nazywane są *etykiety*, i *type1* i *type2* typy tych wartości.</span><span class="sxs-lookup"><span data-stu-id="c49ac-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="c49ac-110">*Lista elementów członkowskich* jest opcjonalna lista elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="c49ac-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="c49ac-111">Można użyć `[<Struct>]` atrybutu, aby utworzyć rekord struktury, a nie rekordu, który jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="c49ac-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="c49ac-112">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="c49ac-112">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="c49ac-113">W przypadku każdej etykiety w osobnym wierszu, średnik jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="c49ac-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="c49ac-114">Można ustawić wartości w wyrażeniach znany jako *rekordów wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="c49ac-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="c49ac-115">Kompilator wnioskuje typ z etykiety używane (Jeśli etykiety są wystarczająco różne inne typy rekordów).</span><span class="sxs-lookup"><span data-stu-id="c49ac-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="c49ac-116">Nawiasy klamrowe ({}) należy ująć wyrażenia rekordu.</span><span class="sxs-lookup"><span data-stu-id="c49ac-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="c49ac-117">Poniższy kod przedstawia wyrażenia rekordu, który inicjuje rekord z trzech elementów typu float z etykietami `x`, `y` i `z`.</span><span class="sxs-lookup"><span data-stu-id="c49ac-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="c49ac-118">Skrócona forma nie należy używać, jeśli może istnieć inny typ, który również ma takie same etykiety.</span><span class="sxs-lookup"><span data-stu-id="c49ac-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="c49ac-119">Etykiety najbardziej ostatnio deklarowanego typu pierwszeństwo wcześniej zadeklarowanego typu tak w powyższym przykładzie `mypoint3D` jest wywnioskowany jako `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="c49ac-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="c49ac-120">Można jawnie określić typ rekordu, zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="c49ac-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="c49ac-121">Metody mogą być definiowane dla typów rekordów, podobnie jak w przypadku typu klasy.</span><span class="sxs-lookup"><span data-stu-id="c49ac-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="c49ac-122">Tworzenie rekordów przy użyciu wyrażenia rekordu</span><span class="sxs-lookup"><span data-stu-id="c49ac-122">Creating Records by Using Record Expressions</span></span>
<span data-ttu-id="c49ac-123">Rekordy można zainicjować za pomocą etykiet, które są zdefiniowane w rekordzie.</span><span class="sxs-lookup"><span data-stu-id="c49ac-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="c49ac-124">To wyrażenie jest określany jako *rekordów wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="c49ac-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="c49ac-125">Użyj nawiasów klamrowych ujmij wyrażenie rekordu i użyj średnika jako ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="c49ac-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="c49ac-126">Poniższy przykład przedstawia sposób tworzenia rekordu.</span><span class="sxs-lookup"><span data-stu-id="c49ac-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="c49ac-127">Średnikami po ostatnim pola w wyrażeniu rekordu i w definicji typu są opcjonalne, niezależnie od tego, czy pola są wszystko w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="c49ac-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="c49ac-128">Po utworzeniu rekordu, należy podać wartości dla każdego pola.</span><span class="sxs-lookup"><span data-stu-id="c49ac-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="c49ac-129">Nie można odwołać się do wartości innych pól w wyrażeniu inicjowania dla dowolnego pola.</span><span class="sxs-lookup"><span data-stu-id="c49ac-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="c49ac-130">W poniższym kodzie typ `myRecord2` jest wywnioskowany na podstawie nazwy pól.</span><span class="sxs-lookup"><span data-stu-id="c49ac-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="c49ac-131">Opcjonalnie można jawnie określić nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="c49ac-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="c49ac-132">Innej formy konstrukcji rekordu może być przydatne podczas kopiowania istniejącego rekordu i prawdopodobnie zmieniania wartości pól.</span><span class="sxs-lookup"><span data-stu-id="c49ac-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="c49ac-133">Następujący wiersz kodu ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="c49ac-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="c49ac-134">Ta postać wyrażenia rekordu jest nazywany *kopiowanie i aktualizację wyrażenia rekordu*.</span><span class="sxs-lookup"><span data-stu-id="c49ac-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="c49ac-135">Rekordy są niezmienne domyślnie; można jednak łatwo utworzyć zmodyfikowanych rekordów przy użyciu wyrażenia Kopiuj i Aktualizuj.</span><span class="sxs-lookup"><span data-stu-id="c49ac-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="c49ac-136">Można również jawnie określić pola modyfikowalnego.</span><span class="sxs-lookup"><span data-stu-id="c49ac-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="c49ac-137">Nie używaj atrybutu DefaultValue z pola rekordu.</span><span class="sxs-lookup"><span data-stu-id="c49ac-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="c49ac-138">Lepszym rozwiązaniem jest zdefiniuj wystąpień rekordy z pola, które są inicjowane wartości domyślne, a następnie użyj kopii i zaktualizuj wyrażenia rekordu, aby ustawić wszystkie pola, które różnią się od wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="c49ac-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="c49ac-139">Dopasowywanie do wzorca z rekordów</span><span class="sxs-lookup"><span data-stu-id="c49ac-139">Pattern Matching with Records</span></span>
<span data-ttu-id="c49ac-140">Rekordy można łączyć z dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="c49ac-140">Records can be used with pattern matching.</span></span> <span data-ttu-id="c49ac-141">Można jawnie określić niektórych pól i podaj zmienne inne pola, które zostaną przypisane, jeśli pasują do.</span><span class="sxs-lookup"><span data-stu-id="c49ac-141">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="c49ac-142">Pokazano to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="c49ac-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="c49ac-143">Poniżej przedstawiono dane wyjściowe tego kodu.</span><span class="sxs-lookup"><span data-stu-id="c49ac-143">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="c49ac-144">Różnice między rekordów i klasy</span><span class="sxs-lookup"><span data-stu-id="c49ac-144">Differences Between Records and Classes</span></span>
<span data-ttu-id="c49ac-145">Pola rekordu różnią się od klasy automatycznie są one widoczne jako właściwości, oraz są one używane do tworzenia i kopiowania rekordów.</span><span class="sxs-lookup"><span data-stu-id="c49ac-145">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="c49ac-146">Konstrukcja rekordów również różni się od klasy konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="c49ac-146">Record construction also differs from class construction.</span></span> <span data-ttu-id="c49ac-147">W polu Typ rekordu nie można definiować konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c49ac-147">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="c49ac-148">Zamiast tego stosuje składni konstrukcji opisanych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="c49ac-148">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="c49ac-149">Klasy nie mają bezpośredniego relacji między parametrami konstruktora, pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="c49ac-149">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="c49ac-150">Jak typy Unii i struktury rekordów mają semantykę równości strukturalnej.</span><span class="sxs-lookup"><span data-stu-id="c49ac-150">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="c49ac-151">Klasy mają odwołania semantykę równości.</span><span class="sxs-lookup"><span data-stu-id="c49ac-151">Classes have reference equality semantics.</span></span> <span data-ttu-id="c49ac-152">W poniższym przykładzie kodu pokazano to.</span><span class="sxs-lookup"><span data-stu-id="c49ac-152">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="c49ac-153">Jeśli piszesz ten sam kod z klasy obiektów dwóch klas może być nierówne dwóch wartości będzie reprezentować dwóch obiektów na stercie i czy można porównywać tylko adresy (o ile nie zastępuje typu klasy `System.Object.Equals` metody).</span><span class="sxs-lookup"><span data-stu-id="c49ac-153">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="c49ac-154">Jeśli konieczne odwołanie równości dla rekordów, Dodaj atrybut `[<ReferenceEquality>]` powyżej rekordu.</span><span class="sxs-lookup"><span data-stu-id="c49ac-154">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="c49ac-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c49ac-155">See Also</span></span>
[<span data-ttu-id="c49ac-156">Typy F#</span><span class="sxs-lookup"><span data-stu-id="c49ac-156">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="c49ac-157">Klasy</span><span class="sxs-lookup"><span data-stu-id="c49ac-157">Classes</span></span>](classes.md)

[<span data-ttu-id="c49ac-158">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="c49ac-158">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="c49ac-159">Równości odwołań</span><span class="sxs-lookup"><span data-stu-id="c49ac-159">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[<span data-ttu-id="c49ac-160">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="c49ac-160">Pattern Matching</span></span>](pattern-matching.md)
