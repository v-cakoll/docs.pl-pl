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
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
ms.openlocfilehash: db46025ca1169f2f93a5b8eabb62a06ccc4bb95e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567422"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej
Aplikacje, których nie można nadal wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej zablokować przed zakończeniem operacji. Mają być blokowane podczas oczekiwania na zakończenie operacji asynchronicznych wątku głównego aplikacji, użyj jednej z następujących opcji:  
  
-   Operacje asynchroniczne wywołanie **zakończenia *** OperationName* metody. Takie podejście jest przedstawiona w tym temacie.  
  
-   Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć *** OperationName* metody. Na przykład, który pokazuje tej metody, zobacz [blokowania aplikacji wykonywania za pomocą właściwości AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikacje używające **zakończenia *** OperationName* zwykle wywoła metodę, aby zablokować aż do zakończenia operacji asynchronicznej **rozpocząć *** OperationName* metody, wykonać pracę, którą można wykonać bez wyniki operacji, a następnie wywołania **zakończenia *** OperationName*.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje używanie metod asynchronicznych w <xref:System.Net.Dns> klasy można pobrać informacji o systemie nazw domen dla komputera określone przez użytkownika. Należy pamiętać, że `null` (`Nothing` w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` i `stateObject` parametry ponieważ tych argumentów nie są wymagane w przypadku korzystania z tej metody.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
