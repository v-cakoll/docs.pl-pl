---
title: try-catch (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: d1fd290444bc7841e32d955a4e7f2134afdbd484
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030895"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="374f3-102">try-catch (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="374f3-102">try-catch (C# Reference)</span></span>
<span data-ttu-id="374f3-103">Instrukcja try-catch, który składa się z `try` bloku, po której następuje co najmniej jeden `catch` zdań, która określa programy obsługi dla różnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="374f3-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="374f3-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="374f3-104">Remarks</span></span>  
 <span data-ttu-id="374f3-105">Gdy wyjątek jest generowany, środowisko uruchomieniowe języka wspólnego (CLR) wyszukuje `catch` instrukcję, która obsługuje ten wyjątek.</span><span class="sxs-lookup"><span data-stu-id="374f3-105">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="374f3-106">Jeśli aktualnie wykonywanej metody nie zawiera takie `catch` zablokować, CLR prezentuje metody, która wywołała bieżącą metodę, i tak dalej w górę stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="374f3-106">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="374f3-107">Jeśli nie `catch` blok zostanie znaleziony, a następnie CLR zostanie wyświetlony komunikat nieobsługiwany wyjątek użytkownikowi i zatrzymuje wykonywanie programu.</span><span class="sxs-lookup"><span data-stu-id="374f3-107">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>  
  
 <span data-ttu-id="374f3-108">`try` Blok zawiera chronioną kod, który może spowodować wystąpienie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="374f3-108">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="374f3-109">Blok jest wykonywany, dopóki nie zostanie zgłoszony wyjątek lub zakończyło się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="374f3-109">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="374f3-110">Na przykład, że próba zrzutowania `null` obiektu zgłasza <xref:System.NullReferenceException> wyjątek:</span><span class="sxs-lookup"><span data-stu-id="374f3-110">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>  
  
```csharp  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 <span data-ttu-id="374f3-111">Mimo że `catch` bez argumentów można użyć klauzuli można przechwycić wyjątek dowolnego typu, to użycie nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="374f3-111">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="374f3-112">Ogólnie rzecz biorąc należy tylko przechwytywać te wyjątki, które należy znać sposób sprawności.</span><span class="sxs-lookup"><span data-stu-id="374f3-112">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="374f3-113">W związku z tym, należy zawsze podać argument obiektu pochodną <xref:System.Exception?displayProperty=nameWithType> na przykład:</span><span class="sxs-lookup"><span data-stu-id="374f3-113">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
}  
```  
  
 <span data-ttu-id="374f3-114">Istnieje możliwość użycia więcej niż jednej określonej `catch` klauzuli w tej samej instrukcji try-catch.</span><span class="sxs-lookup"><span data-stu-id="374f3-114">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="374f3-115">W tym przypadku kolejność `catch` klauzule ważne jest, ponieważ `catch` klauzule są badane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="374f3-115">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="374f3-116">Rejestrować bardziej szczegółowe wyjątki przed mniej określone z nich.</span><span class="sxs-lookup"><span data-stu-id="374f3-116">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="374f3-117">Kompilator generuje błąd, jeśli kolejność, że Twoje catch blokuje tak, aby nigdy nie jest osiągalna nowsze bloku.</span><span class="sxs-lookup"><span data-stu-id="374f3-117">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>  
  
 <span data-ttu-id="374f3-118">Za pomocą `catch` argumentów jest jednym ze sposobów, aby filtrować pod kątem wyjątków, które ma obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="374f3-118">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="374f3-119">Umożliwia także filtr wyjątku, który dodatkowo sprawdza, czy wyjątek zdecydować, czy do jego obsługi.</span><span class="sxs-lookup"><span data-stu-id="374f3-119">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="374f3-120">Jeśli filtr wyjątku zwróci wartość false, wyszukiwanie w przypadku obsługi kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="374f3-120">If the exception filter returns false, then the search for a handler continues.</span></span>  
  
```csharp  
catch (ArgumentException e) when (e.ParamName == "…")  
{  
}  
```  
  
 <span data-ttu-id="374f3-121">Filtry wyjątków są preferowane w porównaniu do przechwytywania i ponowne generowanie (wyjaśnione poniżej), ponieważ filtry pozostaw stosu nieokaleczone.</span><span class="sxs-lookup"><span data-stu-id="374f3-121">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="374f3-122">Jeśli nowszej obsługi zrzuty stosu, zostanie wyświetlony, wyjątek pierwotnie pochodzenia, a nie tylko ostatnie miejsce, który był zgłaszany ponownie.</span><span class="sxs-lookup"><span data-stu-id="374f3-122">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="374f3-123">Typowym zastosowaniem wyrażenia filtru wyjątków jest rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="374f3-123">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="374f3-124">Można utworzyć filtr, która zawsze zwraca wartość FAŁSZ, który również dane wyjściowe do dziennika, możesz rejestrować wyjątki jako komputery przechodzą bez konieczności ich i ponownego zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="374f3-124">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>  
  
 <span data-ttu-id="374f3-125">A [throw](../../../csharp/language-reference/keywords/throw.md) instrukcja może być używana w `catch` bloku, aby można było ponownie zgłosić wyjątek, który zostanie przechwycony przez `catch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="374f3-125">A [throw](../../../csharp/language-reference/keywords/throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="374f3-126">Poniższy przykład wyodrębnia informacje o źródle <xref:System.IO.IOException> wyjątek i następnie zgłasza wyjątek do nadrzędnej metody.</span><span class="sxs-lookup"><span data-stu-id="374f3-126">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>  
  
```csharp  
catch (FileNotFoundException e)  
{  
    // FileNotFoundExceptions are handled here.  
}  
catch (IOException e)  
{  
    // Extract some information from this exception, and then   
    // throw it to the parent method.  
    if (e.Source != null)  
        Console.WriteLine("IOException source: {0}", e.Source);  
    throw;  
}  
```  
  
 <span data-ttu-id="374f3-127">Można przechwycić jeden wyjątek i różnych wyjątku.</span><span class="sxs-lookup"><span data-stu-id="374f3-127">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="374f3-128">Gdy to zrobisz, określ wyjątek, który przechwycono jako wewnętrzny wyjątek, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="374f3-128">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 <span data-ttu-id="374f3-129">Użytkownik może również ponowne zgłoszenie wyjątku, gdy określony warunek ma wartość true, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="374f3-129">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>  
  
```csharp  
catch (InvalidCastException e)  
{  
    if (e.Data == null)  
    {  
        throw;  
    }  
    else  
    {  
        // Take some action.  
    }  
}  
```  

> [!NOTE]
> <span data-ttu-id="374f3-130">Istnieje również możliwość Użyj filtra wyjątku, aby uzyskać podobny efekt w często bardziej przejrzysty sposób (a także nie modyfikowanie stosu, zgodnie z opisem we wcześniejszej części tego dokumentu).</span><span class="sxs-lookup"><span data-stu-id="374f3-130">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="374f3-131">W poniższym przykładzie przedstawiono podobne zachowanie dla obiektów wywołujących, jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="374f3-131">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="374f3-132">Funkcja zgłasza `InvalidCastException` obiektu wywołującego podczas `e.Data` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="374f3-132">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
> 
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)   
> {  
>     // Take some action.  
> }
> ```   

 <span data-ttu-id="374f3-133">Z wewnątrz `try` zablokować, zainicjować tylko zmienne, które są zadeklarowane w nim.</span><span class="sxs-lookup"><span data-stu-id="374f3-133">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="374f3-134">W przeciwnym razie może wystąpić wyjątek, przed zakończeniem wykonywania bloku.</span><span class="sxs-lookup"><span data-stu-id="374f3-134">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="374f3-135">Na przykład w poniższym przykładzie kodu zmiennej `n` jest inicjowany wewnątrz `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="374f3-135">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="374f3-136">Próba użycia tej zmiennej poza `try` bloku `Write(n)` instrukcji spowoduje wygenerowanie błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="374f3-136">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>  
  
```csharp  
static void Main()   
{  
    int n;  
    try   
    {  
        // Do not initialize this variable here.  
        n = 123;  
    }  
    catch  
    {  
    }  
    // Error: Use of unassigned local variable 'n'.  
    Console.Write(n);  
}  
```  
  
 <span data-ttu-id="374f3-137">Aby uzyskać więcej informacji na temat catch, zobacz [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="374f3-137">For more information about catch, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
## <a name="exceptions-in-async-methods"></a><span data-ttu-id="374f3-138">Wyjątki w metodach asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="374f3-138">Exceptions in Async Methods</span></span>  
 <span data-ttu-id="374f3-139">Metoda asynchroniczna jest oznaczony za [async](../../../csharp/language-reference/keywords/async.md) modyfikator i zwykle zawiera jeden lub więcej await wyrażeń lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="374f3-139">An async method is marked  by an  [async](../../../csharp/language-reference/keywords/async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="374f3-140">Wyrażenie await stosuje [await](../../../csharp/language-reference/keywords/await.md) operatora <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="374f3-140">An await expression applies the [await](../../../csharp/language-reference/keywords/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="374f3-141">Gdy kontrola osiąga `await` w metodzie asynchronicznej postęp w metodzie jest wstrzymana, dopóki nie zakończy się oczekiwane zadanie.</span><span class="sxs-lookup"><span data-stu-id="374f3-141">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="374f3-142">Kiedy zadanie zostanie ukończone, wykonanie można wznowić w metodzie.</span><span class="sxs-lookup"><span data-stu-id="374f3-142">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="374f3-143">Aby uzyskać więcej informacji, zobacz [Asynchronous Programming with async i await](../../../csharp/programming-guide/concepts/async/index.md) i [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="374f3-143">For more information, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
 <span data-ttu-id="374f3-144">Ukończone zadanie podrzędne, do którego `await` jest stosowany z powodu nieobsługiwanego wyjątku w metodzie, która zwraca zadanie może znajdować się w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="374f3-144">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="374f3-145">Oczekiwanie na zadanie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="374f3-145">Awaiting the task throws an exception.</span></span> <span data-ttu-id="374f3-146">Zadanie również można znajdą się w stanem anulowane, jeśli proces asynchroniczny, która zwraca go zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="374f3-146">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="374f3-147">Oczekuje na anulowane zadanie zgłasza `OperationCanceledException`.</span><span class="sxs-lookup"><span data-stu-id="374f3-147">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="374f3-148">Aby uzyskać więcej informacji o tym, jak można anulować proces asynchroniczny, zobacz [aplikacji asynchronicznej Fine-Tuning](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="374f3-148">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="374f3-149">Aby przechwycić wyjątek, należy poczekać na zadanie `try` zablokować, a następnie przechwycić wyjątek w skojarzonej `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="374f3-149">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="374f3-150">Aby uzyskać przykład zobacz sekcję "Przykład".</span><span class="sxs-lookup"><span data-stu-id="374f3-150">For an example, see the "Example" section.</span></span>  
  
 <span data-ttu-id="374f3-151">Zadanie może być w nieprawidłowym stanie, ponieważ w metodzie async oczekiwane wystąpił wiele wyjątków.</span><span class="sxs-lookup"><span data-stu-id="374f3-151">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="374f3-152">Na przykład zadanie może być wynikiem wywołania <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="374f3-152">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="374f3-153">W przypadku takich zadań, jest tylko jeden z wyjątków wychwytywane, a nie można przewidzieć, który wyjątek zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="374f3-153">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="374f3-154">Aby uzyskać przykład zobacz sekcję "Przykład".</span><span class="sxs-lookup"><span data-stu-id="374f3-154">For an example, see the "Example" section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="374f3-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="374f3-155">Example</span></span>  
 <span data-ttu-id="374f3-156">W poniższym przykładzie `try` blok zawiera wywołanie `ProcessString` metodę, która może spowodować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="374f3-156">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="374f3-157">`catch` Klauzula zawiera program obsługi wyjątków, który po prostu wyświetla komunikat na ekranie.</span><span class="sxs-lookup"><span data-stu-id="374f3-157">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="374f3-158">Gdy `throw` instrukcji jest wywoływana z wewnątrz `MyMethod`, system wyszukuje `catch` instrukcji i wyświetla komunikat `Exception caught`.</span><span class="sxs-lookup"><span data-stu-id="374f3-158">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="374f3-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="374f3-159">Example</span></span>  
 <span data-ttu-id="374f3-160">W poniższym przykładzie są używane dwa bloki catch, a specyficzny wyjątek, który wykorzystasz, zostanie przechwycony.</span><span class="sxs-lookup"><span data-stu-id="374f3-160">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>  
  
 <span data-ttu-id="374f3-161">Aby przechwycić wyjątek najmniej specyficznych, możesz zastąpić instrukcji "throw" w `ProcessString` przy użyciu następującej instrukcji: `throw new Exception()`.</span><span class="sxs-lookup"><span data-stu-id="374f3-161">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>  
  
 <span data-ttu-id="374f3-162">Jeśli najpierw umieścić blok catch do najmniej specyficznych w przykładzie pojawia się następujący komunikat o błędzie: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span><span class="sxs-lookup"><span data-stu-id="374f3-162">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="374f3-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="374f3-163">Example</span></span>  
 <span data-ttu-id="374f3-164">Poniższy przykład ilustruje wyjątków, obsługa do metod asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="374f3-164">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="374f3-165">Aby przechwytywać wyjątek, który zgłasza zadania asynchronicznego, umieść `await` wyrażenia w `try` zablokować, a następnie przechwycić wyjątek w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="374f3-165">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>  
  
 <span data-ttu-id="374f3-166">Usuń znaczniki komentarza `throw new Exception` wiersza w przykładzie, aby zademonstrować obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="374f3-166">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="374f3-167">Zadania podrzędnego `IsFaulted` właściwość jest ustawiona na `True`, zadania podrzędnego `Exception.InnerException` właściwość jest ustawiona na wyjątek i wyjątek w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="374f3-167">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>  
  
 <span data-ttu-id="374f3-168">Usuń znaczniki komentarza `throw new OperationCancelledException` wiersz, aby zademonstrować, co się stanie, gdy anulujesz proces asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="374f3-168">Uncomment the `throw new OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="374f3-169">Zadania podrzędnego `IsCanceled` właściwość jest ustawiona na `true`, a wyjątek w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="374f3-169">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="374f3-170">W niektórych warunkach, które nie mają zastosowania do tego przykładu, zadania w `IsFaulted` właściwość jest ustawiona na `true` i `IsCanceled` ustawiono `false`.</span><span class="sxs-lookup"><span data-stu-id="374f3-170">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>  
  
 [!code-csharp[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="374f3-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="374f3-171">Example</span></span>  
 <span data-ttu-id="374f3-172">Poniższy przykład ilustruje wyjątków, gdzie wiele zadań może spowodować wiele wyjątków.</span><span class="sxs-lookup"><span data-stu-id="374f3-172">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="374f3-173">`try` Bloku czeka na zadanie, który jest zwracany przez wywołanie <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="374f3-173">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="374f3-174">Zadanie zostało ukończone, po zakończeniu trzech zadań, do których zastosowano WhenAll.</span><span class="sxs-lookup"><span data-stu-id="374f3-174">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>  
  
 <span data-ttu-id="374f3-175">Każdy z trzech zadań, powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="374f3-175">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="374f3-176">`catch` Bloku wykonuje iterację przez wyjątki, które znajdują się w `Exception.InnerExceptions` właściwości zadania, który został zwrócony przez <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="374f3-176">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="374f3-177">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="374f3-177">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="374f3-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="374f3-178">See Also</span></span>

- [<span data-ttu-id="374f3-179">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="374f3-179">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="374f3-180">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="374f3-180">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="374f3-181">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="374f3-181">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="374f3-182">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="374f3-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
- [<span data-ttu-id="374f3-183">Instrukcje obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="374f3-183">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
- [<span data-ttu-id="374f3-184">throw</span><span class="sxs-lookup"><span data-stu-id="374f3-184">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
- [<span data-ttu-id="374f3-185">try-finally</span><span class="sxs-lookup"><span data-stu-id="374f3-185">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
- [<span data-ttu-id="374f3-186">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="374f3-186">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
