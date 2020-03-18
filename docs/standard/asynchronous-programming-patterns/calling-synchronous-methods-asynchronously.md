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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105129"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Wywołanie metod synchronicznych w sposób asynchroniczny

Program .NET Framework umożliwia wywołanie dowolnej metody asynchronicznie. W tym celu należy zdefiniować pełnomocnika z tym samym podpisem co metoda, którą chcesz wywołać; program runtime języka wspólnego `BeginInvoke` automatycznie `EndInvoke` definiuje i metody dla tego delegata, z odpowiednimi podpisami.

> [!NOTE]
> Asynchroniczne wywołania delegata, `BeginInvoke` `EndInvoke` w szczególności i metody, nie są obsługiwane w .NET Compact Framework.

Metoda `BeginInvoke` inicjuje wywołanie asynchroniczne. Ma te same parametry co metoda, którą chcesz wykonać asynchronicznie, plus dwa dodatkowe parametry opcjonalne. Pierwszy parametr jest <xref:System.AsyncCallback> pełnomocnikiem, który odwołuje się do metody, która ma być wywoływana po zakończeniu wywołania asynchronicznego. Drugi parametr jest obiektem zdefiniowanym przez użytkownika, który przekazuje informacje do metody wywołania wywołania. `BeginInvoke`zwraca natychmiast i nie czeka na zakończenie wywołania asynchronicznego. `BeginInvoke`zwraca <xref:System.IAsyncResult>, który może służyć do monitorowania postępu wywołania asynchronicznego.

Metoda `EndInvoke` pobiera wyniki wywołania asynchronicznego. Można go nazwać w `BeginInvoke`dowolnym momencie po . Jeśli wywołanie asynchroniczne nie `EndInvoke` zostało zakończone, blokuje wątek wywołujący, dopóki nie zostanie ukończony. `EndInvoke` Parametry include `out` i `ref` parametry (i`<Out>` `ByRef` `ByRef` w języku Visual Basic) metody, która ma być wykonywana asynchronicznie, plus <xref:System.IAsyncResult> zwrócone przez `BeginInvoke`.

> [!NOTE]
> Funkcja IntelliSense w programie Visual Studio `BeginInvoke` wyświetla `EndInvoke`parametry i . Jeśli nie używasz programu Visual Studio lub podobnego narzędzia lub używasz języka C# w programie Visual Studio, zobacz [Asynchroniczny model programowania (APM),](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) aby uzyskać opis parametrów zdefiniowanych dla tych metod.

Przykłady kodu w tym temacie demonstrować `BeginInvoke` `EndInvoke` cztery typowe sposoby używania i do wykonania wywołań asynchronicznych. Po `BeginInvoke` nadzwonieniu można wykonać następujące czynności:

- Wykonaj pracę, a `EndInvoke` następnie wywołaj, aby zablokować, dopóki połączenie nie zostanie zakończone.

- Uzyskaj <xref:System.Threading.WaitHandle> przy <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> użyciu właściwości, <xref:System.Threading.WaitHandle.WaitOne%2A> użyj jego metody, aby zablokować wykonanie, dopóki <xref:System.Threading.WaitHandle> nie jest sygnalizowane, a następnie wywołać `EndInvoke`.

- Sonduj zwrócone <xref:System.IAsyncResult> przez, `BeginInvoke` aby określić, kiedy wywołanie asynchroniczne zostało zakończone, a następnie wywołać `EndInvoke`.

- Przekaż pełnomocnika dla metody wywołania wywołania `BeginInvoke`do . Metoda jest wykonywana <xref:System.Threading.ThreadPool> w wątku po zakończeniu wywołania asynchronicznego. Wywołuje metodę wywołania wywołania wywołania . `EndInvoke`

> [!IMPORTANT]
> Bez względu na to, `EndInvoke` której techniki używasz, zawsze wywołaj, aby zakończyć wywołanie asynchroniczne.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definiowanie metody testowej i delegata asynchronicznego
 Przykłady kodu, które należy wykazać różne sposoby wywoływania `TestMethod`tej samej metody długotrwałego, asynchronicznie. Metoda `TestMethod` wyświetla komunikat konsoli, aby pokazać, że rozpoczął przetwarzanie, uśpiony przez kilka sekund, a następnie kończy. `TestMethod`ma `out` parametr, aby wykazać sposób, w jaki `BeginInvoke` takie `EndInvoke`parametry są dodawane do podpisów i . Parametry można `ref` obsługiwać podobnie.

 Poniższy przykład kodu pokazuje `TestMethod` definicję i `AsyncMethodCaller` nazwę delegata, `TestMethod` która może służyć do wywoływania asynchronicznie. Aby skompilować przykłady kodu, należy dołączyć `TestMethod` definicje `AsyncMethodCaller` i delegata.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Oczekiwanie na wywołanie asynchroniczne z EndInvoke
 Najprostszym sposobem wykonania metody asynchronicznie jest rozpoczęcie wykonywania metody przez `BeginInvoke` wywołanie metody delegata, wykonanie pracy nad głównym wątkiem, a następnie wywołanie metody delegata. `EndInvoke` `EndInvoke`może zablokować wątek wywołujący, ponieważ nie zwraca, dopóki nie zakończy wywołanie asynchroniczne. Jest to dobra technika do użycia w operacjach plików lub sieci.

> [!IMPORTANT]
> Ponieważ `EndInvoke` może blokować, nigdy nie należy wywoływać go z wątków, które obsługują interfejs użytkownika.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Oczekiwanie na wywołanie asynchroniczne z waithandle
 Można uzyskać <xref:System.Threading.WaitHandle> za pomocą <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwości <xref:System.IAsyncResult> zwróconego `BeginInvoke`przez . Jest <xref:System.Threading.WaitHandle> sygnalizowany po zakończeniu wywołania asynchronicznego i można na <xref:System.Threading.WaitHandle.WaitOne%2A> nie poczekać, wywołując metodę.

 Jeśli używasz <xref:System.Threading.WaitHandle>, można wykonać dodatkowe przetwarzanie przed lub po zakończeniu wywołania `EndInvoke` asynchronicznego, ale przed wywołaniem w celu pobrania wyników.

> [!NOTE]
> Uchwyt oczekiwania nie jest zamykany `EndInvoke`automatycznie po wywołaniu . Jeśli zwolnisz wszystkie odwołania do dojścia oczekiwania, zasoby systemowe są zwalniane, gdy wyrzucanie elementów bezużytecznych odzyskuje dojście oczekiwania. Aby zwolnić zasoby systemowe, gdy tylko skończysz przy użyciu <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> uchwytu oczekiwania, zlikwiduj go, wywołując metodę. Wyrzucanie elementów bezużytecznych działa wydajniej, gdy jednorazowe obiekty są jawnie usuwane.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Sondowanie asynchronicznego zakończenia wywołania
 Można użyć <xref:System.IAsyncResult.IsCompleted%2A> właściwości zwrócone <xref:System.IAsyncResult> przez `BeginInvoke` odkryć po zakończeniu wywołania asynchronicznego. Można to zrobić podczas wykonywania wywołania asynchronicznego z wątku, który służy interfejs użytkownika. Sondowanie do zakończenia umożliwia wątku wywołującego, aby kontynuować wykonywanie <xref:System.Threading.ThreadPool> podczas wykonywania asynchronicznego wywołania w wątku.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Wykonywanie metody wywołania zwrotu po zakończeniu wywołania asynchronicznego
 Jeśli wątek, który inicjuje wywołanie asynchroniczne nie musi być wątek, który przetwarza wyniki, można wykonać metodę wywołania wywołania po zakończeniu wywołania. Metoda wywołania odwróconego jest wykonywana w wątku. <xref:System.Threading.ThreadPool>

 Aby użyć metody wywołania wywołania, należy przekazać `BeginInvoke` pełnomocnika, <xref:System.AsyncCallback> który reprezentuje metodę wywołania wywołania. Można również przekazać obiekt, który zawiera informacje, które mają być używane przez metodę wywołania wywołania. W metodzie wywołania wywołania <xref:System.IAsyncResult>można rzutować , który jest jedynym <xref:System.Runtime.Remoting.Messaging.AsyncResult> parametrem metody wywołania wywołania, do obiektu. Następnie można użyć <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> właściwości, aby uzyskać pełnomocnika, który został użyty `EndInvoke`do zainicjowania wywołania, dzięki czemu można wywołać .

 Uwagi dotyczące przykładu:

- Parametr `threadId` `TestMethod` jest `out` parametrem ([`<Out>` `ByRef` w języku Visual Basic), `TestMethod`więc jego wartość wejściowa nigdy nie jest używana przez . Zmienna fikcyjna jest `BeginInvoke` przekazywana do wywołania. Jeśli `threadId` parametr był `ref` parametrem`ByRef` (w języku Visual Basic), zmienna musiałaby być polem `BeginInvoke` `EndInvoke`na poziomie klasy, aby można było przekazać je obu i .

- Informacje o stanie, `BeginInvoke` który jest przekazywany do jest ciąg formatu, który metoda wywołania wstecznego używa do formatowania komunikatu wyjściowego. Ponieważ jest przekazywana <xref:System.Object>jako typ , informacje o stanie muszą być rzutować do jego właściwego typu, zanim będzie można go użyć.

- Wywołanie wsteczne jest <xref:System.Threading.ThreadPool> dokonywane w wątku. <xref:System.Threading.ThreadPool>wątki są wątki w tle, które nie utrzymują aplikacji uruchomiony, jeśli główny wątek kończy się, więc główny wątek przykładu musi spać wystarczająco długo, aby wywołanie wstecz do końca.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Delegate>
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
