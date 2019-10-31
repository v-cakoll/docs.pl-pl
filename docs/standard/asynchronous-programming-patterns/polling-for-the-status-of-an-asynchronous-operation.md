---
title: Sondowanie stanu operacji asynchronicznych
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: ff9cefc73adfe1ece1bf7545c75ccb6cc618e89f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123959"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Sondowanie stanu operacji asynchronicznych
Aplikacje, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej, nie powinny blokować oczekiwania na zakończenie operacji. Użyj jednej z następujących opcji, aby kontynuować wykonywanie instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej:  
  
- Użyj właściwości <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> zwróconej przez metodę **BEGIN**_OperationName_ operacji asynchronicznej, aby określić, czy operacja została ukończona. Takie podejście jest nazywane sondami i przedstawiono w tym temacie.  
  
- Użyj delegata <xref:System.AsyncCallback>, aby przetwarzać wyniki operacji asynchronicznej w osobnym wątku. Przykład demonstrujący to podejście, zobacz [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje użycie metod asynchronicznych w klasie <xref:System.Net.Dns> do pobrania informacji o systemie nazw domen dla komputera określonego przez użytkownika. Ten przykład uruchamia asynchroniczną operację, a następnie drukuje kropki (".") w konsoli do momentu ukończenia operacji. Należy zauważyć, że **wartość null** (**Nothing** w Visual Basic) jest przesyłana do <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> i <xref:System.Object> parametrów, ponieważ te argumenty nie są wymagane podczas korzystania z tego podejścia.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
