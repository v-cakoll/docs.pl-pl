---
title: "Porady: używanie struktury SpinLock do synchronizacji niskiego poziomu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 11d41a1fd04039fd08d945a72a37a479f79449a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Porady: używanie struktury SpinLock do synchronizacji niskiego poziomu
W poniższym przykładzie pokazano sposób użycia <xref:System.Threading.SpinLock>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie sekcja krytyczna wykonuje minimalnego czasu pracy, dzięki czemu odpowiednimi kandydatami do <xref:System.Threading.SpinLock>. Praca niewielkie zwiększeniu wydajności <xref:System.Threading.SpinLock> w porównaniu do standardowych blokady. Istnieje jednak punkt, jaką struktury SpinLock staje się droższe niż standardowe blokady. Aby zobaczyć, jaki rodzaj blokady zapewnia lepszą wydajność w programie, można użyć profilowania funkcji w narzędziach profilowania współbieżności. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock>mogą być przydatne, jeśli Blokada zasobu udostępnionego nie będzie można przechowywać na bardzo długi. W takich przypadkach na komputerach z procesorami wielordzeniowymi może być wydajne na pokrętła przez kilka cykli do czasu zwolnienia blokady zablokowanych wątku. Przez Obracająca, wątek nie zablokowanie, które jest procesem użycie Procesora CPU. <xref:System.Threading.SpinLock>przestanie Obracająca pewnych warunkach, aby uniknąć zablokowania procesorów logicznych lub odwracanie priorytet w systemach z funkcją Hyper-Threading.  
  
 W tym przykładzie użyto <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> klasy, która wymaga synchronizacji użytkowników dla wielowątkowych dostęp. W aplikacjach przeznaczonych dla platformy .NET Framework w wersji 4, inną opcją jest użycie <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, co nie wymaga żadnych blokady użytkownika.  
  
 Zwróć uwagę na użycie `false` (`False` w języku Visual Basic) w wywołaniu <xref:System.Threading.SpinLock.Exit%2A>. To zapewnia najlepszą wydajność. Określ `true` (`True`) na IA64 architektury do użycia ogrodzenia pamięci, które opróżnienia buforów zapisu, aby upewnić się, że blokady są teraz dostępne dla innych wątków zakończyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)
