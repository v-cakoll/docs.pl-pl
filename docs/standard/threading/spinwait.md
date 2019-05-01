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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b66ec913a6e8726710d90737f97c04335ae6e4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015346"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType> jest typem synchronizacji uproszczone, który można użyć w scenariuszach niskiego poziomu, aby uniknąć przełączeń kontekstu kosztowne i przejścia jądra, które są wymagane dla zdarzeń jądra. Na komputerach wielordzeniowych gdy zasób nie powinno być przechowywane przez długi okresy czasu, może być bardziej wydajne dla wątku oczekiwania w celu uruchomienia w trybie użytkownika dla kilka tuzinów lub kilka cykli kilkuset, a następnie ponów można uzyskać zasobu. Jeśli zasób jest dostępny po obrotowych, zostały zapisane w kilku tysięcy cykli. Jeśli zasób jest nadal nie jest dostępna, następnie poświęcony tylko kilka cykli i nadal można wprowadzić oczekiwanie na podstawie jądra. Ta kombinacja rotowania następnie oczekiwania jest czasami określane jako *dwufazowej operacji oczekiwania*.  
  
 <xref:System.Threading.SpinWait> jest przeznaczony do użycia w połączeniu z typów programu .NET Framework, które otaczają przekazywanie zdarzeń jądra, takich jak <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait> można również samodzielnie dotyczące rotowania podstawowych funkcji programu tylko jeden program.  
  
 <xref:System.Threading.SpinWait> to coś więcej niż tylko pustych pętla. Dokładnie jest implementowane w celu zapewnienia rotowania poprawne zachowanie w przypadku ogólnych i sam zainicjuje przełączeń kontekstu, jeśli go uruchamia wystarczająco długi (około długość czasu wymaganego do przejścia jądra). Na przykład na komputerach jednordzeniowy <xref:System.Threading.SpinWait> daje przedziału czasu wątku od razu, ponieważ bloki rotowania przekazywania postępu we wszystkich wątkach. <xref:System.Threading.SpinWait> daje również nawet w wielordzeniowych maszynach, aby zapobiec wątku oczekiwania zapobiega wątki o wyższym priorytecie lub moduł odśmiecania pamięci. W związku z tym Jeśli używasz <xref:System.Threading.SpinWait> w dwufazowej operacji oczekiwania, firma Microsoft zaleca, wywołuje oczekiwania jądra przed <xref:System.Threading.SpinWait> sam inicjuje przełączenie kontekstu. <xref:System.Threading.SpinWait> udostępnia <xref:System.Threading.SpinWait.NextSpinWillYield%2A> właściwość, która można sprawdzić przed każde wywołanie <xref:System.Threading.SpinWait.SpinOnce%2A>. Gdy właściwość zwraca `true`, zainicjować operacji oczekiwania. Aby uzyskać przykład, zobacz [jak: Korzystanie z metody SpinWait do implementacji dwufazowej operacji oczekiwania](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Jeśli bez wykonywania dwufazowej operacji oczekiwania, ale są po prostu obrotowych, dopóki jakiś warunek ma wartość true, aby umożliwić <xref:System.Threading.SpinWait> przeprowadzić kontekst przełącza się tak, aby dobre dla obywateli w środowisku systemu operacyjnego Windows. Ilustruje poniższy przykład podstawowy <xref:System.Threading.SpinWait> na stosie, wolne od blokady. Jeśli potrzebujesz stosu o wysokiej wydajności, bezpieczna wątkowo, należy wziąć pod uwagę przy użyciu <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread.SpinWait%2A>
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
