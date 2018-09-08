---
title: Rekordy (F#)
description: 'Dowiedz się, jak rekordów F # reprezentują prostych wartości zagregowanych nazwanych wartości opcjonalnie wraz z elementów członkowskich.'
ms.date: 05/16/2016
ms.openlocfilehash: 6103d96b6b80a9e2ed168755958dbe800f7fa862
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128900"
---
# <a name="records"></a><span data-ttu-id="99aa8-103">Rekordy</span><span class="sxs-lookup"><span data-stu-id="99aa8-103">Records</span></span>

<span data-ttu-id="99aa8-104">Rekordy reprezentują prostych wartości zagregowanych nazwanych wartości opcjonalnie wraz z elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="99aa8-104">Records represent simple aggregates of named values, optionally with members.</span></span>  <span data-ttu-id="99aa8-105">Począwszy od F # 4.1, albo można typu struktury lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="99aa8-105">Starting with F# 4.1, they can either be structs or reference types.</span></span>  <span data-ttu-id="99aa8-106">Są one domyślnie typami odwołań.</span><span class="sxs-lookup"><span data-stu-id="99aa8-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="99aa8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="99aa8-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="99aa8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99aa8-108">Remarks</span></span>

<span data-ttu-id="99aa8-109">W poprzedniej składni *typename* jest nazwą typu rekordu *label1* i *etykiety 2* nazwy wartości, nazywane są *etykiety*, i *type1* i *type2* typy tych wartości.</span><span class="sxs-lookup"><span data-stu-id="99aa8-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="99aa8-110">*Lista elementów członkowskich* jest opcjonalna lista elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="99aa8-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="99aa8-111">Możesz użyć `[<Struct>]` atrybutu do utworzenia rekordu struktury, a nie rekord, który jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="99aa8-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="99aa8-112">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="99aa8-112">Following are some examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="99aa8-113">Po każdej etykiety w osobnym wierszu średnik jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="99aa8-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="99aa8-114">Można ustawić wartości w wyrażeniach, znane jako *rejestrowania wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="99aa8-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="99aa8-115">Kompilator wnioskuje typ z etykiet, używane (Jeśli etykiety wystarczająco różnią się od tych innych typów rekordów).</span><span class="sxs-lookup"><span data-stu-id="99aa8-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="99aa8-116">Nawiasy klamrowe ({}) powinno być rekord.</span><span class="sxs-lookup"><span data-stu-id="99aa8-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="99aa8-117">Poniższy kod pokazuje wyrażenie rekordów, które inicjuje rekord za pomocą trzech elementów float z etykietami `x`, `y` i `z`.</span><span class="sxs-lookup"><span data-stu-id="99aa8-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="99aa8-118">Nie należy używać formy skróconej, jeśli może być innym typem, który ma również tej samej etykiety.</span><span class="sxs-lookup"><span data-stu-id="99aa8-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="99aa8-119">Etykiety najbardziej niedawno zadeklarowanym typem pierwszeństwo wcześniej zadeklarowanej typu, więc w powyższym przykładzie `mypoint3D` jest `Point3D`.</span><span class="sxs-lookup"><span data-stu-id="99aa8-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="99aa8-120">Można jawnie określić typ rekordu, tak jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="99aa8-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="99aa8-121">Metody mogą być definiowane dla typów rekordów, podobnie jak w przypadku typu klasy.</span><span class="sxs-lookup"><span data-stu-id="99aa8-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="99aa8-122">Tworzenie rekordów za pomocą wyrażeń rekordów</span><span class="sxs-lookup"><span data-stu-id="99aa8-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="99aa8-123">Rekordy można zainicjować za pomocą etykiet, które są zdefiniowane w rekordzie.</span><span class="sxs-lookup"><span data-stu-id="99aa8-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="99aa8-124">Wyrażenie, które ten jest nazywany *rejestrowania wyrażenie*.</span><span class="sxs-lookup"><span data-stu-id="99aa8-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="99aa8-125">Powinno być rekord i użyj średnika jako ogranicznika, należy użyć nawiasów klamrowych.</span><span class="sxs-lookup"><span data-stu-id="99aa8-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="99aa8-126">Poniższy przykład pokazuje, jak utworzyć rekord.</span><span class="sxs-lookup"><span data-stu-id="99aa8-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="99aa8-127">Średnikami po ostatnim polu w wyrażeniu rekordu i w definicji typu są opcjonalne, niezależnie od tego, czy pola są wszystko w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="99aa8-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="99aa8-128">Podczas tworzenia rekordu należy podać wartości dla każdego pola.</span><span class="sxs-lookup"><span data-stu-id="99aa8-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="99aa8-129">Nie można odwołać się do wartości innych pól w wyrażeniu inicjowania dla dowolnego pola.</span><span class="sxs-lookup"><span data-stu-id="99aa8-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="99aa8-130">W poniższym kodzie typ `myRecord2` wynika z nazwy pól.</span><span class="sxs-lookup"><span data-stu-id="99aa8-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="99aa8-131">Opcjonalnie można jawnie określić nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="99aa8-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="99aa8-132">Inna forma konstrukcji rekord może być przydatne, kiedy trzeba skopiować istniejący rekord, a być może zmienić niektóre wartości pól.</span><span class="sxs-lookup"><span data-stu-id="99aa8-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="99aa8-133">Następujący wiersz kodu ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="99aa8-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="99aa8-134">Ta forma wyrażenia rekordu jest nazywany *kopiowanie i aktualizacja wyrażeń rekordów*.</span><span class="sxs-lookup"><span data-stu-id="99aa8-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="99aa8-135">Rekordy, które są niezmienne domyślnie; jednak można łatwo utworzyć zmodyfikowanych rekordów przy użyciu wyrażenia Kopiuj i Aktualizuj.</span><span class="sxs-lookup"><span data-stu-id="99aa8-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="99aa8-136">Można również jawnie określić mutable pola.</span><span class="sxs-lookup"><span data-stu-id="99aa8-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="99aa8-137">Nie używaj atrybutu DefaultValue przy użyciu pól rekordu.</span><span class="sxs-lookup"><span data-stu-id="99aa8-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="99aa8-138">Lepszym rozwiązaniem jest zdefiniowanie wystąpieniami domyślnymi rekordów z polami, które są inicjowane do wartości domyślnych, a następnie użyć kopii i zaktualizować rekord wyrażenia, aby ustawić wszystkie pola, które różnią się od wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="99aa8-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
    { Field1 : int
      Field2 : int }

let defaultRecord1 = { Field1 = 0; Field2 = 0 }
let defaultRecord2 = { Field1 = 1; Field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with Field2 = 42 }
```

## <a name="pattern-matching-with-records"></a><span data-ttu-id="99aa8-139">Dopasowywanie wzorca z rekordów</span><span class="sxs-lookup"><span data-stu-id="99aa8-139">Pattern Matching with Records</span></span>

<span data-ttu-id="99aa8-140">Rekordy można łączyć z dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="99aa8-140">Records can be used with pattern matching.</span></span> <span data-ttu-id="99aa8-141">Można jawnie określić niektóre pola i podać zmienne dla innych pól, które zostaną przypisane po wystąpieniu dopasowania.</span><span class="sxs-lookup"><span data-stu-id="99aa8-141">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="99aa8-142">Pokazano to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="99aa8-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="99aa8-143">Dane wyjściowe tego kodu jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="99aa8-143">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="99aa8-144">Różnice między rekordami i klasy</span><span class="sxs-lookup"><span data-stu-id="99aa8-144">Differences Between Records and Classes</span></span>

<span data-ttu-id="99aa8-145">Pola rekordu różnią się od klas są one automatycznie dostępne jako właściwości i są one używane do tworzenia i kopiowania rekordów.</span><span class="sxs-lookup"><span data-stu-id="99aa8-145">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="99aa8-146">Konstrukcja rekordów również różni się od konstrukcji klasy.</span><span class="sxs-lookup"><span data-stu-id="99aa8-146">Record construction also differs from class construction.</span></span> <span data-ttu-id="99aa8-147">W polu Typ rekordu nie można zdefiniować Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="99aa8-147">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="99aa8-148">Zamiast tego składni konstrukcji opisane w tym temacie mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="99aa8-148">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="99aa8-149">Klasy nie mają bezpośredniego relacji między parametry konstruktora, pola i właściwości.</span><span class="sxs-lookup"><span data-stu-id="99aa8-149">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="99aa8-150">Podobnie jak typy Unii i struktury rekordy mają semantykę porównania strukturalnego.</span><span class="sxs-lookup"><span data-stu-id="99aa8-150">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="99aa8-151">Klasy mają odniesienie równości semantyki.</span><span class="sxs-lookup"><span data-stu-id="99aa8-151">Classes have reference equality semantics.</span></span> <span data-ttu-id="99aa8-152">Poniższy przykład kodu pokazuje to.</span><span class="sxs-lookup"><span data-stu-id="99aa8-152">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="99aa8-153">Dane wyjściowe tego kodu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="99aa8-153">The output of this code is as follows:</span></span>

```
The records are equal.
```

<span data-ttu-id="99aa8-154">Jeśli piszesz ten sam kod z klasami, obiektów dwóch klas będzie nierówne, ponieważ dwie wartości reprezentuje dwa obiekty na stosie i będzie można porównać tylko adresy (o ile nie zastępuje typ klasy `System.Object.Equals` metody).</span><span class="sxs-lookup"><span data-stu-id="99aa8-154">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="99aa8-155">Jeśli potrzebujesz odwołać równości dla rekordów, Dodaj atrybut `[<ReferenceEquality>]` powyżej rekordu.</span><span class="sxs-lookup"><span data-stu-id="99aa8-155">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="99aa8-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99aa8-156">See also</span></span>

- [<span data-ttu-id="99aa8-157">Typy F#</span><span class="sxs-lookup"><span data-stu-id="99aa8-157">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="99aa8-158">Klasy</span><span class="sxs-lookup"><span data-stu-id="99aa8-158">Classes</span></span>](classes.md)
- [<span data-ttu-id="99aa8-159">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="99aa8-159">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="99aa8-160">Równość odniesienia</span><span class="sxs-lookup"><span data-stu-id="99aa8-160">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="99aa8-161">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="99aa8-161">Pattern Matching</span></span>](pattern-matching.md)
