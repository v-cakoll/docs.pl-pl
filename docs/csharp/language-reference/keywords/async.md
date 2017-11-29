---
title: "async (odwołanie w C#)"
ms.date: 05/22/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: "52"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4a89736822342a9d9a24db6d43435f9795b81b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="async-c-reference"></a>async (odwołanie w C#)
Użyj `async` modyfikator, aby określić, że w metodzie [wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), lub [metody anonimowej](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) jest asynchroniczne. Jeśli używasz modyfikator metody lub wyrażenie, jest ona określana jako *metody asynchronicznej*. W poniższym przykładzie zdefiniowano metody asynchronicznej o nazwie `ExampleMethodAsync`: 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
W przypadku nowych do programowania asynchronicznego lub nie zrozumieć sposób używa metody asynchronicznej `await` — słowo kluczowe w pracy potencjalnie długotrwałe bez blokowania wątków obiektu wywołującego odczytu wprowadzenia w [programowanie asynchroniczne przy użyciu Async i await](../../../csharp/programming-guide/concepts/async/index.md). Poniższy kod znajduje się wewnątrz metody asynchronicznej i wywołania <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metody: 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Metody asynchronicznej jest uruchamiana synchronicznie, dopóki nie osiągnie pierwszych `await` wyrażenie w takim przypadku metoda jest wstrzymane do czasu ukończenia zadania oczekiwano. W międzyczasie sterowanie jest przekazywane do obiektu wywołującego metody, tak jak pokazano w przykładzie w następnej sekcji.  
  
Jeśli metoda który `async` modyfikuje — słowo kluczowe nie zawiera `await` wyrażenia lub instrukcji metoda wykonuje synchronicznie. Ostrzeżenie kompilatora ostrzega o dowolnej metody asynchroniczne, które nie zawierają `await` instrukcji, ponieważ taka sytuacja może wskazywać na błąd. Zobacz [ostrzeżenie kompilatora (poziom 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 `async` — Słowo kluczowe jest kontekstowe słowo kluczowe jest tylko wtedy, gdy modyfikuje metody, wyrażenia lambda lub metody anonimowej. W innych kontekstach jest interpretowane jako identyfikator.  
  
## <a name="example"></a>Przykład  
W poniższym przykładzie przedstawiono struktury i przepływu sterowania między program obsługi zdarzeń async `StartButton_Click`oraz metody asynchronicznej `ExampleMethodAsync`. Wynik metody asynchronicznej jest liczba znaków strony sieci web. Kod jest odpowiedni dla aplikacji Windows Presentation Foundation (WPF) lub aplikacji do Sklepu Windows, który utworzono w programie Visual Studio; Zobacz komentarze w kodzie do konfigurowania aplikacji.  

Możesz uruchomić ten kod w programie Visual Studio jako aplikacji Windows Presentation Foundation (WPF) lub aplikacji ze Sklepu Windows. Należy kontrolkę przycisku o nazwie `StartButton` i kontrolki pola tekstowego o nazwie `ResultsTextBox`. Pamiętaj, aby ustawić nazwy i obsługi, co wymaga mniej więcej tak:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Aby uruchomić kod jako aplikacja WPF:  

- Wklej ten kod do `MainWindow` klasy w MainWindow.xaml.cs.  
- Dodaj odwołanie do System.Net.Http.  
- Dodaj `using` dyrektywy dla System.Net.Http.  
  
Aby uruchomić kod jako aplikacji ze Sklepu Windows:  
- Wklej ten kod do `MainPage` klasy w MainPage.xaml.cs.  
- Dodawanie przy użyciu dyrektyw System.Net.Http i System.Threading.Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  Aby uzyskać więcej informacji na temat zadań i kod, który jest wykonywany podczas oczekiwania na zadania, zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md). Aby uzyskać pełny przykład WPF, która używa podobnych elementów, zobacz [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Typy zwracane  
Metoda asynchroniczna może mieć następujące typy zwracane:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../../../csharp/language-reference/keywords/void.md), które należy używać tylko w przypadku procedury obsługi zdarzeń.
- Począwszy od C# 7, dowolnego typu, który jest dostępny `GetAwaiter` metody. `System.Threading.Tasks.ValueTask<TResult>` Typ jest takie wdrożenie. Jest dostępna przez dodanie pakietu NuGet `System.Threading.Tasks.Extensions`. 

Metoda asynchroniczna nie można zadeklarować żadnego [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out.md) parametry, ani nie może on mieć <!-- [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) -->wartości zwracanej odwołania, ale można wywołać metody, które mają takie parametry.  
  
Należy określić `Task<TResult>` jako zwracany typ metody asynchronicznej Jeśli [zwracać](../../../csharp/language-reference/keywords/return.md) instrukcji metody określa argumentu operacji typu `TResult`. Możesz użyć `Task` Jeśli nie istotnych wartość jest zwracana po zakończeniu metody. Oznacza to, zwraca wywołanie do metody `Task`, ale jeśli `Task` zostało zakończone, wszelkie `await` wyrażenie, które oczekuje na `Task` daje w wyniku `void`.  
  
Możesz użyć `void` zwracany typ głównie w celu definiowania metod obsługi zdarzeń, wymagających, który typ zwracany. Element wywołujący `void`-zwracanie metoda asynchroniczna nie można zdefiniować oczekiwania go i nie można przechwytywać wyjątki, które metoda zgłasza.  

Począwszy od C# 7, zwróć inny typ, zwykle typu wartości, która ma `GetAwaiter` metodę alokacji pamięci miminize w wydajności krytyczne fragmentów kodu. 

Aby uzyskać dodatkowe informacje i przykłady, zobacz [Async zwracać typów](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [await](../../../csharp/language-reference/keywords/await.md)  
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md)
