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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1794b47db87f636cc2ccdf2eecb9e7ca334ae659
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46585431"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Porady: nasłuchiwanie żądań anulowania za pomocą sondowania
Poniższy przykład pokazuje jeden ze sposobów, kod użytkownika można sondować token anulowania w regularnych odstępach czasu, aby zobaczyć, czy zażądano anulowania z wątku wywoływania. W tym przykładzie użyto <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu, ale w tym samym wzorcem dotyczy operacji asynchronicznych utworzone bezpośrednio przez <xref:System.Threading.ThreadPool?displayProperty=nameWithType> typu lub <xref:System.Threading.Thread?displayProperty=nameWithType> typu.  
  
## <a name="example"></a>Przykład  
 Sondowanie wymaga pewnego rodzaju pętli lub cykliczne kod, który okresowo może odczytać wartość typu Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości. Jeśli używasz <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu i oczekuje na zakończenie wątku wywołującego zadania, możesz użyć <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metodę, aby sprawdzić właściwości i zgłosić wyjątek. Za pomocą tej metody, należy upewnić się, czy poprawny wyjątek jest zgłaszany w odpowiedzi na żądanie. Jeśli używasz <xref:System.Threading.Tasks.Task>, wywołanie tej metody jest lepsze niż ręcznie zgłaszanie <xref:System.OperationCanceledException>. Jeśli nie masz zgłosić wyjątek, a następnie można po prostu Sprawdź właściwość i zwraca z metody, jeśli właściwość jest `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Wywoływanie <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> jest bardzo szybkie i nie powoduje znaczne obciążenie w pętli.  
  
 W przypadku wywołania <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, trzeba jawnie sprawdziła <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość, jeśli masz inne zadania do wykonania w odpowiedzi na anulowanie oprócz zostanie zgłoszony wyjątek. W tym przykładzie widać, że kod faktycznie uzyskuje dostęp do właściwości dwa razy: jeden raz w jawny dostęp i ponownie w <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody. Ale ponieważ act odczytu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość obejmuje tylko jeden lotnych instrukcji na dostęp do odczytu, double dostęp nie jest istotne z punktu widzenia wydajności. Nadal lepiej jest wywołać metodę, a nie ręcznie throw <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Zobacz także

- [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)
