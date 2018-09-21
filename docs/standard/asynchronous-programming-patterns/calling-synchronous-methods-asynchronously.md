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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 371e958aca87c922c902d8efd945d94d611672d9
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478256"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Wywołanie metod synchronicznych w sposób asynchroniczny

.NET Framework umożliwia asynchroniczne wywoływanie dowolnej metody. W tym zdefiniowanie pełnomocnika z tym samym podpisie jako metodę, którą chcesz wywołać; środowisko uruchomieniowe języka wspólnego automatycznie definiuje `BeginInvoke` i `EndInvoke` metod dla tego delegata, z odpowiednią sygnaturą.

> [!NOTE]
> Wywołuje delegata asynchronicznego, specjalnie `BeginInvoke` i `EndInvoke` metody, nie są obsługiwane w programie .NET Compact Framework.

`BeginInvoke` Metoda inicjuje wywołania asynchronicznego. Ma on te same parametry jako metodę, która ma zostać wykonany asynchronicznie, a także dwie dodatkowe parametry opcjonalne. Pierwszy parametr jest <xref:System.AsyncCallback> delegat, który odwołuje się do metody do wywołania po ukończeniu wywołania asynchronicznego. Drugi parametr jest zdefiniowane przez użytkownika obiekt, który przekazuje informacje do metody wywołania zwrotnego. `BeginInvoke` zwraca niezwłocznie i nie czeka na ukończenie wywołania asynchronicznego. `BeginInvoke` Zwraca <xref:System.IAsyncResult>, który może służyć do monitorowania postępu wywołania asynchronicznego.

`EndInvoke` Metoda pobiera wyniki wywołania asynchronicznego. Można ją wywołać dowolnym momencie po `BeginInvoke`. Jeśli wywołanie asynchroniczne nie została ukończona, `EndInvoke` blokuje wątek wywołujący, dopóki nie zostanie zakończona. Parametry `EndInvoke` obejmują `out` i `ref` parametrów (`<Out>` `ByRef` i `ByRef` w języku Visual Basic) metody, która ma zostać wykonany asynchronicznie, a także <xref:System.IAsyncResult> zwrócony przez `BeginInvoke`.

> [!NOTE]
> Funkcja IntelliSense w programie Visual Studio Wyświetla parametry `BeginInvoke` i `EndInvoke`. Jeśli nie używasz programu Visual Studio lub podobnego narzędzia lub jeśli używasz języka C# za pomocą programu Visual Studio, zobacz [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) opis parametrów określonych dla tych metod.

Przykłady kodu, w tym temacie ilustrują cztery typowe sposoby korzystania z `BeginInvoke` i `EndInvoke` wykonywanie wywołań asynchronicznych. Po wywołaniu `BeginInvoke` wykonasz następujące czynności:

-   Czy niektóre pracy, jak i następnie wywołać `EndInvoke` do bloku do czasu ukończenia wywołania.

-   Uzyskaj <xref:System.Threading.WaitHandle> przy użyciu <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> właściwości, należy zastosować jego <xref:System.Threading.WaitHandle.WaitOne%2A> metody Zablokuj wykonywanie aż do <xref:System.Threading.WaitHandle> jest sygnalizowane, a następnie wywołaj `EndInvoke`.

-   Sondowania <xref:System.IAsyncResult> zwrócone przez `BeginInvoke` do określania, kiedy wywołanie asynchroniczne zostało ukończone, a następnie wywołaj `EndInvoke`.

-   Przekazywanie obiektu delegate dla metody wywołania zwrotnego do `BeginInvoke`. Metoda jest wykonywana na <xref:System.Threading.ThreadPool> wątków po zakończeniu wywołania asynchronicznego. Wywołania metody wywołania zwrotnego `EndInvoke`.

> [!IMPORTANT]
> Niezależnie od tego, w których technika, należy zawsze wywołuj `EndInvoke` do ukończenia wywołania asynchronicznego.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definiowanie metody testowej i delegatów asynchronicznych
 Przykłady kodu, które należy wykonać pokazują różne sposoby wywoływania tego samego metoda długotrwałych, `TestMethod`, asynchronicznie. `TestMethod` Metoda wyświetla komunikat konsoli, aby pokazać, że rozpoczął przetwarzanie sen przez kilka sekund, a następnie kończy. `TestMethod` ma `out` parametru, aby zademonstrować sposób takie parametry zostaną dodane do sygnatur `BeginInvoke` i `EndInvoke`. Może obsługiwać `ref` parametry podobnie.

 W poniższym przykładzie kodu pokazano definicję `TestMethod` i delegata, o nazwie `AsyncMethodCaller` można wywołać `TestMethod` asynchronicznie. Aby skompilować przykłady kodu, należy uwzględnić definicje `TestMethod` i `AsyncMethodCaller` delegować.

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Oczekiwanie na wywołanie asynchroniczne za pomocą EndInvoke —
 Najprostszym sposobem wykonania metody asynchroniczne jest rozpocząć wykonywanie metody przez wywołanie metody delegata `BeginInvoke` metody, niektóre działać w wątku głównym, a następnie wywołaj delegat `EndInvoke` metody. `EndInvoke` może spowodować zablokowanie wątku wywołującego, ponieważ nie zwraca do momentu ukończenia wywołania asynchronicznego. Jest to dobry technika, za pomocą operacji pliku lub sieci.

> [!IMPORTANT]
> Ponieważ `EndInvoke` może spowodować zablokowanie, nigdy nie należy wywołać go z wątków, które usługi interfejsu użytkownika.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Oczekiwanie na wywołanie asynchroniczne za pomocą WaitHandle
 Możesz uzyskać <xref:System.Threading.WaitHandle> przy użyciu <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwość <xref:System.IAsyncResult> zwrócone przez `BeginInvoke`. <xref:System.Threading.WaitHandle> Jest sygnalizowane po ukończeniu wywołania asynchronicznego i możesz poczekać, aż go przez wywołanie metody <xref:System.Threading.WaitHandle.WaitOne%2A> metody.

 Jeśli używasz <xref:System.Threading.WaitHandle>, można wykonać dodatkowego przetwarzania przed lub po ukończeniu wywołania asynchronicznego, ale przed wywołaniem `EndInvoke` do pobierania wyników.

> [!NOTE]
> Dojście oczekiwania nie zostaną automatycznie zamknięte po wywołaniu `EndInvoke`. Po zwolnieniu wszystkich odwołań do dojście oczekiwania zasoby systemu są zwalniane, gdy zadanie odzyskiwania pamięci Zwraca dojście oczekiwania. Można zwolnić zasobów systemowych, jak najszybciej po zakończeniu używania dojście oczekiwania, usunięcia ich przez wywołanie metody <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> metody. Wyrzucanie elementów bezużytecznych działa wydajniej, gdy obiekty możliwe do rozporządzania są jawnie zlikwidowany.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Sondowanie na zakończenie wywołania asynchronicznego
 Możesz użyć <xref:System.IAsyncResult.IsCompleted%2A> właściwość <xref:System.IAsyncResult> zwrócone przez `BeginInvoke` do odnajdywania, po zakończeniu wywołania asynchronicznego. Można to zrobić, gdy wywołania asynchronicznego z wątku, usług interfejsu użytkownika. Sondowanie w celu ukończenia umożliwia wątku wywołującego do kontynuowania wykonywania podczas wywołania asynchronicznego dla wykonuje <xref:System.Threading.ThreadPool> wątku.

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Wykonywanie metody wywołania zwrotnego po zakończeniu wywołanie asynchroniczne
 Jeśli wątek, który inicjuje wywołanie asynchroniczne musi być wątku, który przetwarza wyniki, należy wykonać metodę wywołania zwrotnego, gdy ukończenia wywołania. Metoda wywołania zwrotnego jest wykonywana na <xref:System.Threading.ThreadPool> wątku.

 Aby użyć metody wywołania zwrotnego, należy przekazać `BeginInvoke` <xref:System.AsyncCallback> delegata, który reprezentuje metodę wywołania zwrotnego. Można również przekazać obiekt, który zawiera informacje używane przez metodę wywołania zwrotnego. W przypadku metody wywołania zwrotnego można rzutować <xref:System.IAsyncResult>, który jest jedynym parametrem metody wywołania zwrotnego do <xref:System.Runtime.Remoting.Messaging.AsyncResult> obiektu. Następnie można użyć <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> właściwości do pobrania delegata, który został użyty do inicjowania wywołanie, dzięki czemu można wywołać `EndInvoke`.

 Uwagi na przykładzie:

-   `threadId` Parametru `TestMethod` jest `out` parametru ([`<Out>` `ByRef` w języku Visual Basic), więc jego wartość wejściowa nie jest nigdy używane przez `TestMethod`. Fikcyjny zmienna jest przekazywana do `BeginInvoke` wywołania. Jeśli `threadId` zostały parametr `ref` parametru (`ByRef` w języku Visual Basic), zmienna będzie miała być polem poziomie klasy, aby go można przekazać do obu `BeginInvoke` i `EndInvoke`.

-   Informacje o stanie, który jest przekazywany do `BeginInvoke` jest ciąg formatu, który korzysta z metody wywołania zwrotnego do sformatowania komunikatu wyjściowego. Ponieważ jest przekazywany jako typ <xref:System.Object>, informacje o stanie, należy zrzutować jego odpowiedniego typu, zanim będzie można używać.

-   Wywołanie zwrotne jest wykonywane na <xref:System.Threading.ThreadPool> wątku. <xref:System.Threading.ThreadPool> wątki są wątków w tle, które nie jest przechowywana aplikacja była uruchomiona, gdy kończy się w wątku głównym, więc nie wątku głównego przykładu w stan uśpienia wystarczająco długo na zakończenie wywołania zwrotnego.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Delegate>
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
