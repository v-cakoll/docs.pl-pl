---
title: Grupowanie wyników zapytania (LINQ w C#)
description: Dowiedz się, jak należy zgrupować wyniki za pomocą LINQ w C#.
ms.date: 12/1/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: f768718cb1435efdc67791612776c9e9ce2b14b8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552325"
---
# <a name="group-query-results"></a><span data-ttu-id="dc850-103">Grupowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="dc850-103">Group query results</span></span>

<span data-ttu-id="dc850-104">Grupowanie jest jednym z najbardziej zaawansowanych funkcji zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="dc850-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="dc850-105">W poniższych przykładach pokazano sposób grupowania danych na różne sposoby:</span><span class="sxs-lookup"><span data-stu-id="dc850-105">The following examples show how to group data in various ways:</span></span>

- <span data-ttu-id="dc850-106">Według jedną właściwość.</span><span class="sxs-lookup"><span data-stu-id="dc850-106">By a single property.</span></span>

- <span data-ttu-id="dc850-107">Przez pierwszą literę właściwość ciągu.</span><span class="sxs-lookup"><span data-stu-id="dc850-107">By the first letter of a string property.</span></span>

- <span data-ttu-id="dc850-108">Obliczona zakresu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="dc850-108">By a computed numeric range.</span></span>

- <span data-ttu-id="dc850-109">Logiczną predykat lub innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="dc850-109">By Boolean predicate or other expression.</span></span>

- <span data-ttu-id="dc850-110">Przy użyciu klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="dc850-110">By a compound key.</span></span>

<span data-ttu-id="dc850-111">Ponadto ostatnie dwa zapytania projektu ich wyniki w nowym typem anonimowym, który zawiera tylko student imienia i nazwiska.</span><span class="sxs-lookup"><span data-stu-id="dc850-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="dc850-112">Aby uzyskać więcej informacji, zobacz [group — klauzula](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="dc850-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="dc850-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc850-113">Example</span></span>

<span data-ttu-id="dc850-114">Wszystkie przykłady w tym temacie, użyj następujących źródeł danych i klasy pomocnika.</span><span class="sxs-lookup"><span data-stu-id="dc850-114">All the examples in this topic use the following helper classes and data sources.</span></span>

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a><span data-ttu-id="dc850-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc850-115">Example</span></span>

<span data-ttu-id="dc850-116">Poniższy przykład pokazuje, jak należy zgrupować elementy źródłowe przy użyciu pojedynczej właściwości elementu jako klucz grupy.</span><span class="sxs-lookup"><span data-stu-id="dc850-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="dc850-117">W tym przypadku jest klucz `string`, Nazwisko ucznia.</span><span class="sxs-lookup"><span data-stu-id="dc850-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="dc850-118">Istnieje również możliwość użycia klucza podciąg.</span><span class="sxs-lookup"><span data-stu-id="dc850-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="dc850-119">W operacji grupowania używa domyślny moduł porównujący równość dla typu.</span><span class="sxs-lookup"><span data-stu-id="dc850-119">The grouping operation uses the default equality comparer for the type.</span></span>

<span data-ttu-id="dc850-120">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="dc850-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="dc850-121">Zmień instrukcji wywołujące w `Main` metody `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="dc850-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a><span data-ttu-id="dc850-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc850-122">Example</span></span>

<span data-ttu-id="dc850-123">Poniższy przykład pokazuje, jak należy zgrupować elementy źródłowe przy użyciu coś innego niż właściwość obiektu dla klucza grupy.</span><span class="sxs-lookup"><span data-stu-id="dc850-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="dc850-124">W tym przykładzie klucz jest pierwszej litery nazwiska uczniów.</span><span class="sxs-lookup"><span data-stu-id="dc850-124">In this example, the key is the first letter of the student's last name.</span></span>

<span data-ttu-id="dc850-125">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="dc850-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="dc850-126">Zmień instrukcji wywołujące w `Main` metody `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="dc850-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a><span data-ttu-id="dc850-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc850-127">Example</span></span>

<span data-ttu-id="dc850-128">Poniższy przykład pokazuje, jak należy zgrupować elementy źródłowe przy użyciu zakresu liczbowego jako klucz grupy.</span><span class="sxs-lookup"><span data-stu-id="dc850-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="dc850-129">Zapytanie projektów następnie wyniki na typ anonimowy, który zawiera tylko imię i nazwisko oraz zakres percentyl, do której należy studenta.</span><span class="sxs-lookup"><span data-stu-id="dc850-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="dc850-130">Typ anonimowy jest używana, ponieważ nie jest konieczne użycie pełnej `Student` obiektu, aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="dc850-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="dc850-131">`GetPercentile` Funkcja pomocnicza, która oblicza percentyl opiera się na średnią ocenę studenta.</span><span class="sxs-lookup"><span data-stu-id="dc850-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="dc850-132">Metoda zwraca liczbę całkowitą od 0 do 10.</span><span class="sxs-lookup"><span data-stu-id="dc850-132">The method returns an integer between 0 and 10.</span></span>

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

<span data-ttu-id="dc850-133">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="dc850-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="dc850-134">Zmień instrukcji wywołujące w `Main` metody `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="dc850-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a><span data-ttu-id="dc850-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc850-135">Example</span></span>

<span data-ttu-id="dc850-136">Poniższy przykład pokazuje, jak należy zgrupować elementy źródłowe przy użyciu wyrażenia logiczne porównania.</span><span class="sxs-lookup"><span data-stu-id="dc850-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="dc850-137">W tym przykładzie wyrażenie logiczne sprawdza, czy studenta średni egzaminu wynik jest większa niż 75.</span><span class="sxs-lookup"><span data-stu-id="dc850-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="dc850-138">Tak jak w poprzednich przykładach wyniki zostają odwzorowane w typ anonimowy, ponieważ element pełną źródła nie jest potrzebna.</span><span class="sxs-lookup"><span data-stu-id="dc850-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="dc850-139">Należy pamiętać, że właściwości typu anonimowego stają się właściwości z `Key` elementu członkowskiego i może zostać oceniony przez nazwę, gdy zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="dc850-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>

<span data-ttu-id="dc850-140">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="dc850-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="dc850-141">Zmień instrukcji wywołujące w `Main` metody `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="dc850-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a><span data-ttu-id="dc850-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc850-142">Example</span></span>

<span data-ttu-id="dc850-143">Poniższy przykład pokazuje, jak hermetyzacji klucz, który zawiera wiele wartości za pomocą typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="dc850-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="dc850-144">W tym przykładzie pierwsze wartość klucza jest pierwszej litery nazwiska uczniów.</span><span class="sxs-lookup"><span data-stu-id="dc850-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="dc850-145">Druga wartość klucza jest wartość logiczna określająca, czy uczeń oceniane ponad 85 na pierwszym egzamin.</span><span class="sxs-lookup"><span data-stu-id="dc850-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="dc850-146">Można uporządkować grupy według dowolnej właściwości w kluczu.</span><span class="sxs-lookup"><span data-stu-id="dc850-146">You can order the groups by any property in the key.</span></span>

<span data-ttu-id="dc850-147">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="dc850-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="dc850-148">Zmień instrukcji wywołujące w `Main` metody `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="dc850-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a><span data-ttu-id="dc850-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc850-149">See also</span></span>

- <xref:System.Linq.Enumerable.GroupBy%2A>  
- <xref:System.Linq.IGrouping%602>  
- [<span data-ttu-id="dc850-150">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="dc850-150">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="dc850-151">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="dc850-151">group clause</span></span>](../language-reference/keywords/group-clause.md)  
- [<span data-ttu-id="dc850-152">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="dc850-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
- [<span data-ttu-id="dc850-153">Wykonanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="dc850-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
- [<span data-ttu-id="dc850-154">Tworzenie grup zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="dc850-154">Create a Nested Group</span></span>](create-a-nested-group.md)  
- [<span data-ttu-id="dc850-155">Grupowanie danych</span><span class="sxs-lookup"><span data-stu-id="dc850-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)  