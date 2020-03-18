---
title: async — odwołanie do języka C#
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 92e94d6fe1c07ab5cd8f29d040401a737a1db78e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173656"
---
# <a name="async-c-reference"></a><span data-ttu-id="134bc-102">async (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="134bc-102">async (C# Reference)</span></span>

<span data-ttu-id="134bc-103">Użyj `async` modyfikatora, aby określić, że metoda, [wyrażenie lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lub [metoda anonimowa](../operators/delegate-operator.md) jest asynchroniczna.</span><span class="sxs-lookup"><span data-stu-id="134bc-103">Use the `async` modifier to specify that a method, [lambda expression](../../programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="134bc-104">Jeśli używasz tego modyfikatora w metodzie lub wyrażeniu, jest on określany jako *metoda asynchroniczna*.</span><span class="sxs-lookup"><span data-stu-id="134bc-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="134bc-105">W poniższym przykładzie zdefiniowano `ExampleMethodAsync`metodę asynchronia o nazwie:</span><span class="sxs-lookup"><span data-stu-id="134bc-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

<span data-ttu-id="134bc-106">Jeśli jesteś nowy w programowaniu asynchronicznym lub nie rozumiesz, jak metoda asynchroniczna używa [ `await` operatora](../operators/await.md) do wykonywania potencjalnie długotrwałej pracy bez blokowania wątku wywołującego, przeczytaj wprowadzenie w [programowaniu asynchronicznym z async i czekam .](../../programming-guide/concepts/async/index.md)</span><span class="sxs-lookup"><span data-stu-id="134bc-106">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="134bc-107">Następujący kod znajduje się wewnątrz metody asynchronicznej i wywołuje <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metodę:</span><span class="sxs-lookup"><span data-stu-id="134bc-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="134bc-108">Metoda asynchroniczna jest uruchamiana synchronicznie, dopóki nie osiągnie swojego pierwszego `await` wyrażenia, w którym to momencie metoda jest zawieszona do momentu zakończenia oczekiwanego zadania.</span><span class="sxs-lookup"><span data-stu-id="134bc-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="134bc-109">W międzyczasie sterowanie jest przekazywane do obiektu wywołującego metody, tak jak pokazano w przykładzie w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="134bc-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="134bc-110">Jeśli metoda, `async` która modyfikuje słowo kluczowe `await` nie zawiera wyrażenia lub instrukcji, metoda jest wykonywana synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="134bc-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="134bc-111">Ostrzeżenie kompilatora ostrzega o wszelkich metodach asynchronicznych, które nie zawierają `await` instrukcji, ponieważ ta sytuacja może wskazywać na błąd.</span><span class="sxs-lookup"><span data-stu-id="134bc-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="134bc-112">Zobacz [Ostrzeżenie o kompilatorze (poziom 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="134bc-112">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="134bc-113">Słowo `async` kluczowe jest kontekstowe, ponieważ jest słowem kluczowym tylko wtedy, gdy modyfikuje metodę, wyrażenie lambda lub metodę anonimową.</span><span class="sxs-lookup"><span data-stu-id="134bc-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="134bc-114">W innych kontekstach jest interpretowane jako identyfikator.</span><span class="sxs-lookup"><span data-stu-id="134bc-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="134bc-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="134bc-115">Example</span></span>  
<span data-ttu-id="134bc-116">W poniższym przykładzie przedstawiono strukturę i przepływ kontroli `StartButton_Click`między programem obsługi `ExampleMethodAsync`zdarzeń asynchronicznych , a metodą asynchronicznej .</span><span class="sxs-lookup"><span data-stu-id="134bc-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="134bc-117">Wynikiem metody asynchronicznej jest liczba znaków strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="134bc-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="134bc-118">Kod jest odpowiedni dla aplikacji Windows Presentation Foundation (WPF) lub aplikacji ze Sklepu Windows utworzonej w programie Visual Studio; zobacz komentarze do kodu dotyczące konfigurowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="134bc-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="134bc-119">Ten kod można uruchomić w programie Visual Studio jako aplikacja ZPF (Windows Presentation Foundation) lub aplikacja ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="134bc-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="134bc-120">Potrzebujesz kontrolki Button `StartButton` o nazwie i `ResultsTextBox`kontrolki Textbox o nazwie .</span><span class="sxs-lookup"><span data-stu-id="134bc-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="134bc-121">Pamiętaj, aby ustawić nazwy i program obsługi, aby mieć coś takiego:</span><span class="sxs-lookup"><span data-stu-id="134bc-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="134bc-122">Aby uruchomić kod jako aplikację WPF:</span><span class="sxs-lookup"><span data-stu-id="134bc-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="134bc-123">Wklej ten kod `MainWindow` do klasy w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="134bc-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="134bc-124">Dodaj odwołanie do System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="134bc-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="134bc-125">Dodaj `using` dyrektywę dla System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="134bc-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="134bc-126">Aby uruchomić kod jako aplikację ze Sklepu Windows:</span><span class="sxs-lookup"><span data-stu-id="134bc-126">To run the code as a Windows Store app:</span></span>  

- <span data-ttu-id="134bc-127">Wklej ten kod `MainPage` do klasy w MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="134bc-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="134bc-128">Dodaj za pomocą dyrektyw dla System.Net.Http i System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="134bc-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> <span data-ttu-id="134bc-129">Aby uzyskać więcej informacji na temat zadań i kodu, który jest wykonywany podczas oczekiwania na zadanie, zobacz [Programowanie asynchroniczne z async i oczekują .](../../programming-guide/concepts/async/index.md)</span><span class="sxs-lookup"><span data-stu-id="134bc-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="134bc-130">Aby uzyskać pełny przykład WPF, który używa podobnych elementów, zobacz [Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="134bc-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="134bc-131">Typy zwracane</span><span class="sxs-lookup"><span data-stu-id="134bc-131">Return Types</span></span>  
<span data-ttu-id="134bc-132">Metoda asynchroniczna może mieć następujące typy zwracane:</span><span class="sxs-lookup"><span data-stu-id="134bc-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="134bc-133">[nieważne](../builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="134bc-133">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="134bc-134">`async void`metody są zazwyczaj odradzane dla kodu innego niż programy `await` obsługi zdarzeń, ponieważ obiekty wywołujące nie mogą tych metod i musi zaimplementować inny mechanizm zgłaszania pomyślnego zakończenia lub warunków błędu.</span><span class="sxs-lookup"><span data-stu-id="134bc-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="134bc-135">Począwszy od języka C# 7.0, `GetAwaiter` dowolnego typu, który ma metodę dostępną.</span><span class="sxs-lookup"><span data-stu-id="134bc-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="134bc-136">Typ `System.Threading.Tasks.ValueTask<TResult>` jest jedną z takich implementacji.</span><span class="sxs-lookup"><span data-stu-id="134bc-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="134bc-137">Jest on dostępny przez dodanie `System.Threading.Tasks.Extensions`pakietu NuGet .</span><span class="sxs-lookup"><span data-stu-id="134bc-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span>

<span data-ttu-id="134bc-138">Metoda asynchroniczna nie może zadeklarować żadnych parametrów [in,](./in-parameter-modifier.md) [ref](./ref.md) lub [out,](./out-parameter-modifier.md) ani nie może mieć [wartości zwracanej odwołania,](../../programming-guide/classes-and-structs/ref-returns.md)ale może wywoływać metody, które mają takie parametry.</span><span class="sxs-lookup"><span data-stu-id="134bc-138">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="134bc-139">Jako `Task<TResult>` typ zwracany metody asynchronicznej można określić, jeśli instrukcja [return](./return.md) metody określa argument typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="134bc-139">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="134bc-140">Można `Task` użyć, jeśli po zakończeniu metody zwracana jest żadna znacząca wartość.</span><span class="sxs-lookup"><span data-stu-id="134bc-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="134bc-141">Oznacza to, że wywołanie `Task`metody zwraca `Task` , ale po `await` zakończeniu, każde wyrażenie, które oczekuje na `Task` ocenę . `void`</span><span class="sxs-lookup"><span data-stu-id="134bc-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="134bc-142">Typ zwracany `void` służy przede wszystkim do definiowania programów obsługi zdarzeń, które wymagają tego typu zwracania.</span><span class="sxs-lookup"><span data-stu-id="134bc-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="134bc-143">Obiekt wywołujący `void`-zwracanie metody asynchronicznej nie może oczekiwać na to i nie można przechwycić wyjątki, które zgłasza metoda.</span><span class="sxs-lookup"><span data-stu-id="134bc-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="134bc-144">Począwszy od języka C# 7.0, zwracasz inny typ, zazwyczaj typ wartości, który ma metodę minimalizującą `GetAwaiter` alokacje pamięci w sekcjach kodu o krytycznym znaczeniu dla wydajności.</span><span class="sxs-lookup"><span data-stu-id="134bc-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span>

<span data-ttu-id="134bc-145">Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="134bc-145">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="134bc-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="134bc-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="134bc-147">await</span><span class="sxs-lookup"><span data-stu-id="134bc-147">await</span></span>](../operators/await.md)
- [<span data-ttu-id="134bc-148">Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie</span><span class="sxs-lookup"><span data-stu-id="134bc-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="134bc-149">Asynchroniczne programowanie z async i czekają</span><span class="sxs-lookup"><span data-stu-id="134bc-149">Asynchronous Programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
