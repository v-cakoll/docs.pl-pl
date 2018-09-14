---
title: Odzyskiwanie pamięci i wydajność
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69a11e99966467de005ab92d3dcdebaa70bbdbe4
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529853"
---
# <a name="garbage-collection-and-performance"></a>Odzyskiwanie pamięci i wydajność
<a name="top"></a> W tym temacie opisano problemy związane z wyrzucania elementów kolekcji oraz użycia pamięci. Ona rozwiązuje problemy, które odnoszą się do zarządzanej sterty i wyjaśnia, jak można zminimalizować wpływ wyrzucania elementów bezużytecznych na swoich aplikacjach. Każde wydanie zawiera łącza do procedur służących do badania problemów.  
  
 Ten temat zawiera następujące sekcje:  
  
-   [Narzędzia do analizy wydajności](#performance_analysis_tools)  
  
-   [Rozwiązywanie problemów z wydajnością](#troubleshooting_performance_issues)  
  
-   [Wskazówki dotyczące rozwiązywania problemów](#troubleshooting_guidelines)  
  
-   [Procedury wyboru wydajności](#performance_check_procedures)  
  
<a name="performance_analysis_tools"></a>   
## <a name="performance-analysis-tools"></a>Narzędzia do analizy wydajności  
 W poniższych sekcjach opisano narzędzia, które są dostępne do badania problemów kolekcji użycia i odzyskiwanie pamięci. [Procedury](#performance_check_procedures) podane w dalszej części tego tematu odnoszą się do tych narzędzi.  
  
<a name="perf_counters"></a>   
### <a name="memory-performance-counters"></a>Liczniki wydajności pamięci  
 Można użyć liczników wydajności do zbierania danych wydajności. Aby uzyskać instrukcje, zobacz [profilowanie środowiska uruchomieniowego](../../../docs/framework/debug-trace-profile/runtime-profiling.md). Pamięć .NET CLR kategorii liczników wydajności, zgodnie z opisem w [liczników wydajności w .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), zawiera informacje dotyczące modułu odśmiecania pamięci.  
  
<a name="sos"></a>   
### <a name="debugging-with-sos"></a>Debugowanie za pomocą SOS  
 Możesz użyć [debuger Windows (WinDbg)](/windows-hardware/drivers/debugger/index) do inspekcji obiektów w zarządzanym stosie.
 
 Aby zainstalować WinDbg, należy zainstalować debugowania Tools for Windows z [Pobierz debugowania narzędzi dla Windows](/windows-hardware/drivers/debugger/debugger-download-tools) strony.
  
<a name="etw"></a>   
### <a name="garbage-collection-etw-events"></a>Zdarzenia ETW odzyskiwania pamięci  
 Śledzenie zdarzeń dla Windows (ETW) to system śledzenia, który uzupełnia profilowania i pomoc techniczna jest świadczona przez program .NET Framework — profilowanie. Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], [zdarzenia ETW odzyskiwania pamięci](../../../docs/framework/performance/garbage-collection-etw-events.md) przechwytywać informacje przydatne do analizowania sterty zarządzanej z punktu widzenia statystycznych. Na przykład `GCStart_V1` zdarzenie, które jest wywoływane, gdy ma wystąpić wyrzucanie elementów bezużytecznych, zawiera następujące informacje:  
  
-   Które generacji obiektów są zbierane.  
  
-   Przyczyny ich wyzwolenia wyrzucania elementów bezużytecznych.  
  
-   Typ wyrzucania elementów bezużytecznych (współbieżnych lub nie współbieżnych).  
  
 Rejestrowanie zdarzeń ETW jest wydajny i nie będzie maskował wszelkich problemów z wydajnością związanych z wyrzucania elementów bezużytecznych. Proces może zapewnić swoje własne zdarzenia w połączeniu z zdarzenia ETW. Po zalogowaniu, zarówno w przypadku zdarzeń aplikacji, jak i zdarzenia odzyskiwania pamięci możliwe było skorelowanie ich ustalenie, jak i kiedy sterty problemów. Na przykład aplikacja serwera może dostarczyć zdarzenia na początku i końcu żądanie klienta.  
  
<a name="profiling_api"></a>   
### <a name="the-profiling-api"></a>API profilowania  
 Wspólnych interfejsów profilowania środowiska uruchomieniowego (języka wspólnego CLR) języka zawierają szczegółowe informacje o obiektach, które miały wpływ podczas wyrzucania elementów bezużytecznych. Program profilujący może zostać poinformowany podczas wyrzucania elementów bezużytecznych rozpoczyna i kończy. Umożliwia ona raportów dotyczących obiektów w zarządzanym stosie, w tym identyfikator obiektów w każdej generacji. Aby uzyskać więcej informacji, zobacz [Przegląd profilowania](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).  
  
 Profilery może zapewnić kompleksowe informacje. Jednak złożone profilery potencjalnie można zmodyfikować zachowanie aplikacji.  
  
### <a name="application-domain-resource-monitoring"></a>Monitorowanie zasobów domen aplikacji  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], (ARM) do monitorowania zasobów domen aplikacji włącza hosty do monitorowania wykorzystania procesora CPU i pamięci przez domenę aplikacji. Aby uzyskać więcej informacji, zobacz [monitorowanie zasobów domeny aplikacji](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).  
  
 [Powrót do początku](#top)  
  
<a name="troubleshooting_performance_issues"></a>   
## <a name="troubleshooting-performance-issues"></a>Rozwiązywanie problemów z wydajnością  
 Pierwszym krokiem jest [ustalić, czy problem jest faktycznie wyrzucania elementów bezużytecznych](#IsGC). Jeśli okaże się, że jest, wybierz z poniższej listy, aby rozwiązać problem.  
  
-   [Wyjątek braku pamięci](#Issue_OOM)  
  
-   [Proces używa zbyt dużo pamięci](#Issue_TooMuchMemory)  
  
-   [Moduł odśmiecania pamięci nie spowoduje odzyskania obiektów wystarczająco szybko](#Issue_NotFastEnough)  
  
-   [Zarządzanego stosu za jest pofragmentowana.](#Issue_Fragmentation)  
  
-   [Wstrzymuje kolekcji wyrzucania elementów są za długie](#Issue_LongPauses)  
  
-   [Generacja 0 jest zbyt duży](#Issue_Gen0)  
  
-   [Użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt wysoka](#Issue_HighCPU)  
  
<a name="Issue_OOM"></a>   
### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Problem: Zostanie zgłoszony wyjątek braku pamięci  
 Istnieją dwa przypadki uzasadnione dla zarządzanej <xref:System.OutOfMemoryException> zgłoszenie:  
  
-   Mało pamięci wirtualnej.  
  
     Moduł odśmiecania pamięci przydziela pamięć z systemu w segmentach ustalonej rozmiaru. Jeśli przydział wymaga dodatkowych segmentu, ale nie ciągłych wolny blok, w obszarze pamięci wirtualnej procesu, alokacji sterty zarządzanej nie powiedzie się.  
  
-   Nie ma wystarczającej ilości pamięci fizycznej do przydzielenia.  
  
|Testy wydajności|  
|------------------------|  
|[Określa, czy wyjątek braku pamięci jest zarządzana.](#OOMIsManaged)<br /><br /> [Określ ilość pamięci wirtualnej może być zarezerwowana.](#GetVM)<br /><br /> [Ustal, czy jest wystarczająca ilość fizycznej pamięci.](#Physical)|  
  
 Jeśli okaże się, że wyjątek nie jest uzasadnione, skontaktuj się z działem obsługi klienta firmy Microsoft i pomocy technicznej z następującymi informacjami:  
  
-   Stos o zarządzanym wyjątku braku pamięci.  
  
-   Pełny zrzut pamięci.  
  
-   Dane, gdy okaże się, że nie jest uzasadnione wyjątku braku pamięci, w tym dane, które pokazuje, że pamięć wirtualny lub fizyczny nie jest problemem.  
  
<a name="Issue_TooMuchMemory"></a>   
### <a name="issue-the-process-uses-too-much-memory"></a>Problem: Proces używa zbyt dużo pamięci  
 Typowe zakłada się, że użycie pamięci jest wyświetlane na **wydajności** kartę w Menedżerze zadań Windows można wskazać, kiedy jest on używany zbyt dużej ilości pamięci. Jednakże obok którego wyświetlona odnoszą się do zestawu roboczego; zapewnia ona informacje na temat użycia pamięci wirtualnej.  
  
 Jeśli okaże się, że problem jest spowodowany przez sterty zarządzanej, muszą mierzyć sterty zarządzanej, wraz z upływem czasu, aby określić wszystkie wzorce.  
  
 Jeśli okaże się, że problem nie leży po zarządzanym stosie, należy użyć debugowanie natywne.  
  
|Testy wydajności|  
|------------------------|  
|[Określ ilość pamięci wirtualnej może być zarezerwowana.](#GetVM)<br /><br /> [Określ, ile pamięci sterty zarządzanej jest zatwierdzanie.](#ManagedHeapCommit)<br /><br /> [Określ, ile pamięci sterty zarządzanej zastrzega sobie.](#ManagedHeapReserve)<br /><br /> [Określ dużych obiektów w generacji 2.](#ExamineGen2)<br /><br /> [Określ odwołania do obiektów.](#ObjRef)|  
  
<a name="Issue_NotFastEnough"></a>   
### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Problem: Moduł odśmiecania pamięci nie spowoduje odzyskania obiektów wystarczająco szybko  
 Gdy się pojawi, tak jakby obiekty nie są są odzyskane, zgodnie z oczekiwaniami do wyrzucania elementów bezużytecznych, należy określić, czy wszystkie silne odwołania do tych obiektów.  
  
 Ten problem może również wystąpić, jeśli nie było żadnych elementów bezużytecznych generacji, która zawiera obiekt martwy, co oznacza, że finalizator martwy obiektu nie został uruchomiony. Na przykład jest to możliwe po uruchomieniu aplikacji apartamentem jednowątkowym (przedziale STA) i wątku tej usługi, których nie można wywołać; kolejka finalizatorów tę sytuację.  
  
|Testy wydajności|  
|------------------------|  
|[Sprawdź odwołania do obiektów.](#ObjRef)<br /><br /> [Ustal, czy finalizator został uruchomiony.](#Induce)<br /><br /> [Ustal, czy istnieją obiekty oczekujące na można sfinalizować.](#Finalize)|  
  
<a name="Issue_Fragmentation"></a>   
### <a name="issue-the-managed-heap-is-too-fragmented"></a>Problem: Zarządzanego stosu jest zbyt pofragmentowana.  
 Poziom fragmentacji jest obliczana jako stosunek wolnego miejsca na dysku łączna ilość przydzielonej pamięci do generowania. Generacji 2 akceptowalny poziom fragmentacji jest nie więcej niż 20%. Ponieważ generacji 2 można uzyskać bardzo duże, stosunek fragmentacji jest ważniejsza niż wartość bezwzględna.  
  
 O dużej ilości wolnego miejsca w generacji 0 nie jest problemem, ponieważ jest generowanie gdzie są przydzielane nowych obiektów.  
  
 Fragmentacja zawsze występuje stertę dużego obiektu, ponieważ nie jest kompaktowana. Bezpłatne obiekty, które sąsiadują naturalnie są zwinięte do pojedynczego obszaru do spełnienia żądania alokacji dużego obiektu.  
  
 Fragmentacja może stać się problemem w generacji 1 i 2. Jeśli generacje te dużą ilością wolnego miejsca na dysku po wyrzucania elementów bezużytecznych, użycie obiektu aplikacji mogą wymagać modyfikacji i należy rozważyć ponownej oceny okresu istnienia obiektów długoterminowego.  
  
 Przypinanie nadmierne obiektów może zwiększyć fragmentacji. Jeśli fragmentacji jest wysoka, można przypiąć za dużo obiektów.  
  
 Jeżeli fragmentacji pamięci wirtualnej uniemożliwia Dodawanie segmentów moduł zbierający elementy bezużyteczne, powoduje, że może to być jeden z następujących czynności:  
  
-   Częste ładowanie i zwalnianie wiele małych zestawów.  
  
-   Przytrzymanie zbyt wiele odwołań do obiektów COM, gdy współdziałanie z kodem niezarządzanym.  
  
-   Tworzenie dużych obiektów przejściowy, co powoduje, że stertę dużego obiektu przydzielać i zwalniać często segmenty sterty.  
  
     W przypadku hostowania środowiska CLR, aplikacja może zażądać zachowanie jego segmentów moduł odśmiecania pamięci. Pozwala to zmniejszyć częstotliwość alokacje segmentu. Jest to realizowane za pomocą flagi STARTUP_HOARD_GC_VM w [startup_flags — wyliczenie](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
|Testy wydajności|  
|------------------------|  
|[Określ ilość wolnego miejsca w zarządzanym stosie.](#Fragmented)<br /><br /> [Określ liczbę przypiętych obiektów.](#Pinned)|  
  
 Jeśli uważasz, że nie stanowi uzasadnione fragmentacji, skontaktuj się z działem obsługi klienta firmy Microsoft i pomocy technicznej.  
  
<a name="Issue_LongPauses"></a>   
### <a name="issue-garbage-collection-pauses-are-too-long"></a>Problem: Wstrzymuje kolekcji wyrzucania elementów są za długie  
 Wyrzucanie elementów bezużytecznych działa w czasie rzeczywistym nietrwałego, więc aplikacja musi być w stanie tolerować kilka wstrzymuje. Kryterium czasu rzeczywistego nietrwałego jest, że 95% operacji musi zostać zakończone na czas.  
  
 W współbieżne wyrzucanie elementów bezużytecznych zarządzane wątki mogą być uruchamiane podczas zbierania, co oznacza, że wstrzymuje są minimalne.  
  
 Tymczasowe wyrzucanie elementów bezużytecznych (generacje 0 i 1) trwać tylko kilka milisekund, więc zmniejsza wstrzymuje zwykle nie jest możliwe. Można jednak zmniejszyć przerw w kolekcji generacji 2, zmieniając wzorzec żądań alokacji przez aplikację.  
  
 Inny, bardziej precyzyjne metoda polega na użyciu [zdarzenia ETW odzyskiwania pamięci](../../../docs/framework/performance/garbage-collection-etw-events.md). Możesz znaleźć chronometrażu dla kolekcji, dodając różnice sygnatury czasu sekwencji zdarzeń. Sekwencja całej kolekcji zawiera zawieszenie aparatu wykonywania, wyrzucanie elementów bezużytecznych, sama i wznowienie aparatu wykonywania.  
  
 Możesz użyć [powiadomienia dotyczące odzyskiwania pamięci](../../../docs/standard/garbage-collection/notifications.md) można określić, czy serwer ma mieć kolekcji generacji 2 i czy Przekierowywanie żądań do innego serwera, można zmniejszyć, problemów z pauzy.  
  
|Testy wydajności|  
|------------------------|  
|[Określ czas, wyrzucanie elementów bezużytecznych.](#TimeInGC)<br /><br /> [Określ, co spowodowało wyrzucania elementów bezużytecznych.](#Triggered)|  
  
<a name="Issue_Gen0"></a>   
### <a name="issue-generation-0-is-too-big"></a>Problem: Generacji 0 jest zbyt duży  
 Może mieć większą liczbę obiektów w systemie 64-bitowych, szczególnie w przypadku, gdy używasz wyrzucanie elementów bezużytecznych serwera zamiast wyrzucanie elementów bezużytecznych jest generacji 0. Jest to spowodowane próg wyzwolenia generację 0 wyrzucania elementów bezużytecznych jest wyższa w tych środowiskach i uzyskać znacznie większe generacji 0. Lepsza wydajność aplikacji przydziela większej ilości pamięci, zanim zostanie wywołany wyrzucania elementów bezużytecznych.  
  
<a name="Issue_HighCPU"></a>   
### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Problem: Użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt wysoka  
 Użycie procesora CPU będzie wysoka podczas wyrzucania elementów bezużytecznych. Znaczną ilość czasu proces odbywa się w wyrzucania elementów bezużytecznych, liczby kolekcji jest zbyt często czy kolekcja jest zbyt długo trwające. Współczynnik zwiększenia alokacji obiektów na stosie zarządzanym powoduje, że wyrzucanie elementów bezużytecznych częściej. Zmniejsza szybkość alokacji zmniejsza częstotliwość wyrzucania elementów bezużytecznych.  
  
 Stawki alokacji można monitorować za pomocą `Allocated Bytes/second` licznika wydajności. Aby uzyskać więcej informacji, zobacz [liczników wydajności w .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
 Czas trwania kolekcji jest głównie współczynnik liczby obiektów, które przeżyły po alokacji pamięci. Moduł zbierający elementy bezużyteczne musi przejść przez dużą ilość pamięci, jeśli wiele obiektów nadal mają być zbierane. Praca kompaktowanie pozostałości jest czasochłonne. Aby ustalić, ile obiekty zostały obsłużone w kolekcji, należy ustawić punkt przerwania w debugerze na końcu wyrzucania elementów bezużytecznych dla określonej generacji.  
  
|Testy wydajności|  
|------------------------|  
|[Określ, jeśli wysokie użycie procesora CPU jest spowodowany przez wyrzucanie elementów bezużytecznych.](#HighCPU)<br /><br /> [Ustaw punkt przerwania na końcu wyrzucania elementów bezużytecznych.](#GenBreak)|  
  
 [Powrót do początku](#top)  
  
<a name="troubleshooting_guidelines"></a>   
## <a name="troubleshooting-guidelines"></a>Wskazówki dotyczące rozwiązywania problemów  
 W tej sekcji opisano wskazówki, które należy wziąć pod uwagę po rozpoczęciu swoje badania.  
  
### <a name="workstation-or-server-garbage-collection"></a>Stacja robocza lub serwer wyrzucania elementów bezużytecznych  
 Określ, jeśli używasz poprawnego typu wyrzucania elementów bezużytecznych. Jeśli aplikacja korzysta z wielu wątków i wystąpienia obiektów, wyrzucanie elementów bezużytecznych serwera należy użyć zamiast wyrzucanie elementów bezużytecznych. Wyrzucanie elementów bezużytecznych serwera działa w wielu wątkach, wyrzucanie elementów bezużytecznych wymaga wielu wystąpień aplikacji do uruchamiania ich własnych wątków wyrzucania elementów bezużytecznych i konkurować o czas procesora CPU.  
  
 Aplikacja ma niskie obciążenie i rzadko w tle, takie jak usługa, która wykonuje zadania można za pomocą wyrzucanie elementów bezużytecznych współbieżne wyrzucanie elementów bezużytecznych wyłączone.  
  
### <a name="when-to-measure-the-managed-heap-size"></a>Gdy do mierzenia rozmiaru sterty zarządzanej  
 O ile nie jest używany program profilujący, trzeba będzie utworzyć spójne wzorzec pomiaru skutecznie zdiagnozować problemy z wydajnością. Należy wziąć pod uwagę następujące kwestie, aby ustanowić harmonogram:  
  
-   Jeśli mierzonych po wyrzucania elementów bezużytecznych generacji 2 całą zarządzaną stertę będą wolne od pamięci (obiekty martwe).  
  
-   Jeśli mierzonych natychmiast po wyrzucania elementów bezużytecznych generacji 0 obiekty w generacji 1 i 2 nie będą zbierane jeszcze.  
  
-   W przypadku mierzonych bezpośrednio przed wyrzucania elementów bezużytecznych będzie zmierzyć tak dużej ilości alokacji, jak to możliwe, zanim rozpocznie się wyrzucanie elementów bezużytecznych.  
  
-   Pomiaru podczas wyrzucania elementów bezużytecznych jest problemem, ponieważ struktur danych modułu odśmiecania pamięci nie znajdują się w nieprawidłowym stanie dla przechodzenia i nie można dostarczać pełnych wyników. To jest celowe.  
  
-   Używając wyrzucania elementów bezużytecznych dla stacji roboczych z współbieżne wyrzucanie elementów bezużytecznych, odzyskiwanego obiekty nie są skompaktowany, dzięki czemu rozmiar sterty może być taki sam lub większy (fragmentacji może wydawać się większe).  
  
-   Współbieżne wyrzucanie elementów bezużytecznych w generacji 2 jest opóźnione, gdy obciążenie pamięci fizycznej jest zbyt duży.  
  
 Poniższa procedura opisuje sposób Ustaw punkt przerwania, dzięki czemu można mierzyć zarządzanego stosu.  
  
<a name="GenBreak"></a>   
##### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Aby ustawić punkt przerwania na końcu wyrzucania elementów bezużytecznych  
  
-   W WinDbg za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:  
  
     **najlepszych praktyk w zakresie mscorwks! WKS::GCHeap::RestartEE "j (dwo (mscorwks! WKS::GCHeap::GcCondemnedGeneration) == 2) "kb"; " g ""**  
  
     gdzie **GcCondemnedGeneration** jest ustawiona na żądaną generacji. To polecenie wymaga symboli prywatnych.  
  
     To polecenie wymusza podziału **RestartEE** jest uruchamiane po obiekty generacji 2 odzyskano do wyrzucania elementów bezużytecznych.  
  
     W serwerze wyrzucanie elementów bezużytecznych, tylko jeden wątek wywołuje **RestartEE**, więc punkt przerwania zostanie wystąpić tylko raz podczas wyrzucania elementów bezużytecznych generacji 2.  
  
 [Powrót do początku](#top)  
  
<a name="performance_check_procedures"></a>   
## <a name="performance-check-procedures"></a>Procedury wyboru wydajności  
 W tej sekcji opisano następujące procedury, aby ustalić przyczynę problemu z wydajnością:  
  
-   [Ustal, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych.](#IsGC)  
  
-   [Określa, czy wyjątek braku pamięci jest zarządzana.](#OOMIsManaged)  
  
-   [Określ ilość pamięci wirtualnej może być zarezerwowana.](#GetVM)  
  
-   [Ustal, czy jest wystarczająca ilość fizycznej pamięci.](#Physical)  
  
-   [Określ, ile pamięci sterty zarządzanej jest zatwierdzanie.](#ManagedHeapCommit)  
  
-   [Określ, ile pamięci sterty zarządzanej zastrzega sobie.](#ManagedHeapReserve)  
  
-   [Określ dużych obiektów w generacji 2.](#ExamineGen2)  
  
-   [Określ odwołania do obiektów.](#ObjRef)  
  
-   [Ustal, czy finalizator został uruchomiony.](#Induce)  
  
-   [Ustal, czy istnieją obiekty oczekujące na można sfinalizować.](#Finalize)  
  
-   [Określ ilość wolnego miejsca w zarządzanym stosie.](#Fragmented)  
  
-   [Określ liczbę przypiętych obiektów.](#Pinned)  
  
-   [Określ czas, wyrzucanie elementów bezużytecznych.](#TimeInGC)  
  
-   [Określ, co wyzwoliło wyrzucania elementów bezużytecznych.](#Triggered)  
  
-   [Ustal, czy wysokie użycie procesora CPU jest spowodowany przez wyrzucanie elementów bezużytecznych.](#HighCPU)  
  
<a name="IsGC"></a>   
##### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Aby określić, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych  
  
-   Sprawdź następujące liczniki wydajności dwóch pamięci:  
  
    -   **% Czas działania modułu GC**. Wyświetla procent minionego czasu, jaki był poświęcony na wykonywanie wyrzucania elementów bezużytecznych od ostatniego cyklu wyrzucania elementów w kolekcji. Ten licznik umożliwia określenie, czy moduł zbierający elementy bezużyteczne zużywa zbyt dużo czasu, aby zwiększyć ilość miejsca na stosie zarządzanym. Jeśli czas potrzebny do wyrzucania elementów bezużytecznych jest stosunkowo niska, który może wskazywać na problem zasobów, poza zarządzanym stosie. Ten licznik mogą być niedokładne, gdy współbieżnych lub uczestniczy wyrzucania elementów bezużytecznych w tle.  
  
    -   **# Łączna liczba przydzielonych bajtów**. Przedstawia ilość pamięci wirtualnej, które aktualnie przydzielonej przez moduł odśmiecania pamięci. Ten licznik umożliwia określenie, czy pamięci używane przez moduł odśmiecania pamięci jest nadmierne część pamięci, która korzysta z aplikacji.  
  
     Większość liczników wydajności pamięci są aktualizowane na końcu każdej operacji wyrzucania elementów bezużytecznych. Może nie odzwierciedlają one bieżące warunki, które chcesz uzyskać informacje.  
  
<a name="OOMIsManaged"></a>   
##### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Aby ustalić, czy wyjątek braku pamięci jest zarządzany  
  
1.  W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane typ wyjątku drukowania (**pe**) polecenia:  
  
     **! pe**  
  
     Jeśli wyjątek jest zarządzany, <xref:System.OutOfMemoryException> jest wyświetlany jako typ wyjątku, jak pokazano w poniższym przykładzie.  
  
    ```  
    Exception object: 39594518  
    Exception type: System.OutOfMemoryException  
    Message: <none>  
    InnerException: <none>  
    StackTrace (generated):  
    ```  
  
2.  Dane wyjściowe nie określony wyjątek, należy określić, który wątek wyjątku braku pamięci pochodzi z. Wpisz następujące polecenie w debugerze, aby wyświetlić wszystkie wątki z ich stosów wywołań:  
  
     **~\*KB**  
  
     Wątek przy użyciu stosu, który ma wywołań wyjątków jest wskazywany przez `RaiseTheException` argumentu. Jest to obiektu zarządzanego wyjątku.  
  
    ```  
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0   
    ```  
  
3.  Następujące polecenie służy do porzucenia wyjątków zagnieżdżonych.  
  
     **! pe-zagnieżdżonych**  
  
     Jeśli nie możesz znaleźć wszystkie wyjątki, wyjątek braku pamięci pochodzi z niezarządzanego kodu.  
  
<a name="GetVM"></a>   
##### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Aby określić ilość pamięci wirtualnej może być zarezerwowana.  
  
-   W WinDbg za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie, aby pobrać największego wolnego regionu:  
  
     **! adresów — podsumowanie**  
  
     Największego wolnego region jest wyświetlany, jak pokazano w następujących danych wyjściowych.  
  
    ```  
    Largest free region: Base 54000000 - Size 0003A980  
    ```  
  
     W tym przykładzie rozmiar największego wolnego region jest około 24000 KB (3A980 w formacie szesnastkowym). Ten region jest znacznie mniejszy niż moduł zbierający elementy bezużyteczne musi dla segmentu.  
  
     —lub—  
  
-   Użyj **vmstat** polecenia:  
  
     **! vmstat**  
  
     Największego wolnego region jest największą wartość w kolumnie maksymalna, jak pokazano w następujących danych wyjściowych.  
  
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
  
1.  Uruchamianie Menedżera zadań Windows.  
  
2.  Na **wydajności** kartę, sprawdź wartość zatwierdzone. (W Windows 7, Przyjrzyj się **zatwierdzenia (KB)** w **grupy systemowej**.)  
  
     Jeśli **całkowita** jest bliska **Limit**, kończy się w pamięci fizycznej.  
  
<a name="ManagedHeapCommit"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Aby określić, ile pamięci zatwierdza sterty zarządzanej  
  
-   Użyj `# Total committed bytes` licznika wydajności pamięci, aby uzyskać liczbę bajtów, które zatwierdza sterty zarządzanej. Moduł zbierający elementy bezużyteczne zatwierdzeń fragmentów w segmencie, zgodnie z potrzebami, nie wszystkie w tym samym czasie.  
  
    > [!NOTE]
    >  Nie używaj `# Bytes in all Heaps` liczników wydajności, ponieważ nie reprezentuje aktualnego stanu użycia pamięci w stosie zarządzanym. Rozmiar generacji znajduje się w tej wartości i jest faktycznie jego rozmiar progu, oznacza to, rozmiar, który wywołuje wyrzucanie elementów bezużytecznych, jeśli generacja jest wypełniony przy użyciu obiektów. W związku z tym ta wartość zazwyczaj wynosi zero.  
  
<a name="ManagedHeapReserve"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Aby określić ilość pamięci sterty zarządzanej rezerwy  
  
-   Użyj `# Total reserved bytes` licznika wydajności pamięci.  
  
     Moduł zbierający elementy bezużyteczne zastrzega pamięć w segmentach i określić, gdzie segment uruchamia się za pomocą **eeheap** polecenia.  
  
    > [!IMPORTANT]
    >  Mimo że można określić ilość pamięci, które moduł odśmiecania pamięci przydziela dla każdego segmentu, rozmiar segmentu jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowe aktualizacje. Twoja aplikacja nigdy nie należy wprowadzić założeń dotyczących lub zależeć od rozmiaru określonego segmentu nie ma podejmować skonfigurować ilość pamięci dostępnej dla alokacji segmentu.  
  
-   W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:  
  
     **! eeheap -gc**  
  
     Wynik jest następujący.  
  
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
  
     Adresy, wskazywanym przez "segmentu" adresów początkowy segmentów.  
  
<a name="ExamineGen2"></a>   
##### <a name="to-determine-large-objects-in-generation-2"></a>Aby określić dużych obiektów w generacji 2  
  
-   W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:  
  
     **! dumpheap-stat**  
  
     Jeśli zarządzanego stosu jest duży, **dumpheap** może potrwać kilka minut na zakończenie.  
  
     Możesz zacząć analizować w ciągu ostatnich kilku wierszy danych wyjściowych, ponieważ ich listę obiektów, które najwięcej miejsca. Na przykład:  
  
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
  
     Ostatni obiekt na liście jest ciągiem i zajmuje najwięcej miejsca na. Można sprawdzić w aplikacji, aby zobaczyć, jak można optymalizować obiektów w postaci ciągów. Aby wyświetlić ciągów, które należą do zakresu od 150 do 200 bajtów, wpisz następujące polecenie:  
  
     **! dumpheap-typ System.String -minutowy 150 - max 200**  
  
     Przykładem wyniki jest następujący.  
  
    ```  
    Address  MT           Size  Gen  
    1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11  
    …  
    ```  
  
     Za pomocą całkowitą zamiast ciągu dla Identyfikatora może być bardziej wydajne. Jeśli ten sam ciąg jest powtarza się tysiące razy, należy wziąć pod uwagę wewnętrzne przygotowanie ciągu. Aby uzyskać więcej informacji na temat wewnętrzne przygotowanie ciągu, zobacz temat referencyjny dotyczący <xref:System.String.Intern%2A?displayProperty=nameWithType> metody.  
  
<a name="ObjRef"></a>   
##### <a name="to-determine-references-to-objects"></a>Aby określić odwołania do obiektów  
  
-   W WinDbg za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie, aby listy odwołania do obiektów:  
  
     **! gcroot**  
  
     `-or-`  
  
-   Aby ustalić, odwołania do określonego obiektu, należy uwzględnić adres:  
  
     **! gcroot 1c37b2ac**  
  
     Znalezione na stosach obiekty główne może być wyników fałszywie dodatnich. Aby uzyskać więcej informacji, użyj polecenia `!help gcroot`.  
  
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
  
     **Gcroot** polecenia może zająć dużo czasu na zakończenie. Każdy obiekt, który nie jest odzyskiwane przez wyrzucanie elementów bezużytecznych jest obiektem na żywo. Oznacza to, że niektóre główny jest bezpośrednio lub pośrednio trzymając na obiekt, więc **gcroot** powinna zwrócić informacje o ścieżce do obiektu. Należy sprawdzić wykresy zwracane i zobacz, dlaczego te obiekty są nadal istnieją odwołania.  
  
<a name="Induce"></a>   
##### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Aby określić, czy finalizator została uruchomiona  
  
-   Uruchom program test, który zawiera następujący kod:  
  
    ```  
    GC.Collect();  
    GC.WaitForPendingFinalizers();  
    GC.Collect();  
    ```  
  
     Jeśli test nie zostanie rozwiązany, oznacza to, że moduł odśmiecania pamięci nie został odzyskiwaniu obiektów, ponieważ została wstrzymana finalizatory dla tych obiektów. <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Metoda umożliwia finalizatory do wykonywania swoich zadań i rozwiąże problem.  
  
<a name="Finalize"></a>   
##### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Aby ustalić, czy istnieją obiekty oczekujące na sfinalizowana  
  
1.  W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:  
  
     **! finalizequeue**  
  
     Spójrz na liczbę obiektów, które są gotowe do finalizacji. Jeśli liczba jest wysokie, należy zbadać, dlaczego te finalizatory nie postępu na wszystkich lub nie postęp szybkiego wystarczająco.  
  
2.  Aby uzyskać dane wyjściowe wątków, wpisz następujące polecenie:  
  
     **wątki — specjalne**  
  
     To polecenie dostarcza dane wyjściowe, takie jak poniżej.  
  
    ```  
       OSID     Special thread type  
    2    cd0    DbgHelper   
    3    c18    Finalizer   
    4    df0    GC SuspendEE   
    ```  
  
     Wątek finalizatora wskazuje, które finalizatora, jeśli jest aktualnie uruchomione. Wątek finalizatora nie jest uruchomiona żadnych finalizatorów, trwa oczekiwanie na zdarzenie nakazać mu wykonać swoją pracę. W większości przypadków zostanie wyświetlony wątek finalizatora w tym stanie ponieważ działa na THREAD_HIGHEST_PRIORITY i powinna zakończyć działanie finalizatorów, jeśli istnieje bardzo szybko.  
  
<a name="Fragmented"></a>   
##### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Aby określić ilość wolnego miejsca w zarządzanym stosie  
  
-   W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:  
  
     **! dumpheap-wpisz bezpłatne - stat**  
  
     To polecenie wyświetla całkowity rozmiar wszystkich obiektów bezpłatne na zarządzanym stosie, jak pokazano w poniższym przykładzie.  
  
    ```  
    total 230 objects  
    Statistics:  
          MT    Count    TotalSize Class Name  
    00152b18      230     40958584      Free  
    Total 230 objects  
    ```  
  
-   Aby określić ilość wolnego miejsca w generacji 0, wpisz następujące polecenie, aby uzyskać informacje dotyczące użycia pamięci przez generacji:  
  
     **! eeheap -gc**  
  
     To polecenie wyświetla dane wyjściowe podobne do następujących. Ostatni wiersz zawiera segment efemeryczny.  
  
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
  
-   Oblicz przestrzeni używanej przez generacji 0:  
  
     **? 49e05d04 0x49521f8c**  
  
     Wynik jest następujący. Generacji 0 to około 9 MB.  
  
    ```  
    Evaluate expression: 9321848 = 008e3d78  
    ```  
  
-   Poniższe polecenie wykonuje ilość wolnego miejsca w zakresie generacji 0:  
  
     **! dumpheap-wpisz bezpłatne - stat 0x49521f8c 49e05d04**  
  
     Wynik jest następujący.  
  
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
  
     Te dane wyjściowe pokazuje, że generacji 0 części stosu obiektów przy użyciu 9 MB miejsca i znajduje się 7 MB wolnego. Ta analiza przedstawia zakres generacji 0 przyczynia się do fragmentacji. Tę kwotę użycie sterty powinien obniżone z łącznej kwoty jako przyczynę fragmentacji przez obiekty długoterminowego.  
  
<a name="Pinned"></a>   
##### <a name="to-determine-the-number-of-pinned-objects"></a>Aby określić liczbę obiektów przypięte  
  
-   W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie:  
  
     **! gchandles**  
  
     Statystyki, wyświetlane zawiera liczbę przypiętych uchwytów, co ilustruje poniższy przykład.  
  
    ```  
    GC Handle Statistics:  
    Strong Handles:      29  
    Pinned Handles:      10  
    ```  
  
<a name="TimeInGC"></a>   
##### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>Aby określić czas w wyrzucania elementów bezużytecznych  
  
-   Sprawdź `% Time in GC` licznika wydajności pamięci.  
  
     Wartość jest obliczana przy użyciu interwałów próbkowania. Ponieważ liczniki zostały zaktualizowane na końcu każdej operacji wyrzucania elementów bezużytecznych, bieżąca przykładowa będzie mieć taką samą wartość jak w poprzednim przykładzie, jeśli żadne kolekcje, które wystąpiły interwału.  
  
     Czas zbierania mnożąc interwałów próbkowania przy użyciu wartości procentowej.  
  
     Następujące dane zawiera cztery próbkowania dwóch sekund do badania 8 sekund. `Gen0`, `Gen1`, I `Gen2` kolumny zawierają liczbę wyrzucania elementów bezużytecznych, które wystąpiły podczas tego interwału dla danej generacji.  
  
    ```  
    Interval    Gen0    Gen1    Gen2    % Time in GC  
           1       9       3       1              10  
           2      10       3       1               1  
           3      11       3       1               3  
           4      11       3       1               3  
    ```  
  
     Te informacje nie są wyświetlane podczas wyrzucania elementów bezużytecznych wystąpił, ale można określić liczbę wyrzucania elementów bezużytecznych, które wystąpiły w odstępach czasu. Zakładając, że najgorszym przypadku, oraz generacji 0 wyrzucania elementów bezużytecznych zostało zakończone na początku drugiej interwał i jedenasty generację 0 wyrzucania elementów bezużytecznych zostało zakończone na końcu interwału piąty. Czas między końcem dziesiątego i na końcu jedenasty wyrzucania elementów bezużytecznych jest około 2 sekundy, a licznik wydajności przedstawia 3%, aby był czas trwania jedenasty wyrzucania elementów bezużytecznych generacji 0 (% w ciągu kilku sekund 2 * 3 = 60ms).  
  
     W tym przykładzie istnieją 5 okresów.  
  
    ```  
    Interval    Gen0    Gen1    Gen2     % Time in GC  
           1       9       3       1                3  
           2      10       3       1                1  
           3      11       4       2                1  
           4      11       4       2                1  
           5      11       4       2               20  
    ```  
  
     Drugiej generacji 2 wyrzucania elementów bezużytecznych pracę trzeci przedział czasu i zostało zakończone w piątym odstępach czasu. Zakładając, że najgorszym przypadku, ostatni wyrzucania elementów bezużytecznych był dla kolekcji generacji 0, które kończy się na początku drugiej interwał i 2 wyrzucania elementów bezużytecznych generacji zakończone na końcu piąty interwał. W związku z tym czas od zakończenia operacji wyrzucania elementów bezużytecznych generacji 0 i na końcu wyrzucania elementów bezużytecznych generacji 2 jest 4 sekundy. Ponieważ `% Time in GC` licznika wynosi 20%, maksymalną ilość czasu, w generacji 2 wyrzucania elementów bezużytecznych może miały jest (w sekundach 4 * 20% = 800ms).  
  
-   Alternatywnie, można określić długość wyrzucania elementów bezużytecznych za pomocą [zdarzenia ETW odzyskiwania pamięci](../../../docs/framework/performance/garbage-collection-etw-events.md)i Analizuj informacje, aby określić czas trwania operacji wyrzucania elementów bezużytecznych.  
  
     Na przykład następujące dane przedstawiono sekwencję zdarzeń, który wystąpił podczas niejednoczesne wyrzucanie elementów bezużytecznych.  
  
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
  
     Rzeczywiste wyrzucania elementów bezużytecznych zajęło 4.8ms (`GCEnd_V1` — `GCStart_V1`).  
  
     Wznawianie wątków zarządzanych trwało 21us (`GCRestartEEEnd` — `GCRestartEEBegin`).  
  
     Następujące dane wyjściowe zawiera przykład wyrzucanie elementów bezużytecznych w tle i obejmuje procesu, wątku i pola, zdarzenia. (Nie wszystkie dane są wyświetlane).  
  
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
  
     `GCStart_V1` Zdarzenie w 42504816 oznacza, że jest tle wyrzucania elementów bezużytecznych, ponieważ jest ostatnim polu `1`. Staje się on wyrzucania elementów bezużytecznych nie. 102019.  
  
     `GCStart` Wystąpi zdarzenie, ponieważ nie istnieje potrzeba efemerycznego wyrzucania elementów bezużytecznych, przed rozpoczęciem bezużytecznych w tle. Staje się on wyrzucania elementów bezużytecznych nie. 102020.  
  
     W 42514170, wyrzucanie elementów bezużytecznych nie. 102020 zostanie zakończone. Zarządzane wątki są ponownie uruchamiane na tym etapie. To pole jest wypełniane w wątku 4372, która wywołała to bezużytecznych w tle.  
  
     W wątku 4744 występuje zawieszenia. Jest to jedyny raz, w tle wyrzucanie elementów bezużytecznych ma wstrzymania zarządzanych wątków. Ten czas trwania wynosi około 99ms ((63784407-63685394)/1000).  
  
     `GCEnd` Zdarzeń do wyrzucania elementów bezużytecznych tła wynosi 89931423. Oznacza to, że odzyskiwanie pamięci w tle trwał o 47seconds ((89931423-42504816)/1000).  
  
     Gdy zarządzane wątki są uruchomione, widać dowolną liczbę tymczasowe wyrzucanie elementów bezużytecznych występuje.  
  
<a name="Triggered"></a>   
##### <a name="to-determine-what-triggered-a-garbage-collection"></a>Aby ustalić przyczyny ich wyzwolenia wyrzucania elementów bezużytecznych  
  
-   W debugerze WinDbg lub Visual Studio za pomocą rozszerzenie debugowania SOS załadowane wpisz następujące polecenie, aby wyświetlić wszystkie wątki z ich stosów wywołań:  
  
     **~\*KB**  
  
     To polecenie wyświetla dane wyjściowe podobne do następujących.  
  
    ```  
    0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect   
    0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4  
    0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48  
    ```  
  
     Wyrzucanie elementów bezużytecznych zostało spowodowane przez powiadomienie małej ilości pamięci systemu operacyjnego, stos wywołań jest podobna, z tą różnicą, że wątek znajduje się wątek finalizatora. Wątek finalizatora pobiera wiadomość z powiadomieniem asynchronicznego małej ilości pamięci i wywołuje wyrzucanie elementów bezużytecznych.  
  
     Jeśli wyrzucanie elementów bezużytecznych zostało spowodowane przez alokacji pamięci, stos wygląda następująco:  
  
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
  
     Pomocnik just-in-time (`JIT_New*`) po pewnym czasie wywołania `GCHeap::GarbageCollectGeneration`. Jeśli okaże się, że wyrzucania generacji 2 są spowodowane przez alokacje, musisz określić obiekty, które są zbierane przez 2 wyrzucania elementów bezużytecznych generacji, a także jak ich unikać. Oznacza to, że chcesz określić różnicę między początek i koniec 2 wyrzucania elementów bezużytecznych generacji i obiekty przez nie spowodował kolekcji generacji 2.  
  
     Na przykład wpisz następujące polecenie w debugerze, aby pokazać początku kolekcji generacji 2:  
  
     **! dumpheap-stat**  
  
     Przykładowe dane wyjściowe (skróconej informacji wyświetlenie obiektów, które używają najwięcej miejsca na):  
  
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
  
     Na koniec generacji 2, powtórz polecenie:  
  
     **! dumpheap-stat**  
  
     Przykładowe dane wyjściowe (skróconej informacji wyświetlenie obiektów, które używają najwięcej miejsca na):  
  
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
  
     `double[]` Obiektów zniknął od końca danych wyjściowych, co oznacza, że zostały zebrane. Obiekty te konta do około 70 MB. Pozostałe obiekty nie został zmieniony wiele. Dlatego te `double[]` obiekty zostały powód, dlaczego wystąpił ten wyrzucania elementów bezużytecznych generacji 2. Następnym krokiem jest, aby ustalić, dlaczego `double[]` obiekty są dostępne i dlaczego ich zostało przerwane. Możesz poprosić kodu dla deweloperów, gdzie pochodzi tych obiektów, lub użyć **gcroot** polecenia.  
  
<a name="HighCPU"></a>   
##### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Aby ustalić, czy wysokie użycie procesora CPU jest spowodowany przez wyrzucanie elementów bezużytecznych  
  
-   Korelowanie `% Time in GC` wartość licznika wydajności pamięci z czasem przetwarzania.  
  
     Jeśli `% Time in GC` wartość gwałtowne wzrosty w tym samym czasie jako czas przetwarzania, wyrzucanie elementów bezużytecznych powoduje wysokie użycie procesora CPU. W przeciwnym razie wykonaj profilowanie aplikacji można znaleźć, gdzie występuje wysokie użycie.  
  
## <a name="see-also"></a>Zobacz także

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
