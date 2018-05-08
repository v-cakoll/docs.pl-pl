---
title: Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a1f9c7a5c1e083500ccf88d7a165e109238e875
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle
Aplikacje, których nie można nadal wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej zablokować przed zakończeniem operacji. Mają być blokowane podczas oczekiwania na zakończenie operacji asynchronicznych wątku głównego aplikacji, użyj jednej z następujących opcji:  
  
-   Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć *** OperationName* metody. Takie podejście jest przedstawiona w tym temacie.  
  
-   Wywołaj operację asynchroniczną **zakończenia *** OperationName* metody. Na przykład, który pokazuje tej metody, zobacz [blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Aplikacje korzystające z co najmniej jeden <xref:System.Threading.WaitHandle> zwykle wywoła obiekty mają być blokowane, aż do zakończenia operacji asynchronicznej **rozpocząć *** OperationName* metody, wykonać pracę, które mogą być przeprowadzane bez wyników Operacja, a następnie bloku dopiero po zakończeniu operacji asynchronicznej. Aplikacja może zablokować w ramach jednej operacji, wywołując jedną z <xref:System.Threading.WaitHandle.WaitOne%2A> przy użyciu metody <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Mają być blokowane podczas oczekiwania na zakończenie operacji asynchronicznych zbiór, przechowywania skojarzonych <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiekty w tablicy i wywołanie jedną <xref:System.Threading.WaitHandle.WaitAll%2A> metody. Mają być blokowane podczas oczekiwania na dowolny zbiór na zakończenie operacji asynchronicznych, przechowywania skojarzonych <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiekty w tablicy i wywołanie jedną <xref:System.Threading.WaitHandle.WaitAny%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje używanie metod asynchronicznych klasy DNS można pobrać informacji o systemie nazw domen dla komputera określone przez użytkownika. W przykładzie pokazano, blokowanie, przy użyciu <xref:System.Threading.WaitHandle> skojarzone z operacji asynchronicznej. Należy pamiętać, że `null` (`Nothing` w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` i `stateObject` parametrów, ponieważ nie są one wymagane przy użyciu tej metody.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
