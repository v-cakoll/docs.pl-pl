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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121426"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blokowanie wykonania aplikacji za pomocą właściwości AsyncWaitHandle
Aplikacje, które nie mogą kontynuować wykonywania innych prac podczas oczekiwania na wyniki operacji asynchronicznej, muszą blokować, dopóki operacja nie zostanie ukończona. Użyj jednej z następujących opcji, aby zablokować główny wątek aplikacji podczas oczekiwania na zakończenie operacji asynchronicznej:  
  
- Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwości zwróconej <xref:System.IAsyncResult> przez operację asynchroniczną **Begin**_OperationName_ metody. Takie podejście przedstawiono w tym temacie.  
  
- Wywołaj metodę **End**_OperationName_ operacji asynchronicznej. Na przykład, który pokazuje to podejście, zobacz [Blokowanie wykonywania aplikacji przez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Aplikacje, które <xref:System.Threading.WaitHandle> używają jednego lub więcej obiektów do blokowania, dopóki operacja asynchroniczna nie zostanie ukończona, zazwyczaj wywołają metodę **Begin**_OperationName,_ wykonają dowolną pracę, którą można wykonać bez wyników operacji, a następnie blokują, dopóki nie zakończy się operacja asynchroniczna. Aplikacja może zablokować jedną operację, <xref:System.Threading.WaitHandle.WaitOne%2A> wywołując jedną <xref:System.IAsyncResult.AsyncWaitHandle%2A>z metod za pomocą pliku . Aby zablokować podczas oczekiwania na zakończenie zestawu operacji asynchronicznych, przechowuj skojarzone <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiekty w tablicy i wywołaj <xref:System.Threading.WaitHandle.WaitAll%2A> jedną z metod. Aby zablokować podczas oczekiwania na wykonanie jednego z zestawu operacji asynchronicznych, przechowuj skojarzone <xref:System.IAsyncResult.AsyncWaitHandle%2A> obiekty w tablicy i wywołaj <xref:System.Threading.WaitHandle.WaitAny%2A> jedną z metod.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje przy użyciu metod asynchronicznych w klasie DNS, aby pobrać informacje systemu nazw domen dla komputera określonego przez użytkownika. W przykładzie pokazano <xref:System.Threading.WaitHandle> blokowanie przy użyciu skojarzonez z operacją asynchroniczną. Należy `null` zauważyć, że`Nothing` (w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` dla parametrów i `stateObject` ponieważ nie są one wymagane podczas korzystania z tego podejścia.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
