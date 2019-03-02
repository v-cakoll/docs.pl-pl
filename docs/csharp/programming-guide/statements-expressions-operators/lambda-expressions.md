---
title: Wyrażenia lambda - C# Programming Guide
ms.custom: seodec18
ms.date: 03/03/2017
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 77701653abacbe6d876c0890a11586f0840bad5d
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200900"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="06d49-102">Wyrażenia lambda (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="06d49-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="06d49-103">Wyrażenie lambda jest [funkcja anonimowa](anonymous-methods.md) używanego do utworzenia [delegatów](../delegates/using-delegates.md) lub [drzewa wyrażeń](../concepts/expression-trees/index.md) typów.</span><span class="sxs-lookup"><span data-stu-id="06d49-103">A lambda expression is an [anonymous function](anonymous-methods.md) that you can use to create [delegates](../delegates/using-delegates.md) or [expression tree](../concepts/expression-trees/index.md) types.</span></span> <span data-ttu-id="06d49-104">Za pomocą wyrażenia lambda można pisać funkcje lokalne, które mogą być przekazywane jako argumenty lub zwracane jako wartość wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="06d49-104">By using lambda expressions, you can write local functions that can be passed as arguments or returned as the value of function calls.</span></span> <span data-ttu-id="06d49-105">Wyrażenia lambda są szczególnie przydatne w przypadku pisania wyrażeń zapytań w języku LINQ.</span><span class="sxs-lookup"><span data-stu-id="06d49-105">Lambda expressions are particularly helpful for writing LINQ query expressions.</span></span>
  
<span data-ttu-id="06d49-106">Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda [ => ](../../../csharp/language-reference/operators/lambda-operator.md), i umieścić blok wyrażenia lub instrukcji po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="06d49-106">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator [=>](../../../csharp/language-reference/operators/lambda-operator.md), and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="06d49-107">Na przykład, wyrażenie lambda `x => x * x` określa parametr o nazwie `x` i zwraca wartość `x` kwadratów.</span><span class="sxs-lookup"><span data-stu-id="06d49-107">For example, the lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="06d49-108">To wyrażenie można przypisać do typu delegata, tak jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="06d49-108">You can assign this expression to a delegate type, as the following example shows:</span></span>  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 <span data-ttu-id="06d49-109">Aby utworzyć typ drzewa wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="06d49-109">To create an expression tree type:</span></span>  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="06d49-110">`=>` Operator ma ten sam priorytet, jako przydział (`=`) i jest [łączność do prawej strony](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (zobacz sekcję "Łączność" artykułu operatory).</span><span class="sxs-lookup"><span data-stu-id="06d49-110">The `=>` operator has the same precedence as assignment (`=`) and is [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (see "Associativity" section of the Operators article).</span></span>  
  
 <span data-ttu-id="06d49-111">Wyrażenia lambda są używane w oparte na metodzie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] jako argumenty do standardowych metod operatorów kwerendy takich zapytań jak <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="06d49-111">Lambdas are used in method-based [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries as arguments to standard query operator methods such as <xref:System.Linq.Enumerable.Where%2A>.</span></span>  
  
 <span data-ttu-id="06d49-112">Kiedy używasz składni oparte na metodzie do wywołania <xref:System.Linq.Enumerable.Where%2A> method in Class metoda <xref:System.Linq.Enumerable> klasy (tak jak w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do obiektów i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) parametr jest typem delegowanym <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06d49-112">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Where%2A> method in the <xref:System.Linq.Enumerable> class (as you do in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="06d49-113">Użycie wyrażenia lambda jest najwygodniejszym sposobem tworzenia delegata.</span><span class="sxs-lookup"><span data-stu-id="06d49-113">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="06d49-114">Po wywołaniu tej samej metody, na przykład <xref:System.Linq.Queryable?displayProperty=nameWithType> klasy (tak jak w [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]), a następnie typ parametru jest <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>< Func\> gdzie Func jest dowolnym delegatem Func o długości do szesnastu parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="06d49-114">When you call the same method in, for example, the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) then the parameter type is an <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> where Func is any of the Func delegates with up to sixteen input parameters.</span></span> <span data-ttu-id="06d49-115">I znowu wyrażenie lambda jest tylko bardzo zwięzłym sposobem konstruowania takiego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="06d49-115">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="06d49-116">Dzięki wyrażeniom lambda `Where` wywołania wyglądają podobnie, choć w rzeczywistości typ obiektu utworzonego z lambdy jest inny.</span><span class="sxs-lookup"><span data-stu-id="06d49-116">The lambdas allow the `Where` calls to look similar although in fact the type of object created from the lambda is different.</span></span>  
  
 <span data-ttu-id="06d49-117">W poprzednim przykładzie, zwróć uwagę, że podpis delegata ma jeden niejawnie wpisany parametr wejściowy typu `int`i zwraca `int`.</span><span class="sxs-lookup"><span data-stu-id="06d49-117">In the previous example, notice that the delegate signature has one implicitly-typed input parameter of type `int`, and returns an `int`.</span></span> <span data-ttu-id="06d49-118">Wyrażenie lambda można przekonwertować na delegata tego typu, ponieważ także ma jeden parametr wejściowy (`x`) i zwracana wartość, którą kompilator może niejawnie przekonwertować na typ `int`.</span><span class="sxs-lookup"><span data-stu-id="06d49-118">The lambda expression can be converted to a delegate of that type because it also has one input parameter (`x`) and a return value that the compiler can implicitly convert to type `int`.</span></span> <span data-ttu-id="06d49-119">(Wnioskowanie typów omówiono bardziej szczegółowo w następnych sekcjach). Kiedy delegat jest wywołany za pomocą parametru wejściowego 5, zwraca wynik 25.</span><span class="sxs-lookup"><span data-stu-id="06d49-119">(Type inference is discussed in more detail in the following sections.) When the delegate is invoked by using an input parameter of 5, it returns a result of 25.</span></span>  
  
 <span data-ttu-id="06d49-120">Wyrażenia lambda nie są dozwolone w lewej części [jest](../../../csharp/language-reference/keywords/is.md) lub [jako](../../../csharp/language-reference/keywords/as.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="06d49-120">Lambdas are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) or [as](../../../csharp/language-reference/keywords/as.md) operator.</span></span>  
  
 <span data-ttu-id="06d49-121">Wszystkie ograniczenia, które dotyczą metod anonimowych, dotyczą także wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="06d49-121">All restrictions that apply to anonymous methods also apply to lambda expressions.</span></span> <span data-ttu-id="06d49-122">Aby uzyskać więcej informacji, zobacz [anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="06d49-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
## <a name="expression-lambdas"></a><span data-ttu-id="06d49-123">Lambdy wyrażeń</span><span class="sxs-lookup"><span data-stu-id="06d49-123">Expression lambdas</span></span>

 <span data-ttu-id="06d49-124">Wyrażenie lambda z wyrażeniem po prawej stronie = > — operator jest wywoływana *wyrażenia lambda*.</span><span class="sxs-lookup"><span data-stu-id="06d49-124">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="06d49-125">Lambdy wyrażeń są często używane w konstrukcji [drzew wyrażeń](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="06d49-125">Expression lambdas are used extensively in the construction of [Expression Trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="06d49-126">Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:</span><span class="sxs-lookup"><span data-stu-id="06d49-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>
  
```csharp
(input-parameters) => expression
```

 <span data-ttu-id="06d49-127">Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="06d49-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="06d49-128">Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="06d49-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>  
  
```csharp
(x, y) => x == y
```

 <span data-ttu-id="06d49-129">Czasami wywnioskowanie typów wejściowych jest dla kompilatora trudne lub wręcz niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="06d49-129">Sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="06d49-130">W takiej sytuacji można jawnie określić typy, tak jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="06d49-130">When this occurs, you can specify the types explicitly as shown in the following example:</span></span>  
  
```csharp
(int x, string s) => s.Length > x
```
 <span data-ttu-id="06d49-131">Typy parametru wejściowego muszą być wszystkie jawne lub niejawne; w przeciwnym razie C# generuje [CS0748](../../misc/cs0748.md) błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="06d49-131">Input parameter types must be all explicit or all implicit; otherwise, C# generates a [CS0748](../../misc/cs0748.md) compiler error.</span></span>

 <span data-ttu-id="06d49-132">Określanie braku parametrów wejściowych za pomocą pustych nawiasów:</span><span class="sxs-lookup"><span data-stu-id="06d49-132">Specify zero input parameters with empty parentheses:</span></span>  
  
```csharp
() => SomeMethod()
```

 <span data-ttu-id="06d49-133">Należy zauważyć, że w poprzednim przykładzie treść wyrażenia lambda może składać się z wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="06d49-133">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="06d49-134">Jednak w przypadku tworzenia drzew wyrażeń, które będą obliczane poza programem .NET Framework, na przykład w programie SQL Server, nie należy używać wywołań metod w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="06d49-134">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="06d49-135">Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="06d49-135">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>  
  
## <a name="statement-lambdas"></a><span data-ttu-id="06d49-136">Lambdy instrukcji</span><span class="sxs-lookup"><span data-stu-id="06d49-136">Statement lambdas</span></span>

 <span data-ttu-id="06d49-137">Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="06d49-137">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>  
  
<span data-ttu-id="06d49-138">(parametry wejściowe) = > {instrukcja;}</span><span class="sxs-lookup"><span data-stu-id="06d49-138">(input-parameters) => { statement; }</span></span>

 <span data-ttu-id="06d49-139">Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.</span><span class="sxs-lookup"><span data-stu-id="06d49-139">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>  
  
[!code-csharp[StatementLambda#1](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLambda#2](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#2)]

 <span data-ttu-id="06d49-140">Lambd instrukcji, podobnie jak metod anonimowych, nie można używać do tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="06d49-140">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="06d49-141">Lambdy asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="06d49-141">Async lambdas</span></span>

 <span data-ttu-id="06d49-142">Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają Przetwarzanie asynchroniczne przy użyciu [async](../../../csharp/language-reference/keywords/async.md) i [await](../../../csharp/language-reference/keywords/await.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="06d49-142">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../../csharp/language-reference/keywords/async.md) and [await](../../../csharp/language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="06d49-143">Na przykład, poniższy przykład Windows Forms zawiera program obsługi zdarzeń, który wywołuje i czeka na metodę asynchroniczną `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="06d49-143">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 <span data-ttu-id="06d49-144">Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="06d49-144">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="06d49-145">Aby dodać ten program obsługi `async` modyfikator przed listą parametrów lambda, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="06d49-145">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 <span data-ttu-id="06d49-146">Aby uzyskać więcej informacji na temat sposobu tworzenia i używania metod asynchronicznych, zobacz [Asynchronous Programming with async i await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="06d49-146">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="06d49-147">Lambdy ze standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="06d49-147">Lambdas with the standard query operators</span></span>

 <span data-ttu-id="06d49-148">Wiele operatorów standardowej kwerendy posiada parametr wejściowy, którego typ jest jednym z <xref:System.Func%602> rodziny ogólnych delegatów.</span><span class="sxs-lookup"><span data-stu-id="06d49-148">Many standard query operators have an input parameter whose type is one of the <xref:System.Func%602> family of generic delegates.</span></span> <span data-ttu-id="06d49-149">Te delegaty używają parametrów typu użycia, aby zdefiniować liczbę i typy parametrów wejściowych oraz zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="06d49-149">These delegates use type parameters to define the number and types of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="06d49-150">`Func` Obiekty delegowane są bardzo przydatne do hermetyzowania wyrażeń zdefiniowanych przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="06d49-150">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="06d49-151">Na przykład rozważmy następujący typ delegata:</span><span class="sxs-lookup"><span data-stu-id="06d49-151">For example, consider the following delegate type:</span></span>  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 <span data-ttu-id="06d49-152">Delegat może być utworzone jako `Func<int,bool> myFunc` gdzie `int` jest parametrem wejściowym i `bool` jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="06d49-152">The delegate can be instantiated as `Func<int,bool> myFunc` where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="06d49-153">Wartość zwracana jest zawsze określona w ostatnim parametrze typu.</span><span class="sxs-lookup"><span data-stu-id="06d49-153">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="06d49-154">`Func<int, string, bool>` Definiuje delegata z dwoma parametrami wejściowymi `int` i `string`, a zwracany typ `bool`.</span><span class="sxs-lookup"><span data-stu-id="06d49-154">`Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="06d49-155">Następujące `Func` delegata, gdy jest wywoływany, zwróci wartość true lub false, aby wskazać, czy parametr wejściowy jest równy 5:</span><span class="sxs-lookup"><span data-stu-id="06d49-155">The following `Func` delegate, when it is invoked, will return true or false to indicate whether the input parameter is equal to 5:</span></span>  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 <span data-ttu-id="06d49-156">Można również dostarczyć Wyrażenie lambda, gdy typ argumentu jest `Expression<Func>`, na przykład w standardowe operatory zapytań zdefiniowanych w System.Linq.Queryable.</span><span class="sxs-lookup"><span data-stu-id="06d49-156">You can also supply a lambda expression when the argument type is an `Expression<Func>`, for example in the standard query operators that are defined in System.Linq.Queryable.</span></span> <span data-ttu-id="06d49-157">Po określeniu `Expression<Func>` argument, lambda będzie podawana do drzewa wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="06d49-157">When you specify an `Expression<Func>` argument, the lambda will be compiled to an expression tree.</span></span>  
  
 <span data-ttu-id="06d49-158">Operator standardowego zapytania, <xref:System.Linq.Enumerable.Count%2A> metody jest następująca:</span><span class="sxs-lookup"><span data-stu-id="06d49-158">A standard query operator, the <xref:System.Linq.Enumerable.Count%2A> method, is shown here:</span></span>  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 <span data-ttu-id="06d49-159">Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="06d49-159">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="06d49-160">To konkretne wyrażenie lambda liczy te liczby całkowite (`n`) które podzielone przez dwa dają resztę 1.</span><span class="sxs-lookup"><span data-stu-id="06d49-160">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>  
  
 <span data-ttu-id="06d49-161">Następujący wiersz kodu stworzy sekwencję która zawiera wszystkie elementy w `numbers` tablicy, które są po lewej stronie 9, ponieważ jest to pierwszy numer w sekwencji, która nie spełnia warunku:</span><span class="sxs-lookup"><span data-stu-id="06d49-161">The following line of code produces a sequence that contains all elements in the `numbers` array that are to the left side of the 9 because that's the first number in the sequence that doesn't meet the condition:</span></span>  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 <span data-ttu-id="06d49-162">W tym przykładzie pokazano, jak określić wiele parametrów danych wejściowych, umieszczając je w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="06d49-162">This example shows how to specify multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="06d49-163">Metoda zwraca wszystkie elementy w tablicy liczb, dopóki nie napotka liczby, której wartość jest mniejsza niż jej pozycja.</span><span class="sxs-lookup"><span data-stu-id="06d49-163">The method returns all the elements in the numbers array until a number is encountered whose value is less than its position.</span></span> <span data-ttu-id="06d49-164">Nie należy mylić operatora lambda (`=>`) z operatorem większe niż lub równe (`>=`).</span><span class="sxs-lookup"><span data-stu-id="06d49-164">Do not confuse the lambda operator (`=>`) with the greater than or equal operator (`>=`).</span></span>  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a><span data-ttu-id="06d49-165">Wnioskowanie o typie w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="06d49-165">Type inference in lambdas</span></span>

 <span data-ttu-id="06d49-166">Podczas pisania wyrażeń lambda często nie trzeba określać typu parametrów wejściowych, ponieważ kompilator może wywnioskować typ na podstawie treści wyrażenia lambda, typu delegata parametru i innych czynników, tak jak opisano w specyfikacji języka C#.</span><span class="sxs-lookup"><span data-stu-id="06d49-166">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter’s delegate type, and other factors as described in the C# Language Specification.</span></span> <span data-ttu-id="06d49-167">Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="06d49-167">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="06d49-168">Tak, jeśli jest wykonywane zapytanie `IEnumerable<Customer>`, a następnie wywnioskowana jest zmienna wejściowa jest `Customer` obiektu, co oznacza, że masz dostęp do metod i właściwości:</span><span class="sxs-lookup"><span data-stu-id="06d49-168">So if you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 <span data-ttu-id="06d49-169">Ogólne reguły dotyczące wyrażeń lambda są następujące:</span><span class="sxs-lookup"><span data-stu-id="06d49-169">The general rules for lambdas are as follows:</span></span>  
  
-   <span data-ttu-id="06d49-170">Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.</span><span class="sxs-lookup"><span data-stu-id="06d49-170">The lambda must contain the same number of parameters as the delegate type.</span></span>  
  
-   <span data-ttu-id="06d49-171">Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="06d49-171">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>  
  
-   <span data-ttu-id="06d49-172">Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="06d49-172">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>  
  
 <span data-ttu-id="06d49-173">Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów wspólnych nie obejmuje wewnętrznej koncepcji „wyrażenia lambda”.</span><span class="sxs-lookup"><span data-stu-id="06d49-173">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="06d49-174">Jednak czasami wygodnie jest mówić potocznie o „typie” wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="06d49-174">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="06d49-175">W takich przypadkach typ odnosi się do typu delegata lub <xref:System.Linq.Expressions.Expression> typ do którego jest konwertowane Wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="06d49-175">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>  
  
## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="06d49-176">Zakres zmiennych w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="06d49-176">Variable scope in lambda expressions</span></span>

 <span data-ttu-id="06d49-177">Wyrażenia lambda mogą odwoływać się do *zmiennych zewnętrznych* (zobacz [anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) znajdujących się w zakresie metody definiującej funkcję lambda lub w zakresie typu, który zawiera wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="06d49-177">Lambdas can refer to *outer variables* (see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="06d49-178">Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="06d49-178">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="06d49-179">Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda.</span><span class="sxs-lookup"><span data-stu-id="06d49-179">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="06d49-180">W poniższym przykładzie pokazano te reguły:</span><span class="sxs-lookup"><span data-stu-id="06d49-180">The following example demonstrates these rules:</span></span>  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 <span data-ttu-id="06d49-181">Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="06d49-181">The following rules apply to variable scope in lambda expressions:</span></span>  
  
-   <span data-ttu-id="06d49-182">Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="06d49-182">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>  
  
-   <span data-ttu-id="06d49-183">Zmienne zawarte w wyrażeniu lambda nie są widoczne w metodzie zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="06d49-183">Variables introduced within a lambda expression are not visible in the outer method.</span></span>  
  
-   <span data-ttu-id="06d49-184">Wyrażenie lambda nie może bezpośrednio przechwycić `in`, `ref`, lub `out` parametr z otaczającym metody.</span><span class="sxs-lookup"><span data-stu-id="06d49-184">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>  
  
-   <span data-ttu-id="06d49-185">Instrukcja return w wyrażeniu lambda nie powoduje wykonania instrukcji return w otaczającej go metodzie.</span><span class="sxs-lookup"><span data-stu-id="06d49-185">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>  
  
-   <span data-ttu-id="06d49-186">Wyrażenie lambda nie może zawierać `goto` instrukcji `break` instrukcji lub `continue` instrukcję, która znajduje się wewnątrz funkcji lambda, jeśli obiekt docelowy instrukcji jump leży poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="06d49-186">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="06d49-187">Błędem jest również instrukcja skoku poza blok funkcji lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="06d49-187">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="06d49-188">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="06d49-188">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="06d49-189">polecany rozdział książki</span><span class="sxs-lookup"><span data-stu-id="06d49-189">Featured book chapter</span></span>

 <span data-ttu-id="06d49-190">[Delegatów, zdarzeń i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3.0 Cookbook, Third Edition: Ponad 250 rozwiązań dla C# ekspertów w programowaniu w wersji 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="06d49-190">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d49-191">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06d49-191">See also</span></span>

- [<span data-ttu-id="06d49-192">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="06d49-192">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="06d49-193">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="06d49-193">LINQ (Language-Integrated Query)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="06d49-194">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="06d49-194">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [<span data-ttu-id="06d49-195">is</span><span class="sxs-lookup"><span data-stu-id="06d49-195">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="06d49-196">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="06d49-196">Expression Trees</span></span>](../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="06d49-197">Visual Studio 2008 C# Samples (zobacz pliki LINQ przykładowe zapytania i XQuery program)</span><span class="sxs-lookup"><span data-stu-id="06d49-197">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="06d49-198">Powtarzalne wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="06d49-198">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
