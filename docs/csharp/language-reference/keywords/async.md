---
title: C# odwołanie asynchroniczne
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 3bf71bbe0e3f4e14f140f5a1b98a662ceaaea419
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68362993"
---
# <a name="async-c-reference"></a>async (odwołanie w C#)

Użyj modyfikatora, aby określić, że metoda, [wyrażenie lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)lub [Metoda anonimowa](../../../csharp/language-reference/operators/delegate-operator.md) jest asynchroniczna. `async` Jeśli używasz tego modyfikatora w metodzie lub wyrażeniu, jest on nazywany *metodą Async*. W poniższym przykładzie zdefiniowano metodę asynchroniczną `ExampleMethodAsync`o nazwie:
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Jeśli dopiero zaczynasz programowanie asynchroniczne lub nie wiesz, jak Metoda async używa `await` słowa kluczowego, aby wykonać potencjalnie długotrwałe działania bez blokowania wątku wywołującego, przeczytaj wprowadzenie do [programowania asynchronicznego przy użyciu Async i Oczekiwanie](../../../csharp/programming-guide/concepts/async/index.md). Poniższy kod znajduje się w metodzie asynchronicznej i wywołuje <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metodę: 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Metoda async jest uruchamiana synchronicznie do momentu, `await` aż osiągnie swoje pierwsze wyrażenie, w którym momencie Metoda jest wstrzymana do momentu ukończenia zadania. W międzyczasie sterowanie jest przekazywane do obiektu wywołującego metody, tak jak pokazano w przykładzie w następnej sekcji.  
  
Jeśli metoda modyfikowana przez `async` słowo kluczowe nie `await` zawiera wyrażenia lub instrukcji, metoda jest wykonywana synchronicznie. Ostrzeżenie kompilatora ostrzega użytkownika o wszelkich metodach asynchronicznych, które `await` nie zawierają instrukcji, ponieważ taka sytuacja może wskazywać na błąd. Zobacz [Ostrzeżenie kompilatora (poziom 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 `async` Słowo kluczowe jest kontekstowe, ponieważ jest słowem kluczowym tylko wtedy, gdy modyfikuje metodę, wyrażenie lambda lub metodę anonimową. W innych kontekstach jest interpretowane jako identyfikator.  
  
## <a name="example"></a>Przykład  
Poniższy przykład pokazuje strukturę i przepływ kontroli między obsługą `StartButton_Click`zdarzeń asynchronicznych, i `ExampleMethodAsync`metodę asynchroniczną. Wynikiem metody asynchronicznej jest liczba znaków strony sieci Web. Kod jest odpowiedni dla aplikacji Windows Presentation Foundation (WPF) lub aplikacji ze sklepu Windows, którą tworzysz w programie Visual Studio; Zobacz komentarze do kodu dotyczące konfigurowania aplikacji.  

Ten kod można uruchomić w programie Visual Studio jako aplikacja Windows Presentation Foundation (WPF) lub aplikacja ze sklepu Windows. Potrzebujesz formantu Button o nazwie `StartButton` i kontrolki TextBox o nazwie. `ResultsTextBox` Pamiętaj, aby ustawić nazwy i obsługę, tak aby wyglądały następująco:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Aby uruchomić kod jako aplikację WPF:  

- Wklej ten kod do `MainWindow` klasy w MainWindow.XAML.cs.  
- Dodaj odwołanie do systemu .NET. http.  
- `using` Dodaj dyrektywę dla systemu .NET. http.  
  
Aby uruchomić kod jako aplikację ze sklepu Windows:  
- Wklej ten kod do `MainPage` klasy w MainPage.XAML.cs.  
- Dodaj dyrektywy using dla systemu .NET. http i system. Threading. Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  Aby uzyskać więcej informacji o zadaniach i kodzie, który jest wykonywany podczas oczekiwania na zadanie, zobacz [programowanie asynchroniczne z Async i await](../../../csharp/programming-guide/concepts/async/index.md). Aby zapoznać się z pełnym przykładem WPF, który używa [podobnych elementów, zobacz Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)Async i await.  
  
## <a name="return-types"></a>Typy zwracane  
Metoda asynchroniczna może mieć następujące zwracane typy:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [typ void](../../../csharp/language-reference/keywords/void.md). `async void`metody są generalnie odradzane dla kodu innego niż programy obsługi zdarzeń, ponieważ obiekty wywołujące nie mogą `await` być tymi metodami i muszą implementować inny mechanizm, aby zgłosić pomyślne zakończenie lub błędy.
- Począwszy od C# 7,0, dowolnego typu, który ma dostępną `GetAwaiter` metodę. `System.Threading.Tasks.ValueTask<TResult>` Typ to taka implementacja. Jest on dostępny przez dodanie pakietu `System.Threading.Tasks.Extensions`NuGet. 

Metoda async nie może deklarować żadnych parametrów [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) ani [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) ani nie może mieć [wartości zwracanej przez odwołanie](../../programming-guide/classes-and-structs/ref-returns.md), ale może wywoływać metody, które mają takie parametry.  
  
Należy określić `Task<TResult>` jako zwracany typ metody asynchronicznej, jeśli instrukcja [Return](../../../csharp/language-reference/keywords/return.md) metody określa argument operacji typu `TResult`. Należy użyć `Task` , jeśli podczas kończenia metody nie zostanie zwrócona wartość znacząca. Oznacza to, `Task`że wywołanie metody zwraca, ale `Task` po zakończeniu, dowolne `await` wyrażenie, `void`które oczekuje `Task` na wartości.  
  
Typ `void` zwracany jest używany głównie do definiowania programów obsługi zdarzeń, które wymagają tego typu zwracanego. Obiekt wywołujący metodę `void`asynchroniczną zwracającą wartość, której nie może oczekiwać i nie może przechwytywać wyjątków zgłaszanych przez metodę.  

Począwszy od C# 7,0, zwracany jest inny typ, zazwyczaj typ wartości, który ma `GetAwaiter` metodę, aby zminimalizować alokacje pamięci w sekcjach o krytycznym znaczeniu dla wydajności kodu. 

Aby uzyskać więcej informacji i przykładów, zobacz [asynchroniczne typy zwracane](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../../../csharp/language-reference/keywords/await.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z Async i Await](../../../csharp/programming-guide/concepts/async/index.md)
