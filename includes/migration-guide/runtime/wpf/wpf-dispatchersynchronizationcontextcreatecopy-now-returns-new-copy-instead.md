---
ms.openlocfilehash: ff4d67a1c821fc96130c4efbd88eb5c56766da06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804743"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext.CreateCopy teraz zwraca nową kopię zamiast bieżącego wystąpienia

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> zwracane odwołanie do bieżącego wystąpienia, przede wszystkim jako optymalizacji wydajności. W .NET Framework 4.5 zwraca nowe wystąpienie, dzięki czemu możliwe po raz pierwszy do zawarcia, że odniesienia równe wskazują, iż wątek wykonujący jest w kontekście poprawne synchronizacji.  Jest mało prawdopodobne, że kod, który sprawdza, czy tożsamość te odwołania zostaną zmienione, ale ze względu na zmianę, kod który wywołuje metodę <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> powinien zostać przetestowany w ramach migracji do programu .NET Framework 4.5 lub nowszej.|
|Sugestia|Należy pamiętać, że <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> teraz zwróci nową <xref:System.Threading.SynchronizationContext?displayProperty=name> obiektu. Wcześniej kod, którego równoważności odwołania wygenerowane w ten sposób nie faktycznie sprawdzał, czy go w prawidłowego kontekstu, ale nie podczas kompilowania dla platformy .NET Framework 4.5 lub nowszej.  Podczas, gdy jest to mało prawdopodobne, aby spowodować problemy, wykonywania ścieżek kodu powinien być wystarczająco dużo, aby określić, jeśli to stanowi problem.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
