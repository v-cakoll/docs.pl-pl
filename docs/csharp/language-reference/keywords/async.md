---
title: "async (odwołanie w C#)"
ms.date: 05/22/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4a89736822342a9d9a24db6d43435f9795b81b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="async-c-reference"></a><span data-ttu-id="bf2a8-102">async (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bf2a8-102">async (C# Reference)</span></span>
<span data-ttu-id="bf2a8-103">Użyj `async` modyfikator, aby określić, że w metodzie [wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), lub [metody anonimowej](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) jest asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="bf2a8-104">Jeśli używasz modyfikator metody lub wyrażenie, jest ona określana jako *metody asynchronicznej*.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="bf2a8-105">W poniższym przykładzie zdefiniowano metody asynchronicznej o nazwie `ExampleMethodAsync`:</span><span class="sxs-lookup"><span data-stu-id="bf2a8-105">The following example defines an async method named `ExampleMethodAsync`:</span></span> 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
<span data-ttu-id="bf2a8-106">W przypadku nowych do programowania asynchronicznego lub nie zrozumieć sposób używa metody asynchronicznej `await` — słowo kluczowe w pracy potencjalnie długotrwałe bez blokowania wątków obiektu wywołującego odczytu wprowadzenia w [programowanie asynchroniczne przy użyciu Async i await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="bf2a8-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="bf2a8-107">Poniższy kod znajduje się wewnątrz metody asynchronicznej i wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="bf2a8-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="bf2a8-108">Metody asynchronicznej jest uruchamiana synchronicznie, dopóki nie osiągnie pierwszych `await` wyrażenie w takim przypadku metoda jest wstrzymane do czasu ukończenia zadania oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="bf2a8-109">W międzyczasie sterowanie jest przekazywane do obiektu wywołującego metody, tak jak pokazano w przykładzie w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="bf2a8-110">Jeśli metoda który `async` modyfikuje — słowo kluczowe nie zawiera `await` wyrażenia lub instrukcji metoda wykonuje synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="bf2a8-111">Ostrzeżenie kompilatora ostrzega o dowolnej metody asynchroniczne, które nie zawierają `await` instrukcji, ponieważ taka sytuacja może wskazywać na błąd.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="bf2a8-112">Zobacz [ostrzeżenie kompilatora (poziom 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="bf2a8-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="bf2a8-113">`async` — Słowo kluczowe jest kontekstowe słowo kluczowe jest tylko wtedy, gdy modyfikuje metody, wyrażenia lambda lub metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="bf2a8-114">W innych kontekstach jest interpretowane jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf2a8-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf2a8-115">Example</span></span>  
<span data-ttu-id="bf2a8-116">W poniższym przykładzie przedstawiono struktury i przepływu sterowania między program obsługi zdarzeń async `StartButton_Click`oraz metody asynchronicznej `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="bf2a8-117">Wynik metody asynchronicznej jest liczba znaków strony sieci web.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="bf2a8-118">Kod jest odpowiedni dla aplikacji Windows Presentation Foundation (WPF) lub aplikacji do Sklepu Windows, który utworzono w programie Visual Studio; Zobacz komentarze w kodzie do konfigurowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="bf2a8-119">Możesz uruchomić ten kod w programie Visual Studio jako aplikacji Windows Presentation Foundation (WPF) lub aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="bf2a8-120">Należy kontrolkę przycisku o nazwie `StartButton` i kontrolki pola tekstowego o nazwie `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="bf2a8-121">Pamiętaj, aby ustawić nazwy i obsługi, co wymaga mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="bf2a8-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="bf2a8-122">Aby uruchomić kod jako aplikacja WPF:</span><span class="sxs-lookup"><span data-stu-id="bf2a8-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="bf2a8-123">Wklej ten kod do `MainWindow` klasy w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="bf2a8-124">Dodaj odwołanie do System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="bf2a8-125">Dodaj `using` dyrektywy dla System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="bf2a8-126">Aby uruchomić kod jako aplikacji ze Sklepu Windows:</span><span class="sxs-lookup"><span data-stu-id="bf2a8-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="bf2a8-127">Wklej ten kod do `MainPage` klasy w MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="bf2a8-128">Dodawanie przy użyciu dyrektyw System.Net.Http i System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="bf2a8-129">Aby uzyskać więcej informacji na temat zadań i kod, który jest wykonywany podczas oczekiwania na zadania, zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="bf2a8-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="bf2a8-130">Aby uzyskać pełny przykład WPF, która używa podobnych elementów, zobacz [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="bf2a8-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="bf2a8-131">Typy zwracane</span><span class="sxs-lookup"><span data-stu-id="bf2a8-131">Return Types</span></span>  
<span data-ttu-id="bf2a8-132">Metoda asynchroniczna może mieć następujące typy zwracane:</span><span class="sxs-lookup"><span data-stu-id="bf2a8-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="bf2a8-133">[void](../../../csharp/language-reference/keywords/void.md), które należy używać tylko w przypadku procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-133">[void](../../../csharp/language-reference/keywords/void.md), which should only be used for event handlers.</span></span>
- <span data-ttu-id="bf2a8-134">Począwszy od C# 7, dowolnego typu, który jest dostępny `GetAwaiter` metody.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-134">Starting with C# 7, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="bf2a8-135">`System.Threading.Tasks.ValueTask<TResult>` Typ jest takie wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-135">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="bf2a8-136">Jest dostępna przez dodanie pakietu NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-136">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="bf2a8-137">Metoda asynchroniczna nie można zadeklarować żadnego [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out.md) parametry, ani nie może on mieć <!-- [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) -->wartości zwracanej odwołania, ale można wywołać metody, które mają takie parametry.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-137">The async method can't declare any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters, nor can it have a <!-- [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) -->reference return value, but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="bf2a8-138">Należy określić `Task<TResult>` jako zwracany typ metody asynchronicznej Jeśli [zwracać](../../../csharp/language-reference/keywords/return.md) instrukcji metody określa argumentu operacji typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-138">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="bf2a8-139">Możesz użyć `Task` Jeśli nie istotnych wartość jest zwracana po zakończeniu metody.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-139">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="bf2a8-140">Oznacza to, zwraca wywołanie do metody `Task`, ale jeśli `Task` zostało zakończone, wszelkie `await` wyrażenie, które oczekuje na `Task` daje w wyniku `void`.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-140">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="bf2a8-141">Możesz użyć `void` zwracany typ głównie w celu definiowania metod obsługi zdarzeń, wymagających, który typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-141">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="bf2a8-142">Element wywołujący `void`-zwracanie metoda asynchroniczna nie można zdefiniować oczekiwania go i nie można przechwytywać wyjątki, które metoda zgłasza.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-142">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="bf2a8-143">Począwszy od C# 7, zwróć inny typ, zwykle typu wartości, która ma `GetAwaiter` metodę alokacji pamięci miminize w wydajności krytyczne fragmentów kodu.</span><span class="sxs-lookup"><span data-stu-id="bf2a8-143">Starting with C# 7, you return another type, typically a value type, that has a `GetAwaiter` method to miminize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="bf2a8-144">Aby uzyskać dodatkowe informacje i przykłady, zobacz [Async zwracać typów](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="bf2a8-144">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf2a8-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf2a8-145">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [<span data-ttu-id="bf2a8-146">await</span><span class="sxs-lookup"><span data-stu-id="bf2a8-146">await</span></span>](../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="bf2a8-147">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await</span><span class="sxs-lookup"><span data-stu-id="bf2a8-147">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="bf2a8-148">Programowanie asynchroniczne z async i await</span><span class="sxs-lookup"><span data-stu-id="bf2a8-148">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
