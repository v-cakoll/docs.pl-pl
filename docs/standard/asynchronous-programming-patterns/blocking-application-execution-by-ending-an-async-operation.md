---
title: Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: aed3b18c154d4b7a4390b28fb1f14536690f6b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121327"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej
Aplikacje, które nie mogą kontynuować wykonywania innych prac podczas oczekiwania na wyniki operacji asynchronicznej, muszą blokować, dopóki operacja nie zostanie ukończona. Użyj jednej z następujących opcji, aby zablokować główny wątek aplikacji podczas oczekiwania na zakończenie operacji asynchronicznej:  
  
- Wywołaj operacje asynchroniczne **End**_OperationName_ metody. Takie podejście przedstawiono w tym temacie.  
  
- Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwości zwróconej <xref:System.IAsyncResult> przez operację asynchroniczną **Begin**_OperationName_ metody. Na przykład, który demonstruje to podejście, zobacz [Blokowanie wykonywania aplikacji przy użyciu AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikacje, które używają **End**_OperationName_ metody do blokowania aż do zakończenia operacji asynchronicznej zazwyczaj wywoła **Begin**_OperationName_ metody, wykonać dowolną pracę, która może być wykonana bez wyników operacji, a następnie **wywołać End**_OperationName_.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje przy użyciu metod asynchronicznych w <xref:System.Net.Dns> klasie, aby pobrać informacje systemu nazw domen dla komputera określonego przez użytkownika. Należy `null` zauważyć,`Nothing` że ( w <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` języku Visual Basic) jest przekazywana dla parametrów i `stateObject` ponieważ te argumenty nie są wymagane podczas korzystania z tego podejścia.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
