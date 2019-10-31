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
ms.openlocfilehash: 16b5a297c13cd9096548ed489e4994b72a48da67
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121426"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle
Aplikacje, które nie mogą kontynuować wykonywania innych zadań podczas oczekiwania na wyniki operacji asynchronicznej, muszą być blokowane do momentu zakończenia operacji. Użyj jednej z następujących opcji, aby zablokować główny wątek aplikacji podczas oczekiwania na ukończenie operacji asynchronicznej:  
  
- Użyj właściwości <xref:System.IAsyncResult.AsyncWaitHandle%2A> <xref:System.IAsyncResult> zwrócone przez metodę **BEGIN**_OperationName_ operacji asynchronicznej. Ta metoda jest przedstawiona w tym temacie.  
  
- Wywołaj metodę **End**_OperationName_ operacji asynchronicznej. Aby zapoznać się z przykładem, który ilustruje to podejście, zobacz [blokowanie wykonywania aplikacji przez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Aplikacje używające co najmniej jednego obiektu <xref:System.Threading.WaitHandle> do zablokowania do momentu ukończenia operacji asynchronicznej zwykle wywołują metodę **BEGIN**_OperationName_ , wykonują wszelkie zadania, które można wykonać bez wyników operacji, a następnie blokują do momentu zakończenia operacji asynchronicznych. Aplikacja może blokować pojedyncze operacje, wywołując jedną z metod <xref:System.Threading.WaitHandle.WaitOne%2A> przy użyciu <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Aby zablokować podczas oczekiwania na zakończenie zestawu operacji asynchronicznych, należy przechowywać skojarzone obiekty <xref:System.IAsyncResult.AsyncWaitHandle%2A> w tablicy i wywoływać jedną z metod <xref:System.Threading.WaitHandle.WaitAll%2A>. Aby zablokować podczas oczekiwania na zakończenie jednego z zestawów operacji asynchronicznych, należy przechowywać skojarzone obiekty <xref:System.IAsyncResult.AsyncWaitHandle%2A> w tablicy i wywoływać jedną z metod <xref:System.Threading.WaitHandle.WaitAny%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje użycie metod asynchronicznych w klasie DNS w celu pobrania informacji o systemie nazw domen dla komputera określonego przez użytkownika. W przykładzie pokazano blokowanie przy użyciu <xref:System.Threading.WaitHandle> skojarzonego z operacją asynchroniczną. Należy zauważyć, że `null` (`Nothing` w Visual Basic) są przesyłane do parametrów <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` i `stateObject`, ponieważ nie są one wymagane podczas korzystania z tego podejścia.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
