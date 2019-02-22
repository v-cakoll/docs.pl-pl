---
title: Używanie delegata AsyncCallback do kończenia operacji asynchronicznej
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a2ce3f194cbdaaa7b244504745c542da7ba8a73
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664175"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Używanie delegata AsyncCallback do kończenia operacji asynchronicznej
Aplikacji, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej nie powinny blokować oczekiwanie, aż do zakończenia operacji. Do kontynuowania wykonywania instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej, użyj jednej z następujących opcji:  
  
-   Użyj <xref:System.AsyncCallback> delegata do przetwarzania wyników operacji asynchronicznych w oddzielnym wątku. To podejście jest przedstawiona w tym temacie.  
  
-   Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć**_OperationName_ metodę pozwala ustalić, czy operacja została ukończona. Aby uzyskać przykład demonstrujący takie podejście, zobacz [sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, za pomocą metod asynchronicznych we <xref:System.Net.Dns> klasy do pobrania informacji systemu nazw domen (DNS, Domain Name System) dla komputerów z określonych przez użytkownika. Ten przykład tworzy <xref:System.AsyncCallback> delegata, który odwołuje się do `ProcessDnsInformation` metody. Ta metoda jest wywoływana jeden raz dla każdego żądania asynchronicznego, aby uzyskać informacje dotyczące systemu DNS.  
  
 Należy zauważyć, że host określonych przez użytkownika jest przekazywany do <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametru. Na przykład demonstrujący definiowanie i korzystanie z bardziej złożonych obiekt stanu zobacz [używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Wywoływanie metod asynchronicznych za pomocą interfejsu IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
