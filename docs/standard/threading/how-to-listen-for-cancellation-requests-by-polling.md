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
ms.openlocfilehash: 6f70ce75b1d6a3d4d7e8a38d739005a261b07241
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279559"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Porady: nasłuchiwanie żądań anulowania za pomocą sondowania
W poniższym przykładzie pokazano jeden ze sposobów, w jaki kod użytkownika może sondować token anulowania w regularnych odstępach czasu, aby sprawdzić, czy żądanie anulowania zostało zażądane z wątku wywołującego. Ten przykład używa <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu, ale ten sam wzorzec dotyczy operacji asynchronicznych utworzonych bezpośrednio przez <xref:System.Threading.ThreadPool?displayProperty=nameWithType> Typ lub <xref:System.Threading.Thread?displayProperty=nameWithType> Typ.  
  
## <a name="example"></a>Przykład  
 Sondowanie wymaga pewnego rodzaju pętli lub cyklicznego kodu, który może okresowo odczytać wartość właściwości logicznej <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> . Jeśli używasz <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu i czekasz na ukończenie zadania w wątku wywołującym, możesz użyć <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody, aby sprawdzić Właściwość i zgłosić wyjątek. Korzystając z tej metody, należy się upewnić, że w odpowiedzi na żądanie zostanie zgłoszony poprawny wyjątek. W przypadku korzystania z programu <xref:System.Threading.Tasks.Task> , wywołanie tej metody jest lepsze niż ręczne wyrzucanie <xref:System.OperationCanceledException> . Jeśli nie trzeba zgłosić wyjątku, można po prostu sprawdzić Właściwość i zwrócić z metody, jeśli właściwość jest `true` .  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Wywoływanie <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> jest niezwykle szybkie i nie wprowadza znaczących obciążeń w pętlach.  
  
 Jeśli wywołujesz <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> , musisz tylko jawnie sprawdzić <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> Właściwość, jeśli masz inne czynności, które należy wykonać w odpowiedzi na anulowanie, nie zgłaszając wyjątku. W tym przykładzie można zobaczyć, że kod faktycznie uzyskuje dostęp do właściwości dwukrotnie: raz w jawnym dostępie i ponownie w <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metodzie. Jednak ze względu na to, że czynność odczytywania <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> Właściwości obejmuje tylko jedną nietrwałą instrukcję Read na Access, podwójnego dostępu nie jest istotne z perspektywy wydajności. Nadal zaleca się wywołanie metody zamiast ręcznie zgłosić <xref:System.OperationCanceledException> .  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](cancellation-in-managed-threads.md)
