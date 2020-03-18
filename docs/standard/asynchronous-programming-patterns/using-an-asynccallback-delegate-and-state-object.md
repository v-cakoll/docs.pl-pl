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
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73094604"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Używanie delegata AsyncCallback i obiektu stanu
Korzystając z <xref:System.AsyncCallback> pełnomocnika do przetwarzania wyników operacji asynchronicznej w oddzielnym wątku, można użyć obiektu stanu do przekazywania informacji między wywołaniami zwrotu i pobrać wynik końcowy. W tym temacie przedstawiono tę praktykę, rozszerzając przykład w [using asyncCallback delegate do zakończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje przy użyciu metod asynchronicznych w <xref:System.Net.Dns> klasie do pobierania informacji dns (Domain Name System) dla komputerów określonych przez użytkownika. W tym przykładzie definiuje `HostRequest` i używa klasy do przechowywania informacji o stanie. Obiekt `HostRequest` zostanie utworzony dla każdej nazwy komputera wprowadzonej przez użytkownika. Ten obiekt jest <xref:System.Net.Dns.BeginGetHostByName%2A> przekazywany do metody. Metoda `ProcessDnsInformation` jest wywoływana za każdym razem, gdy żądanie zostanie zakończone. Obiekt `HostRequest` jest pobierany <xref:System.IAsyncResult.AsyncState%2A> przy użyciu właściwości. Metoda `ProcessDnsInformation` używa `HostRequest` obiektu do <xref:System.Net.IPHostEntry> przechowywania zwróconych przez <xref:System.Net.Sockets.SocketException> żądanie lub thrown przez żądanie. Po zakończeniu wszystkich żądań aplikacja iteruje `HostRequest` obiekty i wyświetla <xref:System.Net.Sockets.SocketException> informacje DNS lub komunikat o błędzie.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
