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
ms.openlocfilehash: 74976176acc0fbb948c514358b7bd323cc20c134
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289957"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej
Aplikacje, które nie mogą kontynuować wykonywania innych zadań podczas oczekiwania na wyniki operacji asynchronicznej, muszą być blokowane do momentu zakończenia operacji. Użyj jednej z następujących opcji, aby zablokować główny wątek aplikacji podczas oczekiwania na ukończenie operacji asynchronicznej:  
  
- Wywołaj metodę **kończenia**_operacji operacji_ asynchronicznej. Ta metoda jest przedstawiona w tym temacie.  
  
- Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwości <xref:System.IAsyncResult> zwracanej przez metodę **BEGIN**_OperationName_ operacji asynchronicznej. Przykład demonstrujący tę metodę można znaleźć w temacie [blokowanie wykonywania aplikacji przy użyciu AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikacje korzystające z **metody End**_OperationName_ do blokowania do momentu ukończenia operacji asynchronicznej zwykle wywołują **metodę Begin**_OperationName_ , wykonują wszelkie zadania, które można wykonać bez wyników operacji, a następnie Wywołaj **zakończenie**_operacji_.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje użycie metod asynchronicznych w <xref:System.Net.Dns> klasie w celu pobrania informacji o systemie nazw domen dla komputera określonego przez użytkownika. Należy zauważyć, że `null` ( `Nothing` w Visual Basic) jest przekazane do <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` parametrów i, `stateObject` ponieważ te argumenty nie są wymagane podczas korzystania z tego podejścia.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](event-based-asynchronous-pattern-overview.md)
