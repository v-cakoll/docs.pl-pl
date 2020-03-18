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
# <a name="async-c-reference"></a>async (odwołanie w C#)

Użyj `async` modyfikatora, aby określić, że metoda, [wyrażenie lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lub [metoda anonimowa](../operators/delegate-operator.md) jest asynchroniczna. Jeśli używasz tego modyfikatora w metodzie lub wyrażeniu, jest on określany jako *metoda asynchroniczna*. W poniższym przykładzie zdefiniowano `ExampleMethodAsync`metodę asynchronia o nazwie:
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Jeśli jesteś nowy w programowaniu asynchronicznym lub nie rozumiesz, jak metoda asynchroniczna używa [ `await` operatora](../operators/await.md) do wykonywania potencjalnie długotrwałej pracy bez blokowania wątku wywołującego, przeczytaj wprowadzenie w [programowaniu asynchronicznym z async i czekam .](../../programming-guide/concepts/async/index.md) Następujący kod znajduje się wewnątrz metody asynchronicznej i wywołuje <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metodę:
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Metoda asynchroniczna jest uruchamiana synchronicznie, dopóki nie osiągnie swojego pierwszego `await` wyrażenia, w którym to momencie metoda jest zawieszona do momentu zakończenia oczekiwanego zadania. W międzyczasie sterowanie jest przekazywane do obiektu wywołującego metody, tak jak pokazano w przykładzie w następnej sekcji.  
  
Jeśli metoda, `async` która modyfikuje słowo kluczowe `await` nie zawiera wyrażenia lub instrukcji, metoda jest wykonywana synchronicznie. Ostrzeżenie kompilatora ostrzega o wszelkich metodach asynchronicznych, które nie zawierają `await` instrukcji, ponieważ ta sytuacja może wskazywać na błąd. Zobacz [Ostrzeżenie o kompilatorze (poziom 1) CS4014](../compiler-messages/cs4014.md).  
  
 Słowo `async` kluczowe jest kontekstowe, ponieważ jest słowem kluczowym tylko wtedy, gdy modyfikuje metodę, wyrażenie lambda lub metodę anonimową. W innych kontekstach jest interpretowane jako identyfikator.  
  
## <a name="example"></a>Przykład  
W poniższym przykładzie przedstawiono strukturę i przepływ kontroli `StartButton_Click`między programem obsługi `ExampleMethodAsync`zdarzeń asynchronicznych , a metodą asynchronicznej . Wynikiem metody asynchronicznej jest liczba znaków strony sieci Web. Kod jest odpowiedni dla aplikacji Windows Presentation Foundation (WPF) lub aplikacji ze Sklepu Windows utworzonej w programie Visual Studio; zobacz komentarze do kodu dotyczące konfigurowania aplikacji.  

Ten kod można uruchomić w programie Visual Studio jako aplikacja ZPF (Windows Presentation Foundation) lub aplikacja ze Sklepu Windows. Potrzebujesz kontrolki Button `StartButton` o nazwie i `ResultsTextBox`kontrolki Textbox o nazwie . Pamiętaj, aby ustawić nazwy i program obsługi, aby mieć coś takiego:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Aby uruchomić kod jako aplikację WPF:  

- Wklej ten kod `MainWindow` do klasy w MainWindow.xaml.cs.  
- Dodaj odwołanie do System.Net.Http.  
- Dodaj `using` dyrektywę dla System.Net.Http.  
  
Aby uruchomić kod jako aplikację ze Sklepu Windows:  

- Wklej ten kod `MainPage` do klasy w MainPage.xaml.cs.  
- Dodaj za pomocą dyrektyw dla System.Net.Http i System.Threading.Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> Aby uzyskać więcej informacji na temat zadań i kodu, który jest wykonywany podczas oczekiwania na zadanie, zobacz [Programowanie asynchroniczne z async i oczekują .](../../programming-guide/concepts/async/index.md) Aby uzyskać pełny przykład WPF, który używa podobnych elementów, zobacz [Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Typy zwracane  
Metoda asynchroniczna może mieć następujące typy zwracane:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [nieważne](../builtin-types/void.md). `async void`metody są zazwyczaj odradzane dla kodu innego niż programy `await` obsługi zdarzeń, ponieważ obiekty wywołujące nie mogą tych metod i musi zaimplementować inny mechanizm zgłaszania pomyślnego zakończenia lub warunków błędu.
- Począwszy od języka C# 7.0, `GetAwaiter` dowolnego typu, który ma metodę dostępną. Typ `System.Threading.Tasks.ValueTask<TResult>` jest jedną z takich implementacji. Jest on dostępny przez dodanie `System.Threading.Tasks.Extensions`pakietu NuGet .

Metoda asynchroniczna nie może zadeklarować żadnych parametrów [in,](./in-parameter-modifier.md) [ref](./ref.md) lub [out,](./out-parameter-modifier.md) ani nie może mieć [wartości zwracanej odwołania,](../../programming-guide/classes-and-structs/ref-returns.md)ale może wywoływać metody, które mają takie parametry.  
  
Jako `Task<TResult>` typ zwracany metody asynchronicznej można określić, jeśli instrukcja [return](./return.md) metody określa argument typu `TResult`. Można `Task` użyć, jeśli po zakończeniu metody zwracana jest żadna znacząca wartość. Oznacza to, że wywołanie `Task`metody zwraca `Task` , ale po `await` zakończeniu, każde wyrażenie, które oczekuje na `Task` ocenę . `void`  
  
Typ zwracany `void` służy przede wszystkim do definiowania programów obsługi zdarzeń, które wymagają tego typu zwracania. Obiekt wywołujący `void`-zwracanie metody asynchronicznej nie może oczekiwać na to i nie można przechwycić wyjątki, które zgłasza metoda.  

Począwszy od języka C# 7.0, zwracasz inny typ, zazwyczaj typ wartości, który ma metodę minimalizującą `GetAwaiter` alokacje pamięci w sekcjach kodu o krytycznym znaczeniu dla wydajności.

Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchroniczne programowanie z async i czekają](../../programming-guide/concepts/async/index.md)
