---
title: 'Porady: nasłuchiwanie żądań anulowania z dojściami oczekiwania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137988"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Porady: nasłuchiwanie żądań anulowania z dojściami oczekiwania
Jeśli metoda jest blokowana, gdy oczekuje na zasygnalizowanie zdarzenia, nie może sprawdzić wartości tokenu anulowania i odpowiedzieć w odpowiednim czasie. Pierwszy przykład pokazuje, jak rozwiązać ten problem podczas pracy ze zdarzeniami, takimi jak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, które nie obsługują natywnie ujednoliconej platformy anulowania. W drugim przykładzie przedstawiono bardziej usprawnione podejście wykorzystujące <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, które obsługuje ujednolicone anulowanie.  
  
> [!NOTE]
> Po włączeniu "Tylko mój kod" program Visual Studio będzie przerywał pracę w wierszu, który zgłosi wyjątek i wyświetli komunikat o błędzie "wyjątek nie jest obsługiwany przez kod użytkownika". Ten błąd jest niegroźny. Możesz nacisnąć klawisz F5, aby kontynuować z niego i zobaczyć zachowanie obsługi wyjątków, które przedstawiono w poniższych przykładach. Aby zapobiec utracie przez program Visual Studio pierwszego błędu, po prostu usuń zaznaczenie pola wyboru "Tylko mój kod" w obszarze **Narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Threading.ManualResetEvent>, aby zademonstrować, jak odblokować dojścia oczekiwania, które nie obsługują ujednoliconego anulowania.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Threading.ManualResetEventSlim>, aby zademonstrować, jak odblokować elementy podstawowe koordynacji, które obsługują ujednolicone anulowanie. Takie samo podejście może być używane z innymi uproszczonymi typami podstawowymi koordynacji, takimi jak <xref:System.Threading.Semaphore>`Slim` i <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
