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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcb2fbf5e0a310156fdc6fac5fe736692e8ec133
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135344"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania
Poniższy przykład pokazuje, jak używać <xref:System.Threading.SpinWait?displayProperty=nameWithType> obiekt do implementacji dwufazowej operacji oczekiwania. W pierwszej fazie obiekt synchronizacji `Latch`, uruchamia dla kilku cykli, podczas gdy sprawdza, czy blokada stał się dostępny. W drugim etapie, jeśli blokada staje się dostępny a następnie `Wait` metoda zwraca bez użycia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> przeprowadzić jego oczekiwania; w przeciwnym razie `Wait` wykonuje czas oczekiwania.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia bardzo podstawową implementację synchronizacji zatrzaśnięcia pierwotnych. Jeśli spodziewane czasy oczekiwania będą bardzo krótkie, możesz użyć tej struktury danych. Ten przykład dotyczy tylko w celach demonstracyjnych. Jeśli potrzebujesz funkcji zatrzaśnięcia typu w swoim programie, należy wziąć pod uwagę przy użyciu <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Używa zatrzaśnięcia <xref:System.Threading.SpinWait> obiektu Cię w miejscu tylko do następnego wywołania metody `SpinOnce` powoduje, że <xref:System.Threading.SpinWait> umożliwiające uzyskanie przedziału czasu wątku. W tym momencie zatrzaśnięcia powoduje, że jego własnej przełączenie kontekstu, wywołując <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> i przekazywania w pozostałej części wartość limitu czasu.  
  
 Dane wyjściowe rejestrowania pokazują, jak często zatrzaśnięcia był w stanie, co pozwoli zwiększyć wydajność przez uzyskanie blokady bez korzystania z <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Zobacz także

- [SpinWait](../../../docs/standard/threading/spinwait.md)  
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
