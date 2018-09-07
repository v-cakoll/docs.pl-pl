---
title: =&gt; Operator (odwołanie w C#)
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: b9216cf61b6b9368112f769d952457df4aab4297
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080540"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="e194b-102">=&gt; Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e194b-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="e194b-103">`=>` Operator może być używany na dwa sposoby, w języku C#:</span><span class="sxs-lookup"><span data-stu-id="e194b-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="e194b-104">Jako [operatora lambda](#lamba-operator) w [wyrażenia lambda](../../lambda-expressions.md), z treści lambda są dzielone zmienne wejściowe.</span><span class="sxs-lookup"><span data-stu-id="e194b-104">As the [lambda operator](#lamba-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="e194b-105">W [definicja treści wyrażenia](#expression-body-definition), nazwa elementu członkowskiego rozdziela od implementacji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e194b-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="e194b-106">Lambda operator</span><span class="sxs-lookup"><span data-stu-id="e194b-106">Lambda operator</span></span>

<span data-ttu-id="e194b-107">`=>` Wywołanie operatora lambda tokenu.</span><span class="sxs-lookup"><span data-stu-id="e194b-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="e194b-108">Jest on używany w *wyrażeń lambda* do oddzielania zmienne wejściowe po lewej stronie z treści lambda po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="e194b-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="e194b-109">Wyrażenia lambda są wbudowane wyrażenia podobne do metod anonimowych, ale bardziej elastyczne. one są często używane w zapytaniach LINQ, które są wyrażone w składni metody.</span><span class="sxs-lookup"><span data-stu-id="e194b-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="e194b-110">Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e194b-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="e194b-111">Poniższy przykład przedstawia dwa sposoby, aby znaleźć i wyświetlić długość ciągu najkrótszej w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="e194b-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="e194b-112">Pierwsza część przykładu stosuje się do wyrażenia lambda (`w => w.Length`) do każdego elementu `words` tablicy, a następnie używa <xref:System.Linq.Enumerable.Min%2A> metody do znalezienia najmniejszej długości.</span><span class="sxs-lookup"><span data-stu-id="e194b-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="e194b-113">Dla porównania druga część przykład pokazuje dłużej rozwiązanie, które używa składni zapytań, aby zrobić to samo.</span><span class="sxs-lookup"><span data-stu-id="e194b-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
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
  
### <a name="remarks"></a><span data-ttu-id="e194b-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e194b-114">Remarks</span></span>  
 <span data-ttu-id="e194b-115">`=>` Operator ma takie samo pierwszeństwo jak operator przypisania (`=`) i jest zespolony z prawej.</span><span class="sxs-lookup"><span data-stu-id="e194b-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="e194b-116">Możesz jawnie określić typ zmienna wejściowa lub pozwolić kompilatorowi wydedukować w obu przypadkach zmienna zdecydowanie jest wpisane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e194b-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="e194b-117">Po określeniu typu, należy ująć nazwę typu, a nazwa zmiennej w nawiasach, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e194b-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="e194b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="e194b-118">Example</span></span>  
 <span data-ttu-id="e194b-119">Poniższy przykład pokazuje, jak wyrażenia lambda przeciążenie metody standardowego operatora zapytania <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> która przyjmuje dwa argumenty.</span><span class="sxs-lookup"><span data-stu-id="e194b-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="e194b-120">Ponieważ wyrażenie lambda ma więcej niż jeden parametr, parametry muszą być ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="e194b-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="e194b-121">Drugi parametr `index`, reprezentuje indeks bieżącego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e194b-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="e194b-122">`Where` Wyrażenie zwraca wszystkie ciągi, których długości jest mniejsza od ich pozycji indeksu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="e194b-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
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
## <a name="expression-body-definition"></a><span data-ttu-id="e194b-123">Definicja treści wyrażenia</span><span class="sxs-lookup"><span data-stu-id="e194b-123">Expression body definition</span></span>

<span data-ttu-id="e194b-124">Definicja treści wyrażenia dostarcza implementację elementu członkowskiego w wysoce skróconego postaci umożliwiającej odczyt.</span><span class="sxs-lookup"><span data-stu-id="e194b-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="e194b-125">Ma następującej składni ogólnej:</span><span class="sxs-lookup"><span data-stu-id="e194b-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="e194b-126">gdzie *wyrażenie* jest prawidłowym wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="e194b-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="e194b-127">Należy pamiętać, że *wyrażenie* może być *wyrażenie instrukcji* tylko jeśli element członkowski zwracany typ jest `void`, lub, jeśli element jest konstruktor lub finalizatora.</span><span class="sxs-lookup"><span data-stu-id="e194b-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="e194b-128">Definicje treści wyrażenia dla metod i właściwości, instrukcje get są obsługiwane, począwszy od C# 6.</span><span class="sxs-lookup"><span data-stu-id="e194b-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="e194b-129">Definicje treści wyrażenia dla konstruktorów finalizatorów, ustawić właściwości instrukcji, a indeksatory są obsługiwane, począwszy od C# 7.</span><span class="sxs-lookup"><span data-stu-id="e194b-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="e194b-130">Oto definicja treści wyrażenia dla `Person.ToString` metody:</span><span class="sxs-lookup"><span data-stu-id="e194b-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="e194b-131">Jest wersją skróconą następującą definicję metody:</span><span class="sxs-lookup"><span data-stu-id="e194b-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="e194b-132">Aby uzyskać szczegółowe informacje na temat definicji treści wyrażenia, zobacz [elementy członkowskie z wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="e194b-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e194b-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e194b-133">See Also</span></span>

- [<span data-ttu-id="e194b-134">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e194b-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)   
- [<span data-ttu-id="e194b-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e194b-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)   
- [<span data-ttu-id="e194b-136">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="e194b-136">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
- <span data-ttu-id="e194b-137">[Elementy członkowskie z wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="e194b-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>