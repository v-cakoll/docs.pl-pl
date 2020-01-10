---
title: C# odwołanie asynchroniczne
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 3d3f045eed3bad3624ed4994aebb862c52a4e196
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713784"
---
# <a name="async-c-reference"></a>async (odwołanie w C#)

Użyj modyfikatora `async`, aby określić, że metoda, [wyrażenie lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lub [Metoda anonimowa](../operators/delegate-operator.md) jest asynchroniczna. Jeśli używasz tego modyfikatora w metodzie lub wyrażeniu, jest on nazywany *metodą Async*. W poniższym przykładzie zdefiniowano metodę asynchroniczną o nazwie `ExampleMethodAsync`:
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Jeśli dopiero zaczynasz programowanie asynchroniczne lub nie wiesz, w jaki sposób Metoda async używa [operatora`await`](../operators/await.md) , aby wykonać potencjalnie długotrwałą działanie bez blokowania wątku wywołującego, przeczytaj wprowadzenie do [programowania asynchronicznego z Async i await](../../programming-guide/concepts/async/index.md). Poniższy kod znajduje się w metodzie asynchronicznej i wywołuje metodę <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType>:
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Metoda asynchroniczna jest uruchamiana synchronicznie do momentu osiągnięcia pierwszego wyrażenia `await`, w którym metoda jest wstrzymana do czasu ukończenia zadania. W międzyczasie sterowanie jest przekazywane do obiektu wywołującego metody, tak jak pokazano w przykładzie w następnej sekcji.  
  
Jeśli metoda modyfikowana przez słowo kluczowe `async` nie zawiera `await` wyrażenia lub instrukcji, metoda jest wykonywana synchronicznie. Ostrzeżenie kompilatora ostrzega użytkownika o wszelkich metodach asynchronicznych, które nie zawierają instrukcji `await`, ponieważ taka sytuacja może wskazywać na błąd. Zobacz [Ostrzeżenie kompilatora (poziom 1) CS4014](../compiler-messages/cs4014.md).  
  
 Słowo kluczowe `async` jest kontekstowe w tym, że jest słowo kluczowe tylko wtedy, gdy modyfikuje metodę, wyrażenie lambda lub metodę anonimową. W innych kontekstach jest interpretowane jako identyfikator.  
  
## <a name="example"></a>Przykład  
W poniższym przykładzie pokazano strukturę i przepływ kontroli między obsługą zdarzeń asynchronicznych, `StartButton_Click`i metodę asynchroniczną `ExampleMethodAsync`. Wynikiem metody asynchronicznej jest liczba znaków strony sieci Web. Kod jest odpowiedni dla aplikacji Windows Presentation Foundation (WPF) lub aplikacji ze sklepu Windows, którą tworzysz w programie Visual Studio; Zobacz komentarze do kodu dotyczące konfigurowania aplikacji.  

Ten kod można uruchomić w programie Visual Studio jako aplikacja Windows Presentation Foundation (WPF) lub aplikacja ze sklepu Windows. Wymagana jest kontrolka przycisku o nazwie `StartButton` i kontrolki TextBox o nazwie `ResultsTextBox`. Pamiętaj, aby ustawić nazwy i obsługę, tak aby wyglądały następująco:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Aby uruchomić kod jako aplikację WPF:  

- Wklej ten kod do klasy `MainWindow` w MainWindow.xaml.cs.  
- Dodaj odwołanie do systemu .NET. http.  
- Dodaj dyrektywę `using` dla systemu .NET. http.  
  
Aby uruchomić kod jako aplikację ze sklepu Windows:  

- Wklej ten kod do klasy `MainPage` w MainPage.xaml.cs.  
- Dodaj dyrektywy using dla systemu .NET. http i system. Threading. Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> Aby uzyskać więcej informacji o zadaniach i kodzie, który jest wykonywany podczas oczekiwania na zadanie, zobacz [programowanie asynchroniczne z Async i await](../../programming-guide/concepts/async/index.md). Aby zapoznać się z pełnym przykładem WPF, który używa podobnych elementów, zobacz [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Typy zwracane  
Metoda asynchroniczna może mieć następujące zwracane typy:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [typ void](./void.md). Metody `async void` są generalnie odradzane w przypadku kodu innego niż programy obsługi zdarzeń, ponieważ obiekty wywołujące nie mogą `await` tych metod i muszą implementować inny mechanizm do zgłaszania pomyślnych warunków ukończenia lub błędów.
- Począwszy od C# 7,0, dowolnego typu, który ma dostępną metodę `GetAwaiter`. Typ `System.Threading.Tasks.ValueTask<TResult>` to taka implementacja. Jest on dostępny przez dodanie pakietu NuGet `System.Threading.Tasks.Extensions`. 

Metoda async nie może deklarować żadnych parametrów [in](./in-parameter-modifier.md), [ref](./ref.md) ani [out](./out-parameter-modifier.md) ani nie może mieć [wartości zwracanej przez odwołanie](../../programming-guide/classes-and-structs/ref-returns.md), ale może wywoływać metody, które mają takie parametry.  
  
Należy określić `Task<TResult>` jako zwracany typ metody asynchronicznej, jeśli instrukcja [Return](./return.md) metody określa argument operacji typu `TResult`. Należy używać `Task`, jeśli podczas kończenia metody nie zostanie zwrócona wartość znacząca. Oznacza to, że wywołanie metody zwraca `Task`, ale po zakończeniu `Task`, każde wyrażenie `await`, które oczekuje na `Task`, daje w wyniku `void`.  
  
Typ zwracany `void` jest używany głównie do definiowania programów obsługi zdarzeń, które wymagają tego typu zwracanego. Obiekt wywołujący metodę asynchroniczną zwracającą `void`nie może czekać na to i nie może przechwytywać wyjątków, które metoda zgłasza.  

Począwszy od C# 7,0, zwracany jest inny typ, zazwyczaj typ wartości, który ma `GetAwaiter` metodę, aby zminimalizować alokacje pamięci w sekcjach o kluczowym znaczeniu dla wydajności. 

Aby uzyskać więcej informacji i przykładów, zobacz [asynchroniczne typy zwracane](../../programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [Przewodnik: uzyskiwanie dostępu do sieci za pomocą Async i Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z Async i Await](../../programming-guide/concepts/async/index.md)
