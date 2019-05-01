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
ms.openlocfilehash: d667135b815dc5d47ba5f7de8d237796a6fd6e10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870165"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle
Aplikacje, które nie mogą w dalszym ciągu wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej należy zablokować, aż do zakończenia operacji. Blokowanie wątku głównego aplikacji podczas oczekiwania na zakończenie operacji asynchronicznej, użyj jednej z następujących opcji:  
  
- Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć**_OperationName_ metody. To podejście jest przedstawiona w tym temacie.  
  
- Wywołaj operację asynchroniczną **zakończenia**_OperationName_ metody. Aby uzyskać przykład demonstrujący takie podejście, zobacz [blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Aplikacje używające co najmniej jeden <xref:System.Threading.WaitHandle> obiektów, aby zablokować do czasu ukończenia operacji asynchronicznej zazwyczaj będzie wywoływać **rozpocząć**_OperationName_ metody, wykonać wszelkie prace, które można zrobić bez wyniki operacji, a następnie bloku, dopóki nie operacje asynchroniczne zostanie ukończone. Aplikacja może zablokować w ramach jednej operacji, wywołując jedną z <xref:System.Threading.WaitHandle.WaitOne%2A> metod za pomocą <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Aby zablokować podczas oczekiwania na zbiór na zakończenie operacji asynchronicznej, przechowywania skojarzonego <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiektów w tablicy i wywołanie jednej <xref:System.Threading.WaitHandle.WaitAll%2A> metody. Aby zablokować podczas oczekiwania na dowolny zbiór na zakończenie operacji asynchronicznej, przechowywania skojarzonego <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiektów w tablicy i wywołanie jednej <xref:System.Threading.WaitHandle.WaitAny%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje używanie metod asynchronicznych w klasie DNS, aby pobrać informacje systemu nazw domen dla komputera określonego przez użytkownika. W przykładzie pokazano, blokowanie, za pomocą <xref:System.Threading.WaitHandle> skojarzony z operacją asynchroniczną. Należy pamiętać, że `null` (`Nothing` w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` i `stateObject` parametrów, ponieważ nie są wymagane podczas używania tej metody.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
