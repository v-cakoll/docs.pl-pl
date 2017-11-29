---
title: "Kiedy należy używać kolekcji bezpiecznych wątkowo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0bfb5ef2679c4e20e99a10dcf82a251673811b41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-a-thread-safe-collection"></a>Kiedy należy używać kolekcji bezpiecznych wątkowo
[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Wprowadza pięć nowych typów kolekcji specjalnie zaprojektowane do obsługi wielowątkowych dodawania i usuwania działań. Aby uzyskać bezpieczeństwo wątków, te nowe typy użyć różnych rodzajów blokowanie wydajne i mechanizmów zwolnić blokady synchronizacji. Synchronizacja narzut dodaje do operacji. Narzut zależy od rodzaju synchronizacji, który jest używany, rodzaj operacji, które są wykonywane i inne czynniki, takie jak liczba wątków, które próbujesz uzyskać jednocześnie dostęp do kolekcji.  
  
 W niektórych scenariuszach synchronizacji obciążenie jest niewielka i umożliwia wielowątkowych typu na znacznie szybsze i znacznie lepszą niż jego odpowiednik z systemem innym niż wątkowo, gdy chronione przez usługę blokady zewnętrznych. W innych sytuacjach obciążenie może spowodować typu wątkowo wykonywania i skalowania o takie same lub nawet wolniej niż wersja zewnętrznie zablokowane, z systemem innym niż wątkowo typu.  
  
 Poniższe sekcje zawierają ogólne wytyczne dotyczące kiedy należy używać kolekcji bezpiecznych wątkowo i jego odpowiednik z systemem innym niż wątkowo, który dostarczane przez użytkownika blokuje wokół jego odczytu i zapisu. Ponieważ wydajność może się różnić w zależności od wielu czynników, wskazówki nie jest określone i nie nadaje się niekoniecznie we wszystkich okolicznościach. Jeśli wydajność jest bardzo ważne, najlepszy sposób, aby określić typ kolekcji do użycia jest mierzenie wydajności na podstawie konfiguracji reprezentatywny komputerów i obciążeń. Ten dokument używa następujących elementów:  
  
 *Scenariusz czysty producent — konsument*  
 Wszelkie danego wątku jest dodanie albo usunięcie elementów, ale nie oba.  
  
 *Scenariusz mieszanych producent — konsument*  
 Wszelkie danego wątku jest dodawanie i usuwanie elementów.  
  
 *Przyspieszenie*  
 Szybsze algorytmicznego wydajności względem innego typu, w tym samym scenariuszu.  
  
 *Skalowalność*  
 Wzrost wydajności, która jest proporcjonalna do liczby rdzeni na komputerze. Algorytm, która może obsłużyć dokonuje szybciej osiem rdzeni niż na dwa rdzenie.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) vs. Queue(T)  
 W scenariuszach czysty producent — konsument, gdzie czas przetwarzania dla każdego elementu jest bardzo mały (kilka instrukcje), następnie <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> mogą oferować niewielkie wydajności za pośrednictwem <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> mający zewnętrznych blokady. W tym scenariuszu <xref:System.Collections.Concurrent.ConcurrentQueue%601> sprawdza się najlepiej, gdy jeden wątek dedykowanych w kolejce i wyłączyć kolejkowanie jest jeden wątek dedykowanych. Jeśli nie wymuszania tej reguły, następnie <xref:System.Collections.Generic.Queue%601> nawet może zapewnić lepszą niż <xref:System.Collections.Concurrent.ConcurrentQueue%601> na komputerach, które mają wiele rdzeni.  
  
 Gdy czas przetwarzania wynosi około 500 FLOPS (operacji zmiennoprzecinkowych) lub więcej, następnie reguły dwa wątku nie ma zastosowania do <xref:System.Collections.Concurrent.ConcurrentQueue%601>, który następnie jest bardzo dobre skalowalności. <xref:System.Collections.Generic.Queue%601>nie działa dobrze w tym scenariuszu.  
  
 W mieszanych producent — konsument scenariuszy, gdy czas przetwarzania jest bardzo mała <xref:System.Collections.Generic.Queue%601> mający zewnętrzne blokady skaluje się lepiej niż <xref:System.Collections.Concurrent.ConcurrentQueue%601> jest. Gdy czas przetwarzania jest jednak FLOPS około 500 lub więcej, a następnie <xref:System.Collections.Concurrent.ConcurrentQueue%601> skaluje się lepiej.  
  
## <a name="concurrentstack-vs-stack"></a>Obiektu concurrentstack została następującą vs. Stos  
 W scenariuszach czysty producent — konsument, gdy czas przetwarzania jest bardzo mały, następnie <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> i <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> mający zewnętrzne blokady prawdopodobnie będzie wykonywać o taki sam jak jeden wątek położenia dedykowanych i jeden wątek dedykowanych o wyświetlaniu. Jednak jako liczba wątków zwiększa obu typów spowolnić z powodu niezgodności zwiększona, i <xref:System.Collections.Generic.Stack%601> może zapewnić lepszą niż <xref:System.Collections.Concurrent.ConcurrentStack%601>. Gdy czas przetwarzania jest FLOPS około 500 lub więcej, a następnie obu typów skali w o tej samej stawki.  
  
 W mieszanych producent — konsument scenariuszach <xref:System.Collections.Concurrent.ConcurrentStack%601> jest szybsze dla małe i duże obciążenia.  
  
 Korzystanie z <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> i <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> może znacznie przyspieszyć godziny dostępu.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>Obiekt ConcurrentDictionary vs. Słownik  
 Ogólnie rzecz biorąc, użyj <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> w jakimkolwiek scenariuszu, w którym Dodawanie i aktualizowanie kluczy lub wartości jednocześnie z wielu wątków. W scenariuszach obejmujących częste aktualizacje i względnie mało odczyty <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zwykle zapewnia korzyści niewielkie. W scenariuszach obejmujących wiele odczytów, jak i wiele aktualizacji <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jest zwykle znacznie szybsze na komputerach z dowolną liczbę rdzeni.  
  
 W scenariuszach obejmujących częste aktualizacje, można zwiększyć stopień współbieżność w <xref:System.Collections.Concurrent.ConcurrentDictionary%602> i pomiarów, aby zobaczyć, czy zwiększona wydajność w przypadku komputerów, które mają większej liczby rdzeni. Jeśli zmienisz poziom współbieżności uniknąć możliwie globalne operacje.  
  
 Jeśli użytkownik jest tylko do odczytu klucza lub wartości, <xref:System.Collections.Generic.Dictionary%602> przebiega szybciej, ponieważ synchronizacja nie jest wymagana, jeśli słownik nie jest modyfikowana przez wszystkie wątki.  
  
## <a name="concurrentbag"></a>Obiekt ConcurrentBag  
 W scenariuszach czysty producent — konsument <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> będzie prawdopodobnie wolniejsze od innych typów kolekcji współbieżnych.  
  
 W mieszanych producent — konsument scenariuszach <xref:System.Collections.Concurrent.ConcurrentBag%601> jest zwykle znacznie szybsze i większą skalowalność niż innego typu kolekcji współbieżnych zarówno dużych i małych obciążeń.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Gdy semantyki blokujących i ograniczających są wymagane, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> prawdopodobnie będzie wykonywać szybciej niż przy użyciu niestandardowych implementacji. Obsługuje ona również sformatowanego anulowania, wyliczenia i obsługi wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekcje obsługujące wielowątkowość](../../../../docs/standard/collections/thread-safe/index.md)  
 [Programowanie równoległe](../../../../docs/standard/parallel-programming/index.md)
