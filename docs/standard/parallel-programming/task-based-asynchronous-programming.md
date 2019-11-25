---
title: Task-based asynchronous programming - .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
ms.openlocfilehash: 51292d977f2be87cec7c3481f5004fe5fe756224
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204544"
---
# <a name="task-based-asynchronous-programming"></a>Task-based asynchronous programming

The Task Parallel Library (TPL) is based on the concept of a *task*, which represents an asynchronous operation. In some ways, a task resembles a thread or <xref:System.Threading.ThreadPool> work item, but at a higher level of abstraction. The term *task parallelism* refers to one or more independent tasks running concurrently. Zadania zapewniają dwie podstawowe korzyści:

- Efektywniejsze i bardziej skalowalne wykorzystanie zasobów systemowych.

     Behind the scenes, tasks are queued to the <xref:System.Threading.ThreadPool>, which has been enhanced with algorithms  that determine and adjust to the number of threads and that provide load balancing to maximize throughput. Dzięki temu zadania są stosunkowo lekkie i można tworzyć wiele takich zadań, aby włączyć równoległość drobnoziarnistą.

- Większa kontrola programistyczna niż jest to możliwe za pomocą wątku lub elementu roboczego.

     Zadania i środowisko zbudowane wokół nich zawierają bogaty zestaw interfejsów API, które obsługują oczekiwanie, anulowanie, kontynuację, niezawodną obsługę wyjątków, szczegółowe informacje o stanie, planowanie niestandardowe i nie tylko.

Dla obu tych powodów w .NET Framework TPL jest preferowanym interfejsem API do pisania kodu wielowątkowego, asynchronicznego i równoległego.

## <a name="creating-and-running-tasks-implicitly"></a>Creating and running tasks implicitly

The <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> method provides a convenient way to run any number of arbitrary statements concurrently. Just pass in an <xref:System.Action> delegate for each item of work. Wyrażenia lambda są najwygodniejszym sposobem na tworzenie tych delegatów. Wyrażenie lambda może wywołać metodę nazwaną lub zapewnić kod inline. The following example shows a basic <xref:System.Threading.Tasks.Parallel.Invoke%2A> call that creates and starts two tasks that run concurrently. The first task is represented by a lambda expression that calls a method named `DoSomeWork`, and the second task is represented by a lambda expression that calls a method named `DoSomeOtherWork`.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL. If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> The number of <xref:System.Threading.Tasks.Task> instances that are created behind the scenes by <xref:System.Threading.Tasks.Parallel.Invoke%2A> is not necessarily equal to the number of delegates that are provided. TPL może wykorzystywać różne optymalizacje, zwłaszcza z dużą liczbą obiektów delegowanych.

For more information, see [How to: Use Parallel.Invoke to Execute Parallel Operations](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

For greater control over task execution or to return a value from the task, you have to work with <xref:System.Threading.Tasks.Task> objects more explicitly.

## <a name="creating-and-running-tasks-explicitly"></a>Creating and running tasks explicitly

A task that does not return a value is represented by the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class. A task that returns a value is represented by the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> class, which inherits from <xref:System.Threading.Tasks.Task>. Obiekt zadania obsługuje szczegóły infrastruktury i zapewnia metody i właściwości, które są dostępne z wątku wywoływania przez cały okres istnienia zadania. For example, you can access the <xref:System.Threading.Tasks.Task.Status%2A> property of a task at any time to determine whether it has started running, ran to completion, was canceled, or has thrown an exception. The status is represented by a <xref:System.Threading.Tasks.TaskStatus> enumeration.

Tworząc zadanie, nadajesz mu delegata użytkownika hermetyzującego kod, który zadanie będzie wykonywało. Delegat może być wyrażony jako delegat nazwany, metoda anonimowa lub wyrażenie lambda. Wyrażenia lambda mogą zawierać wywołanie metody nazwanej, jak pokazano w następującym przykładzie. Note that the example includes a call to the <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> method to ensure that the task completes execution before the console mode application ends.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

You can also use the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> methods to create and start a task in one operation. To manage the task, the <xref:System.Threading.Tasks.Task.Run%2A> methods use the default  task scheduler, regardless of which task scheduler is associated with the current thread. The <xref:System.Threading.Tasks.Task.Run%2A> methods are the preferred way to create and start tasks when more control over the creation and scheduling of the task is not needed.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

You can also use the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method to create and start a task in one operation. Use this method when creation and scheduling do not have to be separated and you require additional task creation options or the use of a specific scheduler, or when you need to pass additional state into the task that you can retrieve through its <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> property, as shown in the following example.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> each expose a static <xref:System.Threading.Tasks.Task.Factory%2A> property that returns a default instance of <xref:System.Threading.Tasks.TaskFactory>, so that you can call the method as `Task.Factory.StartNew()`. Also, in the following example, because the tasks are of type <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, they each have a public <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> property that contains the result of the computation. Zadania są wykonywane asynchroniczne i mogą być kończone w dowolnej kolejności. If the <xref:System.Threading.Tasks.Task%601.Result%2A> property is accessed before the computation finishes, the property blocks the calling thread until the value is available.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

For more information, see [How to: Return a Value from a Task](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Używając wyrażenia lambda do utworzenia delegata, masz dostęp do wszystkich zmiennych, które są widoczne w tym momencie w kodzie źródłowym. Jednak w niektórych przypadkach, zwłaszcza w pętlach, lambda nie przechwytuje zmiennej zgodnie z oczekiwaniami. Przechwytuje tylko wartość końcową, a nie wartość, która mutuje po każdej iteracji. Poniższy przykład ilustruje ten problem. It passes a loop counter to a lambda expression that instantiates a `CustomData` object and uses the loop counter as the object's identifier. As the output from the example shows, each `CustomData` object has an identical identifier.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

Możesz uzyskać dostęp do wartości w każdej iteracji poprzez zapewnienie obiektu stanu do zadania za pośrednictwem jej konstruktora. The following example modifies the previous example by using the loop counter when creating the `CustomData` object, which, in turn, is passed to the lambda expression.  As the output from the example shows, each `CustomData` object now has a unique identifier based on the value of the loop counter at the time the object was instantiated.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

This state is passed as an argument to the task delegate, and it can be accessed from the task object by using the <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> property.  Poniższy przykład jest modyfikacją poprzedniego. It uses the <xref:System.Threading.Tasks.Task.AsyncState%2A> property to display information about the `CustomData` objects passed to the lambda expression.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>Identyfikator zadania

Every task receives an integer ID that uniquely identifies it in an application domain and can be accessed by using the <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType> property. The ID is useful for viewing task information in the Visual Studio debugger **Parallel Stacks** and **Tasks** windows. Identyfikator jest tworzony z opóźnieniem, co oznacza, że nie jest on tworzony do momentu pojawienia się stosownego żądania. Dlatego zadanie może mieć inny identyfikator za każdym razem, gdy program jest uruchamiany. For more information about how to view task IDs in the debugger, see [Using the Tasks Window](/visualstudio/debugger/using-the-tasks-window) and [Using the Parallel Stacks Window](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Task creation options

Most APIs that create tasks provide overloads that accept a <xref:System.Threading.Tasks.TaskCreationOptions> parameter. Określając jedną z poniższych opcji, możesz wskazać harmonogramowi zadań, jak zaplanować zadanie w puli wątków. Poniższa tabela zawiera różne opcje tworzenia zadania.

|<xref:System.Threading.Tasks.TaskCreationOptions> parameter value|Opis|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Domyślna, gdy nie określono żadnej opcji. Harmonogram używa domyślnej heurystyki do zaplanowania zadania.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Określa, że zadanie powinno zostać zaplanowane tak, aby zadania utworzone wcześniej były wykonywane wcześniej, a zadania utworzone później były wykonywane później.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Określa, że zadanie reprezentuje operację długotrwałą.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Określa, że zadanie powinno zostać utworzone jako dołączone zadanie podrzędne do bieżącego zadania, jeśli takie istnieje. For more information, see [Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Specifies that if an inner task specifies the `AttachedToParent` option, that task will not become an attached child task.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Specifies that the task scheduler for tasks created by calling methods like <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> or <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> from within a particular task is the default scheduler instead of the scheduler on which this task is running.|

The options may be combined by using a bitwise **OR** operation. The following example shows a task that has the <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> and <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness> option.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Tasks, threads, and culture

Each thread has an associated culture and UI culture, which is defined by the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> properties, respectively. A thread's culture is used in such operations as formatting, parsing, sorting, and string comparison. A thread's UI culture is used in resource lookup. Ordinarily, unless you specify a default culture for all the threads in an application domain by using the <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> and <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType> properties, the default culture and UI culture of a thread is defined by the system culture. If you explicitly set a thread's culture and launch a new thread, the new thread does not inherit the culture of the calling thread; instead, its culture is the default system culture. The task-based programming model for apps that target versions of the .NET Framework prior to .NET Framework 4.6 adhere to this practice.

> [!IMPORTANT]
> Note that the calling thread's culture as part of a task's context applies to apps that *target* the .NET Framework 4.6, not apps that *run under* the .NET Framework 4.6. You can target a particular version of the .NET Framework when you create your project in Visual Studio by selecting that version from the dropdown list at the top of the **New Project** dialog box, or outside of Visual Studio you can use the <xref:System.Runtime.Versioning.TargetFrameworkAttribute> attribute. For apps that target versions of the .NET Framework prior to the .NET Framework 4.6, or that do not target a specific version of the .NET Framework, a task's culture continues to be determined by the culture of the thread on which it runs.

Starting with apps that target the .NET Framework 4.6, the calling thread's culture is inherited by each task, even if the task runs asynchronously on a thread pool thread.

The following example provides a simple illustration. It uses the <xref:System.Runtime.Versioning.TargetFrameworkAttribute> attribute to target the .NET Framework 4.6 and changes the app's current culture to either French (France) or, if French (France) is already the current culture, English (United States). It then invokes a delegate named `formatDelegate` that returns some numbers formatted as currency values in the new culture. Note that whether the delegate as a task either synchronously or asynchronously, it returns the expected result because the culture of the calling thread is inherited by the asynchronous task.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

If you are using Visual Studio, you can omit the <xref:System.Runtime.Versioning.TargetFrameworkAttribute> attribute and instead select the .NET Framework 4.6 as the target when you create the project in the **New Project** dialog.

For output that reflects the behavior of apps the target versions of the .NET Framework prior to .NET Framework 4.6, remove the <xref:System.Runtime.Versioning.TargetFrameworkAttribute> attribute from the source code. The output will reflect the formatting conventions of the default system culture, not the culture of the calling thread.

For more information on asynchronous tasks and culture, see the "Culture and asynchronous task-based operations" section in the <xref:System.Globalization.CultureInfo> topic.

## <a name="creating-task-continuations"></a>Creating task continuations

The <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> methods let you specify a task to start when the *antecedent task* finishes. The delegate of the continuation task is passed a reference to the antecedent task so that it can examine the antecedent task's status and, by retrieving the value of the <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> property, can use the output of the antecedent as input for the continuation.

In the following example, the `getData` task is started by a call to the <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType> method. The `processData` task is started automatically when `getData` finishes, and `displayData` is started when `processData` finishes. `getData` produces an integer array, which is accessible to the `processData` task through the `getData` task's <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> property. The `processData` task processes that array and returns a result whose type is inferred from the return type of the lambda expression passed to the <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType> method. The `displayData` task executes automatically when `processData` finishes, and the <xref:System.Tuple%603> object returned by the `processData` lambda expression is accessible to the `displayData` task through the `processData` task's <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> property. The `displayData` task takes the result of the `processData` task and produces a result whose type is inferred in a similar manner and which is made available to the program in the <xref:System.Threading.Tasks.Task%601.Result%2A> property.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Because <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> is an instance method, you can chain method calls together instead of instantiating a <xref:System.Threading.Tasks.Task%601> object for each antecedent task. The following example is functionally identical to the previous example, except that it chains together calls to the <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> method. Note that the <xref:System.Threading.Tasks.Task%601> object returned by the chain of method calls is the final continuation task.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

The <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> and <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> methods enable you to continue from multiple tasks.

For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Creating detached child tasks

When user code that is running in a task creates a new task and does not specify the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option, the new task is not synchronized with the parent task in any special way. This type of non-synchronized task is called a *detached nested task* or *detached child task*. Poniższy przykład przedstawia zadanie, które tworzy jedno odłączone zadanie podrzędne.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Należy zauważyć, że zadanie nadrzędne nie czeka na zakończenie odłączonego zadania podrzędnego.

## <a name="creating-child-tasks"></a>Creating child tasks

When user code that is running in a task creates a task with the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option, the new task is known as a *attached child task* of the parent task. You can use the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to express structured task parallelism, because the parent task implicitly waits for all attached child tasks to finish. Poniższy przykład przedstawia zadanie nadrzędne, które tworzy dziesięć dołączonych zadań podrzędnych. Note that although the example calls the <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> method to wait for the parent task to finish, it does not have to explicitly wait for the attached child tasks to complete.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

A parent task can use the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to prevent other tasks from attaching to the parent task. For more information, see [Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Waiting for tasks to finish

The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> types provide several overloads of the <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> methods that enable you to wait for a task to finish. In addition, overloads of the static <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods let you wait for any or all of an array of tasks to finish.

Zazwyczaj użytkownik czeka na zadanie z jednego z poniższych powodów:

- Główny wątek zależy od wyniku końcowego obliczonego przez zadanie.

- Trzeba obsługiwać wyjątki, które mogą być zgłoszone przez zadanie.

- Aplikacja może się zakończyć zanim wszystkie zadania zostaną ukończone. For example, console applications will terminate as soon as all synchronous code in `Main` (the application entry point) has executed.

Poniższy przykład przedstawia podstawowy wzorzec, który nie wymaga obsługi wyjątków.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

For an example that shows exception handling, see [Exception Handling](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

Some overloads let you specify a time-out, and others take an additional <xref:System.Threading.CancellationToken> as an input parameter, so that the wait itself can be canceled either programmatically or in response to user input.

When you wait for a task, you implicitly wait for all children of that task that were created by using the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> returns immediately if the task has already completed. Any exceptions raised by a task will be thrown by a <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> method, even if the <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> method was called after the task completed.

## <a name="composing-tasks"></a>Composing tasks

The <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> classes provide several methods that can help you compose multiple tasks to implement common patterns and to better use the asynchronous language features that are provided by C#, Visual Basic, and F#. This section describes the <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A>, and <xref:System.Threading.Tasks.Task.FromResult%2A> methods.

### <a name="taskwhenall"></a>Task.WhenAll

The <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method asynchronously waits for multiple <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> objects to finish. Zapewnia przeciążone wersje, które umożliwiają czekanie na niejednolite zestawy zadań. For example, you can wait for multiple <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects to complete from one method call.

### <a name="taskwhenany"></a>Task.WhenAny

The <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method asynchronously waits for one of multiple <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> objects to finish. As in the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method, this method provides overloaded versions that enable you to wait for non-uniform sets of tasks. The <xref:System.Threading.Tasks.Task.WhenAny%2A> method is especially useful in the following scenarios.

- Operacje nadmiarowe. Należy wziąć pod uwagę algorytm lub operację, które mogą być wykonywane na wiele sposobów. You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to select the operation that finishes first and then cancel the remaining operations.

- Operacje z przeplotem. You can start multiple operations that must all finish and use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to process results as each operation finishes. Po zakończeniu jednej operacji można uruchomić jedno lub więcej dodatkowych zadań.

- Operacje ograniczane. You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to extend the previous scenario by limiting the number of concurrent operations.

- Wygasłe operacje. You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to select between one or more tasks and a task that finishes after a specific time, such as a task that is returned by the <xref:System.Threading.Tasks.Task.Delay%2A> method. The <xref:System.Threading.Tasks.Task.Delay%2A> method is described in the following section.

### <a name="taskdelay"></a>Task.Delay

The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method produces a <xref:System.Threading.Tasks.Task> object that finishes after the specified time. Możesz użyć tej metoda do tworzenia pętli, które od czasu do czasu pobierają dane, wprowadzają limity czasu, opóźniają obsługę danych wejściowych użytkownika przez wyznaczony czas i tak dalej.

### <a name="tasktfromresult"></a>Task(T).FromResult

By using the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method, you can create a <xref:System.Threading.Tasks.Task%601> object that holds a pre-computed result. This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed. For an example that uses <xref:System.Threading.Tasks.Task.FromResult%2A> to retrieve the results of asynchronous download operations that are held in a cache, see [How to: Create Pre-Computed Tasks](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Handling exceptions in tasks

When a task throws one or more exceptions, the exceptions are wrapped in an <xref:System.AggregateException> exception. That exception is propagated back to the thread that joins with the task, which is typically the thread that is waiting for the task to finish or the thread that accesses the <xref:System.Threading.Tasks.Task%601.Result%2A> property. To zachowanie służy do wymuszania zasady .NET Framework, zgodnie z którą wszystkie nieobsłużone wyjątki powinny domyślnie przerywać proces. The calling code can handle the exceptions by using any of the following in a `try`/`catch` block:

- The <xref:System.Threading.Tasks.Task.Wait%2A> method

- The <xref:System.Threading.Tasks.Task.WaitAll%2A> method

- The <xref:System.Threading.Tasks.Task.WaitAny%2A> method

- The <xref:System.Threading.Tasks.Task%601.Result%2A> property

The joining thread can also handle exceptions by accessing the <xref:System.Threading.Tasks.Task.Exception%2A> property before the task is garbage-collected. Dostęp do tej właściwości zapobiega temu, że nieobsługiwany wyjątek inicjuje zachowanie propagacji wyjątku, które przerywa proces wraz z finalizacją obiektu.

For more information about exceptions and tasks, see [Exception Handling](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Canceling tasks

The <xref:System.Threading.Tasks.Task> class supports cooperative cancellation and is fully integrated with the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> classes, which were introduced in the .NET Framework 4. Many of the constructors in the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class take a <xref:System.Threading.CancellationToken> object as an input parameter. Many of the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> and <xref:System.Threading.Tasks.Task.Run%2A> overloads also include a <xref:System.Threading.CancellationToken> parameter.

You can create the token, and issue the cancellation request at some later time, by using the <xref:System.Threading.CancellationTokenSource> class. Pass the token to the <xref:System.Threading.Tasks.Task> as an argument, and also reference the same token in your user delegate, which does the work of responding to a cancellation request.

For more information, see [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md) and [How to: Cancel a Task and Its Children](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>The TaskFactory class

The <xref:System.Threading.Tasks.TaskFactory> class provides static methods that encapsulate some common patterns for creating and starting tasks and continuation tasks.

- The most common pattern is <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, which creates and starts a task in one statement.

- When you create continuation tasks from multiple antecedents, use the <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> method or <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> method or their equivalents in the <xref:System.Threading.Tasks.Task%601> class. For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

- To encapsulate Asynchronous Programming Model `BeginX` and `EndX` methods in a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> instance, use the <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> methods. For more information, see [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).

The default <xref:System.Threading.Tasks.TaskFactory> can be accessed as a static property on the <xref:System.Threading.Tasks.Task> class or <xref:System.Threading.Tasks.Task%601> class. You can also instantiate a <xref:System.Threading.Tasks.TaskFactory> directly and specify various options that include a <xref:System.Threading.CancellationToken>, a <xref:System.Threading.Tasks.TaskCreationOptions> option, a <xref:System.Threading.Tasks.TaskContinuationOptions> option, or a <xref:System.Threading.Tasks.TaskScheduler>. Whatever options are specified when you create the task factory will be applied to all tasks that it creates, unless the <xref:System.Threading.Tasks.Task> is created by using the <xref:System.Threading.Tasks.TaskCreationOptions> enumeration, in which case the task's options override those of the task factory.

## <a name="tasks-without-delegates"></a>Tasks without delegates

In some cases, you may want to use a <xref:System.Threading.Tasks.Task> to encapsulate some asynchronous operation that is performed by an external component instead of your own user delegate. If the operation is based on the Asynchronous Programming Model Begin/End pattern, you can use the <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> methods. If that is not the case, you can use the <xref:System.Threading.Tasks.TaskCompletionSource%601> object to wrap the operation in a task and thereby gain some of the benefits of <xref:System.Threading.Tasks.Task> programmability, for example, support for exception propagation and continuations. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Custom schedulers

Most application or library developers do not care which processor the task runs on, how it synchronizes its work with other tasks, or how it is scheduled on the <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Wymagają one tylko, aby było wykonane jak najwydajniej na komputerze-hoście. Jeśli potrzebna większa kontrola nad szczegółami planowania, biblioteka zadań równoległych pozwala skonfigurować niektóre ustawienia w domyślnym harmonogramie zadań, a nawet pozwala podać niestandardowy harmonogram. Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>Related data structures

TPL ma kilka nowych typów publicznych, które są przydatne w scenariuszach równoległych i sekwencyjnych. These include several thread-safe, fast and scalable collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and several new synchronization types, for example, <xref:System.Threading.Semaphore?displayProperty=nameWithType> and <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which are more efficient than their predecessors for specific kinds of workloads. Other new types in the .NET Framework 4, for example, <xref:System.Threading.Barrier?displayProperty=nameWithType> and <xref:System.Threading.SpinLock?displayProperty=nameWithType>, provide functionality that was not available in earlier releases. For more information, see [Data Structures for Parallel Programming](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Custom task types

We recommend that you do not inherit from <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> or <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Instead, we recommend that you use the <xref:System.Threading.Tasks.Task.AsyncState%2A> property to associate additional data or state with a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object. You can also use extension methods to extend the functionality of the <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> classes. For more information about extension methods, see [Extension Methods](../../csharp/programming-guide/classes-and-structs/extension-methods.md) and [Extension Methods](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).

If you must inherit from <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, you cannot use <xref:System.Threading.Tasks.Task.Run%2A>, or the <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>, or <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> classes to create instances of your custom task type because these mechanisms create only <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects. In addition, you cannot use the task continuation mechanisms that are provided by <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.TaskFactory>, and  <xref:System.Threading.Tasks.TaskFactory%601> to create instances of your custom task type because these mechanisms also create only <xref:System.Threading.Tasks.Task> and  <xref:System.Threading.Tasks.Task%601> objects.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-|-|
|[Tworzenie łańcuchów zadań przy użyciu zadań kontynuacji](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Opisuje, jak działa kontynuacja.|
|[Dołączone i odłączone zadania podrzędne](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Opisano różnicę między zadaniami podrzędnymi dołączonymi i odłączonymi.|
|[Anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md)|Describes the cancellation support that is built into the <xref:System.Threading.Tasks.Task> object.|
|[Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Opisuje sposób obsługi wyjątków w wątkach współbieżnych.|
|[Instrukcje: wykonywanie operacji równoległych za pomocą elementu Parallel.Invoke](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Describes how to use <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|
|[Instrukcje: zwracanie wartości z zadania](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Zawiera opis sposobu zwracania wartości z zadań.|
|[Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Opisuje, jak anulować zadania.|
|[Instrukcje: tworzenie wstępnie obliczonych zadań](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.|
|[Instrukcje: przenoszenie drzewa binarnego z zadaniami równoległymi](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Opisuje używanie zadań do przechodzenia w drzewie binarnym.|
|[Instrukcje: odpakowywanie zadania zagnieżdżonego](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method.|
|[Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Describes how to use <xref:System.Threading.Tasks.Parallel.For%2A> and <xref:System.Threading.Tasks.Parallel.ForEach%2A> to create parallel loops over data.|
|[Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)|Węzeł najwyższego poziomu dla .NET Framework programowania równoległego.|

## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Samples for Parallel Programming with the .NET Framework](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
