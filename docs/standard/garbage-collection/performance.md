---
title: Odzyskiwanie pamięci i wydajność
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 72cf742aae26f9441229b355dc6e70da7a5fc9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75900582"
---
# <a name="garbage-collection-and-performance"></a>Odzyskiwanie pamięci i wydajność

W tym temacie opisano problemy związane z wyrzucaniem elementów bezużytecznych i użycie pamięci. Rozwiązuje problemy, które odnoszą się do zarządzanego sterty i wyjaśnia, jak zminimalizować wpływ wyrzucania elementów bezużytecznych na aplikacje. Każdy problem ma łącza do procedur, których można użyć do zbadania problemów.

## <a name="performance-analysis-tools"></a>Narzędzia do analizy wydajności

W poniższych sekcjach opisano narzędzia, które są dostępne do badania użycia pamięci i problemów z wyrzucaniem elementów bezużytecznych. [Procedury](#performance-check-procedures) przedstawione w dalszej części tego tematu odnoszą się do tych narzędzi.

### <a name="memory-performance-counters"></a>Liczniki wydajności pamięci

Liczniki wydajności służy do zbierania danych wydajności. Aby uzyskać instrukcje, zobacz [Profilowanie w czasie wykonywania](../../../docs/framework/debug-trace-profile/runtime-profiling.md). Kategoria pamięci CLR .NET liczników wydajności, zgodnie z opisem w [licznikach wydajności w ramach .NET Framework,](../../../docs/framework/debug-trace-profile/performance-counters.md)zawiera informacje o modułodarze pamięci.

### <a name="debugging-with-sos"></a>Debugowanie za pomocą SOS

Za pomocą [debugera systemu Windows (WinDbg)](/windows-hardware/drivers/debugger/index) można sprawdzić obiekty na zarządzanym stercie.

Aby zainstalować usługę WinDbg, zainstaluj narzędzia debugowania dla systemu Windows ze strony Narzędzia do [pobierania debugowania dla systemu Windows.](/windows-hardware/drivers/debugger/debugger-download-tools)

### <a name="garbage-collection-etw-events"></a>Zdarzenia ETW odzyskiwania pamięci

Śledzenie zdarzeń dla systemu Windows (ETW) jest systemem śledzenia, który uzupełnia profilowanie i debugowanie pomocy technicznej świadczonej przez .NET Framework. Począwszy od .NET Framework 4, [wyrzucanie elementów bezużytecznych zdarzenia ETW](../../../docs/framework/performance/garbage-collection-etw-events.md) przechwytywania przydatnych informacji do analizowania sterty zarządzanej z statystycznego punktu widzenia. Na przykład `GCStart_V1` zdarzenie, które jest wywoływane, gdy wyrzucanie elementów bezużytecznych ma wystąpić, zawiera następujące informacje:

- Która generacja obiektów jest zbierana.

- Co wyzwoliło wyrzucania elementów bezużytecznych.

- Typ wyrzucania elementów bezużytecznych (równoczesny lub niewspółbieżny).

Rejestrowanie zdarzeń ETW jest efektywne i nie będzie maskować żadnych problemów z wydajnością związanych z wyrzucaniem elementów bezużytecznych. Proces może dostarczyć własne zdarzenia w połączeniu ze zdarzeniami ETW. Po zalogowaniu zarówno zdarzenia aplikacji, jak i zdarzenia wyrzucania elementów bezużytecznych mogą być skorelowane, aby określić, jak i kiedy występują problemy ze stertami. Na przykład aplikacja serwera może zapewnić zdarzenia na początku i na końcu żądania klienta.

### <a name="the-profiling-api"></a>Interfejs API profilowania

Interfejsy profilowania języka wspólnego (CLR) zawierają szczegółowe informacje o obiektach, których dotyczy problem podczas wyrzucania elementów bezużytecznych. Profiler może być powiadamiany, gdy wyrzucanie elementów bezużytecznych rozpoczyna się i kończy. Może dostarczać raporty dotyczące obiektów na zarządzanym stercie, w tym identyfikację obiektów w każdej generacji. Aby uzyskać więcej informacji, zobacz [Omówienie profilowania](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).

Profilerzy mogą dostarczyć wyczerpujących informacji. Jednak złożone profilery mogą potencjalnie modyfikować zachowanie aplikacji.

### <a name="application-domain-resource-monitoring"></a>Monitorowanie zasobów domen aplikacji

Począwszy od .NET Framework 4, Monitorowanie zasobów domeny aplikacji (ARM) umożliwia hostom monitorowanie użycia procesora CPU i pamięci według domeny aplikacji. Aby uzyskać więcej informacji, zobacz [Monitorowanie zasobów domeny aplikacji](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).

## <a name="troubleshooting-performance-issues"></a>Rozwiązywanie problemów z wydajnością

Pierwszym krokiem jest [ustalenie, czy problem jest rzeczywiście wyrzucania elementów bezużytecznych](#IsGC). Jeśli okaże się, że jest, wybierz z poniższej listy, aby rozwiązać problem.

- [Wyjątek poza pamięcią jest generowany](#Issue_OOM)

- [Proces zużywa zbyt dużo pamięci](#Issue_TooMuchMemory)

- [Moduł zbierający elementy bezużyteczne nie odzyskuje obiektów wystarczająco szybko](#Issue_NotFastEnough)

- [Zarządzana sterta jest zbyt rozdrobniona](#Issue_Fragmentation)

- [Przerwy w wyrzucaniu elementów bezużytecznych są zbyt długie](#Issue_LongPauses)

- [Generacja 0 jest zbyt duża](#Issue_Gen0)

- [Użycie procesora CPU podczas wyrzucania elementów bezużytecznych jest zbyt wysokie](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a>Problem: Wyjątek braku pamięci jest generowany

Istnieją dwa uzasadnione przypadki, <xref:System.OutOfMemoryException> w których udało się wywalić:

- Zabraknie pamięci wirtualnej.

  Moduł zbierający elementy bezużyteczne przydziela pamięć z systemu w segmentach o wstępnie określonym rozmiarze. Jeśli alokacja wymaga dodatkowego segmentu, ale w przestrzeni pamięci wirtualnej procesu nie ma ciągłego wolnego bloku, alokacja zarządzanego stosu zakończy się niepowodzeniem.

- Nie mając wystarczającej ilości pamięci fizycznej do przydzielenia.

|Kontrole wydajności|
|------------------------|
|[Określ, czy wyjątek braku pamięci jest zarządzany.](#OOMIsManaged)<br /><br /> [Określ, ile pamięci wirtualnej można zarezerwować.](#GetVM)<br /><br /> [Określ, czy jest wystarczająca ilość pamięci fizycznej.](#Physical)|

Jeśli ustalisz, że wyjątek nie jest zgodny z prawem, skontaktuj się z działem obsługi klienta i pomocy technicznej firmy Microsoft, aby uzyskać następujące informacje:

- Stos z zarządzanym wyjątkiem braku pamięci.

- Zrzut pełnej pamięci.

- Dane, które udowadniają, że nie jest to uzasadniony wyjątek braku pamięci, w tym dane, które pokazują, że pamięć wirtualna lub fizyczna nie jest problemem.

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a>Problem: Proces zużywa zbyt dużo pamięci

Typowym założeniem jest, że wyświetlanie użycia pamięci na karcie **Wydajność** Menedżera zadań systemu Windows może wskazywać, kiedy jest używana zbyt dużo pamięci. Jednak ten wyświetlacz odnosi się do zestawu roboczego; nie dostarcza informacji o wykorzystaniu pamięci wirtualnej.

Jeśli stwierdzisz, że problem jest spowodowany przez zarządzane sterty, należy zmierzyć zarządzane sterty w czasie, aby określić wszelkie wzorce.

Jeśli stwierdzisz, że problem nie jest spowodowany przez zarządzane sterty, należy użyć debugowania macierzystego.

|Kontrole wydajności|
|------------------------|
|[Określ, ile pamięci wirtualnej można zarezerwować.](#GetVM)<br /><br /> [Określ, ile pamięci zatwierdza zarządzana sterta.](#ManagedHeapCommit)<br /><br /> [Określ, ile pamięci rezerwuje zarządzany stos.](#ManagedHeapReserve)<br /><br /> [Określ duże obiekty w generacji 2.](#ExamineGen2)<br /><br /> [Określ odwołania do obiektów.](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>Problem: Moduł zbierający elementy bezużyteczne nie odzyskuje wystarczająco szybko obiektów

Gdy wydaje się, że obiekty nie są odzyskiwane zgodnie z oczekiwaniami dla wyrzucania elementów bezużytecznych, należy określić, czy istnieją silne odwołania do tych obiektów.

Ten problem może również wystąpić, jeśli nie było wyrzucania elementów bezużytecznych dla generacji, która zawiera martwy obiekt, co oznacza, że finalizator dla martwego obiektu nie został uruchomiony. Na przykład jest to możliwe, gdy używasz aplikacji jednowątkowego mieszkania (STA) i wątku, który usług kolejki finalizatora nie można wywołać do niego.

|Kontrole wydajności|
|------------------------|
|[Sprawdź odwołania do obiektów.](#ObjRef)<br /><br /> [Określ, czy finalizator został uruchomiony.](#Induce)<br /><br /> [Określ, czy istnieją obiekty oczekujące na sfinalizowanie.](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a>Problem: Sterta zarządzana jest zbyt rozdrobniona

Poziom fragmentacji jest obliczany jako stosunek wolnego miejsca do całkowitej przydzielonej pamięci dla generacji. W przypadku generacji 2 dopuszczalny poziom fragmentacji wynosi nie więcej niż 20%. Ponieważ generacja 2 może być bardzo duża, stosunek fragmentacji jest ważniejszy niż wartość bezwzględna.

Posiadanie dużej ilości wolnego miejsca w generacji 0 nie stanowi problemu, ponieważ jest to generacja, w której przydzielane są nowe obiekty.

Fragmentacja zawsze występuje w stercie dużych obiektów, ponieważ nie jest skompaktowany. Wolne obiekty, które sąsiadują są naturalnie zwinięte w jednym miejscu, aby zaspokoić żądania alokacji dużych obiektów.

Fragmentacja może stać się problemem w generacji 1 i generacji 2. Jeśli te generacje mają dużą ilość wolnego miejsca po wyrzucania elementów bezużytecznych, użycie obiektu aplikacji może wymagać modyfikacji i należy rozważyć ponownej oceny okresu istnienia obiektów długoterminowych.

Nadmierne przypinanie obiektów może zwiększyć fragmentację. Jeśli fragmentacja jest wysoka, zbyt wiele obiektów można było przypiąć.

Jeśli fragmentacja pamięci wirtualnej uniemożliwia modułowi odśmiecania pamięci dodawanie segmentów, przyczyny mogą być jedną z następujących czynności:

- Częste załadunek i rozładunek wielu małych zespołów.

- Przechowywanie zbyt wielu odwołań do obiektów COM podczas współdziałania z kodem niezarządzanym.

- Tworzenie dużych obiektów przejściowych, co powoduje, że sterty dużych obiektów do przydzielenia i wolne segmenty sterty często.

  Podczas hostowania CLR, aplikacja może zażądać, aby moduł zbierający elementy bezużyteczne zachował swoje segmenty. Zmniejsza to częstotliwość alokacji segmentów. Jest to realizowane przy użyciu flagi STARTUP_HOARD_GC_VM w [wyliczeniu STARTUP_FLAGS](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).

|Kontrole wydajności|
|------------------------|
|[Określ ilość wolnego miejsca w zarządzanym stercie.](#Fragmented)<br /><br /> [Określ liczbę przypiętych obiektów.](#Pinned)|

Jeśli uważasz, że nie ma uzasadnionej przyczyny fragmentacji, skontaktuj się z działem obsługi klienta i pomocy technicznej firmy Microsoft.

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a>Problem: Przerwy w wyrzucaniu elementów bezużytecznych są zbyt długie

Wyrzucanie elementów bezużytecznych działa w miękkim czasie rzeczywistym, więc aplikacja musi być w stanie tolerować niektóre przerwy. Kryterium dla miękkiego czasu rzeczywistego jest to, że 95% operacji musi zakończyć się na czas.

W równoczesnych wyrzucania elementów bezużytecznych zarządzanych wątków mogą być uruchamiane podczas zbierania, co oznacza, że pauzy są bardzo minimalne.

Efemericzne wyrzucania elementów bezużytecznych (generacje 0 i 1) trwają tylko kilka milisekund, więc zmniejszanie pauz zwykle nie jest możliwe. Jednak można zmniejszyć pauzy w kolekcji generacji 2, zmieniając wzorzec żądań alokacji przez aplikację.

Inną, dokładniejsza, metoda jest użycie [wyrzucania elementów bezużytecznych ETW zdarzeń](../../../docs/framework/performance/garbage-collection-etw-events.md). Chronometraż kolekcji można znaleźć, dodając różnice sygnatury czasowej dla sekwencji zdarzeń. Cała sekwencja kolekcji zawiera zawieszenie aparatu wykonywania, samego wyrzucania elementów bezużytecznych i wznowienie aparatu wykonywania.

Za pomocą [powiadomień o wyrzucaniu elementów bezużytecznych](../../../docs/standard/garbage-collection/notifications.md) można określić, czy serwer ma mieć kolekcję 2 generacji i czy przekierowanie żądań do innego serwera może ułatwić wszelkie problemy z przerwami.

|Kontrole wydajności|
|------------------------|
|[Określ czas w wyrzucania elementów bezużytecznych.](#TimeInGC)<br /><br /> [Określ, co spowodowało wyrzucanie elementów bezużytecznych.](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a>Problem: Generacja 0 jest zbyt duża

Generacja 0 może mieć większą liczbę obiektów w systemie 64-bitowym, szczególnie w przypadku korzystania z wyrzucania elementów bezużytecznych serwera zamiast wyrzucania elementów bezużytecznych stacji roboczej. Jest tak, ponieważ próg wyzwalania generacji 0 wyrzucania elementów bezużytecznych jest wyższa w tych środowiskach, a kolekcji generacji 0 można uzyskać znacznie większe. Wydajność jest zwiększona, gdy aplikacja przydziela więcej pamięci przed wyzwoleniewyrzucanie elementów bezużytecznych.

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>Problem: Użycie procesora PODCZAS wyrzucania elementów bezużytecznych jest zbyt wysokie

Użycie procesora CPU będzie wysokie podczas wyrzucania elementów bezużytecznych. Jeśli znaczna ilość czasu procesu jest spędzana w wyrzucania elementów bezużytecznych, liczba kolekcji jest zbyt częste lub kolekcji trwa zbyt długo. Zwiększony wskaźnik alokacji obiektów na zarządzanym stercie powoduje, że wyrzucanie elementów bezużytecznych występuje częściej. Zmniejszenie szybkości alokacji zmniejsza częstotliwość wyrzucania elementów bezużytecznych.

Stawki alokacji można `Allocated Bytes/second` monitorować przy użyciu licznika wydajności. Aby uzyskać więcej informacji, zobacz [liczniki wydajności w platformie .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).

Czas trwania kolekcji jest przede wszystkim czynnikiem liczby obiektów, które przetrwać po alokacji. Moduł zbierający elementy bezużyteczne musi przejść przez dużą ilość pamięci, jeśli wiele obiektów pozostaje do zebrania. Praca nad zagęszczeniem ocalałych jest czasochłonna. Aby określić, ile obiektów zostały obsłużone podczas zbierania, ustaw punkt przerwania w debugerze na końcu wyrzucania elementów bezużytecznych dla określonej generacji.

|Kontrole wydajności|
|------------------------|
|[Określ, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych.](#HighCPU)<br /><br /> [Ustaw punkt przerwania na końcu wyrzucania elementów bezużytecznych.](#GenBreak)|

## <a name="troubleshooting-guidelines"></a>Wskazówki dotyczące rozwiązywania problemów

W tej sekcji opisano wskazówki, które należy wziąć pod uwagę podczas rozpoczynania dochodzenia.

### <a name="workstation-or-server-garbage-collection"></a>Stacja robocza lub wyrzucanie elementów bezużytecznych serwera

Określ, czy używasz poprawnego typu wyrzucania elementów bezużytecznych. Jeśli aplikacja używa wielu wątków i wystąpień obiektów, należy użyć wyrzucania elementów bezużytecznych serwera zamiast wyrzucania elementów bezużytecznych stacji roboczej. Wyrzucanie elementów bezużytecznych serwera działa na wiele wątków, podczas gdy wyrzucanie elementów bezużytecznych stacji roboczej wymaga wielu wystąpień aplikacji do uruchamiania własnych wątków wyrzucania elementów bezużytecznych i konkurowania o czas procesora CPU.

Aplikacja, która ma niskie obciążenie i która wykonuje zadania rzadko w tle, takich jak usługa, można użyć wyrzucania elementów bezużytecznych stacji roboczej z równoczesnych wyrzucania elementów bezużytecznych wyłączone.

### <a name="when-to-measure-the-managed-heap-size"></a>Kiedy mierzyć rozmiar zarządzanej sterty

Chyba że używasz profilera, trzeba będzie ustalić spójny wzór pomiaru, aby skutecznie diagnozować problemy z wydajnością. Należy wziąć pod uwagę następujące punkty, aby ustanowić harmonogram:

- Jeśli zmierzysz po generacji 2 wyrzucania elementów bezużytecznych, cały zarządzany sterty będzie wolny od śmieci (martwe obiekty).

- Jeśli zmierzysz natychmiast po generacji 0 wyrzucania elementów bezużytecznych, obiekty w generacji 1 i 2 nie będą jeszcze zbierane.

- Jeśli zmierzysz bezpośrednio przed wyrzucania elementów bezużytecznych, będzie zmierzyć jak najwięcej alokacji, jak to możliwe przed rozpoczęciem wyrzucania elementów bezużytecznych.

- Pomiar podczas wyrzucania elementów bezużytecznych jest problematyczny, ponieważ struktury danych modułu odśmiecania elementów bezużytecznych nie są w prawidłowym stanie dla przechodzenia i mogą nie być w stanie podać pełnych wyników. Jest to celowe.

- Gdy używasz wyrzucania elementów bezużytecznych stacji roboczej z równoczesnym wyrzucaniem elementów bezużytecznych, odzyskane obiekty nie są kompaktowane, więc rozmiar sterty może być taki sam lub większy (fragmentacja może sprawić, że będzie większa).

- Równoczesne wyrzucanie elementów bezużytecznych w generacji 2 jest opóźnione, gdy obciążenie pamięci fizycznej jest zbyt wysokie.

W poniższej procedurze opisano sposób ustawiania punktu przerwania, dzięki czemu można zmierzyć zarządzany stos.

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>Aby ustawić punkt przerwania na końcu wyrzucania elementów bezużytecznych

- W usyliwiu WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:

  **bp mscorwks! WKS::GCHeap::RestartEE "j (dwo(mscorwks! WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';' g'"**

  gdzie **GcCondemnedGeneration** jest ustawiony na żądane pokolenie. To polecenie wymaga symboli prywatnych.

  To polecenie wymusza przerwę, jeśli **RestartEE** jest wykonywany po generacji 2 obiekty zostały odzyskane do wyrzucania elementów bezużytecznych.

  W wyrzucania elementów bezużytecznych serwera tylko jeden wątek wywołuje **RestartEE**, więc punkt przerwania wystąpi tylko raz podczas wyrzucania elementów bezużytecznych generacji 2.

## <a name="performance-check-procedures"></a>Procedury sprawdzania wydajności

W tej sekcji opisano następujące procedury wyizolowania przyczyny problemu z wydajnością:

- [Określ, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych.](#IsGC)

- [Określ, czy wyjątek braku pamięci jest zarządzany.](#OOMIsManaged)

- [Określ, ile pamięci wirtualnej można zarezerwować.](#GetVM)

- [Określ, czy jest wystarczająca ilość pamięci fizycznej.](#Physical)

- [Określ, ile pamięci zatwierdza zarządzana sterta.](#ManagedHeapCommit)

- [Określ, ile pamięci rezerwuje zarządzany stos.](#ManagedHeapReserve)

- [Określ duże obiekty w generacji 2.](#ExamineGen2)

- [Określ odwołania do obiektów.](#ObjRef)

- [Określ, czy finalizator został uruchomiony.](#Induce)

- [Określ, czy istnieją obiekty oczekujące na sfinalizowanie.](#Finalize)

- [Określ ilość wolnego miejsca w zarządzanym stercie.](#Fragmented)

- [Określ liczbę przypiętych obiektów.](#Pinned)

- [Określ czas w wyrzucania elementów bezużytecznych.](#TimeInGC)

- [Określ, co wyzwoliło wyrzucanie elementów bezużytecznych.](#Triggered)

- [Określ, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych.](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>Aby ustalić, czy problem jest spowodowany przez wyrzucanie elementów bezużytecznych

- Sprawdź następujące dwa liczniki wydajności pamięci:

  - **% czasu w GC**. Wyświetla procent czasu, który upłynął, który został poświęcony na wykonywanie wyrzucania elementów bezużytecznych po ostatnim cyklu wyrzucania elementów bezużytecznych. Ten licznik służy do określenia, czy moduł zbierający elementy bezużyteczne spędza zbyt dużo czasu, aby udostępnić miejsce na zarządzanych sterty. Jeśli czas spędzony w wyrzucania elementów bezużytecznych jest stosunkowo niski, może to wskazywać na problem z zasobem poza zarządzanym stertą. Ten licznik może nie być dokładne, gdy równoczesnych lub w tle wyrzucania elementów bezużytecznych jest zaangażowany.

  - **# Całkowita suma zatwierdzonych bajtów**. Wyświetla ilość pamięci wirtualnej aktualnie zatwierdzone przez moduł zbierający elementy bezużyteczne. Ten licznik służy do określenia, czy pamięć zużywana przez moduł zbierający elementy bezużyteczne jest nadmierną częścią pamięci używanej przez aplikację.

  Większość liczników wydajności pamięci są aktualizowane na końcu każdego wyrzucania elementów bezużytecznych. W związku z tym mogą nie odzwierciedlać bieżące warunki, o których chcesz uzyskać informacje.

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>Aby ustalić, czy wyjątek braku pamięci jest zarządzany

1. W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz polecenie wyjątek drukowania **(pe):**

    **!pe**

    Jeśli wyjątek jest <xref:System.OutOfMemoryException> zarządzany, jest wyświetlany jako typ wyjątku, jak pokazano w poniższym przykładzie.

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. Jeśli dane wyjściowe nie określają wyjątek, należy określić, który wątek wyjątek poza pamięcią jest z. Wpisz następujące polecenie w debugerze, aby wyświetlić wszystkie wątki z ich stosami wywołań:

    **~\*Kb**

    Wątek ze stosem, który ma `RaiseTheException` wywołania wyjątków jest wskazywany przez argument. Jest to obiekt wyjątku zarządzanego.

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. Za pomocą następującego polecenia można zrzucić zagnieżdżone wyjątki.

    **!pe -zagnieżdżone**

    Jeśli nie znajdziesz żadnych wyjątków, wyjątek braku pamięci pochodzi z kodu niezarządzanego.

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>Aby określić, ile pamięci wirtualnej można zarezerwować

- W usyliwiu WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby uzyskać największy wolny region:

  **!adres -podsumowanie**

  Największy wolny region jest wyświetlany, jak pokazano na poniższym wyjściu.

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  W tym przykładzie rozmiar największego wolnego regionu wynosi około 24000 KB (3A980 w szesnastkowej). Ten region jest znacznie mniejszy niż to, czego potrzebuje moduł zbierający elementy bezużyteczne dla segmentu.

  — lub —

- Użyj polecenia **vmstat:**

  **!vmstat**

  Największy wolny region jest największą wartością w kolumnie MAXIMUM, jak pokazano na poniższym wyjściu.

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

### <a name="to-determine-whether-there-is-enough-physical-memory"></a>Aby ustalić, czy jest wystarczająca ilość pamięci fizycznej

1. Uruchom Menedżera zadań systemu Windows.

2. Na karcie **Wydajność** przyjrzyj się wartości zatwierdzonej. (W systemie Windows 7 przyjrzyj **się zatwierdzeniu (KB)** w **grupie System.**

    Jeśli **wartość Suma** jest zbliżony do **limitu**, zaczyna brakować pamięci fizycznej.

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>Aby określić ilość pamięci, jaką zatwierdza zarządzana sterta

- Użyj `# Total committed bytes` licznika wydajności pamięci, aby uzyskać liczbę bajtów, które zatwierdza sterty zarządzane. Moduł zbierający elementy bezużyteczne zatwierdza fragmenty w segmencie zgodnie z potrzebami, nie wszystkie w tym samym czasie.

  > [!NOTE]
  > Nie należy `# Bytes in all Heaps` używać licznika wydajności, ponieważ nie reprezentuje rzeczywiste użycie pamięci przez zarządzane sterty. Rozmiar generacji jest uwzględniony w tej wartości i jest faktycznie jego rozmiar progu, to znaczy rozmiar, który wywołuje wyrzucania elementów bezużytecznych, jeśli generacji jest wypełniona obiektów. W związku z tym ta wartość jest zwykle zero.

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>Aby określić ilość pamięci rezerwowanej sterty zarządzanej

- Użyj `# Total reserved bytes` licznika wydajności pamięci.

  Moduł zbierający elementy bezużyteczne rezerwuje pamięć w segmentach i można określić, gdzie segment rozpoczyna się za pomocą polecenia **eeheap.**

  > [!IMPORTANT]
  > Chociaż można określić ilość pamięci moduł zbierający elementy bezużyteczne przydziela dla każdego segmentu, rozmiar segmentu jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowych aktualizacji. Aplikacja nigdy nie należy zakładać o lub zależy od określonego rozmiaru segmentu, ani nie należy próbować skonfigurować ilość pamięci dostępnej dla alokacji segmentów.

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:

  **!eeheap -gc**

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

  Adresy oznaczone przez "segment" są adresami początkowymi segmentów.

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a>Aby określić duże obiekty w generacji 2

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:

  **!dumpheap –stat**

  Jeśli zarządzana sterta jest duża, **dumpheap** może zająć trochę czasu, aby zakończyć.

  Można rozpocząć analizowanie z ostatnich kilku wierszy danych wyjściowych, ponieważ lista obiektów, które używają najwięcej miejsca. Przykład:

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

  Ostatni wymieniony obiekt jest ciągiem i zajmuje najwięcej miejsca. Można zbadać aplikacji, aby zobaczyć, jak można zoptymalizować obiekty ciągu. Aby wyświetlić ciągi o przedziale od 150 do 200 bajtów, wpisz następujące ciągi:

  **!dumpheap -type System.String -min 150 -max 200**

  Przykład wyników jest następujący.

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  Użycie liczby całkowitej zamiast ciągu dla identyfikatora może być bardziej efektywne. Jeśli ten sam ciąg jest powtarzany tysiące razy, należy wziąć pod uwagę internowanie ciągu. Aby uzyskać więcej informacji na temat internowania <xref:System.String.Intern%2A?displayProperty=nameWithType> ciągów, zobacz temat odwołania dla metody.

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a>Aby określić odwołania do obiektów

- W usyliwiu WinDbg z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby wyświetlić odwołania do obiektów:

  **!gcroot**

  `-or-`

- Aby określić odwołania dla określonego obiektu, należy podać adres:

  **!gcroot 1c37b2ac**

  Korzenie znalezione na stosach mogą być fałszywie dodatnie. Aby uzyskać więcej informacji, użyj polecenia `!help gcroot`.

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

  Polecenie **gcroot** może zająć dużo czasu, aby zakończyć. Każdy obiekt, który nie jest odzyskiwany przez wyrzucanie elementów bezużytecznych jest obiektem na żywo. Oznacza to, że niektóre root jest bezpośrednio lub pośrednio przytrzymuje na obiekcie, więc **gcroot** powinien zwrócić informacje o ścieżce do obiektu. Należy zbadać wykresy zwrócone i zobaczyć, dlaczego te obiekty są nadal odwołuje się.

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a>Aby ustalić, czy finalizator został uruchomiony

- Uruchom program testowy zawierający następujący kod:

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  Jeśli test rozwiązuje problem, oznacza to, że moduł zbierający elementy bezużyteczne nie odzyskuje obiektów, ponieważ finalizatory dla tych obiektów zostały zawieszone. Metoda <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> umożliwia finalizatorów, aby zakończyć swoje zadania i rozwiązuje problem.

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>Aby ustalić, czy istnieją obiekty oczekujące na finalizacje

1. W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:

    **!finalizequeue**

    Spójrz na liczbę obiektów, które są gotowe do finalizacji. Jeśli liczba jest wysoka, należy zbadać, dlaczego te finalizatorów nie może postępu w ogóle lub nie może poczyć wystarczająco szybko.

2. Aby uzyskać dane wyjściowe wątków, wpisz następujące polecenie:

    **nici -specjalne**

    To polecenie zapewnia dane wyjściowe, takie jak następujące.

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    Finalizator wątku wskazuje, który finalizator, jeśli istnieje, jest obecnie uruchamiany. Gdy wątek finalizatora nie jest uruchomiony żadnych finalizatorów, oczekuje na zdarzenie, aby powiedzieć mu, aby wykonać swoją pracę. W większości czasu zobaczysz wątku finalizatora w tym stanie, ponieważ działa na THREAD_HIGHEST_PRIORITY i ma zakończyć uruchamianie finalizatorów, jeśli w ogóle, bardzo szybko.

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>Aby określić ilość wolnego miejsca w zarządzanym stercie

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:

  **!dumpheap -type Free -stat**

  To polecenie wyświetla całkowity rozmiar wszystkich wolnych obiektów na zarządzanym stercie, jak pokazano w poniższym przykładzie.

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- Aby określić wolne miejsce w generacji 0, wpisz następujące polecenie dla informacji o zużyciu pamięci według generacji:

  **!eeheap -gc**

  To polecenie wyświetla dane wyjściowe podobne do następujących. Ostatni wiersz pokazuje segment efemeryczny.

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

- Oblicz przestrzeń używaną przez generację 0:

  **? 49e05d04-0x49521f8c**

  Wynik jest następujący. Generacja 0 wynosi około 9 MB.

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- Następujące polecenie zrzuca wolne miejsce w zakresie generacji 0:

  **!dumpheap -type Free -stat 0x49521f8c 49e05d04**

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

  To dane wyjściowe pokazuje, że część generacji 0 sterty używa 9 MB miejsca dla obiektów i ma 7 MB wolnego. Analiza ta pokazuje, w jakim stopniu generacja 0 przyczynia się do fragmentacji. Ta kwota użycia sterty powinny być dyskontowane od całkowitej kwoty jako przyczyna fragmentacji przez obiekty długoterminowe.

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a>Aby określić liczbę przypiętych obiektów

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie:

  **!gchandles**

  Wyświetlane statystyki obejmują liczbę przypiętych uchwytów, jak pokazano w poniższym przykładzie.

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>Aby określić czas w wyrzucaniu elementów bezużytecznych

- Sprawdź `% Time in GC` licznik wydajności pamięci.

  Wartość jest obliczana przy użyciu czasu interwału próbki. Ponieważ liczniki są aktualizowane na końcu każdego wyrzucania elementów bezużytecznych, bieżący przykład będzie miał taką samą wartość jak poprzedni przykład, jeśli nie wystąpiły żadne kolekcje podczas interwału.

  Czas zbierania jest uzyskiwany przez pomnożenie czasu interwału próbki z wartością procentową.

  Poniższe dane pokazują cztery interwały próbkowania po dwie sekundy dla 8-sekundowego badania. , `Gen0` `Gen1`i `Gen2` kolumny pokazują liczbę wyrzucań elementów bezużytecznych, które wystąpiły w tym przedziale dla tej generacji.

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  Te informacje nie są wyświetlane, gdy wystąpił wyrzucania elementów bezużytecznych, ale można określić liczbę wyrzucania elementów bezużytecznych, które wystąpiły w przedziale czasu. Zakładając, że w najgorszym przypadku dziesiątej generacji 0 wyrzucania elementów bezużytecznych zakończeniu na początku drugiego interwału, a jedenasta generacja 0 wyrzucania elementów bezużytecznych zakończył się na końcu piątego interwału. Czas między końcem dziesiątej i końca jedenastego wyrzucania elementów bezużytecznych wynosi około 2 sekund, a licznik wydajności pokazuje 3%, więc czas trwania kolekcji elementów bezużytecznych jedenastej generacji 0 był (2 sekundy * 3% = 60 ms).

  W tym przykładzie istnieje 5 okresów.

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  Druga generacja 2 wyrzucania elementów bezużytecznych rozpoczęła się w trzecim interwale i zakończył się w piątym przedziale. Zakładając, że najgorszy przypadek, ostatni wyrzucania elementów bezużytecznych był dla kolekcji generacji 0, który zakończył się na początku drugiego interwału i generacji 2 wyrzucania elementów bezużytecznych zakończeniu na koniec piątego interwału. W związku z tym czas między końcem generacji 0 wyrzucania elementów bezużytecznych i koniec generacji 2 wyrzucania elementów bezużytecznych jest 4 sekundy. Ponieważ `% Time in GC` licznik wynosi 20%, maksymalny czas, jaki mogło wziąć wyrzucanie elementów bezużytecznych generacji 2, wynosi (4 sekundy * 20% = 800 ms).

- Alternatywnie można określić długość wyrzucania elementów bezużytecznych przy użyciu [wyrzucania elementów bezużytecznych ETW zdarzeń](../../../docs/framework/performance/garbage-collection-etw-events.md)i analizować informacje w celu określenia czasu trwania wyrzucania elementów bezużytecznych.

  Na przykład następujące dane pokazuje sekwencję zdarzeń, które wystąpiły podczas nierównoczesnych wyrzucania elementów bezużytecznych.

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

  Zawieszenie zarządzanego wątku zajęło`GCSuspendEEEnd` 26us ( – `GCSuspendEEBegin_V1`).

  Rzeczywista wyrzucanie śmieci trwała 4,8 ms (`GCEnd_V1` – `GCStart_V1`).

  Wznowienie zarządzanych wątków zajęło 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).

  Następujące dane wyjściowe zawiera przykład wyrzucania elementów bezużytecznych w tle i zawiera proces, wątki i pola zdarzeń. (Nie wszystkie dane są wyświetlane).

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

  Zdarzenie `GCStart_V1` na 42504816 wskazuje, że jest to wyrzucanie elementów `1`bezużytecznych w tle, ponieważ ostatnim polem jest . Staje się to nr wyrzucania elementów bezużytecznych. 102019.

  Zdarzenie `GCStart` występuje, ponieważ istnieje potrzeba efemerycznego wyrzucania elementów bezużytecznych przed rozpoczęciem wyrzucania elementów bezużytecznych w tle. Staje się to nr wyrzucania elementów bezużytecznych. 102020.

  Na 42514170, nr wyrzucania elementów bezużytecznych 102020 kończy. Zarządzane wątki są ponownie uruchamiane w tym momencie. Jest to zakończone w wątku 4372, który wyzwolił to wyrzucanie elementów bezużytecznych w tle.

  Na nitce 4744 występuje zawieszenie. Jest to jedyny czas, w którym wyrzucanie elementów bezużytecznych w tle musi zawiesić zarządzane wątki. Ten czas trwania wynosi około 99 ms ((63784407-63685394)/1000).

  Zdarzenie `GCEnd` dla wyrzucania elementów bezużytecznych w tle jest na 89931423. Oznacza to, że wyrzucanie elementów bezużytecznych w tle trwało około 47 sekund ((89931423-42504816)/1000).

  Podczas uruchamiania zarządzanych wątków, można zobaczyć dowolną liczbę tymczasowych wyrzucania elementów bezużytecznych występujących.

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a>Aby ustalić, co wyzwoliło wyrzucanie elementów bezużytecznych

- W debugerze WinDbg lub Visual Studio z załadowanym rozszerzeniem debugera SOS wpisz następujące polecenie, aby wyświetlić wszystkie wątki z ich stosami wywołań:

  **~\*Kb**

  To polecenie wyświetla dane wyjściowe podobne do następujących.

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  Jeśli wyrzucanie elementów bezużytecznych została spowodowana przez powiadomienie o małej ilości pamięci z systemu operacyjnego, stos wywołań jest podobny, z tą różnicą, że wątek jest wątkiem finalizatora. Finalizator wątku pobiera asynchroniczne powiadomienie o niskiej pamięci i wywołuje wyrzucania elementów bezużytecznych.

  Jeśli wyrzucanie elementów bezużytecznych zostało spowodowane przez alokację pamięci, stos jest wyświetlany w następujący sposób:

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

  Just-in-time pomocnika (`JIT_New*`) `GCHeap::GarbageCollectGeneration`w końcu dzwoni . Jeśli stwierdzisz, że generacji 2 wyrzucania elementów bezużytecznych są spowodowane przez alokacje, należy określić, które obiekty są zbierane przez wyrzucanie elementów bezużytecznych generacji 2 i jak ich uniknąć. Oznacza to, że chcesz określić różnicę między początku i końca generacji 2 wyrzucania elementów bezużytecznych i obiektów, które spowodowały kolekcji generacji 2.

  Na przykład wpisz następujące polecenie w debugerze, aby wyświetlić początek kolekcji 2 generacji:

  **!dumpheap –stat**

  Przykładowe dane wyjściowe (skrócone, aby pokazać obiekty, które zajmują najwięcej miejsca):

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

  **!dumpheap –stat**

  Przykładowe dane wyjściowe (skrócone, aby pokazać obiekty, które zajmują najwięcej miejsca):

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

  Obiekty `double[]` zniknęły z końca danych wyjściowych, co oznacza, że zostały zebrane. Obiekty te stanowią około 70 MB. Pozostałe obiekty nie zmieniły się zbytnio. W związku `double[]` z tym te obiekty były przyczyną tej generacji 2 wyrzucania elementów bezużytecznych wystąpił. Następnym krokiem jest ustalenie, `double[]` dlaczego obiekty są tam i dlaczego zginęły. Możesz zapytać programistę kodu, skąd pochodzą te obiekty, lub użyć polecenia **gcroot.**

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>Aby ustalić, czy wysokie użycie procesora CPU jest spowodowane przez wyrzucanie elementów bezużytecznych

- Skoreluj wartość licznika `% Time in GC` wydajności pamięci z czasem procesu.

  Jeśli `% Time in GC` wartość wzrasta w tym samym czasie co czas procesu, wyrzucanie elementów bezużytecznych powoduje wysokie użycie procesora CPU. W przeciwnym razie profil aplikacji, aby znaleźć miejsce wysokiego użycia występuje.

## <a name="see-also"></a>Zobacz też

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
