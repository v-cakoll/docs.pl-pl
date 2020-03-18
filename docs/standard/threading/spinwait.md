---
title: SpinWait
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
ms.openlocfilehash: 91588fc6e9c3c8e85de6a315c0743efb0137ecd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128986"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>jest lekkim typem synchronizacji, którego można używać w scenariuszach niskiego poziomu, aby uniknąć kosztownych przełączników kontekstu i przejść jądra, które są wymagane dla zdarzeń jądra. Na komputerach wielordzeniowych, gdy nie oczekuje się, że zasób będzie przechowywany przez dłuższy czas, może być bardziej wydajny dla wątku oczekiwania, aby obracać się w trybie użytkownika przez kilkanaście lub kilkaset cykli, a następnie ponowić próbę nabycia zasobu. Jeśli zasób jest dostępny po przędzeniu, zapisano kilka tysięcy cykli. Jeśli zasób jest nadal niedostępny, spędziłeś tylko kilka cykli i nadal możesz wprowadzić oczekiwanie oparte na jądrze. Ta kombinacja spinning-then-waiting jest czasami określana jako *operacja oczekiwania dwufazowego*.  
  
 <xref:System.Threading.SpinWait>jest przeznaczony do użycia w połączeniu z typami .NET <xref:System.Threading.ManualResetEvent>Framework, które zawijają zdarzenia jądra, takie jak . <xref:System.Threading.SpinWait>może być również używany samodzielnie do podstawowej funkcji przędzenia w jednym programie.  
  
 <xref:System.Threading.SpinWait>to coś więcej niż tylko pusta pętla. Jest starannie zaimplementowana w celu zapewnienia prawidłowego zachowania przędzenia dla ogólnego przypadku i sama zainicjuje przełączniki kontekstu, jeśli obraca się wystarczająco długo (mniej więcej czas wymagany do przejścia jądra). Na przykład na komputerach <xref:System.Threading.SpinWait> jednordzeniowych daje wycinek czasu wątku natychmiast, ponieważ obracanie bloków do przodu postępu na wszystkich wątków. <xref:System.Threading.SpinWait>również daje nawet na maszynach wielordzeniowych, aby zapobiec wątku oczekiwania blokowania wątków o wyższym priorytecie lub modułzbierający elementy bezużyteczne. W związku z tym <xref:System.Threading.SpinWait> jeśli używasz w operacji oczekiwania dwufazowego, zaleca się <xref:System.Threading.SpinWait> wywołanie czasu jądra, zanim sam inicjuje przełącznik kontekstu. <xref:System.Threading.SpinWait>zapewnia <xref:System.Threading.SpinWait.NextSpinWillYield%2A> właściwość, którą można sprawdzić przed <xref:System.Threading.SpinWait.SpinOnce%2A>każdym połączeniem. Po powrocie `true`właściwości zainicjuj własną operację Wait. Na przykład zobacz [Jak: Użyj SpinWait do wdrożenia operacji oczekiwania dwufazowego](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Jeśli nie wykonujesz operacji oczekiwania dwufazowego, ale po prostu obracasz się, dopóki nie spełnisz pewnego warunku, możesz włączyć <xref:System.Threading.SpinWait> jego przełączniki kontekstu, aby był dobrym obywatelem w środowisku systemu operacyjnego Windows. Poniższy przykład podstawowy <xref:System.Threading.SpinWait> pokazuje w stosie bez blokady. Jeśli potrzebujesz stosu o wysokiej wydajności, <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>bezpieczne dla wątków, należy rozważyć użycie .  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Thread.SpinWait%2A>
- [Wątkowe obiekty i operacje](../../../docs/standard/threading/threading-objects-and-features.md)
