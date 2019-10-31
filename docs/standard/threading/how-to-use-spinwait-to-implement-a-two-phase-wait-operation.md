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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137944"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania
Poniższy przykład pokazuje, jak używać obiektu <xref:System.Threading.SpinWait?displayProperty=nameWithType> do implementowania wielofazowej operacji oczekiwania. W pierwszej fazie obiekt synchronizacji, `Latch`, obraca się dla kilku cykli podczas sprawdzania, czy blokada stanie się dostępna. W drugiej fazie, jeśli blokada zostanie udostępniona, Metoda `Wait` zwraca bez użycia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> do wykonania oczekiwania; w przeciwnym razie `Wait` wykonuje oczekiwanie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono bardzo podstawową implementację elementu pierwotnego synchronizacji zamka. Tej struktury danych można użyć, gdy czasy oczekiwania są bardzo krótkie. Ten przykład służy tylko do celów demonstracyjnych. Jeśli w programie jest wymagana funkcja typu zatrzaśnięcia, należy rozważyć użycie <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Zamk używa obiektu <xref:System.Threading.SpinWait>, aby obracać się tylko do momentu następnego wywołania do `SpinOnce` powoduje, że <xref:System.Threading.SpinWait> uzyskać wycinka czasu wątku. W tym momencie zamk wywołuje swój własny przełącznik kontekstu przez wywołanie <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> i przekazanie w pozostałej części wartości limitu czasu.  
  
 Dane wyjściowe rejestrowania pokazują, jak często zatrzaśnięcie było w stanie zwiększyć wydajność dzięki uzyskaniu blokady bez użycia <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Zobacz także

- [SpinWait](../../../docs/standard/threading/spinwait.md)
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
