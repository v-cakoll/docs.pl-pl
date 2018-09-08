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
ms.openlocfilehash: 46b7839a6bd0086a8ec82e416cdf7aed05707390
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139608"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Używanie delegata AsyncCallback i obiektu stanu
Kiedy używasz <xref:System.AsyncCallback> delegować do przetwarzania wyników operacji asynchronicznych w oddzielnym wątku, można użyć obiektu stanu do przekazywania informacji między wywołania zwrotne i pobrać wynik końcowy. W tym temacie przedstawiono tej praktyką, rozszerzając przykład przedstawiony w [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, za pomocą metod asynchronicznych we <xref:System.Net.Dns> klasy do pobrania informacji systemu nazw domen (DNS, Domain Name System) dla komputerów z określonych przez użytkownika. W tym przykładzie definiuje i używa `HostRequest` klasę do przechowywania informacji o stanie. A `HostRequest` obiekt tworzony dla każdej wprowadzonej przez użytkownika nazwy komputera. Ten obiekt jest przekazywany do <xref:System.Net.Dns.BeginGetHostByName%2A> metody. `ProcessDnsInformation` Metoda jest wywoływana za każdym razem, kończy żądanie. `HostRequest` Obiektu są pobierane przy użyciu <xref:System.IAsyncResult.AsyncState%2A> właściwości. `ProcessDnsInformation` Metoda używa `HostRequest` obiekt ma być przechowywany <xref:System.Net.IPHostEntry> zwróconym przez żądanie jest lub <xref:System.Net.Sockets.SocketException> generowane przez żądanie. Po ukończeniu wszystkich żądań aplikacji wykonuje iterację na `HostRequest` obiektów i wyświetla informacje DNS lub <xref:System.Net.Sockets.SocketException> komunikat o błędzie.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
- [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
