---
title: Funkcje C# obsługujące LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 9fc8adaa49d02f8b69c2db6e94a28b9fab36b3b0
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635798"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="78682-102">Funkcje C# obsługujące LINQ</span><span class="sxs-lookup"><span data-stu-id="78682-102">C# Features That Support LINQ</span></span>

<span data-ttu-id="78682-103">W poniższej sekcji wprowadzono nowe konstrukcje języka wprowadzone w C# 3,0.</span><span class="sxs-lookup"><span data-stu-id="78682-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="78682-104">Chociaż te nowe funkcje są używane do stopnia z zapytania LINQ, nie są ograniczone do LINQ i mogą być używane w dowolnym kontekście, w którym są użyteczne.</span><span class="sxs-lookup"><span data-stu-id="78682-104">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="78682-105">Wyrażenia kwerend</span><span class="sxs-lookup"><span data-stu-id="78682-105">Query Expressions</span></span>

<span data-ttu-id="78682-106">Wyrażenia zapytań używają składni deklaracyjnej podobnej do SQL lub XQuery w celu wykonywania zapytań na kolekcjach IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="78682-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="78682-107">W czasie kompilacji Składnia zapytania jest konwertowana na wywołania metody do implementacji dostawcy LINQ standardowych metod rozszerzenia operatora zapytania.</span><span class="sxs-lookup"><span data-stu-id="78682-107">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="78682-108">Aplikacje kontrolują standardowe operatory zapytań, które znajdują się w zakresie, określając odpowiednią przestrzeń nazw z dyrektywą `using`.</span><span class="sxs-lookup"><span data-stu-id="78682-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="78682-109">Następujące wyrażenie zapytania pobiera tablicę ciągów, grupuje je według pierwszego znaku w ciągu i porządkuje grupy.</span><span class="sxs-lookup"><span data-stu-id="78682-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="78682-110">Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="78682-110">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="78682-111">Niejawnie wpisane zmienne (var)</span><span class="sxs-lookup"><span data-stu-id="78682-111">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="78682-112">Zamiast jawnie określić typ podczas deklarowania i inicjowania zmiennej, można użyć modyfikatora [var](../../../language-reference/keywords/var.md) , aby nakazać kompilatorowi wywnioskowanie i przypisanie typu, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="78682-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="78682-113">Zmienne zadeklarowane jako `var` są równie silnie wpisywane jako zmienne, których typ określa się jawnie.</span><span class="sxs-lookup"><span data-stu-id="78682-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="78682-114">Użycie `var` umożliwia tworzenie typów anonimowych, ale może być używane tylko dla zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="78682-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="78682-115">Tablice mogą być również deklarowane przy użyciu niejawnego wpisywania.</span><span class="sxs-lookup"><span data-stu-id="78682-115">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="78682-116">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="78682-116">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="78682-117">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="78682-117">Object and Collection Initializers</span></span>

<span data-ttu-id="78682-118">Inicjatory obiektów i kolekcji umożliwiają inicjowanie obiektów bez jawnego wywoływania konstruktora dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="78682-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="78682-119">Inicjatory są zwykle używane w wyrażeniach zapytań, gdy projektują dane źródłowe do nowego typu danych.</span><span class="sxs-lookup"><span data-stu-id="78682-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="78682-120">Przy założeniu, że Klasa o nazwie `Customer` z właściwościami publicznymi `Name` i `Phone`, inicjator obiektu może być używany tak jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="78682-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="78682-121">Kontynuując pracę z naszą klasą `Customer`, Załóżmy, że istnieje źródło danych o nazwie `IncomingOrders`i że dla każdego zamówienia z dużą `OrderSize`chcesz utworzyć nową `Customer` na podstawie tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="78682-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="78682-122">Zapytanie LINQ można wykonać w tym źródle danych i użyć inicjalizacji obiektu do wypełnienia kolekcji:</span><span class="sxs-lookup"><span data-stu-id="78682-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="78682-123">Źródło danych może mieć więcej właściwości leżących pod okapem niż Klasa `Customer`, taka jak `OrderSize`, ale z inicjalizacją obiektu dane zwrócone z zapytania są Molded do żądanego typu danych; wybieramy dane, które są istotne dla naszej klasy.</span><span class="sxs-lookup"><span data-stu-id="78682-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="78682-124">W związku z tym teraz mamy `IEnumerable` wypełnione nowym `Customer`s.</span><span class="sxs-lookup"><span data-stu-id="78682-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="78682-125">Powyższe dane można także napisać w składni metody LINQ:</span><span class="sxs-lookup"><span data-stu-id="78682-125">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="78682-126">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="78682-126">For more information, see:</span></span>

- [<span data-ttu-id="78682-127">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="78682-127">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="78682-128">Składnia wyrażeń dla standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="78682-128">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="78682-129">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="78682-129">Anonymous Types</span></span>

<span data-ttu-id="78682-130">Typ anonimowy jest konstruowany przez kompilator, a nazwa typu jest dostępna tylko dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="78682-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="78682-131">Typy anonimowe umożliwiają wygodne grupowanie zestawu właściwości w wyniku zapytania, bez konieczności definiowania oddzielnego nazwanego typu.</span><span class="sxs-lookup"><span data-stu-id="78682-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="78682-132">Typy anonimowe są inicjowane za pomocą nowego wyrażenia i inicjatora obiektów, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="78682-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="78682-133">Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="78682-133">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="78682-134">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="78682-134">Extension Methods</span></span>

<span data-ttu-id="78682-135">Metoda rozszerzenia to metoda statyczna, która może być skojarzona z typem, tak aby można ją było wywołać tak, jakby była metodą wystąpienia w typie.</span><span class="sxs-lookup"><span data-stu-id="78682-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="78682-136">Ta funkcja umożliwia, w efekcie, "dodać" nowe metody do istniejących typów bez ich faktycznego modyfikowania.</span><span class="sxs-lookup"><span data-stu-id="78682-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="78682-137">Standardowe operatory zapytań to zestaw metod rozszerzających, które udostępniają funkcje zapytań LINQ dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="78682-137">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="78682-138">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="78682-138">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="78682-139">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="78682-139">Lambda Expressions</span></span>

<span data-ttu-id="78682-140">Wyrażenie lambda jest funkcją wbudowaną, która używa operatora = > do oddzielania parametrów wejściowych od treści funkcji i może być konwertowana w czasie kompilacji do delegata lub drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="78682-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="78682-141">W programowaniu LINQ, można napotkać wyrażenia lambda podczas wykonywania wywołań metody bezpośredniej do standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="78682-141">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="78682-142">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="78682-142">For more information, see:</span></span>

- [<span data-ttu-id="78682-143">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="78682-143">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="78682-144">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="78682-144">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="78682-145">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="78682-145">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="78682-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78682-146">See also</span></span>

- [<span data-ttu-id="78682-147">Zapytanie zintegrowane z językiem (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="78682-147">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
