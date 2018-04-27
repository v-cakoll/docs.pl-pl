---
title: Odzyskiwanie pamięci i wydajność
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: daf70cdb7344f895059d0bc8b986edddbf7d53bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="garbage-collection-and-performance"></a>Odzyskiwanie pamięci i wydajność
<a name="top"></a> W tym temacie opisano problemy związane z użycia pamięci kolekcji i pamięci. Rozwiązuje problemy, które odnoszą się do sterty zarządzanej, a wyjaśniono sposób zminimalizować wpływ operacji wyrzucania elementów bezużytecznych w aplikacji. Każde wydanie zawiera łącza do procedur, które służy do badania problemów.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Narzędzia analizy wydajności](#performance_analysis_tools)  
  
-   [Rozwiązywanie problemów z wydajnością](#troubleshooting_performance_issues)  
  
-   [Wskazówki dotyczące rozwiązywania problemów](#troubleshooting_guidelines)  
  
-   [Procedury sprawdzania wydajności](#performance_check_procedures)  
  
<a name="performance_analysis_tools"></a>   
## <a name="performance-analysis-tools"></a>Narzędzia analizy wydajności  
 W poniższych sekcjach opisano narzędzia, które są dostępne do badania problemów kolekcji użycia i odzyskiwanie pamięci. [Procedury](#performance_check_procedures) podane w dalszej części tego tematu odwoływać się do tych narzędzi.  
  
<a name="perf_counters"></a>   
### <a name="memory-performance-counters"></a>Liczniki wydajności pamięci  
 Liczniki wydajności służy do zbierania danych wydajności. Aby uzyskać instrukcje, zobacz [profilowanie środowiska uruchomieniowego](../../../docs/framework/debug-trace-profile/runtime-profiling.md). Kategoria .NET CLR pamięci liczników wydajności, zgodnie z opisem w [liczników wydajności w programie .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), informacje na temat modułu zbierającego elementy bezużyteczne.  
  
<a name="sos"></a>   
### <a name="debugging-with-sos"></a>Debugowanie za pomocą SOS  
 Można użyć [debugera systemu Windows (WinDbg)](/windows-hardware/drivers/debugger/index) do zbadania obiektów na stercie zarządzanej.
 
 Aby zainstalować WinDbg, zainstalować narzędzi debugowania dla systemu Windows z [pobieranie narzędzi debugowania dla systemu Windows](/windows-hardware/drivers/debugger/debugger-download-tools) strony.
  
<a name="etw"></a>   
### <a name="garbage-collection-etw-events"></a>Zdarzenia ETW odzyskiwania pamięci  
 Śledzenie zdarzeń systemu Windows (ETW) to system śledzenia, który uzupełnia profilowania i obsługa w programie .NET Framework — profilowanie. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [zdarzenia ETW wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md) przechwytywania przydatne informacje dotyczące analizowania sterty zarządzanej z punktu widzenia statystycznych. Na przykład `GCStart_V1` zdarzenie, które jest wywoływane, gdy ma wystąpić wyrzucania elementów bezużytecznych, zawiera następujące informacje:  
  
-   Zbierane są które generowania obiektów.  
  
-   Co wyzwoliło wyrzucanie elementów bezużytecznych.  
  
-   Typ operacji wyrzucania elementów bezużytecznych (równoczesnych lub nie równoczesnych).  
  
 Rejestrowanie zdarzeń ETW jest wydajne i nie będzie maskował wszelkie problemy z wydajnością skojarzone z wyrzucanie elementów bezużytecznych. Proces może udostępniać swoje własne zdarzenia w połączeniu z zdarzenia ETW. Podczas rejestrowania, zarówno zdarzeń aplikacji, jak i zdarzenia wyrzucania elementów bezużytecznych może zostać skorelowane ustalenie, jak i kiedy sterty problemów. Na przykład aplikacja serwera może dostarczyć zdarzenia na początku i na końcu żądania klienta.  
  
<a name="profiling_api"></a>   
### <a name="the-profiling-api"></a>Interfejsu API profilowania  
 Wspólnych interfejsów profilowania środowiska uruchomieniowego (języka wspólnego CLR) języka zawierają szczegółowe informacje o obiektach, które miały wpływ podczas wyrzucania elementów bezużytecznych. Profiler może otrzymać powiadomienie, gdy wyrzucania elementów bezużytecznych uruchamia i kończy się. Może udostępnić raporty dotyczące obiektów na stercie zarządzanej, w tym identyfikację obiektów w każdej generacji. Aby uzyskać więcej informacji, zobacz [Przegląd profilowania](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).  
  
 Profilery zapewniają szczegółowe informacje. Jednak złożonych profilowania potencjalnie można zmodyfikować zachowanie aplikacji.  
  
### <a name="application-domain-resource-monitoring"></a>Monitorowanie zasobów domen aplikacji  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], zasobów domen aplikacji monitorowania (ARM) umożliwia hostom monitorowanie użycia procesora CPU i pamięci według domeny aplikacji. Aby uzyskać więcej informacji, zobacz [monitorowania zasobów domen aplikacji](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).  
  
 [Powrót do początku](#top)  
  
<a name="troubleshooting_performance_issues"></a>   
## <a name="troubleshooting-performance-issues"></a>Rozwiązywanie problemów z wydajnością  
 Pierwszym krokiem jest [ustalić, czy problem jest rzeczywiście wyrzucanie elementów bezużytecznych](#IsGC). Jeśli okaże się, że jest, wybierz z poniższej listy, aby rozwiązać problem.  
  
-   [Wyjątek braku pamięci](#Issue_OOM)  
  
-   [Proces używa zbyt dużej ilości pamięci](#Issue_TooMuchMemory)  
  
-   [Moduł zbierający elementy bezużyteczne nie odzyskać obiektów tyle szybko](#Issue_NotFastEnough)  
  
-   [Sterta zarządzana za jest pofragmentowana.](#Issue_Fragmentation)  
  
-   [Wyrzucanie elementów kolekcji pauzy jest zbyt długa](#Issue_LongPauses)  
  
-   [Generacji 0 jest zbyt duży](#Issue_Gen0)  
  
-   [Użycie Procesora podczas wyrzucania elementów bezużytecznych jest zbyt wysoka](#Issue_HighCPU)  
  
<a name="Issue_OOM"></a>   
### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Problem: Zgłoszono wyjątek braku pamięci  
 Istnieją dwa uzasadnione przypadki dla zarządzanego <xref:System.OutOfMemoryException> zostanie wygenerowany:  
  
-   Zaczyna brakować pamięci wirtualnej.  
  
     Moduł zbierający elementy bezużyteczne przydziela pamięć z systemu w segmentach wstępnie ustalony rozmiar. Alokacja wymaga dodatkowych segmentu, ale nie nie ciągłego wolnego bloku pozostanie w obszarze pamięci wirtualnej procesu, alokacji sterty zarządzanej zakończy się niepowodzeniem.  
  
-   Nie ma wystarczającej ilości pamięci fizycznej do przydzielenia.  
  
|Testy wydajności|  
|------------------------|  
|[Ustal, czy jest zarządzany wyjątek braku pamięci.](#OOMIsManaged)<br /><br /> [Określ ilość pamięci wirtualnej może być zarezerwowana.](#GetVM)<br /><br /> [Ustal, czy jest wystarczająca ilość pamięci fizycznej.](#Physical)|  
  
 Jeśli okaże się, że wyjątku nie jest uzasadnione, skontaktuj się z pomocą Microsoft dział obsługi klienta i pomocy technicznej następujące informacje:  
  
-   Stos o zarządzanym wyjątku braku pamięci.  
  
-   Pełny zrzut pamięci.  
  
-   Dane, gdy okaże się, że nie jest uzasadnione wyjątku braku pamięci, włącznie z danymi, pokazujący pamięci, wirtualny lub fizyczny nie jest rozwiązaniem problemu.  
  
<a name="Issue_TooMuchMemory"></a>   
### <a name="issue-the-process-uses-too-much-memory"></a>Problem: Proces używa zbyt dużej ilości pamięci  
 Typowe zakłada się, że użycie pamięci wyświetlane na **wydajności** kartę Menedżera zadań systemu Windows można wskazać, kiedy używana jest zbyt dużej ilości pamięci. Jednakże które wyświetlają odnoszą się do zestawu roboczego; nie dostarcza informacje na temat użycia pamięci wirtualnej.  
  
 Jeśli okaże się, że przyczyną problemu jest sterty zarządzanej, musi pomiarów sterty zarządzanej w celu określenia wszelkich wzorce.  
  
 Jeśli okaże się, że problem nie jest spowodowany przez sterty zarządzanej, należy użyć debugowanie natywne.  
  
|Testy wydajności|  
|------------------------|  
|[Określ ilość pamięci wirtualnej może być zarezerwowana.](#GetVM)<br /><br /> [Określ, ile pamięci sterty zarządzanej zatwierdza.](#ManagedHeapCommit)<br /><br /> [Określ, ile pamięci sterty zarządzanej rezerwuje.](#ManagedHeapReserve)<br /><br /> [Określ dużych obiektów podczas generowania 2.](#ExamineGen2)<br /><br /> [Określ odwołania do obiektów.](#ObjRef)|  
  
<a name="Issue_NotFastEnough"></a>   
### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Problem: Moduł zbierający elementy bezużyteczne nie odzyskać obiektów tyle szybko  
 Wygląda na to, jak obiekty nie są odzyskane zgodnie z oczekiwaniami dotyczącymi wyrzucanie elementów bezużytecznych, należy ustalić, czy istnieją silne odwołań do tych obiektów.  
  
 Może również wystąpi ten problem, jeśli nie było żadnych wyrzucanie elementów bezużytecznych generacji, która zawiera obiekt martwy, co oznacza, że finalizatora dla obiekt martwy nie został uruchomiony. Na przykład jest to możliwe po uruchomieniu aplikacji jednowątkowego apartamentu (STA) i wątku tej usługi, których nie można wywołać w kolejce finalizatora do niego.  
  
|Testy wydajności|  
|------------------------|  
|[Sprawdź odwołania do obiektów.](#ObjRef)<br /><br /> [Ustal, czy finalizator został uruchomiony.](#Induce)<br /><br /> [Ustal, czy istnieją obiekty oczekujące na sfinalizowana.](#Finalize)|  
  
<a name="Issue_Fragmentation"></a>   
### <a name="issue-the-managed-heap-is-too-fragmented"></a>Problem: Zarządzane sterty jest zbyt pofragmentowana.  
 Poziom fragmentacji jest obliczana jako stosunek wolnego miejsca za pośrednictwem całkowitej ilości pamięci przydzielony do generowania. Generacji 2 akceptowalnego poziomu fragmentacji jest nie więcej niż 20%. Ponieważ generacji 2 można uzyskać bardzo duży stopień fragmentacji ma większe znaczenie niż wartość bezwzględna.  
  
 Mających duże ilości wolnego miejsca w generacji 0 nie jest problem, ponieważ jest generowanie gdzie nowe obiekty są przydzielone.  
  
 Fragmentacja zawsze występuje w sterty dużego obiektu, ponieważ nie jest skompaktować. Bezpłatne obiektów, które znajdują się obok siebie naturalnie są zwijane do jednego miejsca do spełnienia żądań alokacji dużego obiektu.  
  
 Fragmentacja może stać się problemem w generacji 1 i 2. Jeśli te generacje po wyrzucania elementów bezużytecznych znajduje się duża ilość wolnego miejsca, użycie obiektu aplikacji może wymagać modyfikacji i należy rozważyć ponownej oceny okresu istnienia obiektów długoterminowej.  
  
 Przypinanie nadmiernego obiektów można zwiększyć fragmentacji. Jeśli fragmentacji jest wysoka, można przypięty za dużo obiektów.  
  
 Jeśli fragmentacji pamięci wirtualnej uniemożliwia Dodawanie segmentów moduł garbage collector, przyczyn może być jedną z następujących czynności:  
  
-   Częste ładowanie i zwalnianie wiele małych zestawów.  
  
-   Zawierający zbyt wiele odwołań do obiektów COM, gdy współdziałanie z kodem niezarządzanym.  
  
-   Tworzenie dużych obiektów przejściowy, co powoduje, że sterty dużego obiektu można przydzielić i często bez sterty segmentów.  
  
     Gdy hostingu środowiska CLR, aplikacja może zażądać zachowanie modułu zbierającego elementy bezużyteczne jego segmentów. Pozwala to zmniejszyć częstotliwość alokacji segmentu. Jest to zrobić za pomocą flagi STARTUP_HOARD_GC_VM w [STARTUP_FLAGS — wyliczenie](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
|Testy wydajności|  
|------------------------|  
|[Określ ilość wolnego miejsca na stercie zarządzanej.](#Fragmented)<br /><br /> [Określ liczbę unieruchomionych obiektów.](#Pinned)|  
  
 Jeśli uważasz, że nie stanowi uzasadnionych fragmentacji, skontaktuj się z obsługi klienta firmy Microsoft.  
  
<a name="Issue_LongPauses"></a>   
### <a name="issue-garbage-collection-pauses-are-too-long"></a>Problem: Pauzy kolekcji pamięci jest zbyt długa  
 Wyrzucanie elementów bezużytecznych działa w czasie rzeczywistym miękkie, więc aplikacja musi mieć możliwość tolerować niektórych pauzy. Kryterium nietrwałego czasu rzeczywistego jest, że 95% operacji musi zostać zakończone na czas.  
  
 W współbieżne odzyskiwanie pamięci zarządzanych wątków mogą być uruchamiane podczas zbierania, co oznacza, że pauzy są minimalne.  
  
 Tylko kilka milisekund ostatni tymczasowych wyrzucania (generacji 0 i 1), więc zmniejszenie pauzy zwykle nie jest możliwe. Można jednak zmniejszyć pauzy w kolekcjach generacji 2, zmieniając wzorzec żądań alokacji przez aplikację.  
  
 Inny, bardziej precyzyjne metoda polega na użyciu [zdarzenia ETW wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md). Chronometraż dla kolekcji można znaleźć, dodając różnice sygnatury czasowe sekwencji zdarzeń. Sekwencja całą kolekcję obejmuje zawieszenie aparat wykonywania, wyrzucanie elementów bezużytecznych sam i wznowienie aparat wykonywania.  
  
 Można użyć [powiadomienia dotyczące odzyskiwania pamięci](../../../docs/standard/garbage-collection/notifications.md) można określić, czy serwer ma mieć kolekcji generacji 2 i określa, czy Przekierowanie żądania do innego serwera można zmniejszyć problemów z pauzy.  
  
|Testy wydajności|  
|------------------------|  
|[Określ czas w wyrzucania elementów bezużytecznych.](#TimeInGC)<br /><br /> [Określ, co spowodowało wyrzucania elementów bezużytecznych.](#Triggered)|  
  
<a name="Issue_Gen0"></a>   
### <a name="issue-generation-0-is-too-big"></a>Problem: Generacji 0 jest zbyt duży  
 Generowanie 0 jest mogą mieć większą liczbę obiektów w systemie 64-bitowym, szczególnie w przypadku odzyskiwanie pamięci na serwerze można użyć zamiast stacji roboczej wyrzucanie elementów bezużytecznych. To dlatego próg do wyzwolenia generacji 0 wyrzucania elementów bezużytecznych jest wyższy w tych środowiskach, a kolekcje generacji 0 mogą pobrać znacznie większe. Zwiększona wydajność aplikacji przydziela pamięć więcej wywoła wyrzucania elementów bezużytecznych.  
  
<a name="Issue_HighCPU"></a>   
### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Problem: Użycie Procesora podczas wyrzucania elementów bezużytecznych jest zbyt wysoka  
 Użycie procesora CPU będzie wysoka podczas wyrzucania elementów bezużytecznych. Jeśli znaczną ilość czasu procesu jest przeznaczony na wyrzucanie elementów bezużytecznych, liczby kolekcji jest zbyt częste lub kolekcji jest zbyt długo trwające. Wyrzucanie elementów bezużytecznych do częściej powoduje, że alokacji większa liczba obiektów na stercie zarządzanej. Zmniejsz częstotliwość przydzielania zmniejsza częstotliwość odzyskiwania pamięci.  
  
 Stawki alokacji można monitorować za pomocą `Allocated Bytes/second` licznika wydajności. Aby uzyskać więcej informacji, zobacz [liczników wydajności w programie .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
 Czas trwania kolekcji się głównie liczba obiektów, które pozostają aktualne po po alokacji. Moduł zbierający elementy bezużyteczne musi przechodzić przez dużą ilość pamięci, jeśli wiele obiektów mają być zbierane. Praca kompaktowania przy życiu jest czasochłonne. Aby ustalić, ile obiekty zostały obsłużone podczas zbierania, należy ustawić punkt przerwania w debugerze po zakończeniu wyrzucania elementów bezużytecznych dla określonej generacji.  
  
|Testy wydajności|  
|------------------------|  
|[Ustal, jeśli przyczyną wysokiego użycia procesora CPU jest wyrzucanie elementów bezużytecznych.](#HighCPU)<br /><br /> [Ustaw punkt przerwania po zakończeniu wyrzucania elementów bezużytecznych.](#GenBreak)|  
  
 [Powrót do początku](#top)  
  
<a name="troubleshooting_guidelines"></a>   
## <a name="troubleshooting-guidelines"></a>Wskazówki dotyczące rozwiązywania problemów  
 W tej sekcji opisano wskazówki, które należy wziąć pod uwagę rozpoczęciem badań sieci.  
  
### <a name="workstation-or-server-garbage-collection"></a>Stacji roboczej lub serwera wyrzucanie elementów bezużytecznych  
 Określają, czy używasz poprawnego typu wyrzucanie elementów bezużytecznych. Jeśli aplikacja używa wielu wątków i wystąpienia obiektów, użyj odzyskiwanie pamięci na serwerze zamiast stacji roboczej wyrzucanie elementów bezużytecznych. Odzyskiwanie pamięci na serwerze działa na wielu wątków stacji roboczej wyrzucanie elementów bezużytecznych wymaga wiele wystąpień aplikacji do ich własnych wątków kolekcji pamięci i konkurują o czas procesora CPU.  
  
 Aplikacja z niskim obciążeniu, rzadko w tle, na przykład usługi, która wykonuje zadania może użyć stacji roboczej wyrzucanie elementów bezużytecznych z współbieżne odzyskiwanie pamięci wyłączone.  
  
### <a name="when-to-measure-the-managed-heap-size"></a>Kiedy do mierzenia rozmiaru sterty zarządzanej  
 Jeśli nie używasz profilera, będzie musiał utworzyć spójne wzorzec pomiaru skutecznie zdiagnozować problemy z wydajnością. Należy rozważyć następujące kwestie do ustanawiania harmonogramu:  
  
-   Jeśli mierzonych po wyrzucania elementów bezużytecznych generacji 2 całego sterty zarządzanej będzie bezpłatna pamięci (martwy obiektów).  
  
-   Jeśli mierzonych natychmiast po wyrzucania elementów bezużytecznych generacji 0 obiektów pokolenia 1 i 2 nie będą zbierane jeszcze.  
  
-   Jeśli mierzonych bezpośrednio przed wyrzucania elementów bezużytecznych będzie zmierzyć tyle alokacji, jak to możliwe, przed rozpoczęciem wyrzucanie elementów bezużytecznych.  
  
-   Pomiaru podczas wyrzucania elementów bezużytecznych jest powodować problemów, ponieważ moduł zbierający elementy bezużyteczne struktur danych nie znajdują się w nieprawidłowym stanie dla operacji przechodzenia i nie można udzielić, wyświetlenie pełnych wyników. To jest celowe.  
  
-   Używając stacji roboczej wyrzucanie elementów bezużytecznych z współbieżne odzyskiwanie pamięci, regeneracji obiekty nie są kompaktowanie, dlatego rozmiar stosu może być taka sama lub większa (fragmentacja można wydawać będzie większy).  
  
-   Współbieżne odzyskiwanie pamięci na generacji 2 jest opóźnione, gdy zbyt duże obciążenie pamięci fizycznej.  
  
 W poniższej procedurze opisano, jak ustawić punkt przerwania, dzięki czemu można zmierzyć sterty zarządzanej.  
  
<a name="GenBreak"></a>   
##### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Aby ustawić punkt przerwania po zakończeniu wyrzucania elementów bezużytecznych  
  
-   W WinDbg z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:  
  
     **BP mscorwks! WKS::GCHeap::RestartEE "j (dwo (mscorwks! WKS::GCHeap::GcCondemnedGeneration) == 2) "kb"; " g ""**  
  
     gdzie **GcCondemnedGeneration** ma ustawioną wartość odpowiednią generacji. To polecenie wymaga symboli prywatnych.  
  
     To polecenie wymusza podziału, jeśli **RestartEE** jest wykonywana po odzyskano obiektów pokolenia 2 dla wyrzucanie elementów bezużytecznych.  
  
     W pamięci serwera, wymaga tylko jednego wątku **RestartEE**, więc punkt przerwania zostanie przeprowadzona tylko raz podczas generowania 2 wyrzucania elementów bezużytecznych.  
  
 [Powrót do początku](#top)  
  
<a name="performance_check_procedures"></a>   
## <a name="performance-check-procedures"></a>Procedury sprawdzania wydajności  
 W tej sekcji opisano następujące procedury, aby ustalić przyczynę problemu z wydajnością:  
  
-   [Ustal, czy przyczyną problemu jest wyrzucanie elementów bezużytecznych.](#IsGC)  
  
-   [Ustal, czy jest zarządzany wyjątek braku pamięci.](#OOMIsManaged)  
  
-   [Określ ilość pamięci wirtualnej może być zarezerwowana.](#GetVM)  
  
-   [Ustal, czy jest wystarczająca ilość pamięci fizycznej.](#Physical)  
  
-   [Określ, ile pamięci sterty zarządzanej zatwierdza.](#ManagedHeapCommit)  
  
-   [Określ, ile pamięci sterty zarządzanej rezerwuje.](#ManagedHeapReserve)  
  
-   [Określ dużych obiektów podczas generowania 2.](#ExamineGen2)  
  
-   [Określ odwołania do obiektów.](#ObjRef)  
  
-   [Ustal, czy finalizator został uruchomiony.](#Induce)  
  
-   [Ustal, czy istnieją obiekty oczekujące na sfinalizowana.](#Finalize)  
  
-   [Określ ilość wolnego miejsca na stercie zarządzanej.](#Fragmented)  
  
-   [Określ liczbę unieruchomionych obiektów.](#Pinned)  
  
-   [Określ czas w wyrzucania elementów bezużytecznych.](#TimeInGC)  
  
-   [Określ, co wyzwoliło wyrzucania elementów bezużytecznych.](#Triggered)  
  
-   [Ustal, czy przyczyną wysokiego użycia procesora CPU jest wyrzucanie elementów bezużytecznych.](#HighCPU)  
  
<a name="IsGC"></a>   
##### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Aby określić, czy przyczyną problemu jest wyrzucanie elementów bezużytecznych  
  
-   Sprawdź następujące liczniki wydajności pamięci dwóch:  
  
    -   **% Czasu potrzebnego na Odzyskiwanie**. Wyświetla procent minionego czasu, jaki był poświęcony na operację wyrzucania od ostatniego cyklu wyrzucania elementów w kolekcji. Ten licznik umożliwia określenie, czy moduł zbierający elementy bezużyteczne zużywa zbyt dużo czasu, aby udostępnić miejsce na stercie zarządzanej. Jeśli czas spędzony w pamięci jest stosunkowo niska, który może wskazywać na problem zasobów poza sterty zarządzanej. Ten licznik nie może być niedokładna, gdy są one jednoczesnych lub uczestniczy odzyskiwanie pamięci w tle.  
  
    -   **# Całkowita liczba Zadeklarowane bajty**. Wyświetlana jest ilość pamięci wirtualnej zarezerwowanej aktualnie przez moduł garbage collector. Ten licznik umożliwia określenie, czy pamięci używane przez moduł garbage collector jest nadmierne część pamięci, która korzysta z aplikacji.  
  
     Większość liczników wydajności pamięci jest aktualizowany po zakończeniu każdej operacji wyrzucania elementów bezużytecznych. W związku z tym nie mogą one uwzględniać bieżącego warunki, które chcesz uzyskać informacje.  
  
<a name="OOMIsManaged"></a>   
##### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Aby określić, czy wyjątek braku pamięci jest zarządzany  
  
1.  W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadować typu wyjątku wydruku (**pe**) polecenia:  
  
     **! pe**  
  
     Jeśli wyjątek jest zarządzany, <xref:System.OutOfMemoryException> jest wyświetlana jako typ wyjątku, jak pokazano w poniższym przykładzie.  
  
    ```  
    Exception object: 39594518  
    Exception type: System.OutOfMemoryException  
    Message: <none>  
    InnerException: <none>  
    StackTrace (generated):  
    ```  
  
2.  Dane wyjściowe nie określony wyjątek, należy ustalić, który wątek wyjątku braku pamięci jest z. Wpisz następujące polecenie w debugerze, aby wyświetlić wszystkie wątki z ich stosy wywołań:  
  
     **~\*KB**  
  
     Wątek ze stosu, który ma wywołań wyjątków jest określane przez `RaiseTheException` argumentu. To jest obiektem zarządzanym wyjątku.  
  
    ```  
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0   
    ```  
  
3.  Następujące polecenie służy do zrzutu wyjątków zagnieżdżonych.  
  
     **! pe-zagnieżdżonych**  
  
     Jeśli nie znajdziesz żadnych wyjątków, wyjątek braku pamięci pochodzi z kodem niezarządzanym.  
  
<a name="GetVM"></a>   
##### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Aby określić ilość pamięci wirtualnej może być zarezerwowana.  
  
-   W WinDbg z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie, aby pobrać największego wolnego regionu:  
  
     **! adresów — podsumowanie**  
  
     Największego wolnego regionu jest wyświetlana, jak pokazano w następujących danych wyjściowych.  
  
    ```  
    Largest free region: Base 54000000 - Size 0003A980  
    ```  
  
     W tym przykładzie rozmiar największego wolnego obszaru to około 24000 KB (3A980 w formacie szesnastkowym). Ten region jest znacznie mniejszy niż moduł zbierający elementy bezużyteczne wymagań segment.  
  
     —lub—  
  
-   Użyj **vmstat** polecenia:  
  
     **! vmstat**  
  
     Największego wolnego regionu jest największą wartość w kolumnie maksymalna, jak pokazano w następujących danych wyjściowych.  
  
    ```  
    TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL  
    ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~  
    Free:  
    Small       8K        64K         46K       36          1,671K  
    Medium      80K       864K        349K      3           1,047K  
    Large       1,384K    1,278,848K  151,834K  12          1,822,015K  
    Summary     8K        1,278,848K  35,779K   51          1,824,735K  
    ```  
  
<a name="Physical"></a>   
##### <a name="to-determine-whether-there-is-enough-physical-memory"></a>Aby ustalić, czy jest wystarczająca ilość fizycznej pamięci  
  
1.  Uruchom Menedżera zadań systemu Windows.  
  
2.  Na **wydajności** pozycję przyjrzeć się wartość zatwierdzone. (W systemie Windows 7, obejrzyj **zatwierdzić (KB)** w **grupy systemu**.)  
  
     Jeśli **całkowita** jest blisko **Limit**, możesz zaczyna brakować pamięci fizycznej.  
  
<a name="ManagedHeapCommit"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Aby określić, ile pamięci zatwierdza sterty zarządzanej  
  
-   Użyj `# Total committed bytes` licznika wydajności pamięci, aby uzyskać liczbę bajtów, które zatwierdza sterty zarządzanej. Moduł zbierający elementy bezużyteczne przekazuje fragmentów w segmencie, zgodnie z potrzebami, nie wszystkie w tym samym czasie.  
  
    > [!NOTE]
    >  Nie używaj `# Bytes in all Heaps` licznika wydajności, ponieważ nie reprezentuje aktualnego stanu użycia pamięci przez sterty zarządzanej. Rozmiar generacji znajduje się w tej wartości i jest rzeczywiście jego rozmiar progu, oznacza to, rozmiar, który wywołuje wyrzucania elementów bezużytecznych, jeśli Generowanie jest wypełniony obiektów. W związku z tym ta wartość jest zazwyczaj zero.  
  
<a name="ManagedHeapReserve"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Aby określić, ile pamięci rezerwuje sterty zarządzanej  
  
-   Użyj `# Total reserved bytes` licznika wydajności pamięci.  
  
     Moduł zbierający elementy bezużyteczne zastrzega pamięć w segmentach i można określić, gdzie segment uruchamia się za pomocą **eeheap** polecenia.  
  
    > [!IMPORTANT]
    >  Mimo że możesz określić ilość pamięci przez moduł garbage collector przydziela dla każdego segmentu, rozmiar segmentu jest konkretnej implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowych aktualizacji. Aplikacji nigdy nie może dokonać założeń dotyczących lub zależą od rozmiaru określonego segmentu nie powinny podejmować próby skonfiguruj ilość pamięci dostępnej dla segmentu alokacji.  
  
-   W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:  
  
     **! eeheap -gc**  
  
     Wynik ma następującą składnię.  
  
    ```  
    Number of GC Heaps: 2  
    ------------------------------  
    Heap 0 (002db550)  
    generation 0 starts at 0x02abe29c  
    generation 1 starts at 0x02abdd08  
    generation 2 starts at 0x02ab0038  
    ephemeral segment allocation context: none  
     segment    begin allocated     size  
    02ab0000 02ab0038  02aceff4 0x0001efbc(126908)  
    Large object heap starts at 0x0aab0038  
     segment    begin allocated     size  
    0aab0000 0aab0038  0aab2278 0x00002240(8768)  
    Heap Size   0x211fc(135676)  
    ------------------------------  
    Heap 1 (002dc958)  
    generation 0 starts at 0x06ab1bd8  
    generation 1 starts at 0x06ab1bcc  
    generation 2 starts at 0x06ab0038  
    ephemeral segment allocation context: none  
     segment    begin allocated     size  
    06ab0000 06ab0038  06ab3be4 0x00003bac(15276)  
    Large object heap starts at 0x0cab0038  
     segment    begin allocated     size  
    0cab0000 0cab0038  0cab0048 0x00000010(16)  
    Heap Size    0x3bbc(15292)  
    ------------------------------  
    GC Heap Size   0x24db8(150968)  
    ```  
  
     Adresy wskazywanym przez "segmentu" adresów początkowy segmentów.  
  
<a name="ExamineGen2"></a>   
##### <a name="to-determine-large-objects-in-generation-2"></a>W celu ustalenia, duże obiekty generacji 2  
  
-   W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:  
  
     **! dumpheap — stan**  
  
     Jeśli sterty zarządzanej jest duży, **dumpheap** może zająć trochę czasu, aby zakończyć.  
  
     Analizowanie danych w ciągu ostatnich kilku wierszy danych wyjściowych, można uruchomić, ponieważ ich listy obiektów, które najwięcej miejsca. Na przykład:  
  
    ```  
    2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo  
    00155f80      533     15216804      Free  
    7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary  
    2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo  
    79124228   121143     29064120 System.Object[]  
    035f0ee4    81626     35588936 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    791242ec    40182     90664128 System.Collections.Hashtable+bucket[]  
    790fa3e0  3154024    137881448 System.String  
    Total 8454945 objects  
    ```  
  
     Ostatni obiekt na liście jest ciągiem i zajmuje najwięcej miejsca. Można sprawdzić w aplikacji, aby zobaczyć, jak mogą być optymalizowane obiektów w postaci ciągów. Aby wyświetlić ciągów, które należą do zakresu od 150 do 200 bajtów, wpisz następujące polecenie:  
  
     **! dumpheap — wpisz 150 - max -min System.String 200**  
  
     Przykład wyników ma następującą składnię.  
  
    ```  
    Address  MT           Size  Gen  
    1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11  
    …  
    ```  
  
     Może być skuteczniejsza za pomocą całkowitą zamiast ciągu dla Identyfikatora. Jeśli ten sam ciąg jest zajdą tysięcy razy, należy wziąć pod uwagę interning ciągu. Aby uzyskać więcej informacji na temat interning ciągu, zobacz temat informacje dla <xref:System.String.Intern%2A?displayProperty=nameWithType> metody.  
  
<a name="ObjRef"></a>   
##### <a name="to-determine-references-to-objects"></a>Aby określić odwołania do obiektów  
  
-   W WinDbg z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie, aby listy odwołania do obiektów:  
  
     **! gcroot**  
  
     `-or-`  
  
-   Aby określić odwołania dla konkretnego obiektu, należy uwzględnić adres:  
  
     **! gcroot 1c37b2ac**  
  
     Certyfikaty główne na stosy może być fałszywych alarmów. Aby uzyskać więcej informacji, użyj polecenia `!help gcroot`.  
  
    ```  
    ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->  
    19010b78(DemoApp.FormDemoApp)->  
    19011158(System.Windows.Forms.PropertyStore)->  
    … [omitted]  
    1c3745ec(System.Data.DataTable)->  
    1c3747a8(System.Data.DataColumnCollection)->  
    1c3747f8(System.Collections.Hashtable)->  
    1c376590(System.Collections.Hashtable+bucket[])->  
    1c376c98(System.Data.DataColumn)->  
    1c37b270(System.Data.Common.DoubleStorage)->  
    1c37b2ac(System.Double[])  
    Scan Thread 0 OSTHread 99c  
    Scan Thread 6 OSTHread 484  
    ```  
  
     **Gcroot** polecenia może zająć dużo czasu, aby zakończyć. Każdy obiekt, który nie jest odzyskana przez odzyskiwanie pamięci jest obiektem na żywo. Oznacza to, że niektóre główny jest bezpośrednio lub pośrednio zawierający na obiekt, więc **gcroot** powinny zostać zwrócone informacje ścieżki do obiektu. Należy sprawdzić wykresy zwrócił i zobacz, dlaczego te obiekty są nadal odwołuje się do.  
  
<a name="Induce"></a>   
##### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Aby określić, czy przeprowadzono finalizator  
  
-   Uruchom program test, który zawiera następujący kod:  
  
    ```  
    GC.Collect();  
    GC.WaitForPendingFinalizers();  
    GC.Collect();  
    ```  
  
     Jeśli test zostanie rozwiązany, oznacza to, że moduł zbierający elementy bezużyteczne nie został odzyskiwanie obiektów, ponieważ została wstrzymana finalizatory dla tych obiektów. <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Metody umożliwia finalizatory do wykonywania swoich zadań i rozwiązuje problem.  
  
<a name="Finalize"></a>   
##### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Aby określić, czy istnieją obiekty oczekujące na sfinalizowana  
  
1.  W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:  
  
     **! finalizequeue**  
  
     Sprawdź liczbę obiektów, które są gotowe do finalizacji. Jeśli liczba jest wysokie, należy zbadać dlaczego te finalizatory nie postępu na wszystkich lub nie postępu szybkiego wystarczająco.  
  
2.  Aby uzyskać dane wyjściowe wątków, wpisz następujące polecenie:  
  
     **wątki — specjalne**  
  
     To polecenie dostarcza dane wyjściowe podobne do poniższych.  
  
    ```  
       OSID     Special thread type  
    2    cd0    DbgHelper   
    3    c18    Finalizer   
    4    df0    GC SuspendEE   
    ```  
  
     Wątek finalizatora wskazuje, które finalizator, jeśli istnieje, jest aktualnie uruchomione. Kiedy wątku finalizatora nie jest uruchomiona żadnych finalizatory, oczekuje na zdarzenia, aby wykonać swoją pracę. W większości przypadków zobaczysz wątku finalizatora w tym stanie ponieważ powinien na zakończenie działania finalizatory, jeśli taki występuje i jest uruchamiane w THREAD_HIGHEST_PRIORITY bardzo szybko.  
  
<a name="Fragmented"></a>   
##### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Aby określić ilość wolnego miejsca na stercie zarządzanej  
  
-   W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:  
  
     **! dumpheap — wpisz bezpłatne — stan**  
  
     To polecenie wyświetla całkowity rozmiar wszystkich obiektów wolnego na stercie zarządzanej, jak pokazano w poniższym przykładzie.  
  
    ```  
    total 230 objects  
    Statistics:  
          MT    Count    TotalSize Class Name  
    00152b18      230     40958584      Free  
    Total 230 objects  
    ```  
  
-   Aby określić ilość wolnego miejsca podczas generowania 0, wpisz następujące polecenie dla informacji o użyciu pamięci przez generowanie:  
  
     **! eeheap -gc**  
  
     To polecenie wyświetla dane wyjściowe podobne do następującego. Ostatni wiersz zawiera tymczasowych segmentu.  
  
    ```  
    Heap 0 (0015ad08)  
    generation 0 starts at 0x49521f8c  
    generation 1 starts at 0x494d7f64  
    generation 2 starts at 0x007f0038  
    ephemeral segment allocation context: none  
    segment  begin     allocated  size  
    00178250 7a80d84c  7a82f1cc   0x00021980(137600)  
    00161918 78c50e40  78c7056c   0x0001f72c(128812)  
    007f0000 007f0038  047eed28   0x03ffecf0(67103984)  
    3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)  
    46120000 46120038  49e05d04   0x03ce5ccc(63855820)  
    ```  
  
-   Obliczyć miejsca na dysku używane przez generacji 0:  
  
     **? 49e05d04 0x49521f8c**  
  
     Wynik ma następującą składnię. Generacji 0 to około 9 MB.  
  
    ```  
    Evaluate expression: 9321848 = 008e3d78  
    ```  
  
-   Polecenie zrzuty ilość wolnego miejsca w zakresie generacji 0:  
  
     **! dumpheap-bezpłatne — wpisz 49e05d04 stat 0x49521f8c**  
  
     Wynik ma następującą składnię.  
  
    ```  
    ------------------------------  
    Heap 0  
    total 409 objects  
    ------------------------------  
    Heap 1  
    total 0 objects  
    ------------------------------  
    Heap 2  
    total 0 objects  
    ------------------------------  
    Heap 3  
    total 0 objects  
    ------------------------------  
    total 409 objects  
    Statistics:  
          MT    Count TotalSize Class Name  
    0015a498      409   7296540      Free  
    Total 409 objects  
    ```  
  
     Te dane wyjściowe pokazuje, że część sterty pokolenia 0 za pomocą 9 MB miejsca dla obiektów i ma 7 MB wolnego. Analiza wskazuje zakres generacji 0 przyczynia się do fragmentacji. Ilość użycia sterty powinien rabatem niż suma jako przyczyna fragmentacji przez obiekty długoterminowej.  
  
<a name="Pinned"></a>   
##### <a name="to-determine-the-number-of-pinned-objects"></a>Aby określić liczbę unieruchomionych obiektów  
  
-   W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie:  
  
     **! związane**  
  
     Statystyki, wyświetlane obejmuje liczby dojść przypiętych, jak w poniższym przykładzie pokazano.  
  
    ```  
    GC Handle Statistics:  
    Strong Handles:      29  
    Pinned Handles:      10  
    ```  
  
<a name="TimeInGC"></a>   
##### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>Aby określić czas w wyrzucania elementów bezużytecznych  
  
-   Sprawdź `% Time in GC` licznika wydajności pamięci.  
  
     Wartość jest obliczana przy użyciu interwałów próbkowania. Ponieważ liczniki jest aktualizowany po zakończeniu każdej operacji wyrzucania elementów bezużytecznych, bieżący próbki ma taką samą wartość jak poprzedni przykład, jeśli żadne kolekcje wystąpił w interwale.  
  
     Czas zbierania mnożąc interwałów próbkowania o wartości procentowej.  
  
     Następujące dane zawiera cztery interwałami próbkowania dwóch sekund, badanie 8 sekundy. `Gen0`, `Gen1`, I `Gen2` kolumny zawierają liczbę wyrzucania, które wystąpiły podczas tego interwału dla tej generacji.  
  
    ```  
    Interval    Gen0    Gen1    Gen2    % Time in GC  
           1       9       3       1              10  
           2      10       3       1               1  
           3      11       3       1               3  
           4      11       3       1               3  
    ```  
  
     Te informacje nie są wyświetlane, gdy wystąpił wyrzucanie elementów bezużytecznych, ale można określić liczbę wyrzucania, które wystąpiły w odstępach czasu. Zakładając, że najgorszego, dziesiątego bezużytecznych generacji 0 zakończono na początku Drugi interwał i jedenastego bezużytecznych generacji 0 zakończono na końcu piątej interwału. Czas między koniec dziesiątego i na końcu jedenastego wyrzucanie elementów bezużytecznych jest około 2 sekundy, i licznik wydajności przedstawia 3%, więc trwało jedenastego wyrzucanie elementów bezużytecznych generacji 0 (% s 2 * 3 = 60ms).  
  
     W tym przykładzie są 5 okresów.  
  
    ```  
    Interval    Gen0    Gen1    Gen2     % Time in GC  
           1       9       3       1                3  
           2      10       3       1                1  
           3      11       4       2                1  
           4      11       4       2                1  
           5      11       4       2               20  
    ```  
  
     Drugiej generacji 2 wyrzucanie elementów bezużytecznych rozpoczęcia interwale trzeci i zakończenia w piątym odstępach czasu. Zakładając, że najgorszego, ostatni wyrzucanie elementów bezużytecznych był zakończenia na początku Drugi interwał kolekcji generacji 0, a generacji 2 wyrzucanie elementów bezużytecznych Zakończono na końcu piątej interwał. W związku z tym czas od zakończenia operacji wyrzucania elementów bezużytecznych generacji 0 i na końcu wyrzucanie elementów bezużytecznych generacji 2 jest 4 sekundy. Ponieważ `% Time in GC` licznika wynosi 20%, maksymalną ilość czasu generowania można miały 2 wyrzucanie elementów bezużytecznych (4 sekundy * 20% = 800ms).  
  
-   Alternatywnie można określić długości wyrzucania elementów bezużytecznych przy użyciu [zdarzenia ETW wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md)i analizowania informacji, aby określić czas trwania operacji wyrzucania elementów bezużytecznych.  
  
     Na przykład następujące dane przedstawiono sekwencję zdarzeń, który wystąpił podczas niewspółbieżnego wyrzucania elementów bezużytecznych.  
  
    ```  
    Timestamp    Event name  
    513052        GCSuspendEEBegin_V1  
    513078        GCSuspendEEEnd  
    513090        GCStart_V1  
    517890        GCEnd_V1  
    517894        GCHeapStats  
    517897        GCRestartEEBegin  
    517918        GCRestartEEEnd  
    ```  
  
     Zawieszanie wątków zarządzanych trwało 26us (`GCSuspendEEEnd` — `GCSuspendEEBegin_V1`).  
  
     Rzeczywiste wyrzucanie elementów bezużytecznych trwało 4.8ms (`GCEnd_V1` — `GCStart_V1`).  
  
     Wznawianie wątków zarządzanych trwało 21us (`GCRestartEEEnd` — `GCRestartEEBegin`).  
  
     Następujące dane wyjściowe zawiera przykład odzyskiwanie pamięci w tle, a obejmują procesu, wątku i pola zdarzeń. (Nie wszystkie dane są wyświetlane).  
  
    ```  
    timestamp(us)    event name            process    thread    event field  
    42504385        GCSuspendEEBegin_V1    Test.exe    4372             1  
    42504648        GCSuspendEEEnd         Test.exe    4372          
    42504816        GCStart_V1             Test.exe    4372        102019  
    42504907        GCStart_V1             Test.exe    4372        102020  
    42514170        GCEnd_V1               Test.exe    4372          
    42514204        GCHeapStats            Test.exe    4372        102020  
    42832052        GCRestartEEBegin       Test.exe    4372          
    42832136        GCRestartEEEnd         Test.exe    4372          
    63685394        GCSuspendEEBegin_V1    Test.exe    4744             6  
    63686347        GCSuspendEEEnd         Test.exe    4744          
    63784294        GCRestartEEBegin       Test.exe    4744          
    63784407        GCRestartEEEnd         Test.exe    4744          
    89931423        GCEnd_V1               Test.exe    4372        102019  
    89931464        GCHeapStats            Test.exe    4372          
    ```  
  
     `GCStart_V1` Zdarzenia przy 42504816 wskazuje, że jest Odzyskiwanie pamięci w tle, ponieważ ostatnie pole `1`. Staje się on wyrzucanie elementów bezużytecznych przycisk nie. 102019.  
  
     `GCStart` Wystąpi zdarzenie, ponieważ nie istnieje potrzeba tymczasowych wyrzucanie elementów bezużytecznych przed rozpoczęciem odzyskiwanie pamięci w tle. Staje się on wyrzucanie elementów bezużytecznych przycisk nie. 102020.  
  
     W 42514170, wyrzucanie elementów bezużytecznych nie. Zakończenie 102020. Zarządzane wątki są ponownie uruchamiane w tym momencie. To pole jest wypełniane w wątku 4372, która wywołała to odzyskiwanie pamięci w tle.  
  
     W wątku 4744 zawieszenia występuje. Jest to tylko czas, w którym odzyskiwanie pamięci w tle musi wstrzymać wątków zarządzanych. Ten czas trwania to około 99ms ((63784407-63685394)/1000).  
  
     `GCEnd` Jest zdarzenie dla tła wyrzucanie elementów bezużytecznych w 89931423. Oznacza to, że tło wyrzucanie elementów bezużytecznych trwała o 47seconds ((89931423-42504816)/1000).  
  
     Uruchomionej zarządzane wątki widać dowolną liczbę tymczasowych wyrzucania wystąpienia.  
  
<a name="Triggered"></a>   
##### <a name="to-determine-what-triggered-a-garbage-collection"></a>Aby określić, co wyzwoliło wyrzucania elementów bezużytecznych  
  
-   W debugerze WinDbg lub Visual Studio z rozszerzeniem debugera SOS załadowany wpisz następujące polecenie, aby wyświetlić wszystkie wątki z ich stosy wywołań:  
  
     **~\*KB**  
  
     To polecenie wyświetla dane wyjściowe podobne do następującego.  
  
    ```  
    0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect   
    0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4  
    0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48  
    ```  
  
     Wyrzucanie elementów bezużytecznych spowodowane przez powiadomienie o małej ilości pamięci systemu operacyjnego, stos wywołań jest podobny, z wyjątkiem tego, że wątek znajduje się wątek finalizatora. Wątek finalizatora pobiera wiadomość z powiadomieniem asynchroniczne małej ilości pamięci i wywołuje wyrzucanie elementów bezużytecznych.  
  
     Jeśli wyrzucanie elementów bezużytecznych spowodowane przez alokacji pamięci stosu wygląda następująco:  
  
    ```  
    0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration  
    0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1  
    0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18  
    0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b  
    0012f310 7a02ae4c mscorwks!Alloc+0x60  
    0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd  
    0012f424 300027f4 mscorwks!JIT_NewArr1+0x148  
    000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c  
    0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153  
    ```  
  
     Pomocnik just in time (`JIT_New*`) wywołuje na końcu `GCHeap::GarbageCollectGeneration`. Jeśli okaże się wyrzucania generacji 2 są spowodowane alokacji, należy określić obiekty, które mają być zbierane przez generacji 2 wyrzucania elementów bezużytecznych i sposobu ich uniknięcie. Oznacza to, że chcesz obliczenia różnicy między początkową i końcową generacji 2 wyrzucania elementów bezużytecznych i obiekty, które spowodowało kolekcji generacji 2.  
  
     Na przykład wpisz następujące polecenie w debugerze umożliwiające wyświetlanie na początku kolekcji generacji 2:  
  
     **! dumpheap — stan**  
  
     Przykład danych wyjściowych (skróconej informacji wyświetlenie obiektów, które używają najwięcej miejsca):  
  
    ```  
    79124228    31857      9862328 System.Object[]  
    035f0384    25668     11601936 Toolkit.TlkPosition  
    00155f80    21248     12256296      Free  
    79103b6c   297003     13068132 System.Threading.ReaderWriterLock  
    7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary  
    7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary  
    035f0ee4    89192     38887712 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    7912c444    91616     71887080 System.Double[]  
    791242ec    32451     82462728 System.Collections.Hashtable+bucket[]  
    790fa3e0  2459154    112128436 System.String  
    Total 6471774 objects  
    ```  
  
     Powtórz polecenie na końcu generacji 2:  
  
     **! dumpheap — stan**  
  
     Przykład danych wyjściowych (skróconej informacji wyświetlenie obiektów, które używają najwięcej miejsca):  
  
    ```  
    79124228    26648      9314256 System.Object[]  
    035f0384    25668     11601936 Toolkit.TlkPosition  
    79103b6c   296770     13057880 System.Threading.ReaderWriterLock  
    7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary  
    7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary  
    00155f80    13806     34007212      Free  
    035f0ee4    89187     38885532 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    791242ec    32370     82359768 System.Collections.Hashtable+bucket[]  
    790fa3e0  2440020    111341808 System.String  
    Total 6417525 objects  
    ```  
  
     `double[]` Obiektów zniknęła na końcu danych wyjściowych, co oznacza, że zostały zebrane. Obiekty te konta do około 70 MB. Pozostałe obiekty nie został zmieniony znacznie. W związku z tym te `double[]` obiekty zostały Przyczyna przyczynę wystąpienia tej generacji 2 wyrzucanie elementów bezużytecznych. Następnym krokiem jest ustalenie, dlaczego `double[]` obiekty są dostępne i dlaczego ich zostało przerwane. Można skontaktuj się z deweloperem kodu, w którym pochodzeniu tych obiektów, lub skorzystać z **gcroot** polecenia.  
  
<a name="HighCPU"></a>   
##### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Aby określić, czy przyczyną wysokiego użycia procesora CPU jest wyrzucanie elementów bezużytecznych  
  
-   Korelowanie `% Time in GC` wartość licznika wydajności pamięci w czasie procesu.  
  
     Jeśli `% Time in GC` wartość wzrósł w tym samym czasie jako czas przetwarzania, wyrzucanie elementów bezużytecznych jest przyczyną wysokiego użycia procesora CPU. W przeciwnym razie profilu aplikacji można znaleźć, gdzie występuje wysokiego użycia.  
  
## <a name="see-also"></a>Zobacz też  
 [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
