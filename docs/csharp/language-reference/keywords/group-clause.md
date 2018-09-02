---
title: group — Klauzula (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- group
- group_CSharpKeyword
helpviewer_keywords:
- group keyword [C#]
- group clause [C#]
ms.assetid: c817242e-b12c-4baa-a57e-73ee138f34d1
ms.openlocfilehash: 157bd07f3332883f010ef26ba920dae88276051b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393802"
---
# <a name="group-clause-c-reference"></a><span data-ttu-id="0ef35-102">group — Klauzula (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0ef35-102">group clause (C# Reference)</span></span>

<span data-ttu-id="0ef35-103">`group` Klauzula zwraca sekwencję <xref:System.Linq.IGrouping%602> obiektów zawierających zero lub więcej elementów, które odpowiadają wartości klucza dla grupy.</span><span class="sxs-lookup"><span data-stu-id="0ef35-103">The `group` clause returns a sequence of <xref:System.Linq.IGrouping%602> objects that contain zero or more items that match the key value for the group.</span></span> <span data-ttu-id="0ef35-104">Na przykład można pogrupować sekwencją ciągów, zgodnie z pierwszą literę każdego ciągu.</span><span class="sxs-lookup"><span data-stu-id="0ef35-104">For example, you can group a sequence of strings according to the first letter in each string.</span></span> <span data-ttu-id="0ef35-105">W takim przypadku pierwsza litera jest kluczem i ma typ [char](char.md)i jest przechowywany w `Key` właściwości każdego <xref:System.Linq.IGrouping%602> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0ef35-105">In this case, the first letter is the key and has a type [char](char.md), and is stored in the `Key` property of each <xref:System.Linq.IGrouping%602> object.</span></span> <span data-ttu-id="0ef35-106">Kompilator wnioskuje typ klucza.</span><span class="sxs-lookup"><span data-stu-id="0ef35-106">The compiler infers the type of the key.</span></span>

<span data-ttu-id="0ef35-107">Możesz zakończyć wyrażeniu zapytania z `group` klauzuli, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0ef35-107">You can end a query expression with a `group` clause, as shown in the following example:</span></span>

[!code-csharp[cscsrefQueryKeywords#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#10)]

<span data-ttu-id="0ef35-108">Jeśli chcesz wykonać operacje zapytań dodatkowe w każdej grupie, należy określić identyfikator tymczasowy, za pomocą [do](into.md) kontekstowego słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="0ef35-108">If you want to perform additional query operations on each group, you can specify a temporary identifier by using the [into](into.md) contextual keyword.</span></span> <span data-ttu-id="0ef35-109">Kiedy używasz `into`, należy kontynuować z zapytaniem, a po pewnym czasie Zakończ ją albo `select` instrukcji lub innego `group` klauzuli, jak pokazano w poniższym fragmencie:</span><span class="sxs-lookup"><span data-stu-id="0ef35-109">When you use `into`, you must continue with the query, and eventually end it with either a `select` statement or another `group` clause, as shown in the following excerpt:</span></span>

[!code-csharp[cscsrefQueryKeywords#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#11)]

<span data-ttu-id="0ef35-110">Bardziej kompletne przykłady stosowania `group` z lub bez `into` znajdują się w sekcji przykład tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="0ef35-110">More complete examples of the use of `group` with and without `into` are provided in the Example section of this article.</span></span>

## <a name="enumerating-the-results-of-a-group-query"></a><span data-ttu-id="0ef35-111">Wyliczanie wyników zapytania grupy</span><span class="sxs-lookup"><span data-stu-id="0ef35-111">Enumerating the results of a group query</span></span>

<span data-ttu-id="0ef35-112">Ponieważ <xref:System.Linq.IGrouping%602> obiekty utworzone przez `group` zapytania są zasadniczo listę list, korzystając z zagnieżdżonej [foreach](foreach-in.md) pętli, aby mieć dostęp do elementów w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="0ef35-112">Because the <xref:System.Linq.IGrouping%602> objects produced by a `group` query are essentially a list of lists, you must use a nested [foreach](foreach-in.md) loop to access the items in each group.</span></span> <span data-ttu-id="0ef35-113">Zewnętrzna pętla wykonuje iterację na klucze grupy, a wewnętrzną pętlę iteruje przez każdy element w samej grupy.</span><span class="sxs-lookup"><span data-stu-id="0ef35-113">The outer loop iterates over the group keys, and the inner loop iterates over each item in the group itself.</span></span> <span data-ttu-id="0ef35-114">Grupa może mieć klucza, ale żadne elementy.</span><span class="sxs-lookup"><span data-stu-id="0ef35-114">A group may have a key but no elements.</span></span> <span data-ttu-id="0ef35-115">Poniżej przedstawiono `foreach` pętli, która wykonuje zapytanie w poprzednich przykładach kodu:</span><span class="sxs-lookup"><span data-stu-id="0ef35-115">The following is the `foreach` loop that executes the query in the previous code examples:</span></span>

[!code-csharp[cscsrefQueryKeywords#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#12)]

## <a name="key-types"></a><span data-ttu-id="0ef35-116">Typy kluczy</span><span class="sxs-lookup"><span data-stu-id="0ef35-116">Key types</span></span>

<span data-ttu-id="0ef35-117">Klucze grupy mogą być dowolnego typu, takie jak ciąg, wbudowanego typu liczbowego lub zdefiniowanej przez użytkownika o nazwie typu lub typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="0ef35-117">Group keys can be any type, such as a string, a built-in numeric type, or a user-defined named type or anonymous type.</span></span>

### <a name="grouping-by-string"></a><span data-ttu-id="0ef35-118">Grupowanie według ciągu</span><span class="sxs-lookup"><span data-stu-id="0ef35-118">Grouping by string</span></span>

<span data-ttu-id="0ef35-119">W poprzednich przykładach kodu używany `char`.</span><span class="sxs-lookup"><span data-stu-id="0ef35-119">The previous code examples used a `char`.</span></span> <span data-ttu-id="0ef35-120">Klucza typu ciąg można łatwo określono zamiast tego, na przykład Pełna nazwa ostatnich:</span><span class="sxs-lookup"><span data-stu-id="0ef35-120">A string key could easily have been specified instead, for example the complete last name:</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

### <a name="grouping-by-bool"></a><span data-ttu-id="0ef35-121">Grupowanie według bool</span><span class="sxs-lookup"><span data-stu-id="0ef35-121">Grouping by bool</span></span>

<span data-ttu-id="0ef35-122">Poniższy przykład pokazuje użycie wartość bool klawisz aby podzielić wyniki na dwie grupy.</span><span class="sxs-lookup"><span data-stu-id="0ef35-122">The following example shows the use of a bool value for a key to divide the results into two groups.</span></span> <span data-ttu-id="0ef35-123">Należy pamiętać, że wartość jest generowany przez Podwyrażenie w `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0ef35-123">Note that the value is produced by a sub-expression in the `group` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#14)]

### <a name="grouping-by-numeric-range"></a><span data-ttu-id="0ef35-124">Grupowanie według zakresu liczbowego</span><span class="sxs-lookup"><span data-stu-id="0ef35-124">Grouping by numeric range</span></span>

<span data-ttu-id="0ef35-125">W następnym przykładzie użyto wyrażenia, aby utworzyć klucze grupy numeryczne, które reprezentują zakres percentyl.</span><span class="sxs-lookup"><span data-stu-id="0ef35-125">The next example uses an expression to create numeric group keys that represent a percentile range.</span></span> <span data-ttu-id="0ef35-126">Zwróć uwagę na użycie [umożliwiają](let-clause.md) jako wygodną lokalizację do przechowywania metodę wywołania wynik, dzięki czemu nie trzeba wywoływać metodę dwa razy w `group` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0ef35-126">Note the use of [let](let-clause.md) as a convenient location to store a method call result, so that you don't have to call the method two times in the `group` clause.</span></span> <span data-ttu-id="0ef35-127">Należy pamiętać, również w `group` klauzulę, aby uniknąć wyjątek "dzielenie przez zero" kod sprawdza, upewnij się, że Studenta, nie ma średnio o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="0ef35-127">Note also in the `group` clause that to avoid a "divide by zero" exception the code checks to make sure that the student doesn't have an average of zero.</span></span> <span data-ttu-id="0ef35-128">Aby uzyskać więcej informacji o tym, jak bezpiecznie używać metod w wyrażeniach zapytań, zobacz [porady: obsługa wyjątków w wyrażeniach zapytań](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0ef35-128">For more information about how to safely use methods in query expressions, see [How to: Handle Exceptions in Query Expressions](../../programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md).</span></span>

[!code-csharp[cscsrefQueryKeywords#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#15)]

### <a name="grouping-by-composite-keys"></a><span data-ttu-id="0ef35-129">Grupowanie według kluczy złożonych</span><span class="sxs-lookup"><span data-stu-id="0ef35-129">Grouping by composite keys</span></span>

<span data-ttu-id="0ef35-130">Umożliwia grupowanie elementów według więcej niż jeden klucz za pomocą klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="0ef35-130">Use a composite key when you want to group elements according to more than one key.</span></span> <span data-ttu-id="0ef35-131">Klucz złożony możesz utworzyć przy użyciu typu anonimowego lub typem nazwanym do przechowywania klucza elementu.</span><span class="sxs-lookup"><span data-stu-id="0ef35-131">You create a composite key by using an anonymous type or a named type to hold the key element.</span></span> <span data-ttu-id="0ef35-132">W poniższym przykładzie przyjęto założenie, że klasa `Person` został zadeklarowany za pomocą elementów członkowskich o nazwie `surname` i `city`.</span><span class="sxs-lookup"><span data-stu-id="0ef35-132">In the following example, assume that a class `Person` has been declared with members named `surname` and `city`.</span></span> <span data-ttu-id="0ef35-133">`group` Klauzuli powoduje, że ma zostać utworzony dla każdego zestawu osób z tej samej nazwisko i tym samym mieście osobnej grupy.</span><span class="sxs-lookup"><span data-stu-id="0ef35-133">The `group` clause causes a separate group to be created for each set of persons with the same last name and the same city.</span></span>

```csharp
group person by new {name = person.surname, city = person.city};
```

<span data-ttu-id="0ef35-134">Jeśli zmienna zapytania musi pomyślnie przejść do innej metody, należy użyć typu nazwanego.</span><span class="sxs-lookup"><span data-stu-id="0ef35-134">Use a named type if you must pass the query variable to another method.</span></span> <span data-ttu-id="0ef35-135">Utwórz klasę specjalnych kluczy przy użyciu automatycznie implementowanych właściwości, a następnie zastąpić <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0ef35-135">Create a special class using auto-implemented properties for the keys, and then override the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods.</span></span> <span data-ttu-id="0ef35-136">Można również użyć struktury, w którym to przypadku ściśle trzeba zastąpić te metody.</span><span class="sxs-lookup"><span data-stu-id="0ef35-136">You can also use a struct, in which case you do not strictly have to override those methods.</span></span> <span data-ttu-id="0ef35-137">Aby uzyskać więcej informacji, zobacz [porady: Implementowanie klasy Lightweight przy użyciu implemented Properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) i [porady: zapytanie o zduplikowane pliki w drzewie katalogu](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span><span class="sxs-lookup"><span data-stu-id="0ef35-137">For more information see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md) and [How to: Query for Duplicate Files in a Directory Tree](../../programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md).</span></span> <span data-ttu-id="0ef35-138">Ostatni artykuł zawiera przykładowy kod, który demonstruje sposób skorzystania z kluczem złożonym z typem nazwanym.</span><span class="sxs-lookup"><span data-stu-id="0ef35-138">The latter article has a code example that demonstrates how to use a composite key with a named type.</span></span>

## <a name="example"></a><span data-ttu-id="0ef35-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ef35-139">Example</span></span>

<span data-ttu-id="0ef35-140">Poniższy przykład pokazuje standardowego wzorca porządkowania danych źródłowych w grupach, stosowania logiki nie dodatkowych zapytania do grup.</span><span class="sxs-lookup"><span data-stu-id="0ef35-140">The following example shows the standard pattern for ordering source data into groups when no additional query logic is applied to the groups.</span></span> <span data-ttu-id="0ef35-141">Jest to grupa bez kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="0ef35-141">This is called a grouping without a continuation.</span></span> <span data-ttu-id="0ef35-142">Elementy w tablicy ciągów są pogrupowane według ich pierwszą literę.</span><span class="sxs-lookup"><span data-stu-id="0ef35-142">The elements in an array of strings are grouped according to their first letter.</span></span> <span data-ttu-id="0ef35-143">Wynik zapytania jest <xref:System.Linq.IGrouping%602> typu, który zawiera publiczny `Key` właściwości typu `char` i <xref:System.Collections.Generic.IEnumerable%601> kolekcji, która zawiera każdy element na grupowanie.</span><span class="sxs-lookup"><span data-stu-id="0ef35-143">The result of the query is an <xref:System.Linq.IGrouping%602> type that contains a public `Key` property of type `char` and an <xref:System.Collections.Generic.IEnumerable%601> collection that contains each item in the grouping.</span></span>

<span data-ttu-id="0ef35-144">Wynik `group` klauzula jest sekwencji.</span><span class="sxs-lookup"><span data-stu-id="0ef35-144">The result of a `group` clause is a sequence of sequences.</span></span> <span data-ttu-id="0ef35-145">W związku z tym, aby uzyskać dostęp do poszczególnych elementów w każdej grupie zwrócone, użyj zagnieżdżoną `foreach` pętli wewnątrz pętli, który iteruje po klucze grupy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0ef35-145">Therefore, to access the individual elements within each returned group, use a nested `foreach` loop inside the loop that iterates the group keys, as shown in the following example.</span></span>

[!code-csharp[cscsrefQueryKeywords#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#16)]

## <a name="example"></a><span data-ttu-id="0ef35-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ef35-146">Example</span></span>

<span data-ttu-id="0ef35-147">W tym przykładzie przedstawiono sposób wykonywania dodatkowej logiki w grupach, po ich utworzeniu, za pomocą *kontynuacji* z `into`.</span><span class="sxs-lookup"><span data-stu-id="0ef35-147">This example shows how to perform additional logic on the groups after you have created them, by using a *continuation* with `into`.</span></span> <span data-ttu-id="0ef35-148">Aby uzyskać więcej informacji, zobacz [do](into.md).</span><span class="sxs-lookup"><span data-stu-id="0ef35-148">For more information, see [into](into.md).</span></span> <span data-ttu-id="0ef35-149">Poniższy przykład wysyła zapytanie do każdej grupy, aby wybrać tylko te, których wartość klucza jest samogłosek.</span><span class="sxs-lookup"><span data-stu-id="0ef35-149">The following example queries each group to select only those whose key value is a vowel.</span></span>

[!code-csharp[cscsrefQueryKeywords#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#17)]

## <a name="remarks"></a><span data-ttu-id="0ef35-150">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ef35-150">Remarks</span></span>

<span data-ttu-id="0ef35-151">W czasie kompilacji `group` klauzule są tłumaczone na wywołania <xref:System.Linq.Enumerable.GroupBy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0ef35-151">At compile time, `group` clauses are translated into calls to the <xref:System.Linq.Enumerable.GroupBy%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ef35-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ef35-152">See also</span></span>

- <xref:System.Linq.IGrouping%602>  
- <xref:System.Linq.Enumerable.GroupBy%2A>  
- <xref:System.Linq.Enumerable.ThenBy%2A>  
- <xref:System.Linq.Enumerable.ThenByDescending%2A>  
- [<span data-ttu-id="0ef35-153">Słowa kluczowe zapytania</span><span class="sxs-lookup"><span data-stu-id="0ef35-153">Query Keywords</span></span>](query-keywords.md)  
- [<span data-ttu-id="0ef35-154">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0ef35-154">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)  
- [<span data-ttu-id="0ef35-155">Tworzenie grupy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="0ef35-155">Create a nested group</span></span>](../../linq/create-a-nested-group.md)  
- [<span data-ttu-id="0ef35-156">Grupowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="0ef35-156">Group query results</span></span>](../../linq/group-query-results.md)  
- [<span data-ttu-id="0ef35-157">Wykonanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="0ef35-157">Perform a subquery on a grouping operation</span></span>](../../linq/perform-a-subquery-on-a-grouping-operation.md)