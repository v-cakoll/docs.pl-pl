---
title: Funkcje C# obsługujące LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 51cc24fd8054b87b6c92a02450420a9c4abef525
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191093"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="2c75f-102">Funkcje C# obsługujące LINQ</span><span class="sxs-lookup"><span data-stu-id="2c75f-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="2c75f-103">Poniższa sekcja wprowadza nowe konstrukcji językowych, wprowadzona w języku C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="2c75f-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="2c75f-104">Mimo że te nowe funkcje są używane w stopniu przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, nie są one ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] i mogą być używane w dowolnym kontekście gdzie można je odnaleźć przydatne.</span><span class="sxs-lookup"><span data-stu-id="2c75f-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="2c75f-105">Wyrażenia zapytań</span><span class="sxs-lookup"><span data-stu-id="2c75f-105">Query Expressions</span></span>  
 <span data-ttu-id="2c75f-106">Wyrażenia zapytań użyj składni deklaratywnej podobne do bazy danych SQL lub XQuery zapytania za pośrednictwem kolekcji interfejs IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="2c75f-106">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="2c75f-107">Podczas kompilacji czasu Składnia kwerendy jest konwertowany na wywołania metody do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy implementację metody standardowego operatora zapytań rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="2c75f-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="2c75f-108">Aplikacje kontrolować standardowych operatorów zapytań, które znajdują się w zakresie, określając odpowiedni obszar nazw z `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="2c75f-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="2c75f-109">Poniższe wyrażenie zapytania pobiera tablicę ciągów, grupuje je zgodnie z pierwszego znaku w ciągu i porządkuje grup.</span><span class="sxs-lookup"><span data-stu-id="2c75f-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```csharp  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="2c75f-110">Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="2c75f-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="2c75f-111">Niejawnie wpisane zmienne (var)</span><span class="sxs-lookup"><span data-stu-id="2c75f-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="2c75f-112">Zamiast jawnego określania typu, jeśli zadeklarujesz i zainicjalizujesz zmienną, możesz użyć [var](../../../../csharp/language-reference/keywords/var.md) modyfikator można nakazać kompilatorowi wywnioskowania i przypisać ten typ, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="2c75f-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```csharp  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="2c75f-113">Zmienne zadeklarowane jako `var` są po prostu jako silnie typizowaną jako zmienne o typie należy jawnie określić.</span><span class="sxs-lookup"><span data-stu-id="2c75f-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="2c75f-114">Korzystanie z `var` sprawia, że można utworzyć typy anonimowe, ale może służyć tylko dla zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="2c75f-114">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="2c75f-115">Tablice mogą być także zadeklarowane przy użyciu niejawnego wpisywania.</span><span class="sxs-lookup"><span data-stu-id="2c75f-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="2c75f-116">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="2c75f-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="2c75f-117">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="2c75f-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="2c75f-118">Inicjatory obiektów i kolekcji umożliwiają inicjowanie obiektów bez jawnego wywołania konstruktora obiektu.</span><span class="sxs-lookup"><span data-stu-id="2c75f-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="2c75f-119">Inicjatory są zwykle używane w wyrażeniach zapytań, gdy ich projektu źródła danych na nowy typ danych.</span><span class="sxs-lookup"><span data-stu-id="2c75f-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="2c75f-120">Zakładając, że klasę o nazwie `Customer` z publicznych `Name` i `Phone` właściwości, inicjatora obiektów mogą być używane zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="2c75f-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```csharp  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
<span data-ttu-id="2c75f-121">Kontynuując nasze `Customer` klasy, założono, że jest źródło danych o nazwie `IncomingOrders`oraz że dla każdego zamówienia o dużej `OrderSize`, chcielibyśmy utworzyć nową `Customer` na podstawie tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="2c75f-121">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="2c75f-122">Zapytania LINQ mogą być wykonywane w tym źródle danych i użyj inicjowania obiektu, aby wypełnić kolekcję:</span><span class="sxs-lookup"><span data-stu-id="2c75f-122">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>
```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```
<span data-ttu-id="2c75f-123">Źródło danych może mieć więcej właściwości leżącego kulisy niż `Customer` klasy takie jak `OrderSize`, ale przy użyciu inicjowania obiektu danych zwróconych przez kwerendę jest profilowany na typ danych żądany; Wybierzmy danych, która jest odpowiednia dla klasy Nasze.</span><span class="sxs-lookup"><span data-stu-id="2c75f-123">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="2c75f-124">Co w efekcie mamy `IEnumerable` wypełnione przy użyciu nowego `Customer`Chcieliśmy s.</span><span class="sxs-lookup"><span data-stu-id="2c75f-124">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="2c75f-125">Powyższe można, również będą zapisywane w składni metody LINQ firmy:</span><span class="sxs-lookup"><span data-stu-id="2c75f-125">The above can also be written in LINQ's method syntax:</span></span>
```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```
 <span data-ttu-id="2c75f-126">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="2c75f-126">For more information, see:</span></span>
 
 - [<span data-ttu-id="2c75f-127">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="2c75f-127">Object and Collection Initializers</span></span>](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

 - [<span data-ttu-id="2c75f-128">Składnia wyrażeń dla standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="2c75f-128">Query Expression Syntax for Standard Query Operators</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="2c75f-129">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="2c75f-129">Anonymous Types</span></span>  
 <span data-ttu-id="2c75f-130">Typ anonimowy jest tworzony przez kompilator i nazwę typu jest dostępna tylko dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2c75f-130">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="2c75f-131">Typy anonimowe zapewniają wygodny sposób grupowania zestawu właściwości tymczasowo w wyniku zapytania bez konieczności wcześniejszego definiowania oddzielnego typu nazwanego.</span><span class="sxs-lookup"><span data-stu-id="2c75f-131">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="2c75f-132">Typy anonimowe są inicjowane za pomocą nowego wyrażenia i inicjatora obiektów, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="2c75f-132">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```csharp
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="2c75f-133">Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="2c75f-133">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="2c75f-134">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="2c75f-134">Extension Methods</span></span>  
 <span data-ttu-id="2c75f-135">Metody rozszerzenia jest statycznej metody, które mogą być skojarzone z typem, dzięki czemu można wywołać, tak jakby był metodą wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="2c75f-135">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="2c75f-136">Ta funkcja umożliwia, w efekcie "add" nowych metod do istniejących typów bez faktycznie ich modyfikowania.</span><span class="sxs-lookup"><span data-stu-id="2c75f-136">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="2c75f-137">Standardowe operatory zapytań są zestawem metody rozszerzenia, które zapewniają [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania funkcji dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="2c75f-137">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="2c75f-138">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="2c75f-138">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="2c75f-139">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="2c75f-139">Lambda Expressions</span></span>  
 <span data-ttu-id="2c75f-140">Wyrażenie lambda jest funkcją śródwierszową, który używa = > operator do oddzielania parametrów w treści funkcji wejściowych i mogą być konwertowane w czasie kompilacji do delegata lub drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2c75f-140">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="2c75f-141">W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programowania, można napotkać wyrażenia lambda po wprowadzeniu wywołania metody bezpośredniej do standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="2c75f-141">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="2c75f-142">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="2c75f-142">For more information, see:</span></span>  
  
-   [<span data-ttu-id="2c75f-143">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="2c75f-143">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="2c75f-144">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="2c75f-144">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="2c75f-145">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="2c75f-145">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
   
## <a name="see-also"></a><span data-ttu-id="2c75f-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c75f-146">See Also</span></span>

- [<span data-ttu-id="2c75f-147">Zapytanie o języku zintegrowanym (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2c75f-147">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
