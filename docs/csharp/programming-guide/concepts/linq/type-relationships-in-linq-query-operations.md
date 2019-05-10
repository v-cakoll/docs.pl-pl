---
title: Relacje typu w operacjach kwerend LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 3b8ae80ff17ea2cf12c3d78c092dd3233ac0751d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755959"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="4668d-102">Relacje typu w operacjach kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="4668d-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="4668d-103">Aby efektywnie pisać zapytania, należy zrozumieć jak powiązane są ze sobą typy zmiennych w kompletnej operacji zapytania.</span><span class="sxs-lookup"><span data-stu-id="4668d-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="4668d-104">Jeśli zrozumiesz te relacje będzie łatwiej pojmować [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] i przykłady kodu w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="4668d-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="4668d-105">Ponadto zrozumiesz, co dzieje się, gdy zmienne są wpisywane niejawnie przy użyciu `var`.</span><span class="sxs-lookup"><span data-stu-id="4668d-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="4668d-106">operacje zapytań są silnie typizowane w źródle danych, samo zapytanie i wykonywania zapytań.</span><span class="sxs-lookup"><span data-stu-id="4668d-106">query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="4668d-107">Typ zmiennych w zapytaniu musi być zgodny z typem elementów w źródle danych i z typem zmiennej iteracji w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4668d-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="4668d-108">To pogrubione wpisywanie gwarantuje, że błędy wpisywania są wyłapywane w czasie kompilacji, gdy mogą być poprawione zanim użytkownik je napotka.</span><span class="sxs-lookup"><span data-stu-id="4668d-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="4668d-109">W celu przedstawienia relacji tych typów, większość przykładów, które należy wykonać Użyj jawnego wpisywania wszystkich zmiennych.</span><span class="sxs-lookup"><span data-stu-id="4668d-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="4668d-110">W ostatnim przykładzie pokazano, jak same zasady mają zastosowanie, nawet gdy możesz użyć niejawnego wpisywania, za pomocą [var](../../../../csharp/language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="4668d-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../../csharp/language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="4668d-111">Kwerendy, które nie przetwarzają dane źródłowe</span><span class="sxs-lookup"><span data-stu-id="4668d-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="4668d-112">Poniższa ilustracja przedstawia [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operację, która nie wykonuje transformacji danych zapytania.</span><span class="sxs-lookup"><span data-stu-id="4668d-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="4668d-113">Źródło zawiera sekwencję ciągów i wynik zapytania jest również sekwencją ciągów.</span><span class="sxs-lookup"><span data-stu-id="4668d-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![Diagram przedstawiający Relacja typów danych w zapytaniu programu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="4668d-115">Argument typu źródła danych określa typ zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="4668d-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="4668d-116">Typ wybranego obiektu określa typ zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="4668d-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="4668d-117">W tym miejscu `name` jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="4668d-117">Here `name` is a string.</span></span> <span data-ttu-id="4668d-118">Zmienna zapytania jest `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="4668d-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="4668d-119">Zmienna zapytania jest powtarzana w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4668d-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="4668d-120">Ponieważ zmienna zapytania jest sekwencja ciągów, zmienną iteracji jest ciąg.</span><span class="sxs-lookup"><span data-stu-id="4668d-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="4668d-121">Zapytania, które przetwarzają dane źródłowe</span><span class="sxs-lookup"><span data-stu-id="4668d-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="4668d-122">Poniższa ilustracja przedstawia [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operację, która wykonuje prostą transformację danych zapytania.</span><span class="sxs-lookup"><span data-stu-id="4668d-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="4668d-123">Zapytanie pobiera sekwencję `Customer` obiektów jako dane wejściowe i wybiera jedynie `Name` właściwości w wyniku.</span><span class="sxs-lookup"><span data-stu-id="4668d-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="4668d-124">Ponieważ `Name` jest ciągiem, tworzy zapytanie sekwencji ciągów jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="4668d-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Diagram przedstawiający kwerendę, która przekształca typu danych.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="4668d-126">Argument typu źródła danych określa typ zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="4668d-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="4668d-127">`select` Instrukcja zwraca `Name` właściwości zamiast pełnego `Customer` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4668d-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="4668d-128">Ponieważ `Name` jest ciągiem, argument typu `custNameQuery` jest `string`, a nie `Customer`.</span><span class="sxs-lookup"><span data-stu-id="4668d-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="4668d-129">Ponieważ `custNameQuery` jest sekwencją ciągów, `foreach` Zmienna iteracji pętli musi być również `string`.</span><span class="sxs-lookup"><span data-stu-id="4668d-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="4668d-130">Na poniższej ilustracji przedstawiono nieco bardziej skomplikowaną transformację.</span><span class="sxs-lookup"><span data-stu-id="4668d-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="4668d-131">`select` Instrukcja zwraca typ anonimowy, który przechwytuje tylko dwa elementy członkowskie oryginalnego `Customer` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4668d-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Diagram przedstawiający bardziej złożonego zapytania, który przekształca typu danych.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="4668d-133">Argument typu źródła danych jest zawsze typem zmiennej zakresu w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="4668d-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="4668d-134">Ponieważ `select` instrukcja generuje typ anonimowy, zmienna zapytania musi być wpisana niejawnie przy użyciu `var`.</span><span class="sxs-lookup"><span data-stu-id="4668d-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="4668d-135">Ponieważ typ zmiennej zapytania jest niejawny, Zmienna iteracji w `foreach` pętli musi być niejawne.</span><span class="sxs-lookup"><span data-stu-id="4668d-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="4668d-136">Umożliwienie kompilatorowi wywnioskowania informacji o typie</span><span class="sxs-lookup"><span data-stu-id="4668d-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="4668d-137">Chociaż należy zrozumieć relacje typów w operacji zapytania, masz opcję, aby pozwolić kompilatorowi wykonanie całąj pracy za Ciebie.</span><span class="sxs-lookup"><span data-stu-id="4668d-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="4668d-138">Słowo kluczowe [var](../../../../csharp/language-reference/keywords/var.md) mogą być używane dla dowolnej zmiennej lokalnej w operacji zapytania.</span><span class="sxs-lookup"><span data-stu-id="4668d-138">The keyword [var](../../../../csharp/language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="4668d-139">Na poniższej ilustracji jest podobny do przykładu numer 2, który została omówiony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="4668d-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="4668d-140">Jednak kompilator dostarcza silnego typu dla każdej zmiennej w operacji zapytania.</span><span class="sxs-lookup"><span data-stu-id="4668d-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Diagram pokazujący przepływ typu przy użyciu niejawnego wpisywania.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="4668d-142">Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="4668d-142">For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4668d-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4668d-143">See also</span></span>

- [<span data-ttu-id="4668d-144">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="4668d-144">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
