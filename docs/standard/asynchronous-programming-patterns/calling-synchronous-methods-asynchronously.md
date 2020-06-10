---
title: Wywołanie metod synchronicznych w sposób asynchroniczny
description: Dowiedz się, jak wywoływać metody synchroniczne asynchronicznie w programie .NET przy użyciu metod BeginInvoke i EndInvoke.
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
ms.openlocfilehash: ff2d30c00e7b6becb0c3ff910d825c2e9d6f78e3
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662644"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Wywołanie metod synchronicznych w sposób asynchroniczny

.NET Framework umożliwia Asynchroniczne wywoływanie dowolnej metody. W tym celu należy zdefiniować delegata o tej samej sygnaturze, co metoda, która ma zostać wywołana; środowisko uruchomieniowe języka wspólnego automatycznie definiuje `BeginInvoke` i `EndInvoke` metody dla tego delegata z odpowiednimi sygnaturami.

> [!NOTE]
> Wywołania delegatów asynchronicznych, `BeginInvoke` `EndInvoke` w tym metody i, nie są obsługiwane w .NET Compact Framework.

`BeginInvoke`Metoda inicjuje wywołanie asynchroniczne. Ma te same parametry co metoda, która ma zostać wykonana asynchronicznie, oraz dwa dodatkowe parametry opcjonalne. Pierwszy parametr jest <xref:System.AsyncCallback> delegatem, który odwołuje się do metody, która ma być wywoływana po zakończeniu wywołania asynchronicznego. Drugi parametr jest obiektem zdefiniowanym przez użytkownika, który przekazuje informacje do metody wywołania zwrotnego. `BeginInvoke`zwraca natychmiast i nie czeka na zakończenie wywołania asynchronicznego. `BeginInvoke`zwraca obiekt <xref:System.IAsyncResult> , który może służyć do monitorowania postępu wywołania asynchronicznego.

`EndInvoke`Metoda pobiera wyniki wywołania asynchronicznego. Może być wywoływana za każdym razem po `BeginInvoke` . Jeśli wywołanie asynchroniczne nie zostało zakończone, program `EndInvoke` blokuje wątek wywołujący do momentu jego zakończenia. Parametry `EndInvoke` obejmują `out` `ref` Parametry i ( `<Out>` `ByRef` i `ByRef` w Visual Basic) metody, która ma zostać wykonana asynchronicznie, oraz <xref:System.IAsyncResult> zwracanych przez `BeginInvoke` .

> [!NOTE]
> Funkcja IntelliSense w programie Visual Studio Wyświetla parametry `BeginInvoke` i `EndInvoke` . Jeśli nie używasz programu Visual Studio ani podobnego narzędzia lub jeśli używasz języka C# z programem Visual Studio, zobacz [asynchroniczny model programowania (APM)](asynchronous-programming-model-apm.md) , aby uzyskać opis parametrów zdefiniowanych dla tych metod.

Przykłady kodu w tym temacie przedstawiają cztery typowe sposoby korzystania z `BeginInvoke` i `EndInvoke` wykonywania wywołań asynchronicznych. Po wywołaniu `BeginInvoke` można wykonać następujące czynności:

- Wykonaj pewną pracę, a następnie Wywołaj, `EndInvoke` Aby zablokować do momentu zakończenia wywołania.

- Uzyskaj <xref:System.Threading.WaitHandle> Właściwość using przy użyciu <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> <xref:System.Threading.WaitHandle.WaitOne%2A> metody, aby zablokować wykonywanie do momentu <xref:System.Threading.WaitHandle> zasygnalizowania, a następnie Wywołaj `EndInvoke` .

- Przesondowaj <xref:System.IAsyncResult> zwrócone przez, `BeginInvoke` Aby określić, kiedy wywołanie asynchroniczne zostało zakończone, a następnie Wywołaj metodę `EndInvoke` .

- Przekaż delegat do metody wywołania zwrotnego `BeginInvoke` . Metoda jest wykonywana na wątku, <xref:System.Threading.ThreadPool> gdy wywołanie asynchroniczne zostanie zakończone. Wywołanie metody wywołania zwrotnego `EndInvoke` .

> [!IMPORTANT]
> Niezależnie od używanej techniki, zawsze wywołuj, `EndInvoke` Aby zakończyć wywołanie asynchroniczne.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definiowanie metody testowej i delegata asynchronicznego
 Poniższe przykłady kodu przedstawiają różne sposoby wywoływania tej samej metody długotrwałej, `TestMethod` asynchronicznie. `TestMethod`Metoda wyświetla komunikat konsoli, aby pokazać, że rozpoczęło przetwarzanie, uśpienie przez kilka sekund, a następnie kończy działanie. `TestMethod`ma `out` parametr, który pokazuje, jak takie parametry są dodawane do sygnatur `BeginInvoke` i `EndInvoke` . Parametry można obsłużyć `ref` podobnie.

 Poniższy przykład kodu pokazuje definicję `TestMethod` i delegata o nazwie `AsyncMethodCaller` , który może być używany do wywołania `TestMethod` asynchronicznego. Aby skompilować przykłady kodu, musisz uwzględnić definicje dla `TestMethod` i `AsyncMethodCaller` delegata.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Oczekiwanie na wywołanie asynchroniczne z EndInvoke
 Najprostszym sposobem wykonania metody asynchronicznie jest rozpoczęcie wykonywania metody przez wywołanie metody delegata `BeginInvoke` , wykonanie pewnej pracy w wątku głównym, a następnie wywołanie metody delegata `EndInvoke` . `EndInvoke`może blokować wątek wywołujący, ponieważ nie zwraca do momentu zakończenia wywołania asynchronicznego. Jest to dobrym sposobem na korzystanie z operacji na plikach lub w sieci.

> [!IMPORTANT]
> Ponieważ `EndInvoke` może blokować, nigdy nie należy wywoływać go z wątków, które obsługują interfejs użytkownika.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Oczekiwanie na wywołanie asynchroniczne z elementem WaitHandle
 Można uzyskać <xref:System.Threading.WaitHandle> za pomocą <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwości <xref:System.IAsyncResult> zwracanej przez `BeginInvoke` . <xref:System.Threading.WaitHandle>Jest sygnalizowane sygnałem, gdy wywołanie asynchroniczne zostanie zakończone, i można go oczekiwać przez wywołanie <xref:System.Threading.WaitHandle.WaitOne%2A> metody.

 Jeśli używasz, możesz <xref:System.Threading.WaitHandle> wykonać dodatkowe przetwarzanie przed ukończeniem wywołania asynchronicznego lub po jego zakończeniu, ale przed wywołaniem `EndInvoke` do pobrania wyników.

> [!NOTE]
> Dojście oczekiwania nie jest zamykane automatycznie podczas wywoływania `EndInvoke` . Jeśli zostaną wydane wszystkie odwołania do dojścia oczekiwania, zasoby systemowe są zwalniane, gdy odzyskiwanie pamięci zostanie odzyskane w dojściem oczekiwania. Aby zwolnić zasoby systemowe zaraz po zakończeniu korzystania z dojścia oczekiwania, usuń je, wywołując <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> metodę. Wyrzucanie elementów bezużytecznych działa wydajniej po jawnym usunięciu obiektów do pobrania.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Sondowanie w celu asynchronicznego uzupełniania wywołań
 Możesz użyć <xref:System.IAsyncResult.IsCompleted%2A> właściwości <xref:System.IAsyncResult> zwracanego przez, `BeginInvoke` Aby wykryć, kiedy wywołanie asynchroniczne zostało zakończone. Można to zrobić podczas wykonywania wywołania asynchronicznego z wątku, który jest usługami interfejsu użytkownika. Sondowanie pod kątem ukończenia pozwala wątek wywołujący kontynuować wykonywanie podczas wywołania asynchronicznego wykonywanego na <xref:System.Threading.ThreadPool> wątku.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Wykonywanie metody wywołania zwrotnego po zakończeniu wywołania asynchronicznego
 Jeśli wątek inicjujący wywołanie asynchroniczne nie musi być wątkiem, który przetwarza wyniki, można wykonać metodę wywołania zwrotnego po zakończeniu wywołania. Metoda wywołania zwrotnego jest wykonywana w <xref:System.Threading.ThreadPool> wątku.

 Aby użyć metody wywołania zwrotnego, należy przekazać `BeginInvoke` <xref:System.AsyncCallback> delegata, który reprezentuje metodę wywołania zwrotnego. Można również przekazać obiekt, który zawiera informacje, które będą używane przez metodę wywołania zwrotnego. W metodzie wywołania zwrotnego można rzutować <xref:System.IAsyncResult> , który jest jedynym parametrem metody wywołania zwrotnego do <xref:System.Runtime.Remoting.Messaging.AsyncResult> obiektu. Następnie można użyć właściwości, <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> Aby uzyskać delegata, który został użyty do zainicjowania wywołania, aby można było wywołać `EndInvoke` .

 Uwagi dotyczące przykładu:

- `threadId`Parametr `TestMethod` jest `out` parametrem ( `<Out>` `ByRef` w Visual Basic), więc jego wartość wejściowa nie jest nigdy używana przez `TestMethod` . Zmienna fikcyjna jest przenoszona do `BeginInvoke` wywołania. Jeśli `threadId` parametr był `ref` parametrem ( `ByRef` w Visual Basic), zmienna musi być polem na poziomie klasy, dzięki czemu może być przekazaniem do obu `BeginInvoke` i `EndInvoke` .

- Informacje o stanie przekazywane do programu `BeginInvoke` to ciąg formatu, którego Metoda wywołania zwrotnego używa do formatowania wiadomości wyjściowej. Ponieważ jest przekazywany jako typ <xref:System.Object> , informacje o stanie muszą być rzutowane na jego właściwy typ, zanim będzie można go użyć.

- Wywołanie zwrotne jest wykonywane na <xref:System.Threading.ThreadPool> wątku. <xref:System.Threading.ThreadPool>wątki to wątki w tle, które nie zachowują działania aplikacji, jeśli główny wątek kończy się, więc główny wątek przykładu musi być w stanie uśpienia wystarczająco długo, aby wywołanie zwrotne zostało zakończone.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Delegate>
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md)
