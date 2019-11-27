---
title: Omówienie profilowania
ms.date: 03/30/2017
helpviewer_keywords:
- managed code, profiling API support
- unmanaged code, combining with managed code in profiling
- notification threads [.NET Framework profiling]
- unmanaged code, profiling
- profiling API [.NET Framework], and COM
- profiling API [.NET Framework], unmanaged code profiling
- profilers, writing
- profiling API [.NET Framework], call stacks
- code profilers, writing
- profiling API [.NET Framework], security considerations
- profiling API [.NET Framework], managed code support
- common language runtime, profiling
- profiling API [.NET Framework], notification threads
- call stacks [.NET Framework profiling]
- profiling API [.NET Framework], stack depth
- common language runtime, writing a profiler
- profiling API [.NET Framework], information retrieval interfaces
- shadow stacks [.NET Framework profiling]
- COM, using in the profiling API
- stack snapshots [.NET Framework profiling]
- profiling API [.NET Framework], supported features
- profiling API [.NET Framework], overview
- security, profiling API considerations
- stack depth [.NET Framework profiling]
ms.assetid: 864c2344-71dc-46f9-96b2-ed59fb6427a8
ms.openlocfilehash: 08015e2e5918ca64f601ec912a906cfb6319ed6c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427100"
---
# <a name="profiling-overview"></a>Omówienie profilowania

Profiler to narzędzie monitorujące wykonywanie innej aplikacji. Profiler środowiska uruchomieniowego języka wspólnego (CLR) jest biblioteką dołączaną dynamicznie (DLL), która składa się z funkcji, które odbierają komunikaty i wysyłają komunikaty do programu przy użyciu interfejsu API profilowania. Profiler DLL jest ładowany przez środowisko CLR w czasie wykonywania.

Tradycyjne narzędzia profilowania koncentrują się na mierze wykonywania aplikacji. Oznacza to, że mierzą czas spędzony na każdej funkcji lub użycie pamięci przez aplikację w czasie. Profilowania API jest przeznaczona dla szerszej klasy narzędzi diagnostycznych, takich jak narzędzia do pokrycia kodu, a nawet zaawansowane pomoce debugowania. Te zastosowania mają charakter diagnostyczny. Profilowanie API nie tylko mierzy, ale również monitoruje wykonywanie aplikacji. Z tego powodu interfejs API profilowania nigdy nie powinien być używany przez samą aplikację, a wykonywanie aplikacji nie powinno zależeć od (lub mieć wpływ) na program profilujący.

Profilowanie aplikacji CLR wymaga większego wsparcia niż profilowanie skompilowanego kodu maszynowego. Jest to spowodowane tym, że środowisko CLR wprowadza koncepcje, takie jak domeny aplikacji, wyrzucanie elementów bezużytecznych, obsługa wyjątków w trybie just-in-Time (JIT), Kompilacja kodu (Konwersja języka pośredniego firmy Microsoft lub MSIL, kod na natywny kod maszynowy) i podobna oferowanych. Konwencjonalne mechanizmy profilowania nie mogą identyfikować i dostarczać użytecznych informacji o tych funkcjach. Profiling API nie zapewnia wydajnej informacji przy minimalnym wpływie na wydajność środowiska CLR i profilowanej aplikacji.

Kompilacja JIT w czasie wykonywania zapewnia dobrą możliwość profilowania. Profilowanie API umożliwia profilerowi zmianę strumienia kodu MSIL w pamięci dla procedury przed skompilowaniem JIT. W ten sposób profiler może dynamicznie dodawać kod instrumentacji do określonych procedur, które wymagają dokładniejszego zbadania. Chociaż takie podejście jest możliwe w scenariuszach konwencjonalnych, znacznie łatwiej jest zaimplementować środowisko CLR przy użyciu interfejsu API profilowania.

## <a name="the-profiling-api"></a>Profilowanie API

Zwykle Profiling API jest używany do pisania *profilera kodu*, który jest programem monitorującym wykonywanie zarządzanej aplikacji.

Profilowania API jest używany przez profiler DLL, który jest ładowany do tego samego procesu co aplikacja, która jest profilowana. Biblioteka DLL profilera implementuje interfejs wywołania zwrotnego ([ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) w .NET Framework w wersji 1,0 i 1,1 [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) w wersji 2,0 i nowszych). Środowisko CLR wywołuje metody z tego interfejsu w celu powiadomienia profilera zdarzeń w profilowanym procesie. Profiler może odwoływać się do środowiska uruchomieniowego przy użyciu metod w interfejsach [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) i [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) w celu uzyskania informacji o stanie profilowanej aplikacji.

> [!NOTE]
> Tylko część zbierania danych w ramach rozwiązania profilera powinna być uruchomiona w tym samym procesie co profilowana aplikacja. Wszystkie interfejsy użytkownika i analizy danych należy wykonać w osobnym procesie.

Na poniższej ilustracji pokazano, jak Profiler DLL współdziała z aplikacją, która jest profilowana, oraz środowiskiem CLR.

![Zrzut ekranu przedstawiający architekturę profilowania.](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>Interfejsy powiadomień

[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) mogą być uznawane za Interfejsy powiadomień. Te interfejsy składają się z metod takich jak [ClassLoadStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)i [JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Za każdym razem, gdy środowisko CLR ładuje lub zwalnia klasę, kompiluje funkcję i tak dalej, wywołuje odpowiednią metodę w interfejsie `ICorProfilerCallback` lub `ICorProfilerCallback2`.

Na przykład profiler może mierzyć wydajność kodu przez dwie funkcje powiadomień: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) i [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Tylko sygnatura czasowa oznacza każde powiadomienie, sumuje wyniki i wyprowadza listę, która wskazuje, które funkcje zużywają najwięcej czasu procesora lub zegarka podczas wykonywania aplikacji.

### <a name="the-information-retrieval-interfaces"></a>Interfejsy pobierania informacji

Inne główne interfejsy, które są wykorzystywane do profilowania, to [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) i [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Profiler wywołuje te interfejsy zgodnie z potrzebami, aby uzyskać więcej informacji ułatwiających jego analizę. Na przykład za każdym razem, gdy środowisko CLR wywołuje funkcję [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) , dostarcza identyfikator funkcji. Profiler może uzyskać więcej informacji na temat tej funkcji, wywołując metodę [ICorProfilerInfo2:: GetFunctionInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) w celu odnalezienia klasy nadrzędnej funkcji, jej nazwy i tak dalej.

## <a name="supported-features"></a>Obsługiwane funkcje

Profilowanie API zawiera informacje o różnych zdarzeniach i akcjach, które występują w środowisku uruchomieniowym języka wspólnego. Te informacje służą do monitorowania wewnętrznych działań procesów i analizowania wydajności aplikacji .NET Framework.

Interfejs API profilowania pobiera informacje o następujących akcjach i zdarzeniach, które występują w środowisku CLR:

- Zdarzenia uruchamiania i zamykania środowiska CLR.

- Zdarzenia tworzenia i zamykania domeny aplikacji.

- Ładowanie i zwalnianie zestawów zdarzeń.

- Zdarzenia ładowania i zwalniania modułu.

- Zdarzenia tworzenia i niszczenia tablic wirtualnych COM.

- Kompilacja just-in-Time (JIT) i zdarzenia o pochyleniach kodu.

- Ładowanie i zwalnianie klas zdarzeń.

- Zdarzenia tworzenia i niszczenia wątków.

- Zdarzenia wejścia i wyjścia funkcji.

- Liczba wyjątków.

- Przejścia między zarządzanym i niezarządzanym wykonaniem kodu.

- Przejścia między różnymi kontekstami środowiska uruchomieniowego.

- Informacje o zawieszeniu środowiska uruchomieniowego.

- Informacje na temat sterty pamięci środowiska uruchomieniowego i działania odzyskiwania pamięci.

Profilowanie interfejsu API można wywoływać z dowolnego języka zgodnego z modelem COM (niezarządzanego).

Interfejs API jest wydajny w odniesieniu do zużycia procesora i pamięci. Profilowanie nie obejmuje zmian profilowanej aplikacji, które są wystarczająco duże, aby powodować błędne wyniki.

Profilowanie interfejsu API jest przydatne zarówno do próbkowania, jak i do prepobierających plików. *Profiler próbkowania* sprawdza profil przy zwykłych taktach zegara, powiedzmy, co 5 milisekund. *Profiler bez próbkowania* jest informowany o zdarzeniu synchronicznie z wątkiem powodującym zdarzenie.

### <a name="unsupported-functionality"></a>Nieobsługiwana funkcja

Profilowanie API nie obsługuje następujących funkcji:

- Kod niezarządzany, który musi być profilowany przy użyciu konwencjonalnych metod Win32. Profiler CLR zawiera jednak zdarzenia przejścia, aby określić granice między zarządzanym i niezarządzanym kodem.

- Samomodyfikujące się aplikacje, które modyfikują własny kod do celów, takich jak programowanie zorientowane obiektowo.

- Sprawdzanie granic, ponieważ interfejs API profilowania nie dostarcza tych informacji. Środowisko CLR zapewnia wewnętrzną obsługę kontroli granic dla całego kodu zarządzanego.

- Zdalne profilowanie, które nie jest obsługiwane z następujących powodów:

  - Zdalne profilowanie rozszerza czas wykonywania. W przypadku korzystania z interfejsów profilowania należy zminimalizować czas wykonywania, tak aby nie miały negatywnego wpływ na wyniki profilowania. Jest to szczególnie prawdziwe, gdy wydajność wykonywania jest monitorowana. Jednak profilowanie zdalne nie jest ograniczeniem, gdy interfejsy profilowania są używane do monitorowania użycia pamięci lub do uzyskiwania informacji w czasie wykonywania dotyczących ramek stosu, obiektów i tak dalej.

  - Profiler kodu CLR musi zarejestrować jeden lub więcej interfejsów wywołania zwrotnego w środowisku uruchomieniowym na komputerze lokalnym, na którym jest uruchomiona profilowana aplikacja. Pozwala to ograniczyć możliwość tworzenia zdalnego profilera kodu.

- Profilowanie w środowiskach produkcyjnych z wymaganiami wysokiej dostępności. Interfejs API profilowania został utworzony w celu obsługi diagnostyki w czasie projektowania. Nie przeszło rygorystycznych testów wymaganych do obsługi środowisk produkcyjnych.

## <a name="notification-threads"></a>Wątki powiadomień

W większości przypadków wątek generujący zdarzenie również wykonuje powiadomienia. Takie powiadomienia (na przykład [FunctionEnter —](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) i [FunctionLeave —](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) nie muszą podawać jawnych `ThreadID`. Profiler może również zdecydować się na użycie magazynu lokalnego wątków do przechowywania i aktualizowania bloków analizy zamiast indeksowania bloków analizy w magazynie globalnym na podstawie `ThreadID` wątku, którego to dotyczy.

Należy zauważyć, że te wywołania zwrotne nie są serializowane. Użytkownicy muszą chronić swój kod, tworząc bezpieczne dla wątków struktury danych i blokując kod profilera, gdy jest to konieczne, aby uniemożliwić dostęp równoległy z wielu wątków. Z tego względu w niektórych przypadkach można uzyskać nietypową sekwencję wywołań zwrotnych. Załóżmy na przykład, że aplikacja zarządzana duplikuje dwa wątki wykonujące identyczny kod. W takim przypadku możliwe jest odbieranie zdarzenia [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) dla niektórych funkcji z jednego wątku i wywołania zwrotnego `FunctionEnter` z innego wątku przed odebraniem wywołania zwrotnego [ICorProfilerCallback:: JITCompilationFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) . W takim przypadku użytkownik otrzyma `FunctionEnter` wywołanie zwrotne dla funkcji, która może nie być jeszcze w pełni skompilowana (JIT).

## <a name="security"></a>Bezpieczeństwo

Profiler DLL jest niezarządzaną biblioteką DLL, która działa w ramach aparatu wykonywania środowiska uruchomieniowego języka wspólnego. W związku z tym kod w pliku DLL profilera nie podlega ograniczeniom zabezpieczeń dostępu do kodu zarządzanego. Jedyne ograniczenia dotyczące programu Profiler DLL są nakładane przez system operacyjny na użytkownika, który korzysta z profilowanej aplikacji.

Autorzy profilera powinni podjąć odpowiednie środki ostrożności, aby uniknąć problemów związanych z zabezpieczeniami. Na przykład podczas instalacji należy dodać do listy kontroli dostępu (ACL) plik DLL programu Profiler, aby złośliwy użytkownik nie mógł go zmodyfikować.

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Łączenie kodu zarządzanego i niezarządzanego w profilerze kodu

Niepoprawnie zapisany profiler może spowodować odwołania cykliczne do samego siebie, co skutkuje nieprzewidywalnym zachowaniem.

Przegląd interfejsu API profilowania środowiska CLR może stworzyć wrażenie, że można napisać Profiler zawierający składniki zarządzane i niezarządzane, które wzajemnie się wywołują, za pomocą międzyoperacyjności modelu COM lub wywołań pośrednich.

Chociaż jest to możliwe z perspektywy projektowania, interfejs API profilowania nie obsługuje składników zarządzanych. Profiler CLR musi być całkowicie niezarządzany. Próby połączenia kodu zarządzanego i niezarządzanego w profilerze CLR mogą spowodować naruszenie zasad dostępu, niepowodzenia programu lub zakleszczenia. Zarządzane składniki profilera będą wyzwalać zdarzenia z powrotem do niezarządzanych składników, które następnie ponownie wywołają zarządzane składniki, co spowoduje powstanie odwołań cyklicznych.

Jedyna lokalizacja, w której Profiler CLR może bezpiecznie wywoływać kod zarządzany, jest w treści języka pośredniego (MSIL) firmy Microsoft. Zalecanym sposobem modyfikacji treści MSIL jest użycie metod ponownej kompilacji JIT w interfejsie [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) .

Aby zmodyfikować MSIL, można również użyć starszych metod Instrumentacji. Przed ukończeniem kompilacji funkcji just-in-Time (JIT) dla programu profiler może wstawiać wywołania zarządzane w treści MSIL metody, a następnie kompilować ją w trybie JIT (patrz metoda [ICorProfilerInfo:: GetILFunctionBody —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) ). Ta technika może zostać pomyślnie użyta w przypadku selektywnego oprzyrządowania kodu zarządzanego lub zbierania danych statystycznych i wydajności dotyczących JIT.

Alternatywnie Profiler kodu może wstawiać natywne haki w treści MSIL każdej funkcji zarządzanej, która wywołuje kod niezarządzany. Ta technika może służyć do Instrumentacji i pokrycia. Na przykład Profiler kodu może wstawić punkty zaczepienia Instrumentacji po każdym bloku MSIL, aby upewnić się, że blok został wykonany. Modyfikacja treści MSIL metody jest bardzo delikatną operacją i istnieje wiele czynników, które należy wziąć pod uwagę.

## <a name="profiling-unmanaged-code"></a>Profilowanie kodu niezarządzanego

Interfejs API profilowania środowiska uruchomieniowego języka wspólnego (CLR) zapewnia minimalną obsługę profilowania kodu niezarządzanego. Dostępne są następujące funkcje:

- Wyliczanie łańcuchów stosu. Ta funkcja umożliwia profilerowi kodu określenie granicy między kodem zarządzanym i niezarządzanym kodem.

- Określanie, czy łańcuch stosu odpowiada kodowi zarządzanemu czy kodowi natywnemu.

W .NET Framework wersje 1,0 i 1,1 te metody są dostępne za pomocą podzestawu w procesie interfejsu API debugowania środowiska CLR. Są one zdefiniowane w pliku CorDebug. idl.

W .NET Framework 2,0 i nowszych można użyć metody [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) dla tej funkcji.

## <a name="using-com"></a>Przy użyciu modelu COM

Chociaż interfejsy profilowania są zdefiniowane jako interfejsy COM, środowisko uruchomieniowe języka wspólnego (CLR) nie inicjuje w rzeczywistości modelu COM, aby używać tych interfejsów. Przyczyną jest uniknięcie konieczności ustawiania modelu wątkowości przy użyciu funkcji [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) , zanim aplikacja zarządzana będzie mogła określić odpowiedni model wątkowości. Podobnie Profiler nie powinien wywoływać `CoInitialize`, ponieważ może wybrać model wątkowości, który jest niezgodny z profilowaną aplikacją i może spowodować niepowodzenie aplikacji.

## <a name="call-stacks"></a>Stosy wywołań

Profilowanie interfejsu API zapewnia dwa sposoby uzyskiwania stosów wywołań: metodę migawki stosu, która umożliwia zbieranie rozrzedzonych stosów wywołań i metodę stosu w tle, która śledzi stos wywołań w każdym momencie.

### <a name="stack-snapshot"></a>Migawka stosu

Migawka stosu jest śladem stosu wątku na chwilę. Profiling API obsługuje śledzenie funkcji zarządzanych na stosie, ale pozostawia śledzenie niezarządzanych funkcji do analizatora stosu modułu profilera.

Aby uzyskać więcej informacji na temat sposobu programowania profilera w celu przechodzenia do zarządzanych stosów, zobacz metodę [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) w tym zestawie dokumentacji i [stosu profilera w .NET Framework 2,0: podstawy i więcej](https://go.microsoft.com/fwlink/?LinkId=73638).

### <a name="shadow-stack"></a>Stos cieni

Użycie metody Snapshot jest zbyt często możliwe, aby szybko utworzyć problem z wydajnością. Jeśli chcesz, aby ślady stosu były często wykonywane, profiler powinien zamiast tego kompilować stos w tle za pomocą wywołań zwrotnych wyjątków [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) . Stos cieni jest zawsze aktualny i może być szybko kopiowany do magazynu, gdy wymagana jest migawka stosu.

Stos cienia może uzyskać argumenty funkcji, wartości zwracane i informacje o ogólnych wystąpieniach. Te informacje są dostępne tylko za pomocą stosu w tle i mogą być uzyskiwane, gdy sterowanie jest przekazywane do funkcji. Jednak te informacje mogą być niedostępne w przyszłości podczas uruchamiania funkcji.

## <a name="callbacks-and-stack-depth"></a>Wywołania zwrotne i głębokość stosu

Wywołania zwrotne profilera mogą być emitowane w bardzo ograniczonych warunkach stosu, a przepełnienie stosu w wywołaniu wywołania zwrotnego profilera będzie prowadzić do natychmiastowego zakończenia procesu. Profiler powinien w odpowiedzi na wywołania zwrotne używać możliwie najmniejszego stosu. Jeśli profiler jest przeznaczony do użycia w przypadku procesów, które są niezawodne przed przepełnieniem stosu, profiler powinien również unikać wyzwalania przepełnienia stosu.

## <a name="related-topics"></a>Tematy pokrewne

|Stanowisko|Opis|
|-----------|-----------------|
|[Konfigurowanie środowiska profilowania](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Wyjaśnia, jak zainicjować profiler, ustawić powiadomienia o zdarzeniach i profilować usługę systemu Windows.|
|[Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Opisuje interfejsy niezarządzane używane przez interfejs API profilowania.|
|[Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Opisuje niezarządzane globalne funkcje statyczne, które są używane przez interfejs API profilowania.|
|[Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Opisuje niezarządzane wyliczenia, które są używane przez interfejs API profilowania.|
|[Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Opisuje struktury niezarządzane używane przez interfejs API profilowania.|
