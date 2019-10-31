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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138024"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Porady: nasłuchiwanie żądań anulowania za pomocą sondowania
W poniższym przykładzie pokazano jeden ze sposobów, w jaki kod użytkownika może sondować token anulowania w regularnych odstępach czasu, aby sprawdzić, czy żądanie anulowania zostało zażądane z wątku wywołującego. Ten przykład używa typu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, ale ten sam wzorzec dotyczy operacji asynchronicznych utworzonych bezpośrednio przez typ <xref:System.Threading.ThreadPool?displayProperty=nameWithType> lub typ <xref:System.Threading.Thread?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
 Sondowanie wymaga pewnego rodzaju pętli lub cyklicznego kodu, który może okresowo odczytać wartość właściwości <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> logicznej. Jeśli używasz typu <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i oczekujesz na ukończenie zadania w wątku wywołującym, możesz użyć metody <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, aby sprawdzić Właściwość i zgłosić wyjątek. Korzystając z tej metody, należy się upewnić, że w odpowiedzi na żądanie zostanie zgłoszony poprawny wyjątek. Jeśli używasz <xref:System.Threading.Tasks.Task>, wywołanie tej metody jest lepsze niż ręczne wyrzucanie <xref:System.OperationCanceledException>. Jeśli nie trzeba zgłosić wyjątku, można po prostu sprawdzić Właściwość i zwrócić z metody, jeśli właściwość jest `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Wywoływanie <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> jest niezwykle szybkie i nie wprowadza znaczących obciążeń w pętlach.  
  
 Jeśli wywołujesz <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, musisz tylko jawnie sprawdzić Właściwość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A>, jeśli masz inne czynności, które należy wykonać w odpowiedzi na anulowanie przed wygenerowaniem wyjątku. W tym przykładzie można zobaczyć, że kod faktycznie uzyskuje dostęp do właściwości dwukrotnie: raz w jawnym dostępie i ponownie w metodzie <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>. Jednak ze względu na to, że czynność odczytywania właściwości <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> obejmuje tylko jedną nietrwałą instrukcję Read dla dostępu, podwójny dostęp nie jest istotny od perspektywy wydajności. Nadal zaleca się wywołanie metody zamiast ręcznie zgłosić <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
