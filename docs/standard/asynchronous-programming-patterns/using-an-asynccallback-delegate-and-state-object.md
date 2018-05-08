---
title: Używanie delegata AsyncCallback i obiektu stanu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 259f7de52dff04af043554382a5bad35355d9926
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Używanie delegata AsyncCallback i obiektu stanu
Jeśli używasz <xref:System.AsyncCallback> delegować do przetworzenia wyniki operacji asynchronicznych w oddzielnym wątku, obiekt stanu może być używany do przekazywania informacji między wywołaniami zwrotnymi oraz do pobierania wynik końcowy. W tym temacie przedstawiono tej praktyki rozwijając przykład [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje używanie metod asynchronicznych w <xref:System.Net.Dns> klasy można pobrać informacji o systemie nazw domen (DNS, Domain Name System) dla komputerów określonych przez użytkownika. W tym przykładzie definiuje i używa `HostRequest` klasę do przechowywania informacji o stanie. A `HostRequest` obiekt pobiera utworzony dla każdej wprowadzonej przez użytkownika nazwy komputera. Ten obiekt jest przekazywany do <xref:System.Net.Dns.BeginGetHostByName%2A> metody. `ProcessDnsInformation` Metoda jest wywoływana za każdym razem kończy żądanie. `HostRequest` Pobrać obiektu przy użyciu <xref:System.IAsyncResult.AsyncState%2A> właściwości. `ProcessDnsInformation` Używa metody `HostRequest` obiekt, aby zapisać <xref:System.Net.IPHostEntry> zwracane przez żądanie lub <xref:System.Net.Sockets.SocketException> zgłoszony przez żądanie. Po zakończeniu wszystkich żądań aplikacji przechodzi przez `HostRequest` obiekty i wyświetla informacje dotyczące systemu DNS lub <xref:System.Net.Sockets.SocketException> komunikat o błędzie.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
