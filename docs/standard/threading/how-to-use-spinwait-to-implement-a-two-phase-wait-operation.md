---
title: 'Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 5bac174660177fd47e1f345e64581e35ae4c0ffc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137944"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania
W poniższym przykładzie pokazano, jak użyć <xref:System.Threading.SpinWait?displayProperty=nameWithType> obiektu do zaimplementowania operacji oczekiwania dwufazowego. W pierwszej fazie obiekt synchronizacji, a `Latch`, obraca się przez kilka cykli, podczas gdy sprawdza, czy blokada stała się dostępna. W drugiej fazie, jeśli blokada staje `Wait` się dostępna, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> metoda zwraca bez użycia do wykonania jego oczekiwania; w `Wait` przeciwnym razie wykonuje oczekiwanie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono bardzo podstawową implementację prymitywu synchronizacji zatrzasku. Tej struktury danych można użyć, gdy oczekuje się, że czasy oczekiwania będą bardzo krótkie. W tym przykładzie jest tylko do celów demonstracyjnych. Jeśli w programie wymagana jest funkcja typu <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>zatrzask, rozważ użycie .  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Zatrzask używa <xref:System.Threading.SpinWait> obiektu do obracania się w `SpinOnce` miejscu <xref:System.Threading.SpinWait> tylko do następnego wywołania powoduje, że daje wycinek czasu wątku. W tym momencie zatrzask powoduje własne przełącznik <xref:System.Threading.WaitHandle.WaitOne%2A> kontekstu, wywołując <xref:System.Threading.ManualResetEvent> i przekazując w pozostałej części wartości określającego czas.  
  
 Dane wyjściowe rejestrowania pokazuje, jak często zatrzask był w <xref:System.Threading.ManualResetEvent>stanie zwiększyć wydajność poprzez uzyskanie blokady bez użycia .  
  
## <a name="see-also"></a>Zobacz też

- [SpinWait](../../../docs/standard/threading/spinwait.md)
- [Wątkowe obiekty i operacje](../../../docs/standard/threading/threading-objects-and-features.md)
