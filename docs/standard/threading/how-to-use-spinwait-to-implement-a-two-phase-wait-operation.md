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
ms.openlocfilehash: af6e4e8d0d754b97478788422b4dd84eeddc6491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Porady: korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania
Poniższy przykład przedstawia użycie <xref:System.Threading.SpinWait?displayProperty=nameWithType> obiektu do implementacji dwufazowej operacji oczekiwania. W pierwszej fazie obiektu synchronizacji `Latch`, obraca przez kilka cykli podczas sprawdza, czy blokada stał się dostępny. W drugim etapie, jeśli blokada staje się dostępny a następnie `Wait` metoda zwraca bez użycia <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> przeprowadzić jego oczekiwania; w przeciwnym razie `Wait` wykonuje czas oczekiwania.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia bardzo proste implementacja synchronizacji zatrzaśnięcia pierwotnych. Można użyć tej struktury danych, gdy powinny być bardzo krótki czas oczekiwania. W tym przykładzie jest tylko w celach demonstracyjnych. Jeśli potrzebujesz zatrzaśnięcia typu funkcji w programie, należy rozważyć użycie <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Używa zatrzaśnięcia <xref:System.Threading.SpinWait> obiektu się w miejscu tylko do następnego wywołania `SpinOnce` powoduje, że <xref:System.Threading.SpinWait> umożliwiające uzyskanie przedział czasu wątku. W tym momencie zatrzaśnięcia powoduje jego własnej przełączenie kontekstu wywołując <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> i przekazywanie w pozostałej części wartość limitu czasu.  
  
 Dane wyjściowe rejestrowania pokazuje, jak często zatrzaśnięcia mógł zwiększenia wydajności, uzyskiwanie blokady bez użycia <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Zobacz też  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
