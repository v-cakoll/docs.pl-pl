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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130923"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Używanie delegata AsyncCallback do kończenia operacji asynchronicznej
Aplikacje, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej, nie powinny blokować oczekiwania na zakończenie operacji. Użyj jednej z następujących opcji, aby kontynuować wykonywanie instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej:  
  
- Użyj delegata <xref:System.AsyncCallback>, aby przetwarzać wyniki operacji asynchronicznej w osobnym wątku. Ta metoda jest przedstawiona w tym temacie.  
  
- Użyj właściwości <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> zwróconej przez metodę **BEGIN**_OperationName_ operacji asynchronicznej, aby określić, czy operacja została ukończona. Aby zapoznać się z przykładem, który ilustruje to podejście, zobacz [sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje użycie metod asynchronicznych w klasie <xref:System.Net.Dns> do pobierania informacji o systemie nazw domen (DNS) dla komputerów określonych przez użytkownika. W tym przykładzie jest tworzony delegat <xref:System.AsyncCallback>, który odwołuje się do metody `ProcessDnsInformation`. Ta metoda jest wywoływana jednokrotnie dla każdego żądania asynchronicznego dla informacji DNS.  
  
 Należy zauważyć, że host określony przez użytkownika jest przesyłany do <xref:System.Net.Dns.BeginGetHostByName%2A>parametr <xref:System.Object>. Aby zapoznać się z przykładem, który ilustruje definiowanie i używanie bardziej złożonego obiektu stanu, zobacz [Używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Wywoływanie metod asynchronicznych za pomocą interfejsu IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
