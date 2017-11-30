---
title: "Wywołanie metod synchronicznych w sposób asynchroniczny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 965e5928c03ae573eacba98a7596f55b56aaba26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="calling-synchronous-methods-asynchronously"></a>Wywołanie metod synchronicznych w sposób asynchroniczny
.NET Framework umożliwia asynchroniczne wywoływanie dowolnej metody. W tym celu należy zdefiniować delegata o tej samej sygnaturze jako metodę, która ma zostać wywołana; środowisko uruchomieniowe języka wspólnego automatycznie definiuje `BeginInvoke` i `EndInvoke` metody dla tego obiektu delegowanego z odpowiednim podpisem.  
  
> [!NOTE]
>  Wywołuje delegata asynchroniczne, w szczególności `BeginInvoke` i `EndInvoke` metody, nie są obsługiwane w programie .NET Compact Framework.  
  
 `BeginInvoke` Metoda inicjuje wywołania asynchronicznego. Ma takie same parametry jako metodę, która ma być wykonana asynchronicznie, a także dwóch dodatkowych parametrów opcjonalnych. Pierwszym parametrem jest <xref:System.AsyncCallback> delegata, który odwołuje się do metody do wywołania po zakończeniu wywołania asynchronicznego. Drugi parametr jest zdefiniowane przez użytkownika obiekt, który przekazuje informacje do metody wywołania zwrotnego. `BeginInvoke`Zwraca natychmiast i bez oczekiwania dla wywołania asynchronicznego zakończyć. `BeginInvoke`Zwraca <xref:System.IAsyncResult>, które mogą służyć do monitorowania postępu wywołania asynchronicznego.  
  
 `EndInvoke` Metoda pobiera wyniki wywołania asynchronicznego. Może ona zostać wywołana dowolnym momencie po `BeginInvoke`. Jeśli nie wykonano wywołanie asynchroniczne, `EndInvoke` blokuje wątek wywołujący, dopóki nie ukończy. Parametry `EndInvoke` obejmują `out` i `ref` parametrów (`<Out>` `ByRef` i `ByRef` w języku Visual Basic) metody, która ma być wykonana asynchronicznie, wraz z <xref:System.IAsyncResult> zwrócony przez `BeginInvoke`.  
  
> [!NOTE]
>  Funkcja IntelliSense w [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] Wyświetla parametry `BeginInvoke` i `EndInvoke`. Jeśli nie używasz programu Visual Studio lub podobnego narzędzia lub jeśli używasz C# z [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], zobacz [asynchronicznego programowania modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) opis parametrów zdefiniowanych dla tych metod.  
  
 Przykłady kodu, w tym temacie pokazują cztery typowe sposoby korzystania `BeginInvoke` i `EndInvoke` w celu wykonywania wywołań asynchronicznych. Po wywołaniu `BeginInvoke` można wykonaj następujące czynności:  
  
-   Czy niektóre pracy, jak i wywoływać `EndInvoke` blok do momentu ukończenia wywołania.  
  
-   Uzyskaj <xref:System.Threading.WaitHandle> przy użyciu <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> właściwości, należy zastosować jego <xref:System.Threading.WaitHandle.WaitOne%2A> sposób wykonywania bloku do <xref:System.Threading.WaitHandle> zostanie zasygnalizowane, a następnie wywołać `EndInvoke`.  
  
-   Sondowania <xref:System.IAsyncResult> zwrócony przez `BeginInvoke` do określania, kiedy asynchroniczne wywołanie zostało ukończone, a następnie wywołać `EndInvoke`.  
  
-   Przekazywanie obiektu delegate metody wywołania zwrotnego do `BeginInvoke`. Metoda jest wykonywana na <xref:System.Threading.ThreadPool> wątku po zakończeniu wywołania asynchronicznego. Wywołania metody wywołania zwrotnego `EndInvoke`.  
  
> [!IMPORTANT]
>  Niezależnie od tego, które technika, należy wywołać zawsze `EndInvoke` do ukończenia wywołania asynchronicznego.  
  
## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Definiowanie metody testowej i asynchroniczne delegata  
 Przykłady kodu, które należy wykonać pokazują różnych sposobów wywołanie tej samej metody długotrwałe `TestMethod`, asynchronicznie. `TestMethod` Metoda wyświetla komunikat konsoli do wyświetlenia rozpoczął przetwarzanie, sen przez kilka sekund, a następnie kończy. `TestMethod`ma `out` parametr, aby zademonstrować sposób takie parametry zostaną dodane do sygnatur `BeginInvoke` i `EndInvoke`. Może obsłużyć `ref` parametry podobnie.  
  
 Poniższy przykładowy kod przedstawia definicję `TestMethod` i delegata o nazwie `AsyncMethodCaller` można wywołać `TestMethod` asynchronicznie. Aby skompilować przykłady kodu, musi zawierać definicje `TestMethod` i `AsyncMethodCaller` delegowanie.  
  
 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]  
  
## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Trwa oczekiwanie na wywołanie asynchroniczne z EndInvoke  
 Najprostszym sposobem wykonania metody asynchroniczne jest uruchomienie wykonania metody przez wywołanie metody delegata `BeginInvoke` metody, niektóre pracy w głównym wątku, a następnie wywołać delegata `EndInvoke` metody. `EndInvoke`może spowodować zablokowanie wątek wywołujący, ponieważ nie zwraca do momentu ukończenia wywołania asynchronicznego. Jest to dobra metoda do użycia z operacjami pliku lub sieci.  
  
> [!IMPORTANT]
>  Ponieważ `EndInvoke` może zablokować, nigdy nie należy go wywoływać z wątków, które Usługa interfejsu użytkownika.  
  
 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]  
  
## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Trwa oczekiwanie na wywołanie asynchroniczne z WaitHandle  
 Możesz uzyskać <xref:System.Threading.WaitHandle> za pomocą <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwość <xref:System.IAsyncResult> zwrócony przez `BeginInvoke`. <xref:System.Threading.WaitHandle> Jest sygnalizowane po zakończeniu wywołania asynchronicznego i poczekaj na jego, wywołując <xref:System.Threading.WaitHandle.WaitOne%2A> metody.  
  
 Jeśli używasz <xref:System.Threading.WaitHandle>, można wykonywać dodatkowe przetwarzanie przed lub po zakończeniu wywołania asynchronicznego, ale przed wywołaniem `EndInvoke` można pobrać wyników.  
  
> [!NOTE]
>  Dojście oczekiwania nie jest automatycznie zamknięte podczas wywoływania `EndInvoke`. Jeśli musisz zwolnić wszystkie odwołania do dojścia oczekiwania, zasoby systemowe są zwalniane podczas odzyskiwania pamięci Zwraca dojście oczekiwania. Można zwolnić zasobów systemowych, jak najszybciej po zakończeniu korzystania dojście oczekiwania, usunięcia ich przez wywołanie metody <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType> metody. Wyrzucanie elementów bezużytecznych działa wydajniej, gdy obiekty możliwe do rozporządzania są jawnie zlikwidowany.  
  
 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]  
  
## <a name="polling-for-asynchronous-call-completion"></a>Sondowanie ukończenia wywołania asynchronicznego  
 Można użyć <xref:System.IAsyncResult.IsCompleted%2A> właściwość <xref:System.IAsyncResult> zwrócony przez `BeginInvoke` do odnajdywania, po zakończeniu wykonywania wywołania asynchronicznego. Można to zrobić, gdy co wywołanie asynchroniczne z wątku interfejsu użytkownika z usług. Sondowanie w celu ukończenia umożliwia wątek wywołujący kontynuować wykonywanie podczas wywołania asynchronicznego wykonuje na <xref:System.Threading.ThreadPool> wątku.  
  
 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]  
  
## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Wykonywanie metody wywołania zwrotnego, po zakończeniu wywołanie asynchroniczne  
 Jeśli wątek, który inicjuje asynchroniczne wywołanie muszą być wątku, który przetwarza wyniki, można wykonać metody wywołania zwrotnego, po zakończeniu wywołania. Metoda wywołania zwrotnego jest wykonywana na <xref:System.Threading.ThreadPool> wątku.  
  
 Aby użyć metody wywołania zwrotnego, należy podać `BeginInvoke` <xref:System.AsyncCallback> delegata, który reprezentuje metodę wywołania zwrotnego. Można również przekazać obiekt, który zawiera informacje używane przez metodę wywołania zwrotnego. W przypadku metody wywołania zwrotnego można rzutować <xref:System.IAsyncResult>, tylko parametr metody wywołania zwrotnego, która jest do <xref:System.Runtime.Remoting.Messaging.AsyncResult> obiektu. Następnie można użyć <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> właściwości do pobrania delegata, który został użyty do zainicjować połączenie, dzięki czemu można wywołać `EndInvoke`.  
  
 Uwagi dotyczące na przykład:  
  
-   `threadId` Parametr `TestMethod` jest `out` parametr ([`<Out>` `ByRef` w języku Visual Basic), więc jego wartość wejściowa nie jest nigdy używane przez `TestMethod`. Fikcyjny zmienna jest przekazywana do `BeginInvoke` wywołania. Jeśli `threadId` zostały parametru `ref` parametr (`ByRef` w języku Visual Basic), zmienna musi być polem poziomie klasy tak, aby go mogą być przekazywane zarówno do `BeginInvoke` i `EndInvoke`.  
  
-   Informacje o stanie, który jest przekazywany do `BeginInvoke` jest ciągiem formatu, który używa metody wywołania zwrotnego do sformatowania komunikatu wyjściowego. Ponieważ jest przekazywany jako typ <xref:System.Object>, informacje o stanie musi być rzutowane na jego odpowiedniego typu, zanim będzie można użyć.  
  
-   Wywołanie zwrotne jest podejmowana <xref:System.Threading.ThreadPool> wątku. <xref:System.Threading.ThreadPool>wątki są wątki w tle, które nie jest przechowywana aplikacja była uruchomiona, gdy kończy się wątku głównego, dzięki czemu mają wątku głównego przykładu w stan uśpienia wystarczająco długi dla wywołania zwrotnego zakończyć.  
  
 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Delegate>  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
