---
title: "Używanie delegata AsyncCallback do kończenia operacji asynchronicznej"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Używanie delegata AsyncCallback do kończenia operacji asynchronicznej
Aplikacje, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej nie powinny blokować oczekiwania przed zakończeniem operacji. Do kontynuowania wykonywania instrukcji podczas oczekiwania na zakończenie operacji asynchronicznych, użyj jednej z następujących opcji:  
  
-   Użyj <xref:System.AsyncCallback> pełnomocnika, aby przetworzyć wyników operacji asynchronicznych w oddzielnym wątku. Takie podejście jest przedstawiona w tym temacie.  
  
-   Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć** *OperationName* metodę, aby określić, czy operacja została ukończona. Na przykład, który pokazuje tej metody, zobacz [sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje używanie metod asynchronicznych w <xref:System.Net.Dns> klasy można pobrać informacji o systemie nazw domen (DNS, Domain Name System) dla komputerów określonych przez użytkownika. Ten przykład tworzy <xref:System.AsyncCallback> delegata, który odwołuje się do `ProcessDnsInformation` metody. Ta metoda jest wywoływana raz dla każdego żądania asynchroniczne, aby uzyskać informacje dotyczące systemu DNS.  
  
 Należy pamiętać, że host określone przez użytkownika są przekazywane do <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametru. Na przykład przedstawiający definiowanie i przy użyciu bardziej złożonych obiekt stanu zobacz [przy użyciu delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Omówienie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Wywołanie metod asynchronicznych za pomocą interfejsu IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [Przy użyciu delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
