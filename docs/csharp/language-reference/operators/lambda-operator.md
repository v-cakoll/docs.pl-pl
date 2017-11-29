---
title: "=&gt;Operator (odwołanie w C#)"
ms.date: 10/02/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44cb0485aefa8b0ab10a00ae0525180020ce436d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="55248-102">=&gt;Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="55248-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="55248-103">`=>` Operator może być używany na dwa sposoby w języku C#:</span><span class="sxs-lookup"><span data-stu-id="55248-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="55248-104">Jako [operatora lambda](#lamba-operator) w [wyrażenia lambda](../../lambda-expressions.md), zmienne wejściowe go oddziela od treści lambda.</span><span class="sxs-lookup"><span data-stu-id="55248-104">As the [lambda operator](#lamba-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="55248-105">W [definicja treść wyrażenia](#expression-body-definition), jego oddziela nazwę elementu członkowskiego z implementacją elementu.</span><span class="sxs-lookup"><span data-stu-id="55248-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="55248-106">Lambda operator</span><span class="sxs-lookup"><span data-stu-id="55248-106">Lambda operator</span></span>

<span data-ttu-id="55248-107">`=>` Token jest nazywany operatora lambda.</span><span class="sxs-lookup"><span data-stu-id="55248-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="55248-108">Jest on używany w *wyrażenia lambda* do oddzielania zmienne wejściowe po lewej stronie z treści lambda po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="55248-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="55248-109">Wyrażenia lambda są wbudowane wyrażenia podobna do metody anonimowe, ale bardziej elastyczne. są często używane w zapytań LINQ, które są wyrażane w składni metody.</span><span class="sxs-lookup"><span data-stu-id="55248-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="55248-110">Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="55248-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="55248-111">Poniższy przykład przedstawia dwa sposoby, aby znaleźć i wyświetlić długość ciągu najkrótszy w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="55248-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="55248-112">Pierwsza część przykładzie zastosowanie wyrażenia lambda (`w => w.Length`) do każdego elementu `words` tablicy, a następnie używa <xref:System.Linq.Enumerable.Min%2A> metody do znalezienia najmniejszej długości.</span><span class="sxs-lookup"><span data-stu-id="55248-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="55248-113">Do porównania drugiej części przykładzie pokazano dłużej używaną do tak samo postąpić w składni zapytania.</span><span class="sxs-lookup"><span data-stu-id="55248-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a><span data-ttu-id="55248-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55248-114">Remarks</span></span>  
 <span data-ttu-id="55248-115">`=>` Operator ma takie samo pierwszeństwo jako operator przypisania (`=`) i jest łączny prawo.</span><span class="sxs-lookup"><span data-stu-id="55248-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="55248-116">Można jawnie określić typ zmiennej wejściowy lub pozwolić kompilatora wnioskować w obu przypadkach zmienna jest silnie typizowane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="55248-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="55248-117">Po określeniu typu, należy ująć w nazwy typu i nazwy zmiennych w nawiasach, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="55248-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="55248-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="55248-118">Example</span></span>  
 <span data-ttu-id="55248-119">Poniższy przykład przedstawia sposób wyrażenia lambda przeciążenia operatora standardowej kwerendy <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> który przyjmuje dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="55248-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="55248-120">Wyrażenie lambda ma więcej niż jeden parametr, parametry muszą być ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="55248-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="55248-121">Drugi parametr `index`, reprezentuje indeks bieżącego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="55248-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="55248-122">`Where` Wyrażenie zwraca wszystkie ciągi o długości są mniejsze niż ich położenia indeks w tablicy.</span><span class="sxs-lookup"><span data-stu-id="55248-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a><span data-ttu-id="55248-123">Definicja treść wyrażenia</span><span class="sxs-lookup"><span data-stu-id="55248-123">Expression body definition</span></span>

<span data-ttu-id="55248-124">Definicja treść wyrażenia udostępnia implementację elementu członkowskiego w postaci wysokiej skrócone, czytelne.</span><span class="sxs-lookup"><span data-stu-id="55248-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="55248-125">Ma następującą składnię ogólne:</span><span class="sxs-lookup"><span data-stu-id="55248-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="55248-126">gdzie *wyrażenie* jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="55248-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="55248-127">Należy pamiętać, że *wyrażenie* może być *wyrażenia instrukcji* tylko jeśli element członkowski zwracany typ jest `void`, lub jeśli element jest konstruktorem lub finalizatora.</span><span class="sxs-lookup"><span data-stu-id="55248-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="55248-128">Definicje treść wyrażenia metody i instrukcje get właściwości są obsługiwane począwszy od języka C# 6.</span><span class="sxs-lookup"><span data-stu-id="55248-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="55248-129">Wyrażenie treści definicji dla konstruktorów, finalizatory, instrukcje ustawić właściwości i indeksatorów są obsługiwane w programie C# 7.</span><span class="sxs-lookup"><span data-stu-id="55248-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="55248-130">Poniżej znajduje się definicja treść wyrażenia `Person.ToString` metody:</span><span class="sxs-lookup"><span data-stu-id="55248-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="55248-131">Jest to wersja skrócona definicji następujące metody:</span><span class="sxs-lookup"><span data-stu-id="55248-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="55248-132">Aby uzyskać bardziej szczegółowe informacje dotyczące definicji treść wyrażenia, zobacz [zabudowanych wyrażenia elementów członkowskich](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="55248-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55248-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55248-133">See Also</span></span>  
<span data-ttu-id="55248-134">[Odwołanie w C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="55248-134">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="55248-135">[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="55248-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="55248-136">[Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="55248-136">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
<span data-ttu-id="55248-137">[Członkowie zabudowanych wyrażenia](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="55248-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>