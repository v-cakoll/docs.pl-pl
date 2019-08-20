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
ms.openlocfilehash: 42519a74be1bd6934bc7a3304d154321697d128c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591021"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="b15cc-102">Relacje typu w operacjach kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="b15cc-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="b15cc-103">Aby efektywnie pisać zapytania, należy zrozumieć, jak typy zmiennych w kompletnej operacji zapytania wszystkie odnoszą się do siebie.</span><span class="sxs-lookup"><span data-stu-id="b15cc-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="b15cc-104">Jeśli rozumiesz te relacje, łatwiej będzie comprehend [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przykłady i przykłady kodu w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b15cc-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="b15cc-105">Ponadto dowiesz się, co się dzieje w tle, gdy zmienne są wpisywane niejawnie `var`przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="b15cc-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="b15cc-106">operacje zapytań są jednoznacznie wpisywane w źródle danych, w samej kwerendzie i w wykonaniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="b15cc-106">query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="b15cc-107">Typ zmiennych w zapytaniu musi być zgodny z typem elementów w źródle danych i typem zmiennej iteracji w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b15cc-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="b15cc-108">Takie silne wpisywanie gwarantuje, że błędy typu są przechwytywane w czasie kompilacji, gdy można je poprawić przed ich wystąpieniem przez użytkowników.</span><span class="sxs-lookup"><span data-stu-id="b15cc-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="b15cc-109">Aby przedstawić te relacje typu, większość przykładów, które są zgodne z użyciem jawnego wpisywania dla wszystkich zmiennych.</span><span class="sxs-lookup"><span data-stu-id="b15cc-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="b15cc-110">W ostatnim przykładzie pokazano, jak te same zasady mają zastosowanie nawet w przypadku użycia niejawnego wpisywania przy użyciu funkcji [var](../../../language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="b15cc-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="b15cc-111">Zapytania, które nie przekształcają danych źródłowych</span><span class="sxs-lookup"><span data-stu-id="b15cc-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="b15cc-112">Na poniższej ilustracji przedstawiono [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operację zapytania do obiektów, która nie wykonuje transformacji danych.</span><span class="sxs-lookup"><span data-stu-id="b15cc-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="b15cc-113">Źródło zawiera sekwencję ciągów, a dane wyjściowe zapytania są również sekwencją ciągów.</span><span class="sxs-lookup"><span data-stu-id="b15cc-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![Diagram przedstawiający relację typów danych w zapytaniu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="b15cc-115">Argument typu źródła danych określa typ zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="b15cc-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="b15cc-116">Typ wybranego obiektu określa typ zmiennej zapytania.</span><span class="sxs-lookup"><span data-stu-id="b15cc-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="b15cc-117">Oto `name` ciąg.</span><span class="sxs-lookup"><span data-stu-id="b15cc-117">Here `name` is a string.</span></span> <span data-ttu-id="b15cc-118">W związku z tym zmienna zapytania jest `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="b15cc-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="b15cc-119">Zmienna zapytania jest powtarzana w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b15cc-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="b15cc-120">Ponieważ zmienna zapytania jest sekwencją ciągów, Zmienna iteracji jest również ciągiem.</span><span class="sxs-lookup"><span data-stu-id="b15cc-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="b15cc-121">Zapytania, które przekształcają dane źródłowe</span><span class="sxs-lookup"><span data-stu-id="b15cc-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="b15cc-122">Na poniższej ilustracji przedstawiono [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operację zapytania, która wykonuje prostą transformację danych.</span><span class="sxs-lookup"><span data-stu-id="b15cc-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="b15cc-123">Zapytanie pobiera sekwencję `Customer` obiektów jako dane wejściowe i wybiera `Name` tylko właściwość w wyniku.</span><span class="sxs-lookup"><span data-stu-id="b15cc-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="b15cc-124">Ponieważ `Name` jest ciągiem, zapytanie tworzy sekwencję ciągów jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b15cc-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Diagram przedstawiający zapytanie, które przekształca typ danych.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="b15cc-126">Argument typu źródła danych określa typ zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="b15cc-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="b15cc-127">Instrukcja zwraca właściwość zamiast kompletnego `Customer`obiektu. `select` `Name`</span><span class="sxs-lookup"><span data-stu-id="b15cc-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="b15cc-128">Ponieważ `Name` jest ciągiem, `custNameQuery` argument typu ma wartość `string`, a nie `Customer`.</span><span class="sxs-lookup"><span data-stu-id="b15cc-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="b15cc-129">Ponieważ `custNameQuery` jest sekwencją ciągów `foreach` , `string`Zmienna iteracji pętli musi być również.</span><span class="sxs-lookup"><span data-stu-id="b15cc-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="b15cc-130">Na poniższej ilustracji przedstawiono nieco bardziej skomplikowaną transformację.</span><span class="sxs-lookup"><span data-stu-id="b15cc-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="b15cc-131">Instrukcja zwraca typ anonimowy, który przechwytuje tylko dwa elementy członkowskie oryginalnego `Customer` obiektu. `select`</span><span class="sxs-lookup"><span data-stu-id="b15cc-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Diagram przedstawiający bardziej złożone zapytania, które przekształcają typ danych.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="b15cc-133">Argument typu źródła danych jest zawsze typem zmiennej zakresu w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="b15cc-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="b15cc-134">Ponieważ instrukcja generuje typ anonimowy, zmienna zapytania musi być wpisana niejawnie przy użyciu `var`. `select`</span><span class="sxs-lookup"><span data-stu-id="b15cc-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="b15cc-135">Ponieważ typ zmiennej zapytania jest niejawny, Zmienna iteracji w `foreach` pętli musi być również niejawna.</span><span class="sxs-lookup"><span data-stu-id="b15cc-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="b15cc-136">Zezwalanie na informacje o typie wnioskowania kompilatora</span><span class="sxs-lookup"><span data-stu-id="b15cc-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="b15cc-137">Chociaż należy zrozumieć relacje typu w operacji zapytania, masz możliwość zezwalania kompilatorowi na wykonywanie wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="b15cc-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="b15cc-138">[Var](../../../language-reference/keywords/var.md) słowa kluczowego może być używana dla każdej zmiennej lokalnej w operacji zapytania.</span><span class="sxs-lookup"><span data-stu-id="b15cc-138">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="b15cc-139">Poniższa ilustracja jest podobna do przykładu numer 2, który został omówiony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="b15cc-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="b15cc-140">Jednak kompilator dostarcza mocny typ dla każdej zmiennej w operacji zapytania.</span><span class="sxs-lookup"><span data-stu-id="b15cc-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Diagram przedstawiający przepływ typu z niejawnym wpisywaniem.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="b15cc-142">Aby uzyskać więcej informacji `var`na temat, zobacz niejawnie [wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="b15cc-142">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
