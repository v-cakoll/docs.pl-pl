---
title: Wątki i wątkowość
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework]
- threading [.NET Framework], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02c676e3bb6c0dcc9e65858367d13f41adc797e8
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="threads-and-threading"></a>Wątki i wątkowość
Systemy operacyjne umożliwia rozdzielenie różnych aplikacji, które działają procesów. Wątki są jednostkę podstawową, system operacyjny przydziela czas procesora i więcej niż jeden wątek może wykonywania kodu wewnątrz tego procesu. Każdy wątek obsługuje programy obsługi wyjątków, priorytet i zestaw struktur, które system używa zapisać kontekstu wątku, dopóki nie zostanie określony. Kontekst wątku zawiera wszystkie informacje wymagane przez wątek do bezbłędnie wznowić wykonywanie wątku zestaw rejestrów Procesora i stosu, w tym do przestrzeni adresowej procesu hosta wątku.  
  
 .NET Framework dalsze dzieli procesu systemu operacyjnego do lekkie zarządzanych, podprocesów określanych jako domeny aplikacji, reprezentowany przez <xref:System.AppDomain?displayProperty=nameWithType>. Jeden lub więcej wątków zarządzanych (reprezentowane przez <xref:System.Threading.Thread?displayProperty=nameWithType>) można uruchomić w jednej lub kilku domen aplikacji w ramach tego samego procesu zarządzanego. Każda domena aplikacji została uruchomiona z jednym wątkiem, kodu w tej domenie aplikacji można utworzyć dodatkowe wątki i domen aplikacji dodatkowych. Wynik jest, że zarządzanego wątku mogą swobodnie przemieszczać się między domenami aplikacji wewnątrz tego samego procesu zarządzanego; może istnieć tylko jeden wątek przenoszenia między kilka domen aplikacji.  
  
 System operacyjny, który obsługuje cenią sobie wcześniejsze wielozadaniowości tworzy efekt jednoczesne wykonywanie wielu wątków na podstawie wielu procesów. Jest to możliwe dzięki podział czasu procesora dostępne między wątków, które go potrzebują, przydzielanie przedział czasu procesora, aby każdy wątek jeden po drugim. Aktualnie wykonywane wątek jest zawieszony, gdy jej czas upływający wycinka i innego wątku wznawia uruchomiona. Przełączać się z jednego wątku do innego, go zapisuje kontekst wątku preempted wątku i ponowne załadowanie kontekście wątku zapisane następnego wątku w kolejce wątku.  
  
 Długość przedziału czasu zależy od systemu operacyjnego i procesora. Ponieważ każdy przedział czasu jest mały, wiele wątków ma być wykonywane jednocześnie, nawet jeśli dostępny jest tylko jeden procesor. Jest rzeczywiście w systemach wieloprocesorowych, które wykonywalnego wątki są dystrybuowane między dostępnych procesorów.  
  
## <a name="when-to-use-multiple-threads"></a>Kiedy należy używać wiele wątków  
 Oprogramowanie, które wymaga interakcji użytkownika musi reagować na działania użytkownika tak szybko jak to możliwe, aby zapewnić użyciu zaawansowanego środowiska użytkownika. W tym samym czasie jednak należy ją wykonać obliczeń niezbędnych do przedstawienia danych użytkownika tak szybko, jak to możliwe. Jeśli aplikacja używa tylko jeden wątek, można połączyć [programowanie asynchroniczne](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) z[.NET Framework remoting](https://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462) lub [usług XML sieci Web](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c) utworzone za pomocą ASP .NET na potrzeby czas przetwarzania innych komputerów dodatkowo z własnych zwiększenie czasu odpowiedzi użytkownika i zmniejsza czas przetwarzania danych aplikacji. Jeśli przeprowadzasz znacznym pracy wejścia/wyjścia, można zwiększyć czas odpowiedzi aplikacji w portów We/Wy.  
  
### <a name="advantages-of-multiple-threads"></a>Zalety wiele wątków  
 Jednak przy użyciu więcej niż jeden wątek, jest najbardziej zaawansowanych technik, można zwiększyć czas odpowiedzi dla użytkownika i przetwarzania danych, które są niezbędne, aby uzyskać zadanie wykonywane w niemal tym samym czasie. Na komputerze z jednym procesorem wiele wątków można utworzyć ten efekt, wykorzystaniu małych okresów Between zdarzeń użytkownika do przetwarzania danych w tle. Na przykład użytkownik może edytować arkusza kalkulacyjnego, podczas gdy inny wątek jest ponowne obliczanie inne części arkusza kalkulacyjnego w tej samej aplikacji.  
  
 Bez żadnych modyfikacji ta sama aplikacja będzie znacznie zwiększyć komfort użytkowników uruchamianych na komputerze z więcej niż jeden procesor. Domeny pojedynczej aplikacji można użyć wielu wątków można wykonywać następujące zadania:  
  
-   Komunikacji za pośrednictwem sieci do serwera sieci Web i bazę danych.  
  
-   Wykonywanie operacji, które zająć dużo czasu.  
  
-   Odróżnić zadania różnych priorytetów. Na przykład wątku o wysokim priorytecie zarządza wrażliwego na czas zadania i niskiego priorytetu wątku wykonuje inne zadania.  
  
-   Zezwalaj na interfejsie użytkownika będzie odpowiadać, podczas przydzielania czasu na zadania w tle.  
  
### <a name="disadvantages-of-multiple-threads"></a>Wady wiele wątków  
 Zaleca się używać jak najmniejszej liczby wątków jak to możliwe, a tym samym minimalizując użycie zasobów systemu operacyjnego i poprawia wydajność. Wątkowość ma również wymagania dotyczące zasobów i potencjalnych konfliktów wziąć pod uwagę podczas projektowania aplikacji. Wymagania dotyczące zasobów są następujące:  
  
-   System zajmują pamięć dla wymaganych przez procesy, informacje o kontekście **elementu AppDomain** obiektów i wątków. W związku z tym liczba procesów, **elementu AppDomain** obiektów i wątków, które mogą być tworzone jest ograniczone przez ilość dostępnej pamięci.  
  
-   Rejestrowanie informacji o dużej liczby wątków zużywa czas procesora znaczące. Jeśli ma zbyt wiele wątków, większość z nich nie dokona znaczącego postępu. W przypadku większości aktualna liczba wątków w jeden proces, rzadziej zaplanowane wątków w innych procesów.  
  
-   Kontrolowanie wykonanie kodu z wielu wątków jest złożony i może być źródłem wiele błędów.  
  
-   Niszczenie wątków wymaga uprzedniego uzyskania informacji o to, co może się zdarzyć i obsługi tych problemów.  
  
 Zapewnianie współdzielonym dostępem do zasobów mogą powodować konflikty. Aby uniknąć konfliktów, możesz zsynchronizować lub kontrolować dostęp do zasobów udostępnionych. Synchronizujący dostęp prawidłowo (w domenach aplikacji tego samego lub innego) może doprowadzić do problemów, takich jak zakleszczenie (w których dwoma wątkami przestaje odpowiadać podczas każdego oczekiwania przez drugą do ukończenia) i zastępować warunkami (jeśli jest to wynik nietypowych występuje z powodu Nieoczekiwany krytyczne zależności od chronometrażu dwóch zdarzeń). System udostępnia obiekty synchronizacji, które mogą służyć do zapewnienia koordynacji zasobów, udostępnianie między wiele wątków. Zmniejszenie liczby wątków ułatwia synchronizacji zasobów.  
  
 Zasoby, które wymagają synchronizacji obejmują:  
  
-   Zasoby systemowe (na przykład portów komunikacji).  
  
-   Zasoby współużytkowane przez wiele procesów (np. dojścia do plików).  
  
-   Zasoby aplikacji jednej domeny (np. static globalnych, wystąpienie pola) dostęp wiele wątków.  
  
### <a name="threading-and-application-design"></a>Projekt wątków i aplikacji  
 Ogólnie rzecz biorąc, przy użyciu <xref:System.Threading.ThreadPool> klasy jest najprostszym sposobem obsługi wielu wątków stosunkowo krótkich zadań nieblokowanych innych wątków i gdy nie oczekuje żadnych określonego harmonogramu zadań. Jednak istnieje wiele powodów do tworzenia własnych wątków:  
  
-   Jeśli potrzebujesz zadania określonego priorytetem.  
  
-   Jeśli zadanie, które może być długi czas wykonywania (i w związku z tym zablokować inne zadania).  
  
-   Jeśli musisz umieścić wątków w jednowątkowym trybie apartment (wszystkie **puli wątków** wątki są wielowątkowe apartamentu).  
  
-   Jeśli potrzebujesz stabilna tożsamości, skojarzony z wątkiem. Na przykład należy użyć dedykowanego wątku przerwać wątek, wstrzymanie go lub go odnaleźć według nazwy.  
  
-   Jeśli musisz uruchomić wątki w tle, które współdziałają z interfejsem użytkownika, .NET Framework w wersji 2.0 zapewnia <xref:System.ComponentModel.BackgroundWorker> składnika, który komunikuje się za pomocą zdarzeń, z między wątkami przekazywanie do wątku interfejsu użytkownika.  
  
### <a name="threading-and-exceptions"></a>Wątki i wyjątków  
 Obsługa wyjątków w wątkach. Nieobsługiwane wyjątki w wątkach, wątki w tle nawet, zazwyczaj zakończenie procesu. Istnieją trzy wyjątki od tej reguły:  
  
-   A <xref:System.Threading.ThreadAbortException> wyjątek w wątku, ponieważ <xref:System.Threading.Thread.Abort%2A> została wywołana.  
  
-   <xref:System.AppDomainUnloadedException> Jest zgłaszany w wątku, ponieważ Trwa zwalnianie domen aplikacji.  
  
-   Środowisko uruchomieniowe języka wspólnego lub procesu hosta kończy wątku.  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  W wersji systemu .NET Framework 1.0 i 1.1 środowisko uruchomieniowe języka wspólnego dyskretnie traps niektóre wyjątki, na przykład w wątku puli wątków. Może to doprowadzić do uszkodzenia aplikacji i może spowodować zawieszenie, aplikacje, które mogą być bardzo trudne do debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ThreadPool>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Synchronizowanie danych na potrzeby wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [Zarządzana pula wątków](../../../docs/standard/threading/the-managed-thread-pool.md)
