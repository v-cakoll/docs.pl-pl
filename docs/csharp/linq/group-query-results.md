---
title: Wyniki zapytania grupy
description: "Sposób grupowania wyników."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: ca68cf96a2c27bbd1999d5445c14fc93e8e2566c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="group-query-results"></a><span data-ttu-id="ab5bf-104">Wyniki zapytania grupy</span><span class="sxs-lookup"><span data-stu-id="ab5bf-104">Group query results</span></span>

<span data-ttu-id="ab5bf-105">Grupowanie jest jednym z najbardziej zaawansowanych funkcji LINQ.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="ab5bf-106">Poniższe przykłady przedstawiają sposób grupowania danych na różne sposoby:</span><span class="sxs-lookup"><span data-stu-id="ab5bf-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="ab5bf-107">W jednej właściwości.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-107">By a single property.</span></span>  
  
-   <span data-ttu-id="ab5bf-108">Przez pierwszą literę właściwości ciągu.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="ab5bf-109">Przez obliczoną zakresu numerycznego.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="ab5bf-110">Predykat Boolean lub innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="ab5bf-111">Przy użyciu klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-111">By a compound key.</span></span>  
  
 <span data-ttu-id="ab5bf-112">Ponadto ostatnie dwa zapytania projektu ich wyniki do nowego typu anonimowego, który zawiera tylko student imienia i nazwiska.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="ab5bf-113">Aby uzyskać więcej informacji, zobacz [klauzuli group](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ab5bf-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab5bf-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab5bf-114">Example</span></span>  
 <span data-ttu-id="ab5bf-115">Wszystkie przykłady w tym temacie, użyj następujących źródeł danych i klas pomocnika.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ab5bf-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab5bf-116">Example</span></span>  
 <span data-ttu-id="ab5bf-117">Poniższy przykład przedstawia sposób grupowania elementów źródła przy użyciu jednej właściwości elementu jako klucz grupy.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-117">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="ab5bf-118">W tym przypadku jest klucz `string`, nazwisko studenta.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-118">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="ab5bf-119">Istnieje również możliwość użycia ciąg dla klucza.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-119">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="ab5bf-120">Operacji grupowania używa domyślna funkcja porównująca równości dla typu.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-120">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="ab5bf-121">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-121">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="ab5bf-122">Zmień instrukcję wywoływania w `Main` metodę `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-122">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="ab5bf-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab5bf-123">Example</span></span>  
 <span data-ttu-id="ab5bf-124">Poniższy przykład przedstawia sposób grupowania elementów źródła przy użyciu inną niż właściwość obiektu dla klucza grupy.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-124">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="ab5bf-125">W tym przykładzie klucz jest pierwszą literę nazwisko studenta.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-125">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="ab5bf-126">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-126">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="ab5bf-127">Zmień instrukcję wywoływania w `Main` metodę `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-127">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="ab5bf-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab5bf-128">Example</span></span>  
 <span data-ttu-id="ab5bf-129">Poniższy przykład przedstawia sposób grupowania elementów źródła przy użyciu zakresu numerycznego jako klucz grupy.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-129">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="ab5bf-130">Zapytanie następnie projekcję wyniki do typu anonimowego, zawierający tylko imię i nazwisko i zakres percentyl, do którego należy studenta.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-130">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="ab5bf-131">Typ anonimowy jest używany, ponieważ nie jest to niezbędne do korzystania z pełną `Student` obiektu do wyświetlenia wyników.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-131">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="ab5bf-132">`GetPercentile`Funkcja pomocnika, który oblicza percentyl opiera się na Średnia ocena studenta.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-132">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="ab5bf-133">Metoda zwraca liczbą całkowitą z przedziału od 0 do 10.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-133">The method returns an integer between 0 and 10.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 <span data-ttu-id="ab5bf-134">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-134">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="ab5bf-135">Zmień instrukcję wywoływania w `Main` metodę `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-135">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="ab5bf-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab5bf-136">Example</span></span>  
 <span data-ttu-id="ab5bf-137">Poniższy przykład przedstawia sposób grupowania elementów źródła przy użyciu wyrażenia logicznym.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-137">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="ab5bf-138">W tym przykładzie wyrażenie warunkowe sprawdza, czy wynik egzaminu średni studenta jest większa niż 75.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-138">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="ab5bf-139">Jak w poprzednich przykładach wyniki są przedstawione jako typu anonimowego, ponieważ element pełną źródła nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-139">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="ab5bf-140">Należy pamiętać, że właściwości typu anonimowego stają się właściwości z `Key` elementu członkowskiego i można uzyskać, sprawdzając nazwę podczas wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-140">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="ab5bf-141">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-141">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="ab5bf-142">Zmień instrukcję wywoływania w `Main` metodę `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-142">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="ab5bf-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab5bf-143">Example</span></span>  
 <span data-ttu-id="ab5bf-144">Poniższy przykład przedstawia użycie typu anonimowego w celu hermetyzacji klucz, który zawiera wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-144">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="ab5bf-145">W tym przykładzie pierwszą wartość klucza jest pierwszą literę nazwisko studenta.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-145">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="ab5bf-146">Druga wartość klucza jest wartość logiczna określająca, czy student oceniane ponad 85 na pierwszym stosowana.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-146">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="ab5bf-147">Można zamówić grupy przez dowolną właściwość klucza.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-147">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="ab5bf-148">Wklej następującą metodę do `StudentClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-148">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="ab5bf-149">Zmień instrukcję wywoływania w `Main` metodę `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="ab5bf-149">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ab5bf-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab5bf-150">See also</span></span>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [<span data-ttu-id="ab5bf-151">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="ab5bf-151">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="ab5bf-152">Group — klauzula</span><span class="sxs-lookup"><span data-stu-id="ab5bf-152">group clause</span></span>](../language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="ab5bf-153">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="ab5bf-153">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="ab5bf-154">Wykonanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="ab5bf-154">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="ab5bf-155">Tworzenie grup zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="ab5bf-155">Create a Nested Group</span></span>](create-a-nested-group.md)  
 [<span data-ttu-id="ab5bf-156">Grupowanie danych</span><span class="sxs-lookup"><span data-stu-id="ab5bf-156">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
