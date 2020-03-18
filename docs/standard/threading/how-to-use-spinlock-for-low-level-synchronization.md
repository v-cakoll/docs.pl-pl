---
title: 'Jak: używać SpinLock do synchronizacji niskiego poziomu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: ad254cb6208bff868e5fc689c502b7ddcc175ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137956"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Jak: używać SpinLock do synchronizacji niskiego poziomu

W poniższym przykładzie pokazano, jak używać pliku <xref:System.Threading.SpinLock>. W tym przykładzie sekcja krytyczna wykonuje minimalną ilość pracy, co <xref:System.Threading.SpinLock>czyni go dobrym kandydatem do . Zwiększenie pracy niewielką ilość zwiększa wydajność <xref:System.Threading.SpinLock> w porównaniu do standardowego zamka. Istnieje jednak punkt, w którym SpinLock staje się droższy niż standardowa blokada. Można użyć funkcji profilowania współbieżności w narzędziach profilowania, aby zobaczyć, który typ blokady zapewnia lepszą wydajność w programie. Aby uzyskać więcej informacji, zobacz [Wizualizacja współbieżności](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock>może być przydatne, gdy blokada zasobu udostępnionego nie będzie utrzymywana przez bardzo długi czas. W takich przypadkach na komputerach wielordzeniowych może być efektywne dla zablokowanego wątku do obracania przez kilka cykli, aż do zwolnienia blokady. Obracając się wątek nie zostanie zablokowany, co jest procesem intensywnie korzystającym z procesora CPU. <xref:System.Threading.SpinLock>zatrzyma przędzenia w pewnych warunkach, aby zapobiec głodowi procesorów logicznych lub priorytetowej inwersji w systemach z Hyper-Threading.  
  
 W tym <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> przykładzie użyto klasy, która wymaga synchronizacji użytkownika dla dostępu wielowątkowego. W aplikacjach, które są przeznaczone dla .NET <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>Framework w wersji 4, inną opcją jest użycie , który nie wymaga żadnych blokad użytkownika.  
  
 Zwróć uwagę `false` `False` na użycie (w języku Visual Basic) w wywołaniu <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>. Zapewnia to najlepszą wydajność. `true` Określ`True` (w języku Visual Basic) w architekturach IA64, aby użyć ogrodzenia pamięci, które opróżnia bufory zapisu, aby upewnić się, że blokada jest teraz dostępna dla innych wątków do zakończenia.  
  
## <a name="see-also"></a>Zobacz też

- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [instrukcja lock (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock instrukcja (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
