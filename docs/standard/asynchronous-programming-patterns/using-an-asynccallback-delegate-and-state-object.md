---
title: "Używanie delegata AsyncCallback i obiektu stanu"
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
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8793a78289e9b58407038f41cc9d403ff9f9940
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Używanie delegata AsyncCallback i obiektu stanu
Jeśli używasz <xref:System.AsyncCallback> delegować do przetworzenia wyniki operacji asynchronicznych w oddzielnym wątku, obiekt stanu może być używany do przekazywania informacji między wywołaniami zwrotnymi oraz do pobierania wynik końcowy. W tym temacie przedstawiono tej praktyki rozwijając przykład [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje używanie metod asynchronicznych w <xref:System.Net.Dns> klasy można pobrać informacji o systemie nazw domen (DNS, Domain Name System) dla komputerów określonych przez użytkownika. W tym przykładzie definiuje i używa `HostRequest` klasę do przechowywania informacji o stanie. A `HostRequest` obiekt pobiera utworzony dla każdej wprowadzonej przez użytkownika nazwy komputera. Ten obiekt jest przekazywany do <xref:System.Net.Dns.BeginGetHostByName%2A> metody. `ProcessDnsInformation` Metoda jest wywoływana za każdym razem kończy żądanie. `HostRequest` Pobrać obiektu przy użyciu <xref:System.IAsyncResult.AsyncState%2A> właściwości. `ProcessDnsInformation` Używa metody `HostRequest` obiekt, aby zapisać <xref:System.Net.IPHostEntry> zwracane przez żądanie lub <xref:System.Net.Sockets.SocketException> zgłoszony przez żądanie. Po zakończeniu wszystkich żądań aplikacji przechodzi przez `HostRequest` obiekty i wyświetla informacje dotyczące systemu DNS lub <xref:System.Net.Sockets.SocketException> komunikat o błędzie.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Omówienie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
