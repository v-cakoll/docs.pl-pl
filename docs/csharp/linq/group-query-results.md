---
title: Wyniki kwerendy grupowej (LINQ w języku C#)
description: Dowiedz się, jak grupować wyniki za pomocą LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688465"
---
# <a name="group-query-results"></a><span data-ttu-id="8a2de-103">Grupowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="8a2de-103">Group query results</span></span>

<span data-ttu-id="8a2de-104">Grouping jest jedną z najpotężniejszych możliwości LINQ.</span><span class="sxs-lookup"><span data-stu-id="8a2de-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="8a2de-105">W poniższych przykładach przedstawiono sposób grupowania danych na różne sposoby:</span><span class="sxs-lookup"><span data-stu-id="8a2de-105">The following examples show how to group data in various ways:</span></span>

- <span data-ttu-id="8a2de-106">Przez jedną właściwość.</span><span class="sxs-lookup"><span data-stu-id="8a2de-106">By a single property.</span></span>

- <span data-ttu-id="8a2de-107">Przez pierwszą literę właściwości ciągu.</span><span class="sxs-lookup"><span data-stu-id="8a2de-107">By the first letter of a string property.</span></span>

- <span data-ttu-id="8a2de-108">Według obliczonego zakresu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="8a2de-108">By a computed numeric range.</span></span>

- <span data-ttu-id="8a2de-109">Przez predykat logiczny lub inne wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="8a2de-109">By Boolean predicate or other expression.</span></span>

- <span data-ttu-id="8a2de-110">Przez klucz złożony.</span><span class="sxs-lookup"><span data-stu-id="8a2de-110">By a compound key.</span></span>

<span data-ttu-id="8a2de-111">Ponadto ostatnie dwa zapytania projektu ich wyniki do nowego typu anonimowego, który zawiera tylko imię i nazwisko studenta.</span><span class="sxs-lookup"><span data-stu-id="8a2de-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="8a2de-112">Aby uzyskać więcej informacji, zobacz [klauzulę group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8a2de-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="8a2de-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a2de-113">Example</span></span>

<span data-ttu-id="8a2de-114">Wszystkie przykłady w tym temacie użyć następujących klas pomocnika i źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="8a2de-114">All the examples in this topic use the following helper classes and data sources.</span></span>

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a><span data-ttu-id="8a2de-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a2de-115">Example</span></span>

<span data-ttu-id="8a2de-116">W poniższym przykładzie pokazano, jak grupować elementy źródłowe przy użyciu pojedynczej właściwości elementu jako klucza grupy.</span><span class="sxs-lookup"><span data-stu-id="8a2de-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="8a2de-117">W tym przypadku kluczem `string`jest , nazwisko ucznia.</span><span class="sxs-lookup"><span data-stu-id="8a2de-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="8a2de-118">Możliwe jest również użycie podciągu dla klucza.</span><span class="sxs-lookup"><span data-stu-id="8a2de-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="8a2de-119">Operacja grupowania używa domyślnego porównania równości dla typu.</span><span class="sxs-lookup"><span data-stu-id="8a2de-119">The grouping operation uses the default equality comparer for the type.</span></span>

<span data-ttu-id="8a2de-120">Wklej następującą `StudentClass` metodę do klasy.</span><span class="sxs-lookup"><span data-stu-id="8a2de-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8a2de-121">Zmień instrukcję wywołującą `sc.GroupBySingleProperty()`w metodzie na `Main` .</span><span class="sxs-lookup"><span data-stu-id="8a2de-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a><span data-ttu-id="8a2de-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a2de-122">Example</span></span>

<span data-ttu-id="8a2de-123">W poniższym przykładzie pokazano, jak grupować elementy źródłowe przy użyciu czegoś innego niż właściwość obiektu dla klucza grupy.</span><span class="sxs-lookup"><span data-stu-id="8a2de-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="8a2de-124">W tym przykładzie kluczem jest pierwsza litera nazwiska ucznia.</span><span class="sxs-lookup"><span data-stu-id="8a2de-124">In this example, the key is the first letter of the student's last name.</span></span>

<span data-ttu-id="8a2de-125">Wklej następującą `StudentClass` metodę do klasy.</span><span class="sxs-lookup"><span data-stu-id="8a2de-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8a2de-126">Zmień instrukcję wywołującą `sc.GroupBySubstring()`w metodzie na `Main` .</span><span class="sxs-lookup"><span data-stu-id="8a2de-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a><span data-ttu-id="8a2de-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a2de-127">Example</span></span>

<span data-ttu-id="8a2de-128">W poniższym przykładzie pokazano, jak grupować elementy źródłowe przy użyciu zakresu liczbowego jako klucza grupy.</span><span class="sxs-lookup"><span data-stu-id="8a2de-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="8a2de-129">Kwerenda następnie wyświetla wyniki do typu anonimowego, który zawiera tylko imię i nazwisko oraz zakres percentyla, do którego należy uczeń.</span><span class="sxs-lookup"><span data-stu-id="8a2de-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="8a2de-130">Typ anonimowy jest używany, ponieważ nie jest `Student` konieczne użycie kompletnego obiektu do wyświetlania wyników.</span><span class="sxs-lookup"><span data-stu-id="8a2de-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="8a2de-131">`GetPercentile`jest funkcją pomocnika, która oblicza percentyl na podstawie średniego wyniku ucznia.</span><span class="sxs-lookup"><span data-stu-id="8a2de-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="8a2de-132">Metoda zwraca wartość całkowitą z liczbą całkowitą z liczbą całkowitą z rzędu 0 do 10.</span><span class="sxs-lookup"><span data-stu-id="8a2de-132">The method returns an integer between 0 and 10.</span></span>

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

<span data-ttu-id="8a2de-133">Wklej następującą `StudentClass` metodę do klasy.</span><span class="sxs-lookup"><span data-stu-id="8a2de-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8a2de-134">Zmień instrukcję wywołującą `sc.GroupByRange()`w metodzie na `Main` .</span><span class="sxs-lookup"><span data-stu-id="8a2de-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a><span data-ttu-id="8a2de-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a2de-135">Example</span></span>

<span data-ttu-id="8a2de-136">W poniższym przykładzie pokazano, jak grupować elementy źródłowe przy użyciu wyrażenia porównania logicznego.</span><span class="sxs-lookup"><span data-stu-id="8a2de-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="8a2de-137">W tym przykładzie wyrażenie logiczne sprawdza, czy średni wynik egzaminu ucznia jest większy niż 75.</span><span class="sxs-lookup"><span data-stu-id="8a2de-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="8a2de-138">Podobnie jak w poprzednich przykładach wyniki są rzutowane na typ anonimowy, ponieważ kompletny element źródłowy nie jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="8a2de-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="8a2de-139">Należy zauważyć, że właściwości w typie `Key` anonimowym stają się właściwościami elementu członkowskiego i są dostępne według nazwy podczas wykonywania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="8a2de-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>

<span data-ttu-id="8a2de-140">Wklej następującą `StudentClass` metodę do klasy.</span><span class="sxs-lookup"><span data-stu-id="8a2de-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8a2de-141">Zmień instrukcję wywołującą `sc.GroupByBoolean()`w metodzie na `Main` .</span><span class="sxs-lookup"><span data-stu-id="8a2de-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a><span data-ttu-id="8a2de-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a2de-142">Example</span></span>

<span data-ttu-id="8a2de-143">W poniższym przykładzie pokazano, jak używać typu anonimowego do hermetyzacji klucza, który zawiera wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="8a2de-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="8a2de-144">W tym przykładzie pierwszą wartością klucza jest pierwsza litera nazwiska ucznia.</span><span class="sxs-lookup"><span data-stu-id="8a2de-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="8a2de-145">Drugą wartością klucza jest wartość logiczna, która określa, czy uczeń uzyskał wynik powyżej 85 punktów na pierwszym egzaminie.</span><span class="sxs-lookup"><span data-stu-id="8a2de-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="8a2de-146">Grupy można zamówić według dowolnej właściwości w kluczu.</span><span class="sxs-lookup"><span data-stu-id="8a2de-146">You can order the groups by any property in the key.</span></span>

<span data-ttu-id="8a2de-147">Wklej następującą `StudentClass` metodę do klasy.</span><span class="sxs-lookup"><span data-stu-id="8a2de-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="8a2de-148">Zmień instrukcję wywołującą `sc.GroupByCompositeKey()`w metodzie na `Main` .</span><span class="sxs-lookup"><span data-stu-id="8a2de-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a><span data-ttu-id="8a2de-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a2de-149">See also</span></span>

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [<span data-ttu-id="8a2de-150">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="8a2de-150">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="8a2de-151">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="8a2de-151">group clause</span></span>](../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="8a2de-152">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="8a2de-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="8a2de-153">Wykonywanie podkwerendy w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="8a2de-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="8a2de-154">Tworzenie grupy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="8a2de-154">Create a Nested Group</span></span>](create-a-nested-group.md)
- [<span data-ttu-id="8a2de-155">Grupowanie danych</span><span class="sxs-lookup"><span data-stu-id="8a2de-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
