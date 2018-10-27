---
title: Wątki i wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework]
- threading [.NET Framework], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5049ed1b44155f3c21c53bef24a13006fe97a3fa
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452589"
---
# <a name="threads-and-threading"></a>Wątki i wątkowość
Systemy operacyjne używają procesów do oddzielania innej aplikacji, które są one wykonywane. Wątki są podstawową jednostką, do której system operacyjny przydziela czas procesora, a więcej niż jeden wątek może wykonywać kod wewnątrz tego procesu. Każdy wątek obsługuje programy obsługi wyjątków, priorytet planowania i zestaw struktur, które system używa do zapisania kontekst wątku, dopóki nie zostało zaplanowane. Kontekst wątku zawiera wszystkie informacje wymagane przez wątek do bezbłędnie wznowić wykonania, w tym wątku zestaw rejestrów Procesora i stosu, w przestrzeni adresowej procesu hosta dla wątku.  
  
 .NET Framework na dalsze dzielący uproszczone zarządzanych podprocesów, domeny aplikacji, reprezentowane przez proces systemu operacyjnego <xref:System.AppDomain?displayProperty=nameWithType>. Jeden lub więcej wątków zarządzanych (reprezentowane przez <xref:System.Threading.Thread?displayProperty=nameWithType>) mogą być uruchamiane w jednym lub kilku domen aplikacji w ramach tego samego procesu zarządzanego. Mimo że każda domena aplikacji została uruchomiona z jednym wątkiem, kod w tej domenie aplikacji można utworzyć domeny dodatkowych aplikacji i dodatkowe wątki. Wynik jest, że wątków zarządzanych mogą swobodnie przemieszczać się między domeny aplikacji wewnątrz tego samego procesu zarządzanego; może mieć tylko jeden wątek poruszać się między kilka domen aplikacji.  
  
 System operacyjny obsługuje preemptive wielozadaniowość tworzy efekt jednoczesne wykonywanie wielu wątków na podstawie wielu procesów. Odbywa się to poprzez podział czasu procesora dostępne wśród wątków, które go potrzebują, przydzielania przedziału czasu procesora, do każdego wątku, jeden po drugim. Aktualnie wykonywany wątek jest zawieszony gdy upływa wycinka czasu, a inny wątek wznawia uruchomiona. Można przełączać się z jednego wątku do innego, go zapisuje kontekst wątku preempted wątku i ponowne załadowanie kontekście wątku zapisane następny wątek w kolejce wątku.  
  
 Długość przedziału czasu, zależy od systemu operacyjnego i procesora. Ponieważ każdego przedziału czasu jest mała, można wykonywać w tym samym czasie, pojawiają się wiele wątków, nawet jeśli dostępny jest tylko jeden procesor. Jest to rzeczywiście przypadek w systemach wieloprocesorowych, pliku wykonywalnego wątki są dystrybuowane między procesorów dostępnych.  
  
## <a name="when-to-use-multiple-threads"></a>Kiedy należy używać wielu wątków  
 Oprogramowanie, które wymaga interakcji użytkownika, musi reagują tak szybko jak to możliwe, aby zapewnić rozbudowane środowisko do działań użytkownika. W tym samym czasie jednak należy ją wykonać obliczeń niezbędnych do prezentowania danych użytkowników tak szybko, jak to możliwe. Jeśli aplikacja używa tylko jeden wątek wykonywania, można połączyć [programowania asynchronicznego](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) z [wywołaniem funkcji zdalnych .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100)) lub [usług XML sieci Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100)) utworzone za pomocą ASP .NET do użycia czasu przetwarzania innych komputerów dodatkowo niż swoje własne, aby zwiększyć szybkość reakcji, użytkownika i zmniejszyć czas przetwarzania danych w aplikacji. Jeśli przeprowadzasz intensywnie korzystających z operacji wejścia/wyjścia pracy umożliwia także porty zakończenia operacji We/Wy na zwiększenie szybkości reakcji aplikacji.  
  
### <a name="advantages-of-multiple-threads"></a>Korzyści wynikające z wielu wątków  
 Jednak przy użyciu więcej niż jeden wątek, jest najbardziej zaawansowane techniki umożliwiające zwiększenie szybkości reakcji użytkownika i przetwarzać dane niezbędne do swoją pracę w niemal tym samym czasie. Na komputerze z jednym procesorem wiele wątków można utworzyć ten efekt, korzystając z zalet małych okresy Between zdarzenia użytkownika do przetwarzania danych w tle. Na przykład użytkownik może edytować arkusz kalkulacyjny, podczas gdy inny wątek jest obliczanie innych części arkusza kalkulacyjnego w tej samej aplikacji.  
  
 Bez żadnych modyfikacji ta sama aplikacja może znacznie zwiększyć zadowolenia użytkowników po uruchomieniu na komputerze z więcej niż jednego procesora. Przy użyciu wielu wątków domeny pojedynczej aplikacji można wykonywać następujące zadania:  
  
-   Komunikują się za pośrednictwem sieci, na serwerze sieci Web i bazę danych.  
  
-   Wykonywanie operacji, które zająć dużo czasu.  
  
-   Rozróżnia zadania związane z różnym priorytetem. Na przykład wątku o wysokim priorytecie zarządza zadaniami wrażliwego na czas i wątek o niskim priorytecie wykonuje inne zadania.  
  
-   Zezwalaj na interfejsu użytkownika nadal odpowiadać, podczas przydzielania czasu zadania w tle.  
  
### <a name="disadvantages-of-multiple-threads"></a>Wady wielu wątków  
 Zalecane jest użycie możliwie najmniejszej liczby wątków jak to możliwe, a tym samym minimalizując wykorzystanie zasobów systemu operacyjnego i poprawa wydajności. Wątkowość ma również wymagania dotyczące zasobów i potencjalnych konfliktów wziąć pod uwagę podczas projektowania aplikacji. Wymagania dotyczące zasobów są następujące:  
  
-   System używa pamięci, aby uzyskać informacje o kontekście wymagane przez procesy, **AppDomain** obiektów i wątków. W związku z tym, liczbę procesów, **AppDomain** obiektów i wątki, które mogą być tworzone jest ograniczony przez ilość dostępnej pamięci.  
  
-   Rejestrowanie informacji o dużej liczbie wątków zużywa mocno procesora. W przypadku zbyt wiele wątków, większość z nich nie spowoduje znaczne postępu. W przypadku większości bieżących wątków w jednym procesie, wątki w innych procesów są planowane rzadziej.  
  
-   Kontrolowanie wykonywania kodu za pomocą wielu wątków jest złożona i może być źródłem wiele błędów.  
  
-   Niszczenie wątków wymaga, wiedząc, co może się zdarzyć oraz umiejętności obsługi tych problemów.  
  
 Zapewnianie dostępu do zasobów mogą powodować konflikty. Aby uniknąć konfliktów, możesz zsynchronizować lub kontrolować dostęp do zasobów udostępnionych. Nie można zsynchronizować dostęp prawidłowo (w domenach aplikacji tej samej lub innej) może prowadzić do problemów, takich jak zakleszczenia (w której dwa wątki przestać odpowiadać podczas każdego czeka na drugi ukończyć) i sytuacją wyścigów (sytuacji wynik nietypowe ze względu na Nieoczekiwany znaczenie chronometraż dwa zdarzenia). System zawiera obiekty synchronizacji, które mogą służyć do zapewnienia koordynacji zasobów współużytkowanie danych przez wiele wątków. Zmniejszenie liczby wątków ułatwia do synchronizowania zasobów.  
  
 Zasoby, które wymagają synchronizacji obejmują:  
  
-   Zasoby systemowe (takie jak porty komunikacyjne).  
  
-   Zasoby współużytkowane przez wiele procesów (takie jak dojścia do plików).  
  
-   Zasoby domeny pojedynczej aplikacji (takich jak globalnego, statycznej i wystąpienia pól) uzyskiwał dostęp do wielu wątków.  
  
### <a name="threading-and-application-design"></a>Projekt wątkowości i aplikacji  
 Ogólnie rzecz biorąc, przy użyciu <xref:System.Threading.ThreadPool> klasa jest najprostszym sposobem obsługi wielu wątków dla zadań względnie krótkich, nie będzie blokować innych wątków i gdy nie będzie żadnych określonego planowania zadań. Jednak istnieje kilka powodów do tworzenia własnych wątków:  
  
-   Jeśli potrzebujesz mają priorytet określonego zadania.  
  
-   Jeśli zadanie, które może być długi czas wykonywania (i w związku z tym block innych zadań).  
  
-   Jeśli musisz umieścić wątków w jednowątkowym apartamentem (wszystkie **ThreadPool** wątki są wielowątkowe apartamentu).  
  
-   Jeśli potrzebujesz stabilne tożsamości skojarzonych z wątkiem. Na przykład należy użyć dedykowanego wątku przerwania wątek, je zawiesić lub je odnajdą według nazwy.  
  
-   Jeśli musisz uruchomić wątków w tle, które współdziałają z interfejsem użytkownika, .NET Framework w wersji 2.0 zapewnia <xref:System.ComponentModel.BackgroundWorker> składnik, który komunikuje się za pomocą zdarzeń, za pomocą międzywątkowe skierowanie do wątku interfejsu użytkownika.  
  
### <a name="threading-and-exceptions"></a>Wątki i wyjątki  
 Obsługa wyjątków w wątkach. Nieobsługiwanych wyjątków w wątkach, nawet tła wątków, zazwyczaj zakończyć proces. Istnieją trzy wyjątki od tej reguły:  
  
-   A <xref:System.Threading.ThreadAbortException> jest zgłaszany w wątku, ponieważ <xref:System.Threading.Thread.Abort%2A> została wywołana.  
  
-   <xref:System.AppDomainUnloadedException> Jest zgłaszany w wątku, ponieważ Trwa zwalnianie domeny aplikacji.  
  
-   Środowisko uruchomieniowe języka wspólnego lub procesu hosta kończy działanie wątku.  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki w zarządzanych wątkach](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  W wersjach programu .NET Framework 1.0 i 1.1 środowisko uruchomieniowe języka wspólnego dyskretnie traps niektóre wyjątki, na przykład w przypadku wątków z puli wątków. Może to doprowadzić do uszkodzenia aplikacji i po pewnym czasie powodują, że zawiesza się aplikacje, które mogą być bardzo trudne do debugowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.ThreadPool>  
- <xref:System.ComponentModel.BackgroundWorker>  
- [Synchronizowanie danych na potrzeby wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
- [Zarządzana pula wątków](../../../docs/standard/threading/the-managed-thread-pool.md)
