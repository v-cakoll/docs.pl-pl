---
title: "try-catch (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
caps.latest.revision: "45"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 753beb554796ad0aa2c5e15c715240453de9a3e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="2d108-102">try-catch (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2d108-102">try-catch (C# Reference)</span></span>
<span data-ttu-id="2d108-103">Instrukcji try-catch składa się z `try` bloku, po której następuje co najmniej jeden `catch` postanowienia Określ obsługę różnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2d108-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d108-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d108-104">Remarks</span></span>  
 <span data-ttu-id="2d108-105">Jeśli wyjątek szuka środowisko uruchomieniowe języka wspólnego (CLR) `catch` instrukcji, która obsługuje ten wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2d108-105">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="2d108-106">Jeśli aktualnie wykonywane — metoda nie zawiera takie `catch` zablokować wygląda CLR w metodę, która wywołuje bieżącej metody i tak dalej górę stosu wywołań.</span><span class="sxs-lookup"><span data-stu-id="2d108-106">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="2d108-107">Jeśli nie `catch` bloku zostanie znaleziony, a następnie CLR jest wyświetlany komunikat nieobsługiwany wyjątek i zatrzymuje wykonywanie programu.</span><span class="sxs-lookup"><span data-stu-id="2d108-107">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>  
  
 <span data-ttu-id="2d108-108">`try` Blok zawiera ochroną kod, który może spowodować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2d108-108">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="2d108-109">Blok jest wykonywana do czasu zgłoszenia wyjątku lub zakończyło się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="2d108-109">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="2d108-110">Na przykład następujące próba rzutowania `null` obiekt zgłasza <xref:System.NullReferenceException> wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2d108-110">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>  
  
```csharp  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 <span data-ttu-id="2d108-111">Mimo że `catch` bez argumentów można użyć klauzuli w celu efektywnej dowolnego typu wyjątku, to użycie nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="2d108-111">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="2d108-112">Ogólnie rzecz biorąc powinien catch tylko te wyjątki, które należy znać sposób odzyskanie.</span><span class="sxs-lookup"><span data-stu-id="2d108-112">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="2d108-113">W związku z tym należy zawsze podać argument obiektu pochodną <xref:System.Exception?displayProperty=nameWithType> na przykład:</span><span class="sxs-lookup"><span data-stu-id="2d108-113">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
}  
```  
  
 <span data-ttu-id="2d108-114">Można użyć więcej niż jednej określonej `catch` klauzuli w tej samej instrukcji try-catch.</span><span class="sxs-lookup"><span data-stu-id="2d108-114">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="2d108-115">W tym przypadku kolejność `catch` klauzule ważne jest, ponieważ `catch` klauzule są sprawdzane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="2d108-115">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="2d108-116">CATCH bardziej szczegółowe wyjątki przed mniej określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="2d108-116">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="2d108-117">Kompilator generuje błąd jeśli kolejność się, że Twoje catch blokuje tak, aby nigdy nie można połączyć się z blokiem nowsze.</span><span class="sxs-lookup"><span data-stu-id="2d108-117">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>  
  
 <span data-ttu-id="2d108-118">Przy użyciu `catch` argumentów jest jednym ze sposobów Filtruj wyjątki mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2d108-118">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="2d108-119">Umożliwia także wyrażenie predykatu, dalsze badający wyjątku, aby zdecydować, czy do jego obsługi.</span><span class="sxs-lookup"><span data-stu-id="2d108-119">You can also use a predicate expression that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="2d108-120">Jeśli wyrażenie predykatu zwraca wartość false, jest tworzona wyszukiwania dla programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="2d108-120">If the predicate expression returns false, then the search for a handler continues.</span></span>  
  
```csharp  
catch (ArgumentException e) when (e.ParamName == "…")  
{  
}  
```  
  
 <span data-ttu-id="2d108-121">Filtry wyjątków są preferowane przechwytywanie i ponowne generowanie (wyjaśniono poniżej), ponieważ stos nieokaleczone pozostaw filtrów.</span><span class="sxs-lookup"><span data-stu-id="2d108-121">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="2d108-122">Nowsze obsługi zrzuty stosu, widać gdzie wyjątek pierwotnie pochodzeniu, a nie tylko ostatnie miejsce, który został wywołany ponownie.</span><span class="sxs-lookup"><span data-stu-id="2d108-122">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="2d108-123">Rejestrowanie zdarzeń użycia wyrażeń filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2d108-123">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="2d108-124">Można utworzyć predykatu funkcję, która zawsze zwraca wartość false, również zapisującego w dzienniku można rejestrować wyjątki, jak komputery przechodzą bez konieczności ich i ponownego zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="2d108-124">You can create a predicate function that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>  
  
 <span data-ttu-id="2d108-125">A [throw](../../../csharp/language-reference/keywords/throw.md) instrukcja może być używana w `catch` bloku, aby można było ponownie zgłosić wyjątek, który zostanie przechwycony przez `catch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2d108-125">A [throw](../../../csharp/language-reference/keywords/throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="2d108-126">Poniższy przykład wyodrębnia informacje o źródle <xref:System.IO.IOException> wyjątek, a następnie zgłasza wyjątek do nadrzędnej metody.</span><span class="sxs-lookup"><span data-stu-id="2d108-126">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>  
  
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
  
 <span data-ttu-id="2d108-127">Można przechwytywać elementu exception jednego i zgłoszenie wyjątku różnych.</span><span class="sxs-lookup"><span data-stu-id="2d108-127">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="2d108-128">Gdy to zrobisz, określ wyjątek, który Przechwycono wewnętrzny wyjątek, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2d108-128">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 <span data-ttu-id="2d108-129">Użytkownik może również ponownie Zgłoś wyjątek podczas określony warunek ma wartość true, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2d108-129">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="2d108-130">Z wewnątrz `try` bloków, zainicjować tylko zmienne, które są zadeklarowane w nim.</span><span class="sxs-lookup"><span data-stu-id="2d108-130">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="2d108-131">W przeciwnym razie wyjątek może wystąpić przed zakończeniem wykonywania bloku.</span><span class="sxs-lookup"><span data-stu-id="2d108-131">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="2d108-132">Na przykład w poniższym przykładzie kodu zmiennej `n` zainicjowano wewnątrz `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="2d108-132">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="2d108-133">Próba użycia tej zmiennej poza `try` blok w `Write(n)` instrukcji wygeneruje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2d108-133">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>  
  
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
  
 <span data-ttu-id="2d108-134">Aby uzyskać więcej informacji na temat catch, zobacz [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="2d108-134">For more information about catch, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
## <a name="exceptions-in-async-methods"></a><span data-ttu-id="2d108-135">Wyjątki w metodach asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="2d108-135">Exceptions in Async Methods</span></span>  
 <span data-ttu-id="2d108-136">Metody asynchronicznej zostało oznaczone przez [async](../../../csharp/language-reference/keywords/async.md) modyfikator i zwykle zawiera jeden lub więcej await wyrażenia lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2d108-136">An async method is marked  by an  [async](../../../csharp/language-reference/keywords/async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="2d108-137">Stosuje wyrażenie await [await](../../../csharp/language-reference/keywords/await.md) operatora <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="2d108-137">An await expression applies the [await](../../../csharp/language-reference/keywords/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="2d108-138">Gdy kontrolować osiągnie `await` w metodzie asynchronicznej postęp w metodzie jest wstrzymana, aż do zakończenia oczekiwano zadań.</span><span class="sxs-lookup"><span data-stu-id="2d108-138">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="2d108-139">Po zakończeniu zadania wykonywania można wznowić w metodzie.</span><span class="sxs-lookup"><span data-stu-id="2d108-139">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="2d108-140">Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md) i [przepływ sterowania w aplikacjach asynchronicznych](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="2d108-140">For more information, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
 <span data-ttu-id="2d108-141">Zakończone zadanie, do którego `await` zastosowano może być stan z powodu nieobsługiwany wyjątek w metodzie, która zwraca zadanie.</span><span class="sxs-lookup"><span data-stu-id="2d108-141">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="2d108-142">Oczekiwanie na zadanie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2d108-142">Awaiting the task throws an exception.</span></span> <span data-ttu-id="2d108-143">Zadania można także zakończyć w stanie Anulowane Jeśli proces asynchroniczny, która zwraca go została anulowana.</span><span class="sxs-lookup"><span data-stu-id="2d108-143">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="2d108-144">Oczekiwanie na zadanie anulowane zgłasza `OperationCanceledException`.</span><span class="sxs-lookup"><span data-stu-id="2d108-144">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="2d108-145">Aby uzyskać więcej informacji o sposobie anulować proces asynchroniczny, zobacz [Fine-Tuning Twoja aplikacja Async](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="2d108-145">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="2d108-146">Aby catch wyjątku, await zadanie w `try` zablokować, a także przechwytywanie wyjątków w skojarzonych `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="2d108-146">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="2d108-147">Na przykład zobacz sekcję "Example".</span><span class="sxs-lookup"><span data-stu-id="2d108-147">For an example, see the "Example" section.</span></span>  
  
 <span data-ttu-id="2d108-148">Zadanie może być stan, ponieważ w metodzie asynchronicznej oczekiwano wystąpił wiele wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2d108-148">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="2d108-149">Na przykład zadanie może być wynikiem wywołania do <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d108-149">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2d108-150">Await takie zadania, tylko jeden wyjątek zostanie przechwycony i nie można przewidzieć który wyjątek zostanie przechwycony.</span><span class="sxs-lookup"><span data-stu-id="2d108-150">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="2d108-151">Na przykład zobacz sekcję "Example".</span><span class="sxs-lookup"><span data-stu-id="2d108-151">For an example, see the "Example" section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d108-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d108-152">Example</span></span>  
 <span data-ttu-id="2d108-153">W poniższym przykładzie `try` blok zawiera wywołanie `ProcessString` metodę, która może spowodować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2d108-153">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="2d108-154">`catch` Klauzula zawiera program obsługi wyjątku, który właśnie na ekranie zostanie wyświetlony komunikat.</span><span class="sxs-lookup"><span data-stu-id="2d108-154">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="2d108-155">Gdy `throw` instrukcji jest wywoływana z wewnątrz `MyMethod`, system wyszukuje `catch` instrukcji i wyświetlany jest komunikat `Exception caught`.</span><span class="sxs-lookup"><span data-stu-id="2d108-155">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="2d108-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d108-156">Example</span></span>  
 <span data-ttu-id="2d108-157">W poniższym przykładzie używane są dwa bloki catch, a specyficzny wyjątek, który zostanie osiągnięty jako pierwszy, zostanie przechwycony.</span><span class="sxs-lookup"><span data-stu-id="2d108-157">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>  
  
 <span data-ttu-id="2d108-158">Aby przechwytywać elementu exception najmniej specyficznych, można zastąpić w instrukcji throw `ProcessString` z następujących instrukcji: `throw new Exception()`.</span><span class="sxs-lookup"><span data-stu-id="2d108-158">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>  
  
 <span data-ttu-id="2d108-159">Jeśli najpierw umieścić blok catch do najmniej specyficznych w przykładzie zostanie wyświetlony następujący komunikat o błędzie: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span><span class="sxs-lookup"><span data-stu-id="2d108-159">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="2d108-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d108-160">Example</span></span>  
 <span data-ttu-id="2d108-161">Poniższy przykład przedstawia obsługi dla metod asynchronicznych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2d108-161">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="2d108-162">Aby przechwytywać wyjątku, który zgłasza zadania asynchronicznego, umieść `await` wyrażenie w `try` zablokować, a także catch wyjątku w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="2d108-162">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>  
  
 <span data-ttu-id="2d108-163">Usuń znaczniki komentarza `throw new Exception` wiersza w przykładzie, aby zademonstrować obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2d108-163">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="2d108-164">Zadania `IsFaulted` właściwość jest ustawiona na `True`, zadania `Exception.InnerException` właściwość jest ustawiona na wyjątek i wyjątek w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="2d108-164">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>  
  
 <span data-ttu-id="2d108-165">Usuń znaczniki komentarza `throw new OperationCancelledException` wiersza, aby zademonstrować, co się stanie w przypadku anulowania proces asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="2d108-165">Uncomment the `throw new OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="2d108-166">Zadania `IsCanceled` właściwość jest ustawiona na `true`, i wyjątek w `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="2d108-166">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="2d108-167">W niektórych warunkach, które nie dotyczą w tym przykładzie zadanie w `IsFaulted` właściwość jest ustawiona na `true` i `IsCanceled` ma ustawioną wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="2d108-167">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>  
  
 [!code-csharp[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="2d108-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d108-168">Example</span></span>  
 <span data-ttu-id="2d108-169">Poniższy przykład przedstawia obsługi wyjątków, gdzie wiele zadań może spowodować wiele wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2d108-169">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="2d108-170">`try` Bloku oczekujące na zadanie, które jest zwracany przez wywołanie do <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d108-170">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2d108-171">Zadanie zostało ukończone, po zakończeniu trzech zadań, do których zastosowano WhenAll.</span><span class="sxs-lookup"><span data-stu-id="2d108-171">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>  
  
 <span data-ttu-id="2d108-172">Wszystkie trzy zadania powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2d108-172">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="2d108-173">`catch` Bloku iteruje wyjątki, które znajdują się w `Exception.InnerExceptions` właściwość zadania, który został zwrócony przez <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2d108-173">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2d108-174">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2d108-174">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d108-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d108-175">See Also</span></span>  
 [<span data-ttu-id="2d108-176">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="2d108-176">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2d108-177">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2d108-177">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2d108-178">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2d108-178">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2d108-179">Spróbuj, throw i catch instrukcji (C++)</span><span class="sxs-lookup"><span data-stu-id="2d108-179">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="2d108-180">Instrukcje obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="2d108-180">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="2d108-181">throw</span><span class="sxs-lookup"><span data-stu-id="2d108-181">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="2d108-182">try-finally</span><span class="sxs-lookup"><span data-stu-id="2d108-182">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="2d108-183">Porady: jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="2d108-183">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
