---
title: asynchronizowania — odwołanie do języka C#
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 89133339a75c70e3ac86d627065e78d555bff71d
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507207"
---
# <a name="async-c-reference"></a>async (odwołanie w C#)

Użyj `async` modyfikatora, aby określić, że metoda, [wyrażenie lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lub [metoda anonimowa](../operators/delegate-operator.md) jest asynchroniczne. Jeśli używasz tego modyfikatora w metodzie lub wyrażeniu, jest on określany jako *metoda asynchroniowa*. Poniższy przykład definiuje metodę asynchronizową o nazwie: `ExampleMethodAsync`
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

Jeśli jesteś nowy w programowaniu asynchroniczne lub nie rozumiem, jak metoda asynchroniza [ `await` operatora](../operators/await.md) do potencjalnie długotrwałej pracy bez blokowania wątku wywołującego, przeczytaj wprowadzenie w [programowaniu asynchroniczne z asynchnc i await](../../programming-guide/concepts/async/index.md). Następujący kod znajduje się wewnątrz metody asynchroniiowej i wywołuje <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metodę:
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Metoda asynchronicznego działa synchronicznie, dopóki `await` nie osiągnie pierwszego wyrażenia, w którym to momencie metoda jest zawieszona do czasu zakończenia oczekiwanego zadania. W międzyczasie sterowanie jest przekazywane do obiektu wywołującego metody, tak jak pokazano w przykładzie w następnej sekcji.  
  
Jeśli metoda modyfikuje `async` słowa kluczowego `await` nie zawiera wyrażenia lub instrukcji, metoda jest wykonywana synchronicznie. Ostrzeżenie kompilatora ostrzega o wszelkich metodach asynchronizacyjnych, które nie zawierają `await` instrukcji, ponieważ ta sytuacja może wskazywać na błąd. Zobacz [Ostrzeżenie kompilatora (poziom 1) CS4014](../compiler-messages/cs4014.md).  
  
 Słowo `async` kluczowe jest kontekstowe, ponieważ jest słowem kluczowym tylko wtedy, gdy modyfikuje metodę, wyrażenie lambda lub metodę anonimową. W innych kontekstach jest interpretowane jako identyfikator.  
  
## <a name="example"></a>Przykład  
Poniższy przykład przedstawia strukturę i przepływ kontroli między `StartButton_Click`programem obsługi zdarzeń asynchronicznych i metodą asynchronizną. `ExampleMethodAsync` Wynikiem metody asynchronizowej jest liczba znaków strony sieci web. Kod jest odpowiedni dla aplikacji Windows Presentation Foundation (WPF) lub aplikacji ze Sklepu Windows, którą tworzysz w programie Visual Studio; zobacz komentarze do kodu do skonfigurowania aplikacji.  

Ten kod można uruchomić w programie Visual Studio jako aplikacja Windows Presentation Foundation (WPF) lub w aplikacji ze Sklepu Windows. Potrzebny jest kontrolka Button o `StartButton` `ResultsTextBox`nazwie i kontrolka Textbox o nazwie . Pamiętaj, aby ustawić nazwy i program obsługi, tak aby mieć coś takiego:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Aby uruchomić kod jako aplikację WPF:  

- Wklej ten kod `MainWindow` do klasy w MainWindow.xaml.cs.  
- Dodaj odwołanie do pliku System.Net.http.  
- Dodaj `using` dyrektywę dla System.Net.Http.  
  
Aby uruchomić kod jako aplikację ze Sklepu Windows:  

- Wklej ten kod `MainPage` do klasy w MainPage.xaml.cs.  
- Dodaj za pomocą dyrektyw dla System.Net.Http i System.Threading.Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> Aby uzyskać więcej informacji o zadaniach i kodzie, który jest wykonywany podczas oczekiwania na zadanie, zobacz [Programowanie asynchroniczne za pomocą asynchronicznego i oczekiwania.](../../programming-guide/concepts/async/index.md) Aby uzyskać pełny przykład WPF, który używa podobnych elementów, zobacz [Przewodnik: Uzyskiwanie dostępu do sieci Web przy użyciu async i await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Typy zwracane  
Metoda asynchroniowa może mieć następujące typy zwracane:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../builtin-types/void.md). `async void`metody są zazwyczaj odradzane dla kodu innego `await` niż programy obsługi zdarzeń, ponieważ wywołania nie można tych metod i musi zaimplementować inny mechanizm do zgłaszania pomyślnego zakończenia lub warunków błędu.
- Począwszy od języka C# 7.0, `GetAwaiter` dowolnego typu, który ma metodę dostępną. Typ `System.Threading.Tasks.ValueTask<TResult>` jest jednym z takich implementacji. Jest on dostępny przez dodanie `System.Threading.Tasks.Extensions`pakietu NuGet .

Metoda asynchronizowana nie może deklarować żadnych parametrów [in](./in-parameter-modifier.md), [ref](./ref.md) lub [out,](./out-parameter-modifier.md) ani nie może mieć [referencyjnej wartości zwracanej,](../../programming-guide/classes-and-structs/ref-returns.md)ale może wywoływać metody, które mają takie parametry.  
  
Jako `Task<TResult>` typ zwracany metody asynchronizowej należy określić, jeśli instrukcja `TResult` [zwracana](./return.md) metody określa argument typu . Użyj, `Task` jeśli nie znaczące wartości są zwracane po zakończeniu metody. Oznacza to, że wywołanie `Task`metody zwraca `Task` , ale `await` po zakończeniu, każde `Task` wyrażenie, `void`które oczekuje na ocenę .  
  
Typ zwracany `void` służy przede wszystkim do definiowania programów obsługi zdarzeń, które wymagają tego typu zwracania. Wywołujący `void`metodę asynchronii zwracaną nie może na nią czekać i nie można złapać wyjątków, które zgłasza metoda.  

Począwszy od języka C# 7.0, zwracasz inny typ, `GetAwaiter` zazwyczaj typ wartości, który ma metodę minimalizowania alokacji pamięci w sekcjach krytycznych dla wydajności kodu.

Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [await](../operators/await.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwania](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z asynnc i czekają](../../programming-guide/concepts/async/index.md)
