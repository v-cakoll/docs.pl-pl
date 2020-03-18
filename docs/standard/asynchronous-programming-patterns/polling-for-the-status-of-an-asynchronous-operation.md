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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123959"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Sondowanie stanu operacji asynchronicznych
Aplikacje, które mogą wykonywać inne prace podczas oczekiwania na wyniki operacji asynchronicznej, nie powinny blokować oczekiwania, aż operacja zostanie ukończona. Użyj jednej z następujących opcji, aby kontynuować wykonywanie instrukcji podczas oczekiwania na zakończenie operacji asynchronicznej:  
  
- Użyj <xref:System.IAsyncResult.IsCompleted%2A> właściwości zwróconej <xref:System.IAsyncResult> przez operację asynchroniczną **Begin**_OperationName_ metody, aby ustalić, czy operacja została ukończona. Takie podejście jest znany jako sondowania i wykazano w tym temacie.  
  
- Pełnomocnika <xref:System.AsyncCallback> do przetwarzania wyników operacji asynchronicznej w osobnym wątku. Na przykład, który demonstruje to podejście, zobacz [za pomocą delegata AsyncCallback do zakończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje przy użyciu metod asynchronicznych w <xref:System.Net.Dns> klasie, aby pobrać informacje systemu nazw domen dla komputera określonego przez użytkownika. W tym przykładzie rozpoczyna operację asynchroniczną, a następnie drukuje kropki (".") w konsoli, aż do zakończenia operacji. Należy zauważyć, że **null** (**Nothing** <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> in <xref:System.Object> Visual Basic) jest przekazywana dla parametrów i parametrów, ponieważ te argumenty nie są wymagane podczas korzystania z tego podejścia.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
