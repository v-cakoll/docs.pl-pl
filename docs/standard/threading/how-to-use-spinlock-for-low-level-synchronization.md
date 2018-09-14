---
title: 'Porady: używanie struktury SpinLock do synchronizacji niskiego poziomu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 216480e893f6dbebbb204cbf2bfebae8dc139ec4
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45593859"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Porady: używanie struktury SpinLock do synchronizacji niskiego poziomu
Poniższy przykład pokazuje sposób użycia <xref:System.Threading.SpinLock>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie sekcję krytyczną wykonuje minimalnego czasu pracy, które ułatwia dobrym kandydatem do <xref:System.Threading.SpinLock>. Zwiększanie pracę małą ilością zwiększa wydajność <xref:System.Threading.SpinLock> w porównaniu do standardowych blokady. Jednak znajduje się punkt, w jakim struktury SpinLock staje się bardziej kosztowne niż standardowe blokady. Można użyć profilowania funkcji w narzędziach profilowania współbieżności, aby zobaczyć, jakiego typu blokady zapewnia lepszą wydajność w programie. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> mogą być przydatne, gdy nie ma blokady zasobu udostępnionego dla bardzo długi. W takich przypadkach na komputerach z wielordzeniowymi procesorami może być zablokowany wątek Cię w kilka cykli, dopóki blokada jest zwalniana wydajny. Która pozwala na, wątek nie stać się blokowane, czyli procesu mocy procesora CPU. <xref:System.Threading.SpinLock> przestanie rotowania w pewnych okolicznościach, aby uniknąć zablokowania procesorów logicznych lub odwracanie priorytet w systemach z funkcją Hyper-Threading.  
  
 W tym przykładzie użyto <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> klasy, która wymaga synchronizacji użytkowników dla dostępu wielowątkowych. W aplikacjach przeznaczonych dla platformy .NET Framework w wersji 4, innym rozwiązaniem jest użycie <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, co nie wymaga żadnych blokady użytkownika.  
  
 Zwróć uwagę na użycie `false` (`False` w języku Visual Basic) w wywołaniu <xref:System.Threading.SpinLock.Exit%2A>. Dzięki temu można uzyskać najlepszą wydajność. Określ `true` (`True`) na architektury IA64 używania horyzontu pamięci, która opróżnia buforów zapisu, aby upewnić się, czy blokada jest teraz dostępna dla innych wątków zakończyć pracę.  
  
## <a name="see-also"></a>Zobacz także

- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
