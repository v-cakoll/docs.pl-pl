---
title: Async — C# odwołania
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: f902d6a92f9d982dc00c3446f7b516c372f1a30e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662052"
---
# <a name="async-c-reference"></a>async (odwołanie w C#)
Użyj `async` modyfikator, aby określić, że metoda, [wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), lub [metody anonimowej](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) jest asynchroniczna. Jeśli metoda lub wyrażenie jest używany ten modyfikator, nazywa się *metody asynchronicznej*. W poniższym przykładzie zdefiniowano metodę async o nazwie `ExampleMethodAsync`: 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
Jeśli jesteś nowym użytkownikiem programowaniu asynchronicznym lub nie rozumieją, jak korzysta z metody asynchronicznej `await` — słowo kluczowe do potencjalnie długotrwałej pracy bez blokowania wątku obiektu wywołującego, przeczytaj wprowadzenie w [Asynchronous Programming with Async i await](../../../csharp/programming-guide/concepts/async/index.md). Poniższy kod znajduje się wewnątrz metody asynchronicznej i wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metody: 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Metoda asynchroniczna jest uruchamiana synchronicznie aż do napotkania pierwszego `await` wyrażenia, w tym momencie metoda jest zawieszona do czasu ukończenia oczekiwane zadanie. W międzyczasie sterowanie jest przekazywane do obiektu wywołującego metody, tak jak pokazano w przykładzie w następnej sekcji.  
  
Jeśli metoda, `async` modyfikuje słowo kluczowe nie zawiera `await` wyrażenia lub instrukcji, metoda jest wykonywana synchronicznie. Ostrzeżenia kompilatora ostrzega przed wszystkimi metodami asynchronicznymi, które nie zawierają `await` instrukcji, ponieważ taka sytuacja może wskazywać na błąd. Zobacz [ostrzeżenie kompilatora (poziom 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 `async` — Słowo kluczowe jest kontekstowe w tym jest słowem kluczowym tylko wtedy, gdy modyfikuje metodę, wyrażenie lambda lub metodę anonimową. W innych kontekstach jest interpretowane jako identyfikator.  
  
## <a name="example"></a>Przykład  
Poniższy przykład pokazuje strukturę i przepływ sterowania między programem obsługi zdarzeń asynchronicznych `StartButton_Click`, a metodą asynchroniczną `ExampleMethodAsync`. Wynikiem metody asynchronicznej jest liczbą znaków strony sieci web. Kod jest odpowiedni dla aplikacji Windows Presentation Foundation (WPF) lub aplikacji Windows Store, który zostanie utworzony w programie Visual Studio; Zobacz komentarze w kodzie dotyczące konfiguracji aplikacji.  

Ten kod może działać w programie Visual Studio, jako aplikację Windows Presentation Foundation (WPF) lub aplikację Windows Store. Potrzebujesz formant przycisku o nazwie `StartButton` i formant pola tekstowego o nazwie `ResultsTextBox`. Pamiętaj, aby ustawić nazwy i obsługi, aby mieć podobny do poniższego:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Aby uruchomić kod jako aplikację WPF:  

- Wklej ten kod do `MainWindow` klasy w MainWindow.xaml.cs.  
- Dodaj odwołanie do System.Net.Http.  
- Dodaj `using` dyrektywy dla System.Net.Http.  
  
Aby uruchomić kod jako aplikację Windows Store:  
- Wklej ten kod do `MainPage` klasy w MainPage.xaml.cs.  
- Dodaj dyrektywy using dla System.Net.Http i System.Threading.Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  Aby uzyskać więcej informacji o zadaniach i kodzie, który jest wykonywany podczas oczekiwania na zadanie, zobacz [Asynchronous Programming with async i await](../../../csharp/programming-guide/concepts/async/index.md). Aby uzyskać pełny przykład WPF wykorzystującego podobne, zobacz [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Typy zwracane  
Metoda asynchroniczna może mieć następujące typy zwracane:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../../../csharp/language-reference/keywords/void.md), która powinna służyć wyłącznie do obsługi zdarzeń.
- Począwszy od C# 7.0, dowolny typ, który jest dostępny `GetAwaiter` metody. `System.Threading.Tasks.ValueTask<TResult>` Typ jest takie wdrożenie. Jest on dostępny, dodając pakiet NuGet `System.Threading.Tasks.Extensions`. 

Metoda async nie może deklarować [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów ani nie może on mieć [odwoływać się do wartości zwracanej](../../programming-guide/classes-and-structs/ref-returns.md), ale może wywołać metody które mają takie parametry.  
  
Należy określić `Task<TResult>` jako zwracany typ metody asynchronicznej Jeśli [zwracają](../../../csharp/language-reference/keywords/return.md) instrukcja metody określa operandę typu `TResult`. Możesz użyć `Task` Jeśli żadna mająca znaczenie wartość jest zwracana, gdy metoda zostanie zakończona. Oznacza to, że wywołanie metody zwraca `Task`, ale gdy `Task` zostanie zakończona, wszelkie `await` wyrażenie, które oczekuje na `Task` daje w wyniku `void`.  
  
Możesz użyć `void` zwracany typ głównie do definiowania uchwytów zdarzeń, które wymagają typów zwracanych. Obiekt wywołujący `void`— metodę asynchroniczną zwracającą nie może oczekiwać i nie może przechwytywać wyjątków, które metoda wygeneruje.  

Począwszy od C# 7.0, zwróć inny typ, zwykle typu wartości, która ma `GetAwaiter` metodę, aby zminimalizować, alokacje pamięci w newralgicznym dla wydajności sekcje kodu. 

Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../../../csharp/language-reference/keywords/await.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z Async i Await](../../../csharp/programming-guide/concepts/async/index.md)
