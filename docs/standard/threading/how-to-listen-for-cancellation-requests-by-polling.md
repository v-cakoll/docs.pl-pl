---
title: 'Porady: nasłuchiwanie żądań anulowania za pomocą sondowania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
ms.openlocfilehash: df76674e3003bbb77ef062e90b1dc3283f681d35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138024"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Porady: nasłuchiwanie żądań anulowania za pomocą sondowania
W poniższym przykładzie przedstawiono jeden sposób, że kod użytkownika można sondować token anulowania w regularnych odstępach czasu, aby sprawdzić, czy zażądano anulowania z wątku wywołującego. W tym <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> przykładzie użyto tego typu, ale ten sam wzorzec ma zastosowanie do operacji asynchronicznych utworzonych bezpośrednio przez <xref:System.Threading.ThreadPool?displayProperty=nameWithType> typ lub <xref:System.Threading.Thread?displayProperty=nameWithType> typ.  
  
## <a name="example"></a>Przykład  
 Sondowanie wymaga pewnego rodzaju pętli lub kodu cyklicznego, który może <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> okresowo odczytywać wartość właściwości logicznej. Jeśli używasz <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> tego typu i oczekujesz na zakończenie zadania w wątku <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> wywołującego, można użyć metody, aby sprawdzić właściwość i zgłosić wyjątek. Za pomocą tej metody, upewnij się, że poprawny wyjątek jest generowany w odpowiedzi na żądanie. Jeśli używasz <xref:System.Threading.Tasks.Task>, a następnie wywołanie tej metody <xref:System.OperationCanceledException>jest lepsze niż ręczne rzucanie . Jeśli nie musisz zgłaszać wyjątku, możesz po prostu sprawdzić właściwość i zwrócić `true`z metody, jeśli właściwość jest .  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Wywołanie <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> jest bardzo szybkie i nie wprowadza znaczących narzutów w pętlach.  
  
 Jeśli dzwonisz, <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>musisz tylko jawnie <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> sprawdzić właściwość, jeśli masz inną pracę do wykonania w odpowiedzi na anulowanie oprócz zgłaszania wyjątku. W tym przykładzie widać, że kod faktycznie uzyskuje dostęp do właściwości dwa <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> razy: raz w jawny dostęp i ponownie w metodzie. Ale ponieważ akt odczytu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości obejmuje tylko jedną instrukcję odczytu lotnych na dostęp, podwójny dostęp nie jest istotny z punktu widzenia wydajności. Nadal lepiej jest wywołać metodę, a <xref:System.OperationCanceledException>nie ręcznie wrzucić .  
  
## <a name="see-also"></a>Zobacz też

- [Anulowanie w wątkach zarządzanych](../../../docs/standard/threading/cancellation-in-managed-threads.md)
