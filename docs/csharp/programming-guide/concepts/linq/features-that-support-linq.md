---
title: Funkcje C# obsługujące LINQ
description: Dowiedz się więcej na temat funkcji języka C# do użycia z kwerendami LINQ i w innych kontekstach. Te konstrukcje języka zostały wprowadzone w języku C# 3,0.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: f72b82180d794086dcea9f11a7a057dc26ab0b26
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105422"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="65168-104">Funkcje C# obsługujące LINQ</span><span class="sxs-lookup"><span data-stu-id="65168-104">C# Features That Support LINQ</span></span>

<span data-ttu-id="65168-105">W poniższej sekcji wprowadzono nowe konstrukcje języka wprowadzone w języku C# 3,0.</span><span class="sxs-lookup"><span data-stu-id="65168-105">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="65168-106">Chociaż te nowe funkcje są używane do stopnia z zapytania LINQ, nie są ograniczone do LINQ i mogą być używane w dowolnym kontekście, w którym są użyteczne.</span><span class="sxs-lookup"><span data-stu-id="65168-106">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="65168-107">Wyrażenia kwerend</span><span class="sxs-lookup"><span data-stu-id="65168-107">Query Expressions</span></span>

<span data-ttu-id="65168-108">Wyrażenia zapytań używają składni deklaracyjnej podobnej do SQL lub XQuery w celu wykonywania zapytań na kolekcjach IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="65168-108">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="65168-109">W czasie kompilacji Składnia zapytania jest konwertowana na wywołania metody do implementacji dostawcy LINQ standardowych metod rozszerzenia operatora zapytania.</span><span class="sxs-lookup"><span data-stu-id="65168-109">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="65168-110">Aplikacje kontrolują standardowe operatory zapytań, które znajdują się w zakresie przez określenie odpowiedniej przestrzeni nazw z `using` dyrektywą.</span><span class="sxs-lookup"><span data-stu-id="65168-110">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="65168-111">Następujące wyrażenie zapytania pobiera tablicę ciągów, grupuje je według pierwszego znaku w ciągu i porządkuje grupy.</span><span class="sxs-lookup"><span data-stu-id="65168-111">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="65168-112">Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="65168-112">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="65168-113">Niejawnie wpisane zmienne (var)</span><span class="sxs-lookup"><span data-stu-id="65168-113">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="65168-114">Zamiast jawnie określić typ podczas deklarowania i inicjowania zmiennej, można użyć modyfikatora [var](../../../language-reference/keywords/var.md) , aby nakazać kompilatorowi wywnioskowanie i przypisanie typu, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="65168-114">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="65168-115">Zmienne zadeklarowane jako `var` są równie silnie wpisywane jako zmienne, których typ określa się jawnie.</span><span class="sxs-lookup"><span data-stu-id="65168-115">Variables declared as `var` are just as strongly typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="65168-116">Użycie systemu `var` umożliwia tworzenie typów anonimowych, ale może być używane tylko dla zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="65168-116">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="65168-117">Tablice mogą być również deklarowane przy użyciu niejawnego wpisywania.</span><span class="sxs-lookup"><span data-stu-id="65168-117">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="65168-118">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="65168-118">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="65168-119">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="65168-119">Object and Collection Initializers</span></span>

<span data-ttu-id="65168-120">Inicjatory obiektów i kolekcji umożliwiają inicjowanie obiektów bez jawnego wywoływania konstruktora dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="65168-120">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="65168-121">Inicjatory są zwykle używane w wyrażeniach zapytań, gdy projektują dane źródłowe do nowego typu danych.</span><span class="sxs-lookup"><span data-stu-id="65168-121">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="65168-122">Przy założeniu klasy o nazwie `Customer` z publiczną `Name` i `Phone` właściwością inicjatora obiektów można używać tak jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="65168-122">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="65168-123">Kontynuując pracę z naszą `Customer` klasą, Załóżmy, że istnieje źródło danych o nazwie `IncomingOrders` i że dla każdego zamówienia z dużą, chcemy `OrderSize` utworzyć nową wartość `Customer` na podstawie tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="65168-123">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="65168-124">Zapytanie LINQ można wykonać w tym źródle danych i użyć inicjalizacji obiektu do wypełnienia kolekcji:</span><span class="sxs-lookup"><span data-stu-id="65168-124">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="65168-125">Źródło danych może mieć więcej właściwości znajdujących się pod okapem niż `Customer` Klasa, taka jak `OrderSize` , ale z inicjalizacją obiektu, dane zwrócone z zapytania są Molded do żądanego typu danych. wybieramy dane, które są istotne dla naszej klasy.</span><span class="sxs-lookup"><span data-stu-id="65168-125">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="65168-126">W związku z tym mamy teraz `IEnumerable` wypełnioną nową, `Customer` pożądaną nowością.</span><span class="sxs-lookup"><span data-stu-id="65168-126">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="65168-127">Powyższe dane można także napisać w składni metody LINQ:</span><span class="sxs-lookup"><span data-stu-id="65168-127">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="65168-128">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="65168-128">For more information, see:</span></span>

- [<span data-ttu-id="65168-129">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="65168-129">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="65168-130">Składnia wyrażeń dla standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="65168-130">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="65168-131">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="65168-131">Anonymous Types</span></span>

<span data-ttu-id="65168-132">Typ anonimowy jest konstruowany przez kompilator, a nazwa typu jest dostępna tylko dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="65168-132">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="65168-133">Typy anonimowe umożliwiają wygodne grupowanie zestawu właściwości w wyniku zapytania, bez konieczności definiowania oddzielnego nazwanego typu.</span><span class="sxs-lookup"><span data-stu-id="65168-133">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="65168-134">Typy anonimowe są inicjowane za pomocą nowego wyrażenia i inicjatora obiektów, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="65168-134">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="65168-135">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="65168-135">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="65168-136">Metody rozszerzania</span><span class="sxs-lookup"><span data-stu-id="65168-136">Extension Methods</span></span>

<span data-ttu-id="65168-137">Metoda rozszerzenia to metoda statyczna, która może być skojarzona z typem, tak aby można ją było wywołać tak, jakby była metodą wystąpienia w typie.</span><span class="sxs-lookup"><span data-stu-id="65168-137">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="65168-138">Ta funkcja umożliwia, w efekcie, "dodać" nowe metody do istniejących typów bez ich faktycznego modyfikowania.</span><span class="sxs-lookup"><span data-stu-id="65168-138">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="65168-139">Standardowe operatory zapytań to zestaw metod rozszerzających, które udostępniają funkcje zapytań LINQ dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="65168-139">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="65168-140">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="65168-140">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="65168-141">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="65168-141">Lambda Expressions</span></span>

<span data-ttu-id="65168-142">Wyrażenie lambda jest funkcją wbudowaną, która używa operatora => do oddzielania parametrów wejściowych od treści funkcji i może być konwertowana w czasie kompilacji do delegata lub drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="65168-142">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="65168-143">W programowaniu LINQ, można napotkać wyrażenia lambda podczas wykonywania wywołań metody bezpośredniej do standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="65168-143">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="65168-144">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="65168-144">For more information, see:</span></span>

- [<span data-ttu-id="65168-145">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="65168-145">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="65168-146">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="65168-146">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="65168-147">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="65168-147">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="65168-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65168-148">See also</span></span>

- [<span data-ttu-id="65168-149">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="65168-149">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
