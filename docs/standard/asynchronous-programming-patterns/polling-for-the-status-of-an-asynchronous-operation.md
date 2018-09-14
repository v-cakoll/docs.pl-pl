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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d380e369d9620fc0fc87a2c443be318083174882
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591389"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Sondowanie stanu operacji asynchronicznych
Aplikacji, które mogą wykonywać inne zadania podczas oczekiwania na wyniki operacji asynchronicznej nie powinny blokować oczekiwanie, aż do zakończenia operacji. Do kontynuowania wykonywania instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej, użyj jednej z następujących opcji:  
  
-   Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwość <xref:System.IAsyncResult> zwrócony przez operację asynchroniczną **rozpocząć *** OperationName* metodę pozwala ustalić, czy operacja została ukończona. To podejście jest znany jako sondowania i została przedstawiona w tym temacie.  
  
-   Użyj <xref:System.AsyncCallback> delegata do przetwarzania wyników operacji asynchronicznych w oddzielnym wątku. Aby uzyskać przykład demonstrujący takie podejście, zobacz [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, za pomocą metod asynchronicznych we <xref:System.Net.Dns> klasy do pobrania informacji System nazw domen dla komputera określonego przez użytkownika. W tym przykładzie rozpoczyna operację asynchroniczną, a następnie drukuje kropki (".") w konsoli aż do zakończenia operacji. Należy pamiętać, że **null** (**nic** w języku Visual Basic) jest przekazywana <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> i <xref:System.Object> parametry ponieważ tych argumentów nie są wymagane w przypadku korzystania z tej metody.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
