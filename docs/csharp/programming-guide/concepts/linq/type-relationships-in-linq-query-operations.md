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
ms.openlocfilehash: 41853e6858fae9e8d449aeed95a6a84f343d5874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635616"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="ad132-102">Relacje typu w operacjach kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="ad132-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="ad132-103">Aby skutecznie zapisywać zapytania, należy zrozumieć, jak typy zmiennych w operacji kwerendy pełnej odnoszą się do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="ad132-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="ad132-104">Jeśli rozumiesz te relacje będzie łatwiej zrozumieć przykłady LINQ i przykłady kodu w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="ad132-104">If you understand these relationships you will more easily comprehend the LINQ samples and code examples in the documentation.</span></span> <span data-ttu-id="ad132-105">Ponadto można zrozumieć, co dzieje się za kulisami, gdy `var`zmienne są niejawnie wpisane przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="ad132-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="ad132-106">Operacje zapytań LINQ są silnie wpisane w źródle danych, w samej kwerendzie i w wykonywaniu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="ad132-106">LINQ query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="ad132-107">Typ zmiennych w kwerendzie musi być zgodny z typem elementów w źródle danych i typem `foreach` zmiennej iteracji w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad132-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="ad132-108">To silne wpisywanie gwarantuje, że błędy typu są przechwycone w czasie kompilacji, gdy można je poprawić, zanim użytkownicy napotkają je.</span><span class="sxs-lookup"><span data-stu-id="ad132-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="ad132-109">W celu zademonstrowania tych relacji typu, większość przykładów, które należy wykonać użyć jawnego wpisywania dla wszystkich zmiennych.</span><span class="sxs-lookup"><span data-stu-id="ad132-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="ad132-110">Ostatni przykład pokazuje, jak te same zasady mają zastosowanie nawet w przypadku używania niejawnego pisania przy użyciu [var](../../../language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="ad132-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="ad132-111">Kwerendy, które nie przekształcają danych źródłowych</span><span class="sxs-lookup"><span data-stu-id="ad132-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="ad132-112">Na poniższej ilustracji przedstawiono linq do obiektów zapytanie operacji, która wykonuje żadnych przekształceń na danych.</span><span class="sxs-lookup"><span data-stu-id="ad132-112">The following illustration shows a LINQ to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="ad132-113">Źródło zawiera sekwencję ciągów i dane wyjściowe kwerendy jest również sekwencja ciągów.</span><span class="sxs-lookup"><span data-stu-id="ad132-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![Diagram, który pokazuje relację typów danych w kwerendzie LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="ad132-115">Argument typu źródła danych określa typ zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="ad132-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="ad132-116">Typ wybranego obiektu określa typ zmiennej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="ad132-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="ad132-117">Oto `name` ciąg.</span><span class="sxs-lookup"><span data-stu-id="ad132-117">Here `name` is a string.</span></span> <span data-ttu-id="ad132-118">W związku z tym `IEnumerable<string>`zmienna kwerendy jest .</span><span class="sxs-lookup"><span data-stu-id="ad132-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="ad132-119">Zmienna kwerendy jest iterowana w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad132-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="ad132-120">Ponieważ zmienna kwerendy jest sekwencją ciągów, zmienna iteracji jest również ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ad132-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="ad132-121">Kwerendy przekształcające dane źródłowe</span><span class="sxs-lookup"><span data-stu-id="ad132-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="ad132-122">Na poniższej [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ilustracji przedstawiono operację kwerendy, która wykonuje prostą transformację danych.</span><span class="sxs-lookup"><span data-stu-id="ad132-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="ad132-123">Kwerenda przyjmuje sekwencję `Customer` obiektów jako dane wejściowe `Name` i wybiera tylko właściwość w wyniku.</span><span class="sxs-lookup"><span data-stu-id="ad132-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="ad132-124">Ponieważ `Name` jest ciągiem, kwerenda tworzy sekwencję ciągów jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ad132-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Diagram przedstawiający kwerendę, która przekształca typ danych.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="ad132-126">Argument typu źródła danych określa typ zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="ad132-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="ad132-127">Instrukcja `select` zwraca `Name` właściwość zamiast `Customer` kompletnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ad132-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="ad132-128">Ponieważ `Name` jest ciągiem, argument `custNameQuery` `string`typu `Customer`jest , nie .</span><span class="sxs-lookup"><span data-stu-id="ad132-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="ad132-129">Ponieważ `custNameQuery` jest sekwencją ciągów, zmienna iteracji `foreach` pętli `string`musi być również .</span><span class="sxs-lookup"><span data-stu-id="ad132-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="ad132-130">Na poniższej ilustracji przedstawiono nieco bardziej złożoną transformację.</span><span class="sxs-lookup"><span data-stu-id="ad132-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="ad132-131">Instrukcja `select` zwraca typ anonimowy, który przechwytuje `Customer` tylko dwa elementy członkowskie oryginalnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ad132-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Diagram przedstawiający bardziej złożoną kwerendę, która przekształca typ danych.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="ad132-133">Argument typu źródła danych jest zawsze typem zmiennej zakresu w kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="ad132-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="ad132-134">Ponieważ `select` instrukcja tworzy typ anonimowy, zmienna kwerendy musi `var`być niejawnie wpisana przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="ad132-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="ad132-135">Ponieważ typ zmiennej kwerendy jest niejawna, `foreach` zmienna iteracji w pętli musi być również niejawna.</span><span class="sxs-lookup"><span data-stu-id="ad132-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="ad132-136">Zezwalanie kompilatorowi na wywnioskować informacje o typie</span><span class="sxs-lookup"><span data-stu-id="ad132-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="ad132-137">Chociaż należy zrozumieć relacje typu w operacji kwerendy, masz możliwość, aby umożliwić kompilator wykonać całą pracę dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="ad132-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="ad132-138">Słowo kluczowe [var](../../../language-reference/keywords/var.md) może służyć dla dowolnej zmiennej lokalnej w operacji kwerendy.</span><span class="sxs-lookup"><span data-stu-id="ad132-138">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="ad132-139">Poniższa ilustracja jest podobna do przykładu numer 2, który został omówiony wcześniej.</span><span class="sxs-lookup"><span data-stu-id="ad132-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="ad132-140">Jednak kompilator dostarcza silny typ dla każdej zmiennej w operacji kwerendy.</span><span class="sxs-lookup"><span data-stu-id="ad132-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Diagram, który pokazuje przepływ typu z niejawnym wpisywaniem.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="ad132-142">Aby uzyskać `var`więcej informacji na temat , zobacz [Niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="ad132-142">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
