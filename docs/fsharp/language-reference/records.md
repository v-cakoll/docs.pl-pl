---
title: Rekordy (F#)
description: "Dowiedz się, jak F # rekordów reprezentują proste agreguje nazwanych wartości, opcjonalnie z elementami członkowskimi."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: 478ab74ad32cc6e53daffd1bd6229729149d2a1e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="records"></a><span data-ttu-id="0940c-104">Rekordy</span><span class="sxs-lookup"><span data-stu-id="0940c-104">Records</span></span>

<span data-ttu-id="0940c-105">Rejestruje reprezentują proste agreguje nazwanych wartości, opcjonalnie z elementami członkowskimi.</span><span class="sxs-lookup"><span data-stu-id="0940c-105">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="0940c-106">Począwszy od 4.1 F #, może to być typy struktur lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="0940c-106">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="0940c-107">Są one typy referencyjne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0940c-107">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="0940c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="0940c-108">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="0940c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0940c-109">Remarks</span></span>
<span data-ttu-id="0940c-110">W poprzednich składni *typename* jest nazwa typu rekordu *label1* i *label2* nazwy wartości, nazywane są *etykiety*, i *type1* i *type2* typy tych wartości.</span><span class="sxs-lookup"><span data-stu-id="0940c-110">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="0940c-111">*Lista elementów członkowskich* jest opcjonalna lista elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="0940c-111">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="0940c-112">Można użyć `[<Struct>]` atrybutu, aby utworzyć rekord struktury, a nie rekordu, który jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="0940c-112">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="0940c-113">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="0940c-113">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="0940c-114">W przypadku każdej etykiety w osobnym wierszu, średnik jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0940c-114">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="0940c-115">Można ustawić wartości w wyrażeniach znany jako *rekordów wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="0940c-115">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="0940c-116">Kompilator wnioskuje typ z etykiety używane (Jeśli etykiety są wystarczająco różne inne typy rekordów).</span><span class="sxs-lookup"><span data-stu-id="0940c-116">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="0940c-117">Nawiasy klamrowe ({}) należy ująć wyrażenia rekordu.</span><span class="sxs-lookup"><span data-stu-id="0940c-117">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="0940c-118">Poniższy kod przedstawia wyrażenia rekordu, który inicjuje rekord z trzech elementów typu float z etykietami `x`, `y` i `z`.</span><span class="sxs-lookup"><span data-stu-id="0940c-118">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="0940c-119">Skrócona forma nie należy używać, jeśli może istnieć inny typ, który również ma takie same etykiety.</span><span class="sxs-lookup"><span data-stu-id="0940c-119">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="0940c-120">Etykiety najbardziej ostatnio deklarowanego typu pierwszeństwo wcześniej zadeklarowanego typu tak w powyższym przykładzie `mypoint3D` jest wywnioskowany jako `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="0940c-120">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="0940c-121">Można jawnie określić typ rekordu, zgodnie z poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="0940c-121">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="0940c-122">Metody mogą być definiowane dla typów rekordów, podobnie jak w przypadku typu klasy.</span><span class="sxs-lookup"><span data-stu-id="0940c-122">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="0940c-123">Tworzenie rekordów przy użyciu wyrażenia rekordu</span><span class="sxs-lookup"><span data-stu-id="0940c-123">Creating Records by Using Record Expressions</span></span>
<span data-ttu-id="0940c-124">Rekordy można zainicjować za pomocą etykiet, które są zdefiniowane w rekordzie.</span><span class="sxs-lookup"><span data-stu-id="0940c-124">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="0940c-125">To wyrażenie jest określany jako *rekordów wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="0940c-125">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="0940c-126">Użyj nawiasów klamrowych ujmij wyrażenie rekordu i użyj średnika jako ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="0940c-126">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="0940c-127">Poniższy przykład przedstawia sposób tworzenia rekordu.</span><span class="sxs-lookup"><span data-stu-id="0940c-127">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="0940c-128">Średnikami po ostatnim pola w wyrażeniu rekordu i w definicji typu są opcjonalne, niezależnie od tego, czy pola są wszystko w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="0940c-128">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="0940c-129">Po utworzeniu rekordu, należy podać wartości dla każdego pola.</span><span class="sxs-lookup"><span data-stu-id="0940c-129">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="0940c-130">Nie można odwołać się do wartości innych pól w wyrażeniu inicjowania dla dowolnego pola.</span><span class="sxs-lookup"><span data-stu-id="0940c-130">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="0940c-131">W poniższym kodzie typ `myRecord2` jest wywnioskowany na podstawie nazwy pól.</span><span class="sxs-lookup"><span data-stu-id="0940c-131">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="0940c-132">Opcjonalnie można jawnie określić nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="0940c-132">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="0940c-133">Innej formy konstrukcji rekordu może być przydatne podczas kopiowania istniejącego rekordu i prawdopodobnie zmieniania wartości pól.</span><span class="sxs-lookup"><span data-stu-id="0940c-133">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="0940c-134">Następujący wiersz kodu ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="0940c-134">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="0940c-135">Ta postać wyrażenia rekordu jest nazywany *kopiowanie i aktualizację wyrażenia rekordu*.</span><span class="sxs-lookup"><span data-stu-id="0940c-135">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="0940c-136">Rekordy są niezmienne domyślnie; można jednak łatwo utworzyć zmodyfikowanych rekordów przy użyciu wyrażenia Kopiuj i Aktualizuj.</span><span class="sxs-lookup"><span data-stu-id="0940c-136">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="0940c-137">Można również jawnie określić pola modyfikowalnego.</span><span class="sxs-lookup"><span data-stu-id="0940c-137">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="0940c-138">Nie używaj atrybutu DefaultValue z pola rekordu.</span><span class="sxs-lookup"><span data-stu-id="0940c-138">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="0940c-139">Lepszym rozwiązaniem jest zdefiniuj wystąpień rekordy z pola, które są inicjowane wartości domyślne, a następnie użyj kopii i zaktualizuj wyrażenia rekordu, aby ustawić wszystkie pola, które różnią się od wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="0940c-139">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

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

## <a name="pattern-matching-with-records"></a><span data-ttu-id="0940c-140">Dopasowywanie do wzorca z rekordów</span><span class="sxs-lookup"><span data-stu-id="0940c-140">Pattern Matching with Records</span></span>
<span data-ttu-id="0940c-141">Rekordy można łączyć z dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="0940c-141">Records can be used with pattern matching.</span></span> <span data-ttu-id="0940c-142">Można jawnie określić niektórych pól i podaj zmienne inne pola, które zostaną przypisane, jeśli pasują do.</span><span class="sxs-lookup"><span data-stu-id="0940c-142">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="0940c-143">Pokazano to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="0940c-143">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="0940c-144">Poniżej przedstawiono dane wyjściowe tego kodu.</span><span class="sxs-lookup"><span data-stu-id="0940c-144">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="0940c-145">Różnice między rekordów i klasy</span><span class="sxs-lookup"><span data-stu-id="0940c-145">Differences Between Records and Classes</span></span>
<span data-ttu-id="0940c-146">Pola rekordu różnią się od klasy automatycznie są one widoczne jako właściwości, oraz są one używane do tworzenia i kopiowania rekordów.</span><span class="sxs-lookup"><span data-stu-id="0940c-146">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="0940c-147">Konstrukcja rekordów również różni się od klasy konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="0940c-147">Record construction also differs from class construction.</span></span> <span data-ttu-id="0940c-148">W polu Typ rekordu nie można definiować konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0940c-148">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="0940c-149">Zamiast tego stosuje składni konstrukcji opisanych w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="0940c-149">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="0940c-150">Klasy nie mają bezpośredniego relacji między parametrami konstruktora, pól i właściwości.</span><span class="sxs-lookup"><span data-stu-id="0940c-150">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="0940c-151">Jak typy Unii i struktury rekordów mają semantykę równości strukturalnej.</span><span class="sxs-lookup"><span data-stu-id="0940c-151">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="0940c-152">Klasy mają odwołania semantykę równości.</span><span class="sxs-lookup"><span data-stu-id="0940c-152">Classes have reference equality semantics.</span></span> <span data-ttu-id="0940c-153">W poniższym przykładzie kodu pokazano to.</span><span class="sxs-lookup"><span data-stu-id="0940c-153">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="0940c-154">Jeśli piszesz ten sam kod z klasy obiektów dwóch klas może być nierówne dwóch wartości będzie reprezentować dwóch obiektów na stercie i czy można porównywać tylko adresy (o ile nie zastępuje typu klasy `System.Object.Equals` metody).</span><span class="sxs-lookup"><span data-stu-id="0940c-154">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="0940c-155">Jeśli konieczne odwołanie równości dla rekordów, Dodaj atrybut `[<ReferenceEquality>]` powyżej rekordu.</span><span class="sxs-lookup"><span data-stu-id="0940c-155">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="0940c-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0940c-156">See Also</span></span>
[<span data-ttu-id="0940c-157">Typy F#</span><span class="sxs-lookup"><span data-stu-id="0940c-157">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="0940c-158">Klasy</span><span class="sxs-lookup"><span data-stu-id="0940c-158">Classes</span></span>](classes.md)

[<span data-ttu-id="0940c-159">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="0940c-159">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="0940c-160">Równości odwołań</span><span class="sxs-lookup"><span data-stu-id="0940c-160">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[<span data-ttu-id="0940c-161">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="0940c-161">Pattern Matching</span></span>](pattern-matching.md)
