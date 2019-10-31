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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094604"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Używanie delegata AsyncCallback i obiektu stanu
W przypadku użycia delegata <xref:System.AsyncCallback> do przetwarzania wyników operacji asynchronicznej w osobnym wątku, można użyć obiektu stanu do przekazywania informacji między wywołaniami zwrotnymi i pobrania końcowego wyniku. W tym temacie pokazano, jak to zrobić, rozszerzając przykład przy [użyciu delegata AsyncCallback w celu zakończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje użycie metod asynchronicznych w klasie <xref:System.Net.Dns> do pobierania informacji o systemie nazw domen (DNS) dla komputerów określonych przez użytkownika. Ten przykład definiuje i używa klasy `HostRequest` do przechowywania informacji o stanie. Tworzony jest obiekt `HostRequest` dla każdej nazwy komputera wprowadzonej przez użytkownika. Ten obiekt jest przesyłany do metody <xref:System.Net.Dns.BeginGetHostByName%2A>. Metoda `ProcessDnsInformation` jest wywoływana za każdym razem, gdy żądanie zostanie zakończone. Obiekt `HostRequest` jest pobierany przy użyciu właściwości <xref:System.IAsyncResult.AsyncState%2A>. Metoda `ProcessDnsInformation` używa obiektu `HostRequest` do przechowywania <xref:System.Net.IPHostEntry> zwrócone przez żądanie lub <xref:System.Net.Sockets.SocketException> zgłoszone przez żądanie. Po zakończeniu wszystkich żądań aplikacja iteruje `HostRequest` obiektów i wyświetla informacje DNS lub <xref:System.Net.Sockets.SocketException> komunikat o błędzie.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
