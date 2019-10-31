---
title: Wywołanie metod synchronicznych w sposób asynchroniczny
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- asynchronous programming, delegates
- asynchronous delegates
- AsyncWaitHandle property
- callback methods
- calling synchronous methods in asynchronous manner
- WaitHandle class, code examples
- asynchronous programming, status polling
- polling asynchronous operation status
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
- waiting for asynchronous calls
- status information [.NET Framework], asynchronous operations
ms.assetid: 41972034-92ed-450a-9664-ab93fcc6f1fb
ms.openlocfilehash: 06df584f0120fbd4978e18647854a3ee844a2095
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105129"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Wywołanie metod synchronicznych w sposób asynchroniczny

.NET Framework umożliwia Asynchroniczne wywoływanie dowolnej metody. W tym celu należy zdefiniować delegata o tej samej sygnaturze, co metoda, która ma zostać wywołana; środowisko uruchomieniowe języka wspólnego automatycznie definiuje metody `BeginInvoke` i `EndInvoke` dla tego delegata z odpowiednimi sygnaturami.

> [!NOTE]
> Wywołania delegatów asynchronicznych, w odróżnieniu od metod `BeginInvoke` i `EndInvoke`, nie są obsługiwane w .NET Compact Framework.

Metoda `BeginInvoke` inicjuje wywołanie asynchroniczne. Ma te same parametry co metoda, która ma zostać wykonana asynchronicznie, oraz dwa dodatkowe parametry opcjonalne. Pierwszy parametr jest delegatem <xref:System.AsyncCallback>, który odwołuje się do metody, która ma być wywoływana po zakończeniu wywołania asynchronicznego. Drugi parametr jest obiektem zdefiniowanym przez użytkownika, który przekazuje informacje do metody wywołania zwrotnego. `BeginInvoke` zwraca natychmiast i nie czeka na zakończenie wywołania asynchronicznego. `BeginInvoke` zwraca <xref:System.IAsyncResult>, za pomocą którego można monitorować postęp wywołania asynchronicznego.

Metoda `EndInvoke` pobiera wyniki wywołania asynchronicznego. Może być wywoływana w dowolnym momencie po `BeginInvoke`. Jeśli wywołanie asynchroniczne nie zostało ukończone, `EndInvoke` blokuje wątek wywołujący do momentu jego zakończenia. Parametry `EndInvoke` obejmują parametry `out` i `ref` (`<Out>` `ByRef` i `ByRef` w Visual Basic) metody, która ma zostać wykonana asynchronicznie, oraz <xref:System.IAsyncResult> zwrócone przez `BeginInvoke`.

> [!NOTE]
> Funkcja IntelliSense w programie Visual Studio Wyświetla parametry `BeginInvoke` i `EndInvoke`. Jeśli nie używasz programu Visual Studio ani podobnego narzędzia lub jeśli używasz programu C# z programem Visual Studio, zobacz [asynchroniczny model programowania (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) , aby uzyskać opis parametrów zdefiniowanych dla tych metod.

Przykłady kodu w tym temacie przedstawiają cztery typowe sposoby używania `BeginInvoke` i `EndInvoke` do wykonywania wywołań asynchronicznych. Po wywołaniu `BeginInvoke` można wykonać następujące czynności:

- Wykonaj pewną pracę, a następnie Wywołaj `EndInvoke`, aby zablokować do momentu zakończenia wywołania.

- Uzyskaj <xref:System.Threading.WaitHandle> przy użyciu właściwości <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType>, użyj <xref:System.Threading.WaitHandle.WaitOne%2A> metody, aby zablokować wykonywanie do momentu zasygnalizowania <xref:System.Threading.WaitHandle>, a następnie Wywołaj `EndInvoke`.

- Przesondowaj <xref:System.IAsyncResult> zwrócone przez `BeginInvoke`, aby określić, kiedy wywołanie asynchroniczne zostało zakończone, a następnie Wywołaj `EndInvoke`.

- Przekaż delegata metodę wywołania zwrotnego do `BeginInvoke`. Metoda jest wykonywana na wątku <xref:System.Threading.ThreadPool> po zakończeniu wywołania asynchronicznego. Metoda wywołania zwrotnego wywołuje `EndInvoke`.

> [!IMPORTANT]
> Niezależnie od używanej techniki, zawsze Wywołaj `EndInvoke`, aby zakończyć wywołanie asynchroniczne.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definiowanie metody testowej i delegata asynchronicznego
 Poniższe przykłady kodu przedstawiają różne sposoby wywoływania tej samej metody długotrwałej, `TestMethod`, asynchronicznie. Metoda `TestMethod` wyświetla komunikat konsoli, aby pokazać, że rozpoczęło przetwarzanie, uśpienie przez kilka sekund, a następnie kończy działanie. `TestMethod` ma parametr `out`, aby pokazać sposób dodawania takich parametrów do sygnatur `BeginInvoke` i `EndInvoke`. Parametry `ref` można obsłużyć podobnie.

 Poniższy przykład kodu pokazuje definicję `TestMethod` i delegata o nazwie `AsyncMethodCaller`, który może służyć do wywoływania `TestMethod` asynchronicznie. Aby skompilować przykłady kodu, musisz uwzględnić definicje `TestMethod` i delegata `AsyncMethodCaller`.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Oczekiwanie na wywołanie asynchroniczne z EndInvoke
 Najprostszym sposobem wykonania metody asynchronicznie jest rozpoczęcie wykonywania metody przez wywołanie metody `BeginInvoke` delegata, wykonanie pewnej pracy w wątku głównym, a następnie wywołanie metody `EndInvoke` delegata. `EndInvoke` może blokować wątek wywołujący, ponieważ nie zwraca do momentu zakończenia wywołania asynchronicznego. Jest to dobrym sposobem na korzystanie z operacji na plikach lub w sieci.

> [!IMPORTANT]
> Ponieważ `EndInvoke` może blokować, nigdy nie należy go wywoływać z wątków, które obsługują interfejs użytkownika.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Oczekiwanie na wywołanie asynchroniczne z elementem WaitHandle
 <xref:System.Threading.WaitHandle> można uzyskać przy użyciu właściwości <xref:System.IAsyncResult.AsyncWaitHandle%2A> <xref:System.IAsyncResult> zwróconej przez `BeginInvoke`. <xref:System.Threading.WaitHandle> jest sygnalizowane, gdy asynchroniczne wywołanie zakończy się, i można go oczekiwać przez wywołanie metody <xref:System.Threading.WaitHandle.WaitOne%2A>.

 Jeśli używasz <xref:System.Threading.WaitHandle>, możesz wykonać dodatkowe przetwarzanie przed ukończeniem wywołania asynchronicznego lub po jego zakończeniu, ale przed wywołaniem `EndInvoke`, aby pobrać wyniki.

> [!NOTE]
> Dojście oczekiwania nie jest zamykane automatycznie podczas wywoływania `EndInvoke`. Jeśli zostaną wydane wszystkie odwołania do dojścia oczekiwania, zasoby systemowe są zwalniane, gdy odzyskiwanie pamięci zostanie odzyskane w dojściem oczekiwania. Aby zwolnić zasoby systemowe zaraz po zakończeniu korzystania z dojścia oczekiwania, usuń je, wywołując metodę <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType>. Wyrzucanie elementów bezużytecznych działa wydajniej po jawnym usunięciu obiektów do pobrania.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Sondowanie w celu asynchronicznego uzupełniania wywołań
 Można użyć właściwości <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> zwróconej przez `BeginInvoke`, aby wykryć, kiedy wywołanie asynchroniczne zostanie zakończone. Można to zrobić podczas wykonywania wywołania asynchronicznego z wątku, który jest usługami interfejsu użytkownika. Sondowanie pod kątem ukończenia pozwala wątek wywołujący kontynuować wykonywanie podczas wywołania asynchronicznego wykonywanego na wątku <xref:System.Threading.ThreadPool>.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Wykonywanie metody wywołania zwrotnego po zakończeniu wywołania asynchronicznego
 Jeśli wątek inicjujący wywołanie asynchroniczne nie musi być wątkiem, który przetwarza wyniki, można wykonać metodę wywołania zwrotnego po zakończeniu wywołania. Metoda wywołania zwrotnego jest wykonywana na wątku <xref:System.Threading.ThreadPool>.

 Aby użyć metody wywołania zwrotnego, należy przekazać `BeginInvoke` delegata <xref:System.AsyncCallback>, który reprezentuje metodę wywołania zwrotnego. Można również przekazać obiekt, który zawiera informacje, które będą używane przez metodę wywołania zwrotnego. W metodzie wywołania zwrotnego można rzutować <xref:System.IAsyncResult>, który jest jedynym parametrem metody wywołania zwrotnego do obiektu <xref:System.Runtime.Remoting.Messaging.AsyncResult>. Następnie można użyć właściwości <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType>, aby uzyskać delegata, który został użyty do zainicjowania wywołania, aby można było wywołać `EndInvoke`.

 Uwagi dotyczące przykładu:

- `threadId` parametr `TestMethod` jest parametrem `out` ([`<Out>` `ByRef` w Visual Basic), więc jego wartość wejściowa nie jest nigdy używana przez `TestMethod`. Zmienna fikcyjna jest przenoszona do wywołania `BeginInvoke`. Jeśli parametr `threadId` był `ref` parametrem (`ByRef` w Visual Basic), zmienna będzie musiała być polem na poziomie klasy, aby mogła zostać przeniesiona do obu `BeginInvoke` i `EndInvoke`.

- Informacje o stanie przekazywane do `BeginInvoke` to ciąg formatu, którego Metoda wywołania zwrotnego używa do formatowania wiadomości wyjściowej. Ponieważ jest przekazywany jako typ <xref:System.Object>, informacje o stanie muszą być rzutowane na jego właściwy typ, zanim będzie można go użyć.

- Wywołanie zwrotne jest wykonywane na wątku <xref:System.Threading.ThreadPool>. wątki <xref:System.Threading.ThreadPool> są wątkiem w tle, co nie utrzymuje uruchamiania aplikacji, jeśli główny wątek kończy się, więc główny wątek przykładu musi być w stanie uśpienia wystarczająco długo, aby wywołanie zwrotne zostało zakończone.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Delegate>
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
