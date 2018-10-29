---
title: async (odwołanie w C#)
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 021a4291f550eca517cbdc9769c2a9f0aca99d1e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199880"
---
# <a name="async-c-reference"></a><span data-ttu-id="16f56-102">async (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="16f56-102">async (C# Reference)</span></span>
<span data-ttu-id="16f56-103">Użyj `async` modyfikator, aby określić, że metoda, [wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), lub [metody anonimowej](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) jest asynchroniczna.</span><span class="sxs-lookup"><span data-stu-id="16f56-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="16f56-104">Jeśli metoda lub wyrażenie jest używany ten modyfikator, nazywa się *metody asynchronicznej*.</span><span class="sxs-lookup"><span data-stu-id="16f56-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="16f56-105">W poniższym przykładzie zdefiniowano metodę async o nazwie `ExampleMethodAsync`:</span><span class="sxs-lookup"><span data-stu-id="16f56-105">The following example defines an async method named `ExampleMethodAsync`:</span></span> 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
<span data-ttu-id="16f56-106">Jeśli jesteś nowym użytkownikiem programowaniu asynchronicznym lub nie rozumieją, jak korzysta z metody asynchronicznej `await` — słowo kluczowe do potencjalnie długotrwałej pracy bez blokowania wątku obiektu wywołującego, przeczytaj wprowadzenie w [Asynchronous Programming with Async i await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="16f56-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="16f56-107">Poniższy kod znajduje się wewnątrz metody asynchronicznej i wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="16f56-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="16f56-108">Metoda asynchroniczna jest uruchamiana synchronicznie aż do napotkania pierwszego `await` wyrażenia, w tym momencie metoda jest zawieszona do czasu ukończenia oczekiwane zadanie.</span><span class="sxs-lookup"><span data-stu-id="16f56-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="16f56-109">W międzyczasie sterowanie jest przekazywane do obiektu wywołującego metody, tak jak pokazano w przykładzie w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="16f56-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="16f56-110">Jeśli metoda, `async` modyfikuje słowo kluczowe nie zawiera `await` wyrażenia lub instrukcji, metoda jest wykonywana synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="16f56-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="16f56-111">Ostrzeżenia kompilatora ostrzega przed wszystkimi metodami asynchronicznymi, które nie zawierają `await` instrukcji, ponieważ taka sytuacja może wskazywać na błąd.</span><span class="sxs-lookup"><span data-stu-id="16f56-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="16f56-112">Zobacz [ostrzeżenie kompilatora (poziom 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="16f56-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="16f56-113">`async` — Słowo kluczowe jest kontekstowe w tym jest słowem kluczowym tylko wtedy, gdy modyfikuje metodę, wyrażenie lambda lub metodę anonimową.</span><span class="sxs-lookup"><span data-stu-id="16f56-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="16f56-114">W innych kontekstach jest interpretowane jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="16f56-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16f56-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="16f56-115">Example</span></span>  
<span data-ttu-id="16f56-116">Poniższy przykład pokazuje strukturę i przepływ sterowania między programem obsługi zdarzeń asynchronicznych `StartButton_Click`, a metodą asynchroniczną `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="16f56-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="16f56-117">Wynikiem metody asynchronicznej jest liczbą znaków strony sieci web.</span><span class="sxs-lookup"><span data-stu-id="16f56-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="16f56-118">Kod jest odpowiedni dla aplikacji Windows Presentation Foundation (WPF) lub aplikacji Windows Store, który zostanie utworzony w programie Visual Studio; Zobacz komentarze w kodzie dotyczące konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16f56-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="16f56-119">Ten kod może działać w programie Visual Studio, jako aplikację Windows Presentation Foundation (WPF) lub aplikację Windows Store.</span><span class="sxs-lookup"><span data-stu-id="16f56-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="16f56-120">Potrzebujesz formant przycisku o nazwie `StartButton` i formant pola tekstowego o nazwie `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="16f56-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="16f56-121">Pamiętaj, aby ustawić nazwy i obsługi, aby mieć podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="16f56-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="16f56-122">Aby uruchomić kod jako aplikację WPF:</span><span class="sxs-lookup"><span data-stu-id="16f56-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="16f56-123">Wklej ten kod do `MainWindow` klasy w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="16f56-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="16f56-124">Dodaj odwołanie do System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="16f56-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="16f56-125">Dodaj `using` dyrektywy dla System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="16f56-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="16f56-126">Aby uruchomić kod jako aplikację Windows Store:</span><span class="sxs-lookup"><span data-stu-id="16f56-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="16f56-127">Wklej ten kod do `MainPage` klasy w MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="16f56-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="16f56-128">Dodaj dyrektywy using dla System.Net.Http i System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="16f56-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="16f56-129">Aby uzyskać więcej informacji o zadaniach i kodzie, który jest wykonywany podczas oczekiwania na zadanie, zobacz [Asynchronous Programming with async i await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="16f56-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="16f56-130">Aby uzyskać pełny przykład WPF wykorzystującego podobne, zobacz [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="16f56-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="16f56-131">Typy zwracane</span><span class="sxs-lookup"><span data-stu-id="16f56-131">Return Types</span></span>  
<span data-ttu-id="16f56-132">Metoda asynchroniczna może mieć następujące typy zwracane:</span><span class="sxs-lookup"><span data-stu-id="16f56-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="16f56-133">[void](../../../csharp/language-reference/keywords/void.md), która powinna służyć wyłącznie do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="16f56-133">[void](../../../csharp/language-reference/keywords/void.md), which should only be used for event handlers.</span></span>
- <span data-ttu-id="16f56-134">Począwszy od C# 7.0, dowolny typ, który jest dostępny `GetAwaiter` metody.</span><span class="sxs-lookup"><span data-stu-id="16f56-134">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="16f56-135">`System.Threading.Tasks.ValueTask<TResult>` Typ jest takie wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="16f56-135">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="16f56-136">Jest on dostępny, dodając pakiet NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="16f56-136">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="16f56-137">Metoda async nie może deklarować [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów ani nie może on mieć [odwoływać się do wartości zwracanej](../../programming-guide/classes-and-structs/ref-returns.md), ale może wywołać metody które mają takie parametry.</span><span class="sxs-lookup"><span data-stu-id="16f56-137">The async method can't declare any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="16f56-138">Należy określić `Task<TResult>` jako zwracany typ metody asynchronicznej Jeśli [zwracają](../../../csharp/language-reference/keywords/return.md) instrukcja metody określa operandę typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="16f56-138">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="16f56-139">Możesz użyć `Task` Jeśli żadna mająca znaczenie wartość jest zwracana, gdy metoda zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="16f56-139">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="16f56-140">Oznacza to, że wywołanie metody zwraca `Task`, ale gdy `Task` zostanie zakończona, wszelkie `await` wyrażenie, które oczekuje na `Task` daje w wyniku `void`.</span><span class="sxs-lookup"><span data-stu-id="16f56-140">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="16f56-141">Możesz użyć `void` zwracany typ głównie do definiowania uchwytów zdarzeń, które wymagają typów zwracanych.</span><span class="sxs-lookup"><span data-stu-id="16f56-141">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="16f56-142">Obiekt wywołujący `void`— metodę asynchroniczną zwracającą nie może oczekiwać i nie może przechwytywać wyjątków, które metoda wygeneruje.</span><span class="sxs-lookup"><span data-stu-id="16f56-142">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="16f56-143">Począwszy od C# 7.0, zwróć inny typ, zwykle typu wartości, która ma `GetAwaiter` metodę, aby zminimalizować, alokacje pamięci w newralgicznym dla wydajności sekcje kodu.</span><span class="sxs-lookup"><span data-stu-id="16f56-143">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="16f56-144">Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="16f56-144">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f56-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16f56-145">See Also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
- [<span data-ttu-id="16f56-146">await</span><span class="sxs-lookup"><span data-stu-id="16f56-146">await</span></span>](../../../csharp/language-reference/keywords/await.md)  
- [<span data-ttu-id="16f56-147">Przewodnik: uzyskiwanie dostępu do sieci za pomocą Async i Await</span><span class="sxs-lookup"><span data-stu-id="16f56-147">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [<span data-ttu-id="16f56-148">Programowanie asynchroniczne z Async i Await</span><span class="sxs-lookup"><span data-stu-id="16f56-148">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
