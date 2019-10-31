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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128986"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType> jest lekkim typem synchronizacji, którego można użyć w scenariuszach niskiego poziomu, aby uniknąć kosztownych przełączeń kontekstu i przejść jądra wymaganych dla zdarzeń jądra. W przypadku komputerów z wieloma rdzeniami, gdy nie jest oczekiwany czas przechowywania zasobu przez długi okres, może być bardziej wydajny w przypadku wątku oczekującego na przejście w tryb użytkownika dla kilku dziesiątek lub kilku setek cykli, a następnie ponowienie próby pobrania zasobu. Jeśli zasób jest dostępny po nawirowaniu, zapisano kilka tysięcy cykli. Jeśli zasób nadal nie jest dostępny, nastąpiło tylko kilka cykli i nadal można wprowadzić oczekiwania na jądro. Ta kombinacja obracająca się po tej operacji jest czasami nazywana *operacją oczekiwania dwufazowego*.  
  
 <xref:System.Threading.SpinWait> jest przeznaczony do użycia w połączeniu z typami .NET Framework, które zawijają zdarzenia jądra, takie jak <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait> może być również używana dla podstawowych funkcji obracających się tylko w jednym programie.  
  
 <xref:System.Threading.SpinWait> jest więcej niż tylko pusta pętla. Jest to starannie zaimplementowane w celu zapewnienia poprawnego, odnoszącego się do przypadku ogólnego zastosowania, a sama będzie inicjować przełączenia kontekstu, jeśli zostanie on przedłużony do długiego czasu (w przybliżeniu czas wymagany do przejścia jądra). Na przykład na komputerach z jednym rdzeniem program <xref:System.Threading.SpinWait> automatycznie generuje wycinek czasu wątku, ponieważ obracając bloki przekazują postęp we wszystkich wątkach. <xref:System.Threading.SpinWait> również zapewnia nawet na maszynach wielordzeniowych, aby zapobiec blokowaniu wątków z wyższym priorytetem lub modułem wyrzucania elementów bezużytecznych. W związku z tym, jeśli używasz <xref:System.Threading.SpinWait> w wielofazowej operacji oczekiwania, zalecamy Wywołaj jądro przed zainicjowaniem przez siebie <xref:System.Threading.SpinWait> kontekstu. <xref:System.Threading.SpinWait> zawiera właściwość <xref:System.Threading.SpinWait.NextSpinWillYield%2A>, którą można sprawdzić przed każdym wywołaniem do <xref:System.Threading.SpinWait.SpinOnce%2A>. Gdy właściwość zwraca `true`, zainicjuj własną operację oczekiwania. Aby zapoznać się z przykładem, zobacz [How to: use Metody SpinWait w celu zaimplementowania wielofazowej operacji oczekiwania](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Jeśli nie wykonujesz operacji oczekiwania dwufazowego, ale po prostu nastąpi odwirowanie do momentu, w którym spełniony jest jakiś warunek, możesz włączyć <xref:System.Threading.SpinWait> do wykonywania jego przełączników kontekstowych, tak aby był to dobry obywatel w środowisku systemu operacyjnego Windows. Poniższy przykład podstawowy ilustruje <xref:System.Threading.SpinWait> w stosie bez blokady. Jeśli jest potrzebny stos bezpieczny dla wątków, należy rozważyć użycie <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread.SpinWait%2A>
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
