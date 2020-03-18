---
title: klauzula grupy — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 75a366ec24e4e48af7e87d3372950aad8d76435b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713470"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="df595-102">group — Klauzula (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="df595-102">group clause (C# Reference)</span></span>

<span data-ttu-id="df595-103">Klauzula `group` zwraca sekwencję <xref:System.Linq.IGrouping%602> obiektów, które zawierają zero lub więcej elementów, które pasują do wartości klucza dla grupy.</span><span class="sxs-lookup"><span data-stu-id="df595-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="df595-104">Na przykład można grupować sekwencję ciągów zgodnie z pierwszą literą w każdym ciągu.</span><span class="sxs-lookup"><span data-stu-id="df595-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="df595-105">W takim przypadku pierwsza litera jest kluczem i ma [znak](../builtin-types/char.md)typu i jest przechowywana we `Key` właściwości każdego <xref:System.Linq.IGrouping%602> obiektu.</span><span class="sxs-lookup"><span data-stu-id="df595-105">In this case, the first letter is the key and has a type [char](../builtin-types/char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="df595-106">Kompilator wywnioskuje typ klucza.</span><span class="sxs-lookup"><span data-stu-id="df595-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="df595-107">Wyrażenie kwerendy można zakończyć `group` klauzulą, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="df595-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="df595-108">Jeśli chcesz wykonać dodatkowe operacje kwerendy dla każdej grupy, możesz określić tymczasowy identyfikator za pomocą słowa kluczowego [w](into.md) kontekście.</span><span class="sxs-lookup"><span data-stu-id="df595-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="df595-109">Użycie `into`należy kontynuować kwerendę, a następnie zakończyć ją `select` instrukcją `group` lub inną klauzulą, jak pokazano w poniższym fragmencie:</span><span class="sxs-lookup"><span data-stu-id="df595-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="df595-110">Pełniejsze przykłady użycia `group` z i `into` bez znajdują się w sekcji Przykład tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="df595-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="df595-111">Wyliczanie wyników kwerendy grupowej</span><span class="sxs-lookup"><span data-stu-id="df595-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="df595-112">Ponieważ <xref:System.Linq.IGrouping%602> obiekty tworzone `group` przez kwerendę są zasadniczo listę list, należy użyć zagnieżdżonych [foreach](foreach-in.md) pętli, aby uzyskać dostęp do elementów w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="df595-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="df595-113">Zewnętrzna pętla itere nad kluczami grupy, a wewnętrzna pętla iteuje nad każdym elementem w samej grupie.</span><span class="sxs-lookup"><span data-stu-id="df595-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="df595-114">Grupa może mieć klucz, ale nie ma elementów.</span><span class="sxs-lookup"><span data-stu-id="df595-114">A group may have a key but no elements.</span></span> <span data-ttu-id="df595-115">Poniżej przedstawiono `foreach` pętlę, która wykonuje kwerendę w poprzednich przykładach kodu:</span><span class="sxs-lookup"><span data-stu-id="df595-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="df595-116">Typy kluczy</span><span class="sxs-lookup"><span data-stu-id="df595-116">Key types</span></span>

<span data-ttu-id="df595-117">Klucze grupy mogą być dowolnym typem, takim jak ciąg, wbudowany typ liczbowy lub zdefiniowany przez użytkownika nazwany typ lub typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="df595-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="df595-118">Grupowanie według ciągów</span><span class="sxs-lookup"><span data-stu-id="df595-118">Grouping by string</span></span>

<span data-ttu-id="df595-119">W poprzednich przykładach `char`kodu użyto pliku .</span><span class="sxs-lookup"><span data-stu-id="df595-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="df595-120">Zamiast tego można łatwo określić klucz ciągu, na przykład pełne nazwisko:</span><span class="sxs-lookup"><span data-stu-id="df595-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="df595-121">Grupowanie według bool</span><span class="sxs-lookup"><span data-stu-id="df595-121">Grouping by bool</span></span>

<span data-ttu-id="df595-122">W poniższym przykładzie przedstawiono użycie wartości bool dla klucza, aby podzielić wyniki na dwie grupy.</span><span class="sxs-lookup"><span data-stu-id="df595-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="df595-123">Należy zauważyć, że wartość jest tworzona `group` przez wyrażenie podrzędne w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="df595-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="df595-124">Grupowanie według zakresu liczbowego</span><span class="sxs-lookup"><span data-stu-id="df595-124">Grouping by numeric range</span></span>

<span data-ttu-id="df595-125">W następnym przykładzie użyto wyrażenia do utworzenia kluczy grupy numerycznej, które reprezentują zakres percentyla.</span><span class="sxs-lookup"><span data-stu-id="df595-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="df595-126">Należy zwrócić uwagę na użycie [let](let-clause.md) jako dogodną lokalizację do przechowywania wyniku wywołania metody, dzięki czemu nie trzeba wywołać metodę dwa razy w klauzuli. `group`</span><span class="sxs-lookup"><span data-stu-id="df595-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="df595-127">Aby uzyskać więcej informacji na temat bezpiecznego używania metod w wyrażeniach kwerend, zobacz [Obsługa wyjątków w wyrażeniach kwerend .](../../linq/handle-exceptions-in-query-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="df595-127">For more information about how to safely use methods in query expressions, see [Handle exceptions in query expressions](../../linq/handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="df595-128">Grupowanie według kluczy złożonych</span><span class="sxs-lookup"><span data-stu-id="df595-128">Grouping by composite keys</span></span>

<span data-ttu-id="df595-129">Klucz złożony należy użyć, aby pogrupować elementy zgodnie z więcej niż jednym kluczem.</span><span class="sxs-lookup"><span data-stu-id="df595-129">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="df595-130">Klucz złożony można utworzyć przy użyciu typu anonimowego lub nazwanego typu do przechowywania elementu klucza.</span><span class="sxs-lookup"><span data-stu-id="df595-130">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="df595-131">W poniższym przykładzie załóżmy, że `Person` klasa `surname` `city`została zadeklarowana z członkami o nazwie i .</span><span class="sxs-lookup"><span data-stu-id="df595-131">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="df595-132">Klauzula `group` powoduje utworzenie oddzielnej grupy dla każdego zestawu osób o tym samym nazwisku i tym samym mieście.</span><span class="sxs-lookup"><span data-stu-id="df595-132">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="df595-133">Użyj nazwanego typu, jeśli zmienna kwerendy musi zostać przekazana innej metodzie.</span><span class="sxs-lookup"><span data-stu-id="df595-133">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="df595-134">Utwórz specjalną klasę przy użyciu właściwości implementowane automatycznie dla <xref:System.Object.Equals%2A> kluczy, a następnie zastąpić i <xref:System.Object.GetHashCode%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="df595-134">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="df595-135">Można również użyć struktury, w którym to przypadku nie trzeba ściśle zastąpić te metody.</span><span class="sxs-lookup"><span data-stu-id="df595-135">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="df595-136">Aby uzyskać więcej informacji, zobacz [Jak zaimplementować klasę lekką z właściwościami zaimplementowanymi automatycznie](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) i Jak [wysyłać zapytania o zduplikowane pliki w drzewie katalogów](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="df595-136">For more information see [How to implement a lightweight class with auto-implemented properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to query for duplicate files in a directory tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="df595-137">Ten ostatni artykuł zawiera przykład kodu, który pokazuje, jak używać klucza złożonego o nazwanym typie.</span><span class="sxs-lookup"><span data-stu-id="df595-137">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="df595-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="df595-138">Example</span></span>

<span data-ttu-id="df595-139">W poniższym przykładzie przedstawiono standardowy wzorzec do porządkowania danych źródłowych w grupy, gdy do grup nie jest stosowana żadna dodatkowa logika kwerendy.</span><span class="sxs-lookup"><span data-stu-id="df595-139">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="df595-140">Nazywa się to grupowaniem bez kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="df595-140">This is called a grouping without a continuation.</span></span> <span data-ttu-id="df595-141">Elementy w tablicy ciągów są grupowane według ich pierwszej litery.</span><span class="sxs-lookup"><span data-stu-id="df595-141">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="df595-142">Wynik kwerendy jest <xref:System.Linq.IGrouping%602> typem, który `Key` zawiera `char` właściwość <xref:System.Collections.Generic.IEnumerable%601> publiczną typu i kolekcji, która zawiera każdy element w grupowaniu.</span><span class="sxs-lookup"><span data-stu-id="df595-142">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="df595-143">Wynik `group` klauzuli jest sekwencja sekwencji.</span><span class="sxs-lookup"><span data-stu-id="df595-143">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="df595-144">W związku z tym, aby uzyskać dostęp do `foreach` poszczególnych elementów w każdej zwróconej grupy, należy użyć pętli zagnieżdżonej wewnątrz pętli, która iteruje klucze grupy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="df595-144">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="df595-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="df595-145">Example</span></span>

<span data-ttu-id="df595-146">W tym przykładzie pokazano, jak wykonać dodatkową logikę na grupach po ich utworzeniu, przy użyciu *kontynuacji* z . `into`</span><span class="sxs-lookup"><span data-stu-id="df595-146">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="df595-147">Aby uzyskać więcej informacji, zobacz [w](into.md).</span><span class="sxs-lookup"><span data-stu-id="df595-147">For more information, see [into](into.md).</span></span> <span data-ttu-id="df595-148">Poniższy przykład wysyła kwerendy każdej grupy, aby wybrać tylko te, których wartość klucza jest samogłoska.</span><span class="sxs-lookup"><span data-stu-id="df595-148">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="df595-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df595-149">Remarks</span></span>

<span data-ttu-id="df595-150">W czasie kompilacji `group` klauzule są tłumaczone <xref:System.Linq.Enumerable.GroupBy%2A> na wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="df595-150">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="df595-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df595-151">See also</span></span>

- <xref:System.Linq.IGrouping%602>
- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.Enumerable.ThenBy%2A>
- <xref:System.Linq.Enumerable.ThenByDescending%2A>
- [<span data-ttu-id="df595-152">Słowa kluczowe zapytania</span><span class="sxs-lookup"><span data-stu-id="df595-152">Query Keywords</span></span>](query-keywords.md)
- [<span data-ttu-id="df595-153">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="df595-153">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="df595-154">Tworzenie grupy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="df595-154">Create a nested group</span></span>](../../linq/create-a-nested-group.md)
- [<span data-ttu-id="df595-155">Grupowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="df595-155">Group query results</span></span>](../../linq/group-query-results.md)
- [<span data-ttu-id="df595-156">Wykonywanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="df595-156">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)
