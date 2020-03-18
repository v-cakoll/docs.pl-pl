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
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130923"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Używanie delegata AsyncCallback do kończenia operacji asynchronicznej
Aplikacje, które mogą wykonywać inne prace podczas oczekiwania na wyniki operacji asynchronicznej, nie powinny blokować oczekiwania, aż operacja zostanie ukończona. Użyj jednej z następujących opcji, aby kontynuować wykonywanie instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej:  
  
- Pełnomocnika <xref:System.AsyncCallback> do przetwarzania wyników operacji asynchronicznej w osobnym wątku. Takie podejście przedstawiono w tym temacie.  
  
- Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwości zwróconej <xref:System.IAsyncResult> przez operację asynchroniczną **Begin**_OperationName_ metody, aby ustalić, czy operacja została ukończona. Na przykład, który demonstruje to podejście, zobacz [Sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje przy użyciu metod asynchronicznych w <xref:System.Net.Dns> klasie do pobierania informacji dns (Domain Name System) dla komputerów określonych przez użytkownika. W tym <xref:System.AsyncCallback> przykładzie tworzy delegata, który odwołuje się do `ProcessDnsInformation` metody. Ta metoda jest wywoływana raz dla każdego asynchronicznego żądania informacji DNS.  
  
 Należy zauważyć, że host określony przez <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> użytkownika jest przekazywany do parametru. Na przykład, który demonstruje definiowanie i używanie bardziej złożonego obiektu stanu, zobacz [Korzystanie z delegata asynurowania i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Wywoływanie metod asynchronicznych za pomocą interfejsu IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
