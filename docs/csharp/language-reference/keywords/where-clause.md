---
title: Klauzula where (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: bc040e17f5c612b9fc43a9ef24fb6f15f0942b8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="ab3a4-102">Klauzula where (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ab3a4-102">where clause (C# Reference)</span></span>
<span data-ttu-id="ab3a4-103">`where` Klauzuli jest używany w wyrażeniu zapytania, aby określić, które elementy ze źródła danych zostaną zwrócone w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="ab3a4-104">Ma to zastosowanie warunek typu Boolean (*predykatu*) do każdego elementu źródłowego (odwołuje się zmienna zakresu) i zwraca te, dla których określony warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="ab3a4-105">Wyrażenie pojedynczego zapytania mogą zawierać wiele `where` klauzule i jedną klauzulę może zawierać wiele zakresie predykatu.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab3a4-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab3a4-106">Example</span></span>  
 <span data-ttu-id="ab3a4-107">W poniższym przykładzie `where` klauzuli odfiltrowuje wszystkie liczby, z wyjątkiem tych, które są mniej niż 5.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="ab3a4-108">Jeśli usuniesz `where` klauzuli, wszystkie liczby ze źródła danych będą zwracane.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="ab3a4-109">Wyrażenie `num < 5` jest predykatu, która jest stosowana do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ab3a4-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab3a4-110">Example</span></span>  
 <span data-ttu-id="ab3a4-111">W jednym `where` klauzuli, można określić dowolną liczbę predykaty odpowiednio przy użyciu [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) i [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="ab3a4-112">W poniższym przykładzie zapytanie określa dwa predykaty wybór liczby parzyste, które są mniej niż 5.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="ab3a4-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab3a4-113">Example</span></span>  
 <span data-ttu-id="ab3a4-114">A `where` klauzula może zawierać jedną lub kilka metod, które zwracają wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="ab3a4-115">W poniższym przykładzie `where` klauzuli używa metody w celu ustalenia, czy bieżąca wartość zmiennej zakresu jest parzysta lub nieparzysta.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="ab3a4-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab3a4-116">Remarks</span></span>  
 <span data-ttu-id="ab3a4-117">`where` Klauzula jest mechanizm filtrowania.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="ab3a4-118">Go może być umieszczony niemal z dowolnego miejsca w wyrażeniu zapytania z tym nie może być pierwszym lub ostatnim klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="ab3a4-119">A `where` klauzula może występować przed lub po [grupy](../../../csharp/language-reference/keywords/group-clause.md) klauzuli w zależności od tego, czy masz do filtrowania elementów źródła przed lub po ich grupowania.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-119">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="ab3a4-120">Jeśli określony predykat nie jest prawidłowy dla elementów w źródle danych, spowoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="ab3a4-121">To korzyścią silnego typu sprawdzania pochodzącymi [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab3a4-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="ab3a4-122">W czasie kompilacji `where` — słowo kluczowe jest konwertowany na wywołanie <xref:System.Linq.Enumerable.Where%2A> metody standardowe — Operator zapytań.</span><span class="sxs-lookup"><span data-stu-id="ab3a4-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab3a4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab3a4-123">See Also</span></span>  
 [<span data-ttu-id="ab3a4-124">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ab3a4-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="ab3a4-125">from, klauzula</span><span class="sxs-lookup"><span data-stu-id="ab3a4-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="ab3a4-126">select, klauzula</span><span class="sxs-lookup"><span data-stu-id="ab3a4-126">select clause</span></span>](../../../csharp/language-reference/keywords/select-clause.md)  
 [<span data-ttu-id="ab3a4-127">Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="ab3a4-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)  
 [<span data-ttu-id="ab3a4-128">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="ab3a4-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="ab3a4-129">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="ab3a4-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
