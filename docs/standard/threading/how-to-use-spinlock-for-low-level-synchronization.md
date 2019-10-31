---
title: 'Instrukcje: korzystanie z struktury spinlock w przypadku synchronizacji niskiego poziomu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: ad254cb6208bff868e5fc689c502b7ddcc175ad5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137956"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Instrukcje: korzystanie z struktury spinlock w przypadku synchronizacji niskiego poziomu

Poniższy przykład ilustruje sposób użycia <xref:System.Threading.SpinLock>. W tym przykładzie Sekcja krytyczna wykonuje minimalną ilość pracy, co sprawia, że jest to dobry kandydat do <xref:System.Threading.SpinLock>. Zwiększenie nakładu pracy spowoduje zwiększenie wydajności <xref:System.Threading.SpinLock> w porównaniu do standardowej blokady. Istnieje jednak punkt, w którym struktury SpinLock jest droższa od standardowej blokady. Możesz użyć funkcji profilowania współbieżności w narzędziach profilowania, aby sprawdzić, który typ blokady zapewnia lepszą wydajność programu. Aby uzyskać więcej informacji, zobacz [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> może być przydatne, gdy blokada zasobu udostępnionego nie będzie utrzymywana przez bardzo długi czas. W takich przypadkach na komputerach z procesorem wielordzeniowym może być skuteczny, aby zablokowany wątek mógł obracać się na kilka cykli do momentu zwolnienia blokady. Przez nawirowanie wątek nie stanie się zablokowany, co stanowi proces intensywnie obciążający procesor CPU. <xref:System.Threading.SpinLock> przestaną nawirowania w pewnych warunkach, aby zapobiec zastępowaniu procesorów logicznych lub niewersji priorytetu w systemach z funkcją wielowątkowości.  
  
 W tym przykładzie używamy klasy <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, która wymaga synchronizacji użytkowników dla wielowątkowego dostępu. W aplikacjach przeznaczonych dla .NET Framework w wersji 4, inną opcją jest użycie <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, która nie wymaga żadnych blokad użytkownika.  
  
 Zwróć uwagę na użycie `false` (`False` w Visual Basic) w wywołaniu do <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>. Zapewnia to najlepszą wydajność. Określ `true` (`True` w Visual Basic) na architekturach IA64, aby użyć ogrodzenia pamięci, która opróżnia bufory zapisu, aby upewnić się, że blokada jest teraz dostępna dla innych wątków do zakończenia.  
  
## <a name="see-also"></a>Zobacz także

- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Lock — instrukcjaC#()](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock — instrukcja (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
