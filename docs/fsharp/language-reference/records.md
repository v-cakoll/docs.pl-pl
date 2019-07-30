---
title: Rekordy
description: Dowiedz F# się, jak rekordy reprezentują proste Agregowanie wartości nazwanych, opcjonalnie z elementami członkowskimi.
ms.date: 06/09/2019
ms.openlocfilehash: d92a1a7517e5b05ee687926df29f33fab123b4dd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627283"
---
# <a name="records"></a><span data-ttu-id="ac9fc-103">Rekordy</span><span class="sxs-lookup"><span data-stu-id="ac9fc-103">Records</span></span>

<span data-ttu-id="ac9fc-104">Rekordy reprezentują proste Agregowanie wartości nazwanych, opcjonalnie z elementami członkowskimi.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-104">Records represent simple aggregates of named values, optionally with members.</span></span> <span data-ttu-id="ac9fc-105">Mogą to być struktury lub typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-105">They can either be structs or reference types.</span></span>  <span data-ttu-id="ac9fc-106">Domyślnie są to typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-106">They are reference types by default.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac9fc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac9fc-107">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] typename =
    { [ mutable ] label1 : type1;
      [ mutable ] label2 : type2;
      ... }
    [ member-list ]
```

## <a name="remarks"></a><span data-ttu-id="ac9fc-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac9fc-108">Remarks</span></span>

<span data-ttu-id="ac9fc-109">W poprzedniej składni, *TypeName* jest nazwą typu rekordu, *Label1* i *etykiety 2* są nazwami wartości, zwanymi *etykietami*, a *Type1* i *Type2* są typami tych wartości.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-109">In the previous syntax, *typename* is the name of the record type, *label1* and *label2* are names of values, referred to as *labels*, and *type1* and *type2* are the types of these values.</span></span> <span data-ttu-id="ac9fc-110">*Lista elementów członkowskich* jest opcjonalną listą elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-110">*member-list* is the optional list of members for the type.</span></span>  <span data-ttu-id="ac9fc-111">Możesz użyć atrybutu, `[<Struct>]` aby utworzyć rekord struktury, a nie rekord, który jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-111">You can use the `[<Struct>]` attribute to create a struct record rather than a record which is a reference type.</span></span>

<span data-ttu-id="ac9fc-112">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-112">Following are some examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

<span data-ttu-id="ac9fc-113">Gdy każda etykieta znajduje się w osobnym wierszu, średnik jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-113">When each label is on a separate line, the semicolon is optional.</span></span>

<span data-ttu-id="ac9fc-114">Można ustawić wartości w wyrażeniach nazywanych *wyrażeniami rekordów*.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-114">You can set values in expressions known as *record expressions*.</span></span> <span data-ttu-id="ac9fc-115">Kompilator wnioskuje typ z użytych etykiet (Jeśli etykiety są wystarczająco odrębne od tych z innych typów rekordów).</span><span class="sxs-lookup"><span data-stu-id="ac9fc-115">The compiler infers the type from the labels used (if the labels are sufficiently distinct from those of other record types).</span></span> <span data-ttu-id="ac9fc-116">Nawiasy klamrowe ({}) otaczają wyrażenie rekordu.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-116">Braces ({ }) enclose the record expression.</span></span> <span data-ttu-id="ac9fc-117">Poniższy kod przedstawia wyrażenie rekordu, które inicjuje rekord z trzema elementami zmiennoprzecinkowymi z `x`etykietami `y` i `z`.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-117">The following code shows a record expression that initializes a record with three float elements with labels `x`, `y` and `z`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

<span data-ttu-id="ac9fc-118">Nie używaj skróconej formy, jeśli może istnieć inny typ, który ma również te same etykiety.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-118">Do not use the shortened form if there could be another type that also has the same labels.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

<span data-ttu-id="ac9fc-119">Etykiety ostatnio zadeklarowanego typu mają pierwszeństwo przed poprzednimi zadeklarowanymi typem, więc w poprzednim przykładzie `mypoint3D` jest wywnioskowane. `Point3D`</span><span class="sxs-lookup"><span data-stu-id="ac9fc-119">The labels of the most recently declared type take precedence over those of the previously declared type, so in the preceding example, `mypoint3D` is inferred to be `Point3D`.</span></span> <span data-ttu-id="ac9fc-120">Można jawnie określić typ rekordu, jak w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-120">You can explicitly specify the record type, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

<span data-ttu-id="ac9fc-121">Metody można definiować dla typów rekordów, tak jak w przypadku typów klas.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-121">Methods can be defined for record types just as for class types.</span></span>

## <a name="creating-records-by-using-record-expressions"></a><span data-ttu-id="ac9fc-122">Tworzenie rekordów przy użyciu wyrażeń rekordu</span><span class="sxs-lookup"><span data-stu-id="ac9fc-122">Creating Records by Using Record Expressions</span></span>

<span data-ttu-id="ac9fc-123">Rekordy można inicjować przy użyciu etykiet, które są zdefiniowane w rekordzie.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-123">You can initialize records by using the labels that are defined in the record.</span></span> <span data-ttu-id="ac9fc-124">Wyrażenie, które jest nazywane *wyrażeniem rekordu*.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-124">An expression that does this is referred to as a *record expression*.</span></span> <span data-ttu-id="ac9fc-125">Użyj nawiasów klamrowych, aby ująć wyrażenie rekordu i użyć średnika jako ogranicznika.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-125">Use braces to enclose the record expression and use the semicolon as a delimiter.</span></span>

<span data-ttu-id="ac9fc-126">Poniższy przykład pokazuje, jak utworzyć rekord.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-126">The following example shows how to create a record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

<span data-ttu-id="ac9fc-127">Średniki po ostatnim polu w wyrażeniu rekordu i w definicji typu są opcjonalne, bez względu na to, czy wszystkie pola znajdują się w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-127">The semicolons after the last field in the record expression and in the type definition are optional, regardless of whether the fields are all in one line.</span></span>

<span data-ttu-id="ac9fc-128">Podczas tworzenia rekordu należy podać wartości dla każdego pola.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-128">When you create a record, you must supply values for each field.</span></span> <span data-ttu-id="ac9fc-129">Nie można odwołać się do wartości innych pól w wyrażeniu inicjalizacji dla każdego pola.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-129">You cannot refer to the values of other fields in the initialization expression for any field.</span></span>

<span data-ttu-id="ac9fc-130">W poniższym kodzie typ `myRecord2` jest wywnioskowany na podstawie nazw pól.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-130">In the following code, the type of `myRecord2` is inferred from the names of the fields.</span></span> <span data-ttu-id="ac9fc-131">Opcjonalnie można jawnie określić nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-131">Optionally, you can specify the type name explicitly.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="ac9fc-132">Inna forma konstruowania rekordów może być przydatna, gdy trzeba skopiować istniejący rekord i ewentualnie zmienić niektóre wartości pól.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-132">Another form of record construction can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span> <span data-ttu-id="ac9fc-133">Ilustruje to poniższy wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-133">The following line of code illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

<span data-ttu-id="ac9fc-134">Ta forma wyrażenia rekordu jest nazywana wyrażeniem *Copy i Update Record*.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-134">This form of the record expression is called the *copy and update record expression*.</span></span>

<span data-ttu-id="ac9fc-135">Rekordy są domyślnie niezmienne; można jednak łatwo tworzyć zmodyfikowane rekordy przy użyciu wyrażenia Copy i Update.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-135">Records are immutable by default; however, you can easily create modified records by using a copy and update expression.</span></span> <span data-ttu-id="ac9fc-136">Można również jawnie określić pole modyfikowalne.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-136">You can also explicitly specify a mutable field.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

<span data-ttu-id="ac9fc-137">Nie używaj atrybutu DefaultValue z polami rekordów.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-137">Don't use the DefaultValue attribute with record fields.</span></span> <span data-ttu-id="ac9fc-138">Lepszym rozwiązaniem jest zdefiniowanie domyślnych wystąpień rekordów z polami, które są inicjowane do wartości domyślnych, a następnie użycie wyrażenia Kopiuj i Aktualizuj rekord, aby ustawić wszystkie pola, które różnią się od wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-138">A better approach is to define default instances of records with fields that are initialized to default values and then use a copy and update record expression to set any fields that differ from the default values.</span></span>

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

## <a name="creating-mutually-recursive-records"></a><span data-ttu-id="ac9fc-139">Tworzenie wzajemnie rekurencyjnych rekordów</span><span class="sxs-lookup"><span data-stu-id="ac9fc-139">Creating Mutually Recursive Records</span></span>

<span data-ttu-id="ac9fc-140">Czasami podczas tworzenia rekordu można zależeć od innego typu, który ma zostać zdefiniowany później.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-140">Sometime when creating a record, you may want to have it depend on another type that you would like to define afterwards.</span></span> <span data-ttu-id="ac9fc-141">Jest to błąd kompilacji, chyba że zostanie zdefiniowany typ rekordu, który ma być wzajemnie cykliczne.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-141">This is a compile error unless you define the record types to be mutually recursive.</span></span>

<span data-ttu-id="ac9fc-142">Definiowanie wzajemnie cyklicznych rekordów odbywa się za `and` pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-142">Defining mutually recursive records is done with the `and` keyword.</span></span> <span data-ttu-id="ac9fc-143">Dzięki temu można połączyć 2 lub więcej typów rekordów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-143">This lets you link 2 or more record types together.</span></span>

<span data-ttu-id="ac9fc-144">Na przykład poniższy kod definiuje `Person` a i `Address` typ jako wzajemnie cyklicznie:</span><span class="sxs-lookup"><span data-stu-id="ac9fc-144">For example, the following code defines a `Person` and `Address` type as mutually recursive:</span></span>

```fsharp
// Create a Person type and use the Address type that is not defined
type Person =
  { Name: string
    Age: int
    Address: Address }
// Define the Address type which is used in the Person record
and Address =
  { Line1: string
    Line2: string
    PostCode: string }
```

<span data-ttu-id="ac9fc-145">Jeśli zdefiniowano poprzedni przykład bez `and` słowa kluczowego, nie zostanie on skompilowany.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-145">If you were to define the previous example without the `and` keyword, then it would not compile.</span></span> <span data-ttu-id="ac9fc-146">`and` Słowo kluczowe jest wymagane dla wzajemnie cyklicznych definicji.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-146">The `and` keyword is required for mutually recursive definitions.</span></span>

## <a name="pattern-matching-with-records"></a><span data-ttu-id="ac9fc-147">Dopasowanie wzorca z rekordami</span><span class="sxs-lookup"><span data-stu-id="ac9fc-147">Pattern Matching with Records</span></span>

<span data-ttu-id="ac9fc-148">Rekordy mogą być używane z dopasowywaniem do wzorca.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-148">Records can be used with pattern matching.</span></span> <span data-ttu-id="ac9fc-149">Niektóre pola można określić jawnie i podać zmienne dla innych pól, które będą przypisywane w przypadku wystąpienia dopasowania.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-149">You can specify some fields explicitly and provide variables for other fields that will be assigned when a match occurs.</span></span> <span data-ttu-id="ac9fc-150">Pokazano to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-150">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

<span data-ttu-id="ac9fc-151">Dane wyjściowe tego kodu są następujące.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-151">The output of this code is as follows.</span></span>

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a><span data-ttu-id="ac9fc-152">Różnice między rekordami i klasami</span><span class="sxs-lookup"><span data-stu-id="ac9fc-152">Differences Between Records and Classes</span></span>

<span data-ttu-id="ac9fc-153">Pola rekordów różnią się od klas, które są automatycznie uwidaczniane jako właściwości i są używane podczas tworzenia i kopiowania rekordów.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-153">Record fields differ from classes in that they are automatically exposed as properties, and they are used in the creation and copying of records.</span></span> <span data-ttu-id="ac9fc-154">Konstrukcja rekordu różni się także od konstrukcji klasy.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-154">Record construction also differs from class construction.</span></span> <span data-ttu-id="ac9fc-155">W typie rekordu nie można zdefiniować konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-155">In a record type, you cannot define a constructor.</span></span> <span data-ttu-id="ac9fc-156">Zamiast tego stosuje się składnię konstrukcyjną opisaną w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-156">Instead, the construction syntax described in this topic applies.</span></span> <span data-ttu-id="ac9fc-157">Klasy nie mają bezpośredniej relacji między parametrami konstruktora, polami i właściwościami.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-157">Classes have no direct relationship between constructor parameters, fields, and properties.</span></span>

<span data-ttu-id="ac9fc-158">Podobnie jak w przypadku typów Unii i struktury, rekordy mają semantykę równości strukturalnej.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-158">Like union and structure types, records have structural equality semantics.</span></span> <span data-ttu-id="ac9fc-159">Klasy mają semantykę równości odwołań.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-159">Classes have reference equality semantics.</span></span> <span data-ttu-id="ac9fc-160">Poniższy przykład kodu demonstruje ten sposób.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-160">The following code example demonstrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

<span data-ttu-id="ac9fc-161">Dane wyjściowe tego kodu są następujące:</span><span class="sxs-lookup"><span data-stu-id="ac9fc-161">The output of this code is as follows:</span></span>

```
The records are equal.
```

<span data-ttu-id="ac9fc-162">Jeśli piszesz ten sam kod z klasami, obiekty obu klas byłyby nierówne, ponieważ dwie wartości przedstawiają dwa obiekty na stercie i porównywane są tylko te adresy (chyba że typ klasy zastępuje `System.Object.Equals` metodę).</span><span class="sxs-lookup"><span data-stu-id="ac9fc-162">If you write the same code with classes, the two class objects would be unequal because the two values would represent two objects on the heap and only the addresses would be compared (unless the class type overrides the `System.Object.Equals` method).</span></span>

<span data-ttu-id="ac9fc-163">Jeśli potrzebujesz równości odwołań dla rekordów, Dodaj atrybut `[<ReferenceEquality>]` powyżej rekordu.</span><span class="sxs-lookup"><span data-stu-id="ac9fc-163">If you need reference equality for records, add the attribute `[<ReferenceEquality>]` above the record.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac9fc-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac9fc-164">See also</span></span>

- [<span data-ttu-id="ac9fc-165">Typy F#</span><span class="sxs-lookup"><span data-stu-id="ac9fc-165">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="ac9fc-166">Klasy</span><span class="sxs-lookup"><span data-stu-id="ac9fc-166">Classes</span></span>](classes.md)
- [<span data-ttu-id="ac9fc-167">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="ac9fc-167">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="ac9fc-168">Odwołanie — równość</span><span class="sxs-lookup"><span data-stu-id="ac9fc-168">Reference-Equality</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)
- [<span data-ttu-id="ac9fc-169">Dopasowanie do wzorca</span><span class="sxs-lookup"><span data-stu-id="ac9fc-169">Pattern Matching</span></span>](pattern-matching.md)
