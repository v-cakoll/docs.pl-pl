---
title: "Funkcje C# obsługujące LINQ"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2f5accb188e54e0d3e2b941832637ec33afc26b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="f8979-102">Funkcje C# obsługujące LINQ</span><span class="sxs-lookup"><span data-stu-id="f8979-102">C# Features That Support LINQ</span></span>
<span data-ttu-id="f8979-103">Poniższa sekcja wprowadza nowe konstrukcje języka wprowadzono w języku C# 3.0.</span><span class="sxs-lookup"><span data-stu-id="f8979-103">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="f8979-104">Chociaż te nowe funkcje są używane w stopniu z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, nie są one ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] i mogą być używane w dowolnym kontekście gdzie użyteczna je.</span><span class="sxs-lookup"><span data-stu-id="f8979-104">Although these new features are all used to a degree with [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, they are not limited to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] and can be used in any context where you find them useful.</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="f8979-105">Wyrażenia zapytań</span><span class="sxs-lookup"><span data-stu-id="f8979-105">Query Expressions</span></span>  
 <span data-ttu-id="f8979-106">Wyrażenia zapytań użyj składni deklaratywnej podobne do bazy danych SQL lub XQuery zapytania za pośrednictwem interfejsu IEnumerable kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f8979-106">Queries expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="f8979-107">W kompilacji czasu Składnia kwerendy jest konwertowana na wywołania metody do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy implementacja metody rozszerzenia operator standardowej kwerendy.</span><span class="sxs-lookup"><span data-stu-id="f8979-107">At compile time query syntax is converted to method calls to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="f8979-108">Aplikacje kontroli standardowych operatorów zapytań, które znajdują się w zakresie, określając odpowiedni obszar nazw z `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="f8979-108">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="f8979-109">Poniższe wyrażenie zapytania pobiera tablicę ciągów, grupy, zgodnie z pierwszego znaku w ciągu i porządkuje grup.</span><span class="sxs-lookup"><span data-stu-id="f8979-109">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 <span data-ttu-id="f8979-110">Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8979-110">For more information, see [LINQ Query Expressions](../../../../csharp/programming-guide/linq-query-expressions/index.md).</span></span>  
  
## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="f8979-111">Niejawnie wpisane zmienne (var)</span><span class="sxs-lookup"><span data-stu-id="f8979-111">Implicitly Typed Variables (var)</span></span>  
 <span data-ttu-id="f8979-112">Zamiast jawne określenie typu, gdy zadeklarować i zainicjuj zmienną, możesz użyć [var](../../../../csharp/language-reference/keywords/var.md) modyfikator nakazać kompilatora wnioskować i przypisać ten typ, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="f8979-112">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../../csharp/language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 <span data-ttu-id="f8979-113">Zmienne zadeklarowane jako `var` są po prostu jako silnie typizowaną jako zmienne o typie, określ w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="f8979-113">Variables declared as `var` are just as strongly-typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="f8979-114">Korzystanie z `var` sprawia, że można tworzyć typy anonimowe, ale może służyć do dowolnej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f8979-114">The use of `var` makes it possible to create anonymous types, but it can be used for any local variable.</span></span> <span data-ttu-id="f8979-115">Ponadto można deklarować tablic w trakcie pisania niejawne.</span><span class="sxs-lookup"><span data-stu-id="f8979-115">Arrays can also be declared with implicit typing.</span></span>  
  
 <span data-ttu-id="f8979-116">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="f8979-116">For more information, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="object-and-collection-initializers"></a><span data-ttu-id="f8979-117">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="f8979-117">Object and Collection Initializers</span></span>  
 <span data-ttu-id="f8979-118">Inicjatory obiektów i kolekcji umożliwiają inicjowanie obiektów bez jawnego wywołania konstruktora dla obiekt.</span><span class="sxs-lookup"><span data-stu-id="f8979-118">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="f8979-119">Inicjatory są zazwyczaj używane w wyrażeniach zapytań do ich projektu źródło danych do nowego typu danych.</span><span class="sxs-lookup"><span data-stu-id="f8979-119">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="f8979-120">Zakładając, że klasa o nazwie `Customer` z publicznych `Name` i `Phone` można używać właściwości, inicjatora obiektu zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="f8979-120">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 <span data-ttu-id="f8979-121">Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="f8979-121">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="f8979-122">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="f8979-122">Anonymous Types</span></span>  
 <span data-ttu-id="f8979-123">Typ anonimowy jest tworzony przez kompilator i nazwa typu jest dostępna tylko dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f8979-123">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="f8979-124">Typy anonimowe zapewnić wygodny sposób grupowania zestawu właściwości tymczasowo w wyniku zapytania bez konieczności zdefiniuj oddzielnej o nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="f8979-124">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="f8979-125">Typy anonimowe są inicjowane z nowym wyrażeniu i inicjatora obiektów, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="f8979-125">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 <span data-ttu-id="f8979-126">Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f8979-126">For more information, see [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="f8979-127">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="f8979-127">Extension Methods</span></span>  
 <span data-ttu-id="f8979-128">Metody rozszerzenia jest statyczną metodę, która może być skojarzony z typem, dzięki czemu można wywołać, tak jakby był on metodę wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="f8979-128">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="f8979-129">Ta funkcja umożliwia, w efekcie "Dodaj" nowych metod do istniejących typów nie modyfikując je.</span><span class="sxs-lookup"><span data-stu-id="f8979-129">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="f8979-130">Standardowe operatory zapytań to zbiór metody rozszerzenia, które zapewniają [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania funkcji dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="f8979-130">The standard query operators are a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="f8979-131">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f8979-131">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="f8979-132">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="f8979-132">Lambda Expressions</span></span>  
 <span data-ttu-id="f8979-133">Wyrażenie lambda jest wbudowanej funkcji, która używa = > operator do rozdzielenia parametrów z treści funkcji wejściowych i mogą być przekonwertowane na delegata lub drzewo wyrażeń w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f8979-133">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="f8979-134">W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programowania, można napotkać wyrażenia lambda po wprowadzeniu wywołania metody bezpośrednio do standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="f8979-134">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>  
  
 <span data-ttu-id="f8979-135">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="f8979-135">For more information, see:</span></span>  
  
-   [<span data-ttu-id="f8979-136">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="f8979-136">Anonymous Functions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [<span data-ttu-id="f8979-137">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="f8979-137">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [<span data-ttu-id="f8979-138">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="f8979-138">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a><span data-ttu-id="f8979-139">Właściwości zaimplementowane automatycznie</span><span class="sxs-lookup"><span data-stu-id="f8979-139">Auto-Implemented Properties</span></span>  
 <span data-ttu-id="f8979-140">Właściwości zaimplementowane automatycznie należy bardziej zwięzły deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="f8979-140">Auto-implemented properties make property-declaration more concise.</span></span> <span data-ttu-id="f8979-141">Jak pokazano w poniższym przykładzie w deklaracji właściwości, kompilator utworzy polem zapasowym prywatne i anonimowy, który nie jest dostępny z wyjątkiem za pośrednictwem metody pobierającej i ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="f8979-141">When you declare a property as shown in the following example, the compiler will create a private, anonymous backing field that is not accessible except through the property getter and setter.</span></span>  
  
```  
public string Name {get; set;}  
```  
  
 <span data-ttu-id="f8979-142">Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="f8979-142">For more information, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8979-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8979-143">See Also</span></span>  
 [<span data-ttu-id="f8979-144">Zapytanie o języku zintegrowanym (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="f8979-144">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
