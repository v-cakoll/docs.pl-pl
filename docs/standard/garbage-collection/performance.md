---
title: Odzyskiwanie pamięci i wydajność
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 8d40091420c29c86f2ebb25f14c17ae4f7a1c44a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974761"
---
# <a name="garbage-collection-and-performance"></a>Odzyskiwanie pamięci i wydajność

W tym temacie opisano problemy związane z wyrzucaniem elementów bezużytecznych i użyciem pamięci. Rozwiązuje on problemy związane z zarządzanym stertą i wyjaśnia, jak zminimalizować efekt wyrzucania elementów bezużytecznych w aplikacjach. Każdy problem zawiera linki do procedur, których można użyć do badania problemów.

## <a name="performance-analysis-tools"></a>Narzędzia do analizy wydajności

W poniższych sekcjach opisano narzędzia, które są dostępne do badania problemów dotyczących użycia pamięci i wyrzucania elementów bezużytecznych. [Procedury](#performance-check-procedures) opisane w dalszej części tego tematu odnoszą się do tych narzędzi.

### <a name="memory-performance-counters"></a>Liczniki wydajności pamięci

Liczników wydajności można używać do zbierania danych wydajności. Aby uzyskać instrukcje, zobacz [profilowanie środowiska uruchomieniowego](../../../docs/framework/debug-trace-profile/runtime-profiling.md). Kategoria pamięci środowiska CLR platformy .NET liczników wydajności, zgodnie z opisem w [licznikach wydajności w .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), zawiera informacje na temat modułu wyrzucania elementów bezużytecznych.

### <a name="debugging-with-sos"></a>Debugowanie za pomocą SOS

Aby sprawdzić obiekty na zarządzanym stosie, można użyć [debugera systemu Windows (WinDbg)](/windows-hardware/drivers/debugger/index) .

Aby zainstalować program WinDbg, zainstaluj narzędzia debugowania dla systemu Windows ze strony [Pobierz narzędzia debugowania dla systemu Windows](/windows-hardware/drivers/debugger/debugger-download-tools) .

### <a name="garbage-collection-etw-events"></a>Zdarzenia ETW odzyskiwania pamięci

Śledzenie zdarzeń systemu Windows (ETW) to system śledzenia, który uzupełnia profilowanie i obsługę debugowania zapewniane przez .NET Framework. Począwszy od .NET Framework 4, [zdarzenia ETW do wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md) przechwytują przydatne informacje na potrzeby analizowania zarządzanego sterty z punktu widzenia statystycznego. Na przykład zdarzenie `GCStart_V1`, które jest zgłaszane, gdy występuje wyrzucanie elementów bezużytecznych, zawiera następujące informacje:

- Które Generowanie obiektów jest zbierane.

- Co wyzwoliło wyrzucanie elementów bezużytecznych.

- Typ wyrzucania elementów bezużytecznych (współbieżne lub niewspółbieżne).

Rejestrowanie zdarzeń ETW jest wydajne i nie będzie maskować żadnych problemów z wydajnością związanych z odzyskiwaniem pamięci. Proces może zapewnić własne zdarzenia w połączeniu ze zdarzeniami ETW. Po zarejestrowaniu zarówno zdarzenia aplikacji, jak i zdarzenia wyrzucania elementów bezużytecznych mogą być skorelowane, aby określić sposób i czas wystąpienia problemów sterty. Na przykład aplikacja serwera może zapewnić zdarzenia na początku i na końcu żądania klienta.

### <a name="the-profiling-api"></a>Profilowanie API

Interfejsy profilowania środowiska uruchomieniowego języka wspólnego (CLR) zawierają szczegółowe informacje o obiektach, których dotyczyły podczas wyrzucania elementów bezużytecznych. Program profilujący może zostać powiadomiony, gdy rozpocznie się i skończy odzyskiwanie pamięci. Może ona dostarczać raporty dotyczące obiektów na zarządzanym stosie, w tym identyfikowanie obiektów w każdej generacji. Aby uzyskać więcej informacji, zobacz [profilowanie — Omówienie](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).

Prepliky mogą dostarczać wyczerpujące informacje. Jednak złożone profilowania mogą potencjalnie modyfikować zachowanie aplikacji.

### <a name="application-domain-resource-monitoring"></a>Monitorowanie zasobów domen aplikacji

Począwszy od .NET Framework 4, monitorowanie zasobów domeny aplikacji (ARM) umożliwia hostom monitorowanie użycia procesora i pamięci przez domenę aplikacji. Aby uzyskać więcej informacji, zobacz [monitorowanie zasobów domeny aplikacji](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).

## <a name="troubleshooting-performance-issues"></a>Rozwiązywanie problemów z wydajnością

Pierwszym krokiem jest [określenie, czy problem jest w rzeczywistości odzyskiwaniem pamięci](#IsGC). Jeśli określisz, że jest to możliwe, wybierz z poniższej listy, aby rozwiązać problem.

- [Zgłaszany jest wyjątek braku pamięci](#Issue_OOM)

- [Proces używa zbyt dużej ilości pamięci](#Issue_TooMuchMemory)

- [Moduł wyrzucania elementów bezużytecznych nie odzyska obiektów wystarczająco szybko](#Issue_NotFastEnough)

- [Sterta zarządzana jest zbyt pofragmentowana](#Issue_Fragmentation)

- [Wyrzucanie elementów bezużytecznych jest zbyt długie](#Issue_LongPauses)

- [Generacja 0 jest zbyt duża](#Issue_Gen0)

- [Użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt duże](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Problem: zgłoszono wyjątek braku pamięci

Istnieją dwa słuszne przypadki, w których zostanie zgłoszony <xref:System.OutOfMemoryException> zarządzany:

- Zaczyna brakować pamięci wirtualnej.

  Moduł wyrzucania elementów bezużytecznych przydziela pamięć z systemu w segmentach wstępnie określonego rozmiaru. Jeśli alokacja wymaga dodatkowego segmentu, ale w obszarze pamięci wirtualnej procesu nie ma ciągłego wolnego bloku, alokacja dla sterty zarządzanej nie powiedzie się.

- Brak wystarczającej ilości pamięci fizycznej do przydzielenia.

|Sprawdzanie wydajności|
|------------------------|
|[Ustal, czy jest zarządzany wyjątek braku pamięci.](#OOMIsManaged)<br /><br /> [Określ ilość pamięci wirtualnej, która może być zarezerwowana.](#GetVM)<br /><br /> [Należy określić, czy jest dostępna wystarczająca ilość pamięci fizycznej.](#Physical)|

Jeśli ustalisz, że wyjątek nie jest wiarygodny, skontaktuj się z działem obsługi klienta i pomocy technicznej firmy Microsoft, podając następujące informacje:

- Stos z wyjątkiem zarządzanego wyjątku out-of-memory.

- Pełny zrzut pamięci.

- Dane, które udowadniają, że nie jest to słuszny wyjątek braku pamięci, w tym dane, które pokazują, że pamięć wirtualna lub fizyczna nie jest problemem.

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a>Problem: proces używa zbyt dużej ilości pamięci

Typowym założeniem jest, że użycie pamięci na karcie **wydajność** Menedżera zadań systemu Windows może wskazywać, kiedy jest zbyt dużo pamięci. Jednak te wyświetlacze odnoszą się do zestawu roboczego; nie zawiera on informacji o użyciu pamięci wirtualnej.

Jeśli okaże się, że przyczyną problemu jest sterta zarządzana, należy zmierzyć stertę zarządzaną w miarę upływu czasu, aby określić wzorce.

W przypadku stwierdzenia, że problem nie jest spowodowany przez zarządzaną stertę, należy użyć debugowania natywnego.

|Sprawdzanie wydajności|
|------------------------|
|[Określ ilość pamięci wirtualnej, która może być zarezerwowana.](#GetVM)<br /><br /> [Określ ilość pamięci, która jest zatwierdzana przez stertę zarządzaną.](#ManagedHeapCommit)<br /><br /> [Określ ilość pamięci, jaką rezerwuje sterta zarządza.](#ManagedHeapReserve)<br /><br /> [Określ duże obiekty w generacji 2.](#ExamineGen2)<br /><br /> [Określanie odwołań do obiektów.](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Problem: moduł zbierający elementy bezużyteczne nie odzyska obiektów wystarczająco szybko

Gdy pojawia się tak, jakby obiekty nie są odzyskiwane w oczekiwany sposób na wyrzucanie elementów bezużytecznych, należy określić, czy istnieją silne odwołania do tych obiektów.

Ten problem może również wystąpić, jeśli nie wyrzucanie elementów bezużytecznych dla generacji, która zawiera martwy obiekt, co oznacza, że finalizator dla martwego obiektu nie został uruchomiony. Na przykład jest to możliwe, gdy uruchamiasz aplikację jednowątkowego typu Apartment (STA) i wątek, w którym usługi kolejki finalizatora nie mogą wywoływać do niej.

|Sprawdzanie wydajności|
|------------------------|
|[Sprawdź odwołania do obiektów.](#ObjRef)<br /><br /> [Ustal, czy finalizator został uruchomiony.](#Induce)<br /><br /> [Ustal, czy istnieją obiekty oczekujące na sfinalizowanie.](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a>Problem: sterta zarządzana jest zbyt pofragmentowana

Poziom fragmentacji jest obliczany jako stosunek ilości wolnego miejsca na łączną przydzieloną pamięć dla generacji. W przypadku generacji 2 akceptowalny poziom fragmentacji nie przekracza 20%. Ponieważ generacja 2 może być bardzo duża, stosunek fragmentacji jest ważniejszy niż wartość bezwzględna.

Posiadanie dużej ilości wolnego miejsca w generacji 0 nie jest problemem, ponieważ jest to generacja, w której przydzielono nowe obiekty.

Fragmentacja zawsze występuje w stercie dużego obiektu, ponieważ nie jest kompaktowana. Wolne obiekty, które są przyległe, są naturalnie zwijane do pojedynczej przestrzeni w celu zaspokojenia żądań alokacji dużego obiektu.

Fragmentacja może stać się problemem w przypadku generacji 1 i generacji 2. Jeśli te generacje mają dużą ilość wolnego miejsca po wyrzucaniu elementów bezużytecznych, użycie obiektu aplikacji może wymagać modyfikacji i należy rozważyć ponowne obliczenie okresu istnienia długoterminowych obiektów.

Nadmierne Przypinanie obiektów może zwiększyć fragmentację. Jeśli fragmentacja jest wysoka, zbyt wiele obiektów może być przypiętych.

Jeśli fragmentacja pamięci wirtualnej uniemożliwia dodanie segmentów przez moduł wyrzucania elementów bezużytecznych, przyczyny mogą być następujące:

- Częste ładowanie i zwalnianie wielu małych zestawów.

- Przechowywanie zbyt wielu odwołań do obiektów COM podczas współdziałania z niezarządzanym kodem.

- Tworzenie dużych obiektów przejściowych, co sprawia, że sterta dużych obiektów często przydziela i zwalnia segmenty sterty.

  W przypadku hostowania środowiska CLR aplikacja może zażądać, aby moduł zbierający elementy bezużyteczne zachował swoje segmenty. Zmniejsza to częstotliwość alokacji segmentu. Jest to realizowane przy użyciu flagi STARTUP_HOARD_GC_VM w [Wyliczeniu STARTUP_FLAGS](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).

|Sprawdzanie wydajności|
|------------------------|
|[Określ ilość wolnego miejsca w zarządzanym stosie.](#Fragmented)<br /><br /> [Określ liczbę przypiętych obiektów.](#Pinned)|

Jeśli uważasz, że nie istnieje uzasadniona przyczyna fragmentacji, skontaktuj się z działem obsługi klienta i pomocy technicznej firmy Microsoft.

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a>Problem: wstrzymanie odzyskiwania pamięci jest zbyt długie

Wyrzucanie elementów bezużytecznych działa w czasie rzeczywistym, więc aplikacja musi być w stanie tolerować pewne przerwy. Kryterium dla miękkiego czasu rzeczywistego jest to, że 95% operacji musi zakończyć się w czasie.

W współbieżnym wyrzucaniu elementów bezużytecznych, zarządzane wątki można uruchamiać w kolekcji, co oznacza, że pauzy są bardzo minimalne.

Tymczasowe wyrzucanie elementów bezużytecznych (generacji 0 i 1) ostatnie tylko kilka milisekund, więc zmniejszenie wstrzymania nie jest zazwyczaj możliwe. Można jednak zmniejszyć wstrzymania w kolekcjach generacji 2, zmieniając wzorzec żądań alokacji przez aplikację.

Innym, dokładniej, metoda polega na użyciu [zdarzeń ETW wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md). Chronometraż kolekcji można znaleźć, dodając różnice czasu dla sekwencji zdarzeń. Cała sekwencja kolekcji obejmuje zawieszenie aparatu wykonywania, samego wyrzucania elementów bezużytecznych i wznowienie aparatu wykonywania.

Możesz użyć powiadomień o wykorzystaniu [elementów bezużytecznych](../../../docs/standard/garbage-collection/notifications.md) , aby określić, czy serwer ma kolekcję generacji 2 i czy żądania przekierowania na inny serwer mogą ułatwić rozwiązywanie problemów z wstrzymywaniem.

|Sprawdzanie wydajności|
|------------------------|
|[Określ długość czasu w wyrzucaniu elementów bezużytecznych.](#TimeInGC)<br /><br /> [Określ, co spowodowało wyrzucanie elementów bezużytecznych.](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a>Problem: generacja 0 jest zbyt duża

Generacja 0 może mieć większą liczbę obiektów w systemie 64-bitowym, szczególnie w przypadku używania odzyskiwania pamięci serwera zamiast wyrzucania elementów bezużytecznych stacji roboczej. Wynika to z faktu, że próg wyzwalający wyrzucanie elementów bezużytecznych generacji 0 jest wyższy w tych środowiskach, a kolekcje generacji 0 mogą być znacznie większe. Zwiększona wydajność, gdy aplikacja przydzieli więcej pamięci przed wyzwoleniem wyrzucania elementów bezużytecznych.

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Problem: użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt duże

Użycie procesora CPU będzie wysokie podczas wyrzucania elementów bezużytecznych. Jeśli w wyrzucaniu elementów bezużytecznych jest dużo czasu procesu, liczba kolekcji jest zbyt częste lub kolekcja jest zbyt długa. Zwiększona szybkość alokacji obiektów na stercie zarządzanym powoduje częstsze wyrzucanie elementów bezużytecznych. Zmniejszenie szybkości alokacji zmniejsza częstotliwość wyrzucania elementów bezużytecznych.

Stawki przydziału można monitorować przy użyciu `Allocated Bytes/second` licznika wydajności. Aby uzyskać więcej informacji, zobacz [liczniki wydajności w .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).

Czas trwania kolekcji jest przede wszystkim czynnikiem liczby obiektów, które przeżyły po alokacji. Moduł wyrzucania elementów bezużytecznych musi przekroczyć dużą ilość pamięci, jeśli wiele obiektów pozostanie do zebrania. Prace do kompaktowania pozostałego czasu są czasochłonne. Aby określić liczbę obiektów obsłużonych podczas zbierania, należy ustawić punkt przerwania w debugerze na końcu wyrzucania elementów bezużytecznych dla określonej generacji.

|Sprawdzanie wydajności|
|------------------------|
|[Ustal, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych.](#HighCPU)<br /><br /> [Ustaw punkt przerwania na końcu odzyskiwania pamięci.](#GenBreak)|

## <a name="troubleshooting-guidelines"></a>Wskazówki dotyczące rozwiązywania problemów

W tej sekcji opisano wskazówki, które należy wziąć pod uwagę podczas rozpoczynania badań.

### <a name="workstation-or-server-garbage-collection"></a>Stacja robocza lub odzyskiwanie pamięci serwera

Ustal, czy używasz poprawnego typu wyrzucania elementów bezużytecznych. Jeśli aplikacja używa wielu wątków i wystąpień obiektów, użyj wyrzucania elementów bezużytecznych serwera zamiast wyrzucania elementów bezużytecznych stacji roboczej. Odzyskiwanie pamięci serwera działa w wielu wątkach, podczas gdy wyrzucanie elementów bezużytecznych stacji roboczej wymaga wielu wystąpień aplikacji do uruchamiania własnych wątków odzyskiwania pamięci i konkurowania na czas procesora CPU.

Aplikacja o niskim obciążeniu i wykonująca zadania rzadko w tle, taka jak usługa, może użyć wyrzucania elementów bezużytecznych stacji roboczej z wyłączonym współbieżnym wyrzucaniem elementów bezużytecznych.

### <a name="when-to-measure-the-managed-heap-size"></a>Kiedy mierzyć rozmiar sterty zarządzanej

Jeśli nie korzystasz z profilera, konieczne będzie ustanowienie spójnego wzorca pomiarów w celu efektywnego zdiagnozowania problemów z wydajnością. Aby określić harmonogram, należy wziąć pod uwagę następujące kwestie:

- Jeśli mierzy się po wyrzucaniu elementów bezużytecznych generacji 2, cały stos zarządzany będzie wolny od elementów bezużytecznych (martwych obiektów).

- W przypadku mierzenia natychmiast po wyrzucaniu elementów bezużytecznych generacji 0 obiekty w generacjach 1 i 2 nie zostaną jeszcze zebrane.

- Jeśli miara jest mierzona bezpośrednio przed wyrzucaniem elementów bezużytecznych, po rozpoczęciu wyrzucania elementów bezużytecznych należy mierzyć możliwie tyle przydziału.

- Pomiar podczas wyrzucania elementów bezużytecznych jest problematyczny, ponieważ struktury danych modułu wyrzucania elementów bezużytecznych są w nieprawidłowym stanie do przechodzenia i mogą nie być w stanie uzyskać pełnych wyników. Jest to zaprojektowane.

- W przypadku korzystania z wyrzucania elementów bezużytecznych stacji roboczej z współbieżnym wyrzucaniem elementów bezużytecznych obiekty odzyskiwane nie są kompaktne, dzięki czemu rozmiar sterty może być taki sam lub większy (fragmentacja może sprawiać, że jest większa).

- Współbieżne wyrzucanie elementów bezużytecznych w generacji 2 jest opóźnione, gdy obciążenie pamięci fizycznej jest zbyt wysokie.

Poniższa procedura opisuje, jak ustawić punkt przerwania, aby można było zmierzyć stertę zarządzaną.

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Aby ustawić punkt przerwania na końcu odzyskiwania pamięci

- W programie WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:

  **mscorwks BP! WKS:: GCHeap:: RestartEE "j (dwo (mscorwks! WKS:: GCHeap:: GcCondemnedGeneration) = = 2) "KB"; " g ""**

  gdzie **GcCondemnedGeneration** jest ustawiona na żądaną generację. To polecenie wymaga symboli prywatnych.

  To polecenie wymusza przerwanie, jeśli **RestartEE** jest wykonywane po odbraniu obiektów generacji 2 do wyrzucania elementów bezużytecznych.

  W wyrzucaniu elementów bezużytecznych serwera tylko jedno wywołanie wątku **RestartEE**, więc punkt przerwania wystąpi tylko raz podczas wyrzucania elementów bezużytecznych generacji 2.

## <a name="performance-check-procedures"></a>Procedury sprawdzania wydajności

W tej sekcji opisano następujące procedury umożliwiające odizolowanie przyczyny problemu z wydajnością:

- [Ustal, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych.](#IsGC)

- [Ustal, czy jest zarządzany wyjątek braku pamięci.](#OOMIsManaged)

- [Określ ilość pamięci wirtualnej, która może być zarezerwowana.](#GetVM)

- [Należy określić, czy jest dostępna wystarczająca ilość pamięci fizycznej.](#Physical)

- [Określ ilość pamięci, która jest zatwierdzana przez stertę zarządzaną.](#ManagedHeapCommit)

- [Określ ilość pamięci, jaką rezerwuje sterta zarządza.](#ManagedHeapReserve)

- [Określ duże obiekty w generacji 2.](#ExamineGen2)

- [Określanie odwołań do obiektów.](#ObjRef)

- [Ustal, czy finalizator został uruchomiony.](#Induce)

- [Ustal, czy istnieją obiekty oczekujące na sfinalizowanie.](#Finalize)

- [Określ ilość wolnego miejsca w zarządzanym stosie.](#Fragmented)

- [Określ liczbę przypiętych obiektów.](#Pinned)

- [Określ długość czasu w wyrzucaniu elementów bezużytecznych.](#TimeInGC)

- [Określ, co wyzwoliło wyrzucanie elementów bezużytecznych.](#Triggered)

- [Ustal, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych.](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Aby określić, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych

- Zapoznaj się z poniższymi dwoma licznikami wydajności pamięci:

  - **Czas (%) w usłudze GC**. Wyświetla procent czasu, który upłynął podczas wykonywania wyrzucania elementów bezużytecznych po ostatnim cyklu wyrzucania elementów bezużytecznych. Użyj tego licznika, aby określić, czy moduł wyrzucania elementów bezużytecznych poświęca zbyt dużo czasu na udostępnienie zarządzanej przestrzeni sterty. Jeśli czas spędzony na wyrzucaniu elementów bezużytecznych jest stosunkowo niski, może to wskazywać na problem z zasobem poza zarządzaną stertą. Ten licznik może nie być dokładny, gdy jest wykorzystywane współbieżne lub w tle odzyskiwanie pamięci.

  - Liczba **bajtów zadeklarowanych łącznie**. Wyświetla ilość pamięci wirtualnej aktualnie zatwierdzonej przez moduł wyrzucania elementów bezużytecznych. Użyj tego licznika, aby określić, czy pamięć wykorzystywana przez moduł wyrzucania elementów bezużytecznych jest nadmierną częścią pamięci używanej przez aplikację.

  Większość liczników wydajności pamięci jest aktualizowanych na końcu każdego wyrzucania elementów bezużytecznych. W związku z tym mogą nie odzwierciedlać bieżących warunków, o których chcesz uzyskać informacje.

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Aby określić, czy wyjątek braku pamięci jest zarządzany

1. W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz polecenie Print Exception (**PE**):

    **! PE**

    Jeśli wyjątek jest zarządzany, <xref:System.OutOfMemoryException> jest wyświetlany jako typ wyjątku, jak pokazano w poniższym przykładzie.

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. Jeśli dane wyjściowe nie określają wyjątku, należy określić, z którego wątku jest wykonywany wyjątek braku pamięci. Wpisz następujące polecenie w debugerze, aby pokazać wszystkie wątki ze stosami wywołań:

    **~\*KB**

    Wątek ze stosem, który zawiera wywołania wyjątku jest wskazywany przez argument `RaiseTheException`. Jest to obiekt wyjątku zarządzanego.

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. Poniższe polecenie służy do zrzutu zagnieżdżonych wyjątków.

    **! PE — zagnieżdżone**

    Jeśli nie występują żadne wyjątki, wyjątek braku pamięci pochodzący z kodu niezarządzanego.

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Aby określić ilość pamięci wirtualnej, którą można zarezerwować

- W programie WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby uzyskać największy wolny region:

  **! Address — podsumowanie**

  Jest wyświetlany największy wolny region, jak pokazano w poniższych danych wyjściowych.

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  W tym przykładzie rozmiar największego wolnego regionu wynosi około 24000 KB (3A980 w formacie szesnastkowym). Ten region jest znacznie mniejszy niż to, co wymagają Moduł wyrzucania elementów bezużytecznych dla segmentu.

  —lub—

- Użyj **vmstat** polecenia:

  **! vmstat**

  Największy wolny region jest największą wartością w kolumnie MAXIMUM, jak pokazano w poniższych danych wyjściowych.

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a>Aby określić, czy jest dostępna wystarczająca ilość pamięci fizycznej

1. Uruchom Menedżera zadań systemu Windows.

2. Na karcie **wydajność** Przyjrzyj się wartości zatwierdzonej. (W systemie Windows 7 zapoznaj się z tematem **zatwierdzenie (KB)** w **grupie system**.)

    Jeśli **Suma** zbliża się do **limitu**, zaczyna brakować pamięci fizycznej.

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Aby określić ilość pamięci, która jest zatwierdzana przez stertę zarządzaną

- Użyj licznika wydajności `# Total committed bytes` pamięci, aby uzyskać liczbę bajtów, które są zatwierdzane przez stertę zarządzaną. Moduł zbierający elementy bezużyteczne zatwierdza fragmenty segmentów w razie konieczności, nie wszystkie w tym samym czasie.

  > [!NOTE]
  > Nie należy używać `# Bytes in all Heaps` licznika wydajności, ponieważ nie reprezentuje rzeczywiste użycie pamięci przez stos zarządzany. Rozmiar generacji jest uwzględniany w tej wartości i jest w rzeczywistości rozmiarem jego progu, czyli rozmiarem, który wywołuje wyrzucanie elementów bezużytecznych, jeśli generacja jest zapełniona obiektami. W związku z tym ta wartość jest zwykle równa zero.

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Aby określić ilość pamięci, jaką rezerwuje sterta zarządza

- Użyj licznika wydajności `# Total reserved bytes` pamięci.

  Moduł wyrzucania elementów bezużytecznych rezerwuje pamięć w segmentach i można określić, gdzie zostanie uruchomiony segment przy użyciu polecenia **eeheap** .

  > [!IMPORTANT]
  > Chociaż można określić ilość pamięci przydzielanej przez moduł wyrzucania elementów bezużytecznych dla każdego segmentu, rozmiar segmentu jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami. Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:

  **! eeheap — GC**

  Wynik jest następujący.

  ```console
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

  Adresy wskazywane przez "segment" są adresami początkowymi segmentów.

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a>Aby określić duże obiekty w generacji 2

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:

  **! DumpHeap — stat**

  Jeśli zarządzana sterta jest duża, **DumpHeap** może chwilę potrwać.

  Możesz rozpocząć analizowanie z ostatnich kilku wierszy danych wyjściowych, ponieważ zawierają one listę obiektów, które używają najwięcej miejsca. Na przykład:

  ```console
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

  Ostatni wymieniony obiekt jest ciągiem i zajmuje najwięcej miejsca. Możesz sprawdzić swoją aplikację, aby zobaczyć, jak można zoptymalizować obiekty ciągu. Aby wyświetlić ciągi z zakresu od 150 do 200 bajtów, wpisz następujące polecenie:

  **! DumpHeap-Type System. String — min 150 — maks 200**

  Poniżej przedstawiono przykładowe wyniki.

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  Użycie liczby całkowitej zamiast ciągu dla identyfikatora może być bardziej wydajne. Jeśli ten sam ciąg jest powtarzany tysiące razy, weź pod uwagę ciąg InterNIC. Aby uzyskać więcej informacji na temat informowania o ciągach, zobacz temat referencyjny dla metody <xref:System.String.Intern%2A?displayProperty=nameWithType>.

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a>Aby określić odwołania do obiektów

- W programie WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby wyświetlić listę odwołań do obiektów:

  **!gcroot**

  `-or-`

- Aby określić odwołania dla określonego obiektu, Dołącz adres:

  **!gcroot 1c37b2ac**

  Elementy główne znalezione na stosach mogą być fałszywie pozytywne. Aby uzyskać więcej informacji, użyj polecenia `!help gcroot`.

  ```console
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

  Ukończenie polecenia **gcroot** może zająć dużo czasu. Wszelkie obiekty, które nie są odzyskiwane przez wyrzucanie elementów bezużytecznych, są obiektem aktywnym. Oznacza to, że część elementu głównego jest bezpośrednio lub pośrednio umieszczana na obiekcie, więc **gcroot** powinna zwracać informacje o ścieżce do obiektu. Należy sprawdzić, czy wykresy zostały zwrócone, i sprawdzić, dlaczego te obiekty nadal są przywoływane.

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Aby określić, czy finalizator został uruchomiony

- Uruchom program testowy, który zawiera następujący kod:

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  Jeśli test rozwiąże problem, oznacza to, że moduł wyrzucania elementów bezużytecznych nie odzyskał obiektów, ponieważ finalizatory dla tych obiektów zostały zawieszone. Metoda <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> umożliwia finalizatorom ukończenie zadań i rozwiązanie problemu.

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Aby określić, czy istnieją obiekty oczekujące na sfinalizowanie

1. W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:

    **!finalizequeue**

    Przyjrzyj się liczbie obiektów, które są gotowe do finalizacji. Jeśli liczba jest wysoka, należy zapoznać się z tym, dlaczego tacy finalizatory nie mogą postępować w ogóle lub nie mogą postępować wystarczająco szybko.

2. Aby uzyskać dane wyjściowe wątków, wpisz następujące polecenie:

    **wątki — specjalne**

    To polecenie zapewnia dane wyjściowe, takie jak poniższe.

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    Wątek finalizatora wskazuje, który finalizator, jeśli istnieje, jest obecnie uruchamiany. Gdy wątek finalizatora nie działa żadnych finalizatorów, oczekuje na zdarzenie, aby je wypowiedzieć. Większość czasu zobaczysz wątek finalizatora w tym stanie, ponieważ działa on w THREAD_HIGHEST_PRIORITY i będzie można zakończyć pracę finalizatorów, jeśli istnieją, bardzo szybko.

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Aby określić ilość wolnego miejsca w zarządzanym stosie

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:

  **! DumpHeap-Type Free-stat**

  To polecenie wyświetla łączny rozmiar wszystkich wolnych obiektów na stercie zarządzanym, jak pokazano w poniższym przykładzie.

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- Aby określić ilość wolnego miejsca w generacji 0, wpisz następujące polecenie, aby uzyskać informacje o zużyciu pamięci według generacji:

  **! eeheap — GC**

  To polecenie wyświetla dane wyjściowe podobne do poniższego. Ostatni wiersz przedstawia segment tymczasowych.

  ```console
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

- Oblicz miejsce używane przez generację 0:

  **? 49e05d04-0x49521f8c**

  Wynik jest następujący. Generacja 0 wynosi około 9 MB.

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- Następujące polecenie zrzuca wolne miejsce w zakresie generacji 0:

  **! DumpHeap-Type Free-stat 0x49521f8c 49e05d04**

  Wynik jest następujący.

  ```console
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

  Te dane wyjściowe pokazują, że część generacji 0 sterty używa dla obiektów wartości 9 MB i ma 7 MB wolnego miejsca. Ta analiza pokazuje zakres, do którego generacja 0 przyczynia się do fragmentacji. Ta ilość użycia sterty powinna być obniżona od łącznej kwoty jako przyczyny fragmentacji obiektów długoterminowych.

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a>Aby określić liczbę przypiętych obiektów

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie:

  **!gchandles**

  Wyświetlane dane statystyczne zawierają liczbę przypiętych dojść, jak pokazano w poniższym przykładzie.

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>Aby określić długość czasu w wyrzucaniu elementów bezużytecznych

- Przejrzyj licznik wydajności pamięci `% Time in GC`.

  Wartość jest obliczana przy użyciu przykładowego interwału czasu. Ponieważ liczniki są aktualizowane na końcu każdego wyrzucania elementów bezużytecznych, bieżąca próbka będzie miała taką samą wartość jak w poprzednim przykładzie, jeśli nie wystąpiły żadne kolekcje w interwale.

  Czas zbierania jest uzyskiwany przez pomnożenie przykładowego czasu interwału z wartością procentową.

  Poniższe dane pokazują cztery interwały próbkowania wynoszące dwie sekundy w przypadku studiów 8-sekundowych. Kolumny `Gen0`, `Gen1`i `Gen2` przedstawiają liczbę kolekcji elementów bezużytecznych, które wystąpiły w tym interwale dla tej generacji.

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  Te informacje nie są wyświetlane, gdy wystąpiło wyrzucanie elementów bezużytecznych, ale można określić liczbę wyrzucania elementów bezużytecznych, które wystąpiły w przedziale czasu. Zakładając, że najgorszy przypadek, zbieranie elementów bezużytecznych dziesiątki generacji 0 zakończyło się na początku drugiego interwału, a zbieranie elementów bezużytecznych generacji 0 zakończyło się po upływie piątego interwału. Czas między końcem dziesiątego i końca jedenastego wyrzucania elementów bezużytecznych wynosi około 2 sekundy, a licznik wydajności pokazuje 3%, więc czas trwania wyrzucania elementów bezużytecznych generacji 0 wynosi (2 sekundy * 3% = 60ms).

  W tym przykładzie wystąpiły 5 okresów.

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  Druga generacja elementów bezużytecznych generacji 2 rozpoczęła się w trzecim interwale i została zakończona z piątym interwałem. Przy założeniu najgorszego przypadku ostatnie wyrzucanie elementów bezużytecznych dotyczyło kolekcji generacji 0, która została zakończona na początku drugiego interwału, a wyrzucanie elementów bezużytecznych generacji 2 zakończyło się z końcem piątego interwału. W związku z tym czas między końcem wyrzucania elementów bezużytecznych generacji 0 a końcem wyrzucania elementów bezużytecznych generacji 2 wynosi 4 sekundy. Ponieważ licznik `% Time in GC` jest 20%, maksymalna ilość czasu, jaką może pobrać wyrzucanie elementów bezużytecznych generacji 2, to (4 sekundy * 20% = 800ms).

- Alternatywnie można określić długość wyrzucania elementów bezużytecznych za pomocą [zdarzeń ETW wyrzucania elementów](../../../docs/framework/performance/garbage-collection-etw-events.md)bezużytecznych i analizować informacje w celu określenia czasu trwania odzyskiwania pamięci.

  Na przykład następujące dane przedstawiają sekwencję zdarzeń, która wystąpiła podczas niewspółbieżnego wyrzucania elementów bezużytecznych.

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  Wstrzymanie wątku zarządzanego zajęło 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).

  Rzeczywista wyrzucanie elementów bezużytecznych zajęło MS (`GCEnd_V1` – `GCStart_V1`).

  Wznowienie zarządzanych wątków trwało 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).

  Poniższe dane wyjściowe przedstawiają przykład do wyrzucania elementów bezużytecznych w tle, a także zawierają pola procesu, wątku i zdarzenia. (Nie wszystkie dane są wyświetlane).

  ```console
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

  Zdarzenie `GCStart_V1` w 42504816 wskazuje, że jest to wyrzucanie elementów bezużytecznych w tle, ponieważ ostatnie pole jest `1`. To nie spowoduje odrzucania elementów bezużytecznych. 102019.

  Zdarzenie `GCStart` występuje, ponieważ istnieje potrzeba tymczasowej wyrzucania elementów bezużytecznych przed rozpoczęciem wyrzucania elementów bezużytecznych w tle. To nie spowoduje odrzucania elementów bezużytecznych. 102020.

  O 42514170, wyrzucanie elementów bezużytecznych. 102020 kończy się. Zarządzane wątki są ponownie uruchamiane w tym momencie. Jest to wykonywane w wątku 4372, który wyzwolił to wyrzucanie elementów bezużytecznych w tle.

  W wątku 4744 następuje zawieszenie. Jest to jedyny czas, w którym wyrzucanie elementów bezużytecznych w tle ma wstrzymywać zarządzane wątki. Ten czas trwania jest około 99ms ((63784407-63685394)/1000).

  Zdarzenie `GCEnd` dla wyrzucania elementów bezużytecznych w tle ma wartość 89931423. Oznacza to, że wyrzucanie elementów bezużytecznych w tle zostało ostatnio za47seconds ((89931423-42504816)/1000).

  Gdy zarządzane wątki są uruchomione, można zobaczyć dowolną liczbę tymczasowych kolekcji elementów bezużytecznych.

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a>Aby określić, które wyzwolone odzyskiwanie pamięci

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debuggera SOS wpisz następujące polecenie, aby wyświetlić wszystkie wątki z stosami wywołań:

  **~\*KB**

  To polecenie wyświetla dane wyjściowe podobne do poniższego.

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  Jeśli wyrzucanie elementów bezużytecznych zostało spowodowane przez powiadomienie o niskim poziomie pamięci z systemu operacyjnego, stos wywołań jest podobny, z tą różnicą, że wątek jest wątkiem finalizatora. Wątek finalizatora pobiera asynchroniczne powiadomienie o niskiej ilości pamięci i wywołuje wyrzucanie elementów bezużytecznych.

  Jeśli wyrzucanie elementów bezużytecznych zostało spowodowane przez alokację pamięci, stos pojawia się w następujący sposób:

  ```console
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

  Chwilowe wywołania pomocnika just in Time (`JIT_New*`) `GCHeap::GarbageCollectGeneration`. Jeśli okaże się, że wyrzucanie elementów bezużytecznych generacji 2 jest spowodowane przez przydziały, należy określić, które obiekty są zbierane przez wyrzucanie elementów bezużytecznych generacji 2 i jak można je uniknąć. Oznacza to, że chcesz określić różnicę między początkiem i końcem wyrzucania elementów bezużytecznych generacji 2 oraz obiektami, które spowodowały wygenerowanie kolekcji generacji 2.

  Na przykład wpisz następujące polecenie w debugerze, aby wyświetlić początek kolekcji generacji 2:

  **! DumpHeap — stat**

  Przykładowe dane wyjściowe (w skrócie, aby pokazać obiekty, które używają najwięcej spacji):

  ```console
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

  **! DumpHeap — stat**

  Przykładowe dane wyjściowe (w skrócie, aby pokazać obiekty, które używają najwięcej spacji):

  ```console
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

  Obiekty `double[]` zniknęły z końca danych wyjściowych, co oznacza, że zostały zebrane. Te obiekty są uwzględniane przez około 70 MB. Pozostałe obiekty nie zmieniły się. W związku z tym te `double[]` obiekty były przyczyną tego, że wystąpiło wyrzucanie elementów bezużytecznych generacji 2. Następnym krokiem jest określenie, dlaczego `double[]` obiekty znajdują się tam i dlaczego zapadły. Możesz polecić deweloperowi kodu, z którego pochodzą te obiekty, lub użyć polecenia **gcroot** .

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Aby określić, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych

- Należy skorelować wartość licznika wydajności `% Time in GC` pamięci z czasem przetwarzania.

  Jeśli wartość `% Time in GC` zostanie nadana w tym samym czasie co czas procesu, wyrzucanie elementów bezużytecznych spowoduje wysokie użycie procesora CPU. W przeciwnym razie należy profilować aplikację, aby znaleźć miejsce wystąpienia wysokiego użycia.

## <a name="see-also"></a>Zobacz także

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
