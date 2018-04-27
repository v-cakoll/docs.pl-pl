---
title: Kolekcje bezpieczne wątkowo
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- thread-safe collections, overview
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
caps.latest.revision: 24
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5850335a13960df9094c1a6276799de043eb28f3
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="thread-safe-collections"></a>Kolekcje bezpieczne wątkowo
W programie [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] wprowadzono przestrzeń nazw <xref:System.Collections.Concurrent?displayProperty=nameWithType> zawierającą kilka klas kolekcji, które są zarówno bezpieczne wątkowo, jak i skalowalne. Wiele wątków można bezpiecznie i efektywnie Dodaj lub usuń elementy z tych kolekcji bez konieczności dodatkowe synchronizacji w kodzie użytkownika. Pisząc nowy kod, należy używać klas kolekcji współbieżnych w każdej sytuacji, gdy kolekcja będzie zapisywać równocześnie do wielu wątków. Jeśli z udostępnionej kolekcji odbywa się tylko odczyt, można używać klas z przestrzeni nazw <xref:System.Collections.Generic?displayProperty=nameWithType>. Zalecamy nieużywanie klas kolekcji w wersji 1.0, chyba że aplikacje mają być przeznaczone dla środowiska uruchomieniowego .NET Framework 1.1 lub starszego.  
  
## <a name="thread-synchronization-in-the-net-framework-10-and-20-collections"></a>Synchronizacja wątków w kolekcjach środowisk .NET Framework 1.0 i 2.0  
 Kolekcje wprowadzone w środowisku .NET Framework 1.0 znajdują się w przestrzeni nazw <xref:System.Collections?displayProperty=nameWithType>. Kolekcje te, wśród których są m.in. powszechnie używane <xref:System.Collections.ArrayList> i <xref:System.Collections.Hashtable>, oferują pewne bezpieczeństwo wątkowe za pomocą właściwości `Synchronized`, która zwraca bezpieczną wątkowo otokę wokół kolekcji. Otoka działa w ten sposób, że blokuje całą kolekcję podczas każdej operacji dodawania lub usuwania. W związku z tym każdy wątek, który próbuje uzyskać dostęp do kolekcji, musi czekać na swoją kolej, aby nałożyć jedną blokadę. Takie rozwiązanie nie jest skalowalne i przy dużych kolekcjach może powodować znaczne pogorszenie wydajności. Ponadto konstrukcja nie jest całkowicie chroniona przed sytuacjami wyścigu. Aby uzyskać więcej informacji, zobacz [synchronizacji w kolekcji](https://blogs.msdn.microsoft.com/bclteam/2005/03/15/synchronization-in-generic-collections-brian-grunkemeyer/).  
  
 Klasy kolekcji wprowadzone w środowisku .NET Framework 2.0 są umieszczone w przestrzeni nazw <xref:System.Collections.Generic?displayProperty=nameWithType>. Należą do nich <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602> itd. Te klasy oferują większe bezpieczeństwo pod względem typów i lepszą wydajność niż klasy środowiska .NET Framework 1.0. Jednak klasy kolekcji środowiska .NET Framework 2.0 nie zawierają żadnych funkcji synchronizacji wątków. Gdy elementy są dodawane lub usuwane równolegle w wielu wątkach, całą synchronizację musi zapewniać kod użytkownika.  
  
 Firma Microsoft zaleca klasy kolekcji współbieżnych w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ponieważ udostępniają one nie tylko bezpieczeństwo typu klas kolekcji .NET Framework 2.0, ale również bardziej efektywne i bardziej szczegółowy bezpieczeństwa wątku niż [!INCLUDE[net_v10_short](../../../../includes/net-v10-short-md.md)] Podaj kolekcje.  
  
## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>Blokowanie szczegółowe i mechanizmy bezblokadowe  
 Niektóre typy kolekcji współbieżnych wykorzystują uproszczone mechanizmy synchronizacji, takie jak <xref:System.Threading.SpinLock>, <xref:System.Threading.SpinWait>, <xref:System.Threading.SemaphoreSlim> i <xref:System.Threading.CountdownEvent>, które po raz pierwszy wprowadzono w środowisku [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Zazwyczaj korzystają z tych typów synchronizacji *zajęty Obracająca* przez krótki czas, przed ich wprowadzeniem do rzeczywisty stan oczekiwania wątku. Jeśli spodziewane czasy oczekiwania będą bardzo krótkie, warto stosować rotowanie, ponieważ znacznie mniej obciąża ono zasoby systemu niż przejścia jądra występujące w czekaniu. W przypadku klas kolekcji wykorzystujących mechanizm rotowania lepsza wydajność oznacza możliwość dodawania i usuwania elementów równolegle przez wiele wątków z bardzo dużą szybkością. Aby uzyskać więcej informacji na temat Obracająca a blokuje zobacz [struktury SpinLock](../../../../docs/standard/threading/spinlock.md) i [metody SpinWait](../../../../docs/standard/threading/spinwait.md).  
  
 Klasy <xref:System.Collections.Concurrent.ConcurrentQueue%601> i <xref:System.Collections.Concurrent.ConcurrentStack%601> w ogóle nie nakładają blokad. Zamiast tego do zapewnienia bezpieczeństwa wątkowego wykorzystują operacje <xref:System.Threading.Interlocked>.  
  
> [!NOTE]
>  Ponieważ klasy kolekcji współbieżnych obsługują interfejs <xref:System.Collections.ICollection>, implementują one właściwości <xref:System.Collections.ICollection.IsSynchronized%2A> i <xref:System.Collections.ICollection.SyncRoot%2A>, nawet jeśli te właściwości są nieistotne. Właściwość `IsSynchronized` zawsze zwraca wartość `false`, a właściwość `SyncRoot` zawsze ma wartość `null` (`Nothing` w języku Visual Basic).  
  
 W tabeli poniżej wymieniono typy kolekcji istniejące w przestrzeni nazw <xref:System.Collections.Concurrent?displayProperty=nameWithType>.  
  
|Typ|Opis|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|Zapewnia funkcjonalność ograniczania i blokowania dla wszystkich typów implementujących interfejs <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>. Aby uzyskać więcej informacji, zobacz [BlockingCollection — Przegląd](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Bezpieczna wątkowo implementacja słownika par klucz-wartość.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Bezpieczna wątkowo implementacja kolejki FIFO („pierwszy na wejściu, pierwszy na wyjściu”).|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Bezpieczna wątkowo implementacja stosu LIFO („ostatni na wejściu, pierwszy na wyjściu”).|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Bezpieczna wątkowo implementacja nieuporządkowanej kolekcji elementów.|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Interfejs, który musi implementować typ, aby mógł być używany w klasie `BlockingCollection`.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[BlockingCollection — omówienie](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|Opisuje funkcje zawarte w typie <xref:System.Collections.Concurrent.BlockingCollection%601>.|  
|[Instrukcje: Dodawanie elementów do kolekcji ConcurrentDictionary i ich usuwanie](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|Opisuje metody dodawania i usuwania elementów w klasie <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.|  
|[Instrukcje: Dodawanie i pobieranie elementów osobno w ramach kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|Opisuje metody dodawania i pobierania elementów z kolekcji blokującej bez używania modułu wyliczającego z właściwością tylko do odczytu.|  
|[Instrukcje: Dodawanie funkcji blokujących i ograniczających do kolekcji](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|Opisuje wykorzystywanie klas kolekcji jako podstawowego mechanizmu przechowywania dla kolekcji <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>.|  
|[Instrukcje: Używanie metody ForEach do usuwania elementów z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|Opisuje zastosowanie instrukcji `foreach` (`For Each` w języku Visual Basic) do usuwania wszystkich elementów w kolekcji blokującej.|  
|[Instrukcje: Używanie tablic kolekcji blokujących w potoku](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|Opisuje zastosowanie wielu kolekcji blokujących równocześnie w celu zaimplementowania potoku.|  
|[Instrukcje: Tworzenie puli obiektów przy użyciu obiektu ConcurrentBag](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|Pokazuje, jak za pomocą współbieżnego zbioru poprawić wydajność w scenariuszach, gdzie można wykorzystywać istniejące obiekty zamiast ciągle tworzyć nowe.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>
