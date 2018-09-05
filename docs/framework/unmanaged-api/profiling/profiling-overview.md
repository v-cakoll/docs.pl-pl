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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd0fef0e8a2c4b94cd5dd7beb140e669c52a07a8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554031"
---
# <a name="profiling-overview"></a>Omówienie profilowania
<a name="top"></a> Program profilujący to narzędzie, które monitoruje wykonanie innej aplikacji. Typowe profiler środowiska uruchomieniowego (języka wspólnego CLR) języka jest biblioteki dołączanej dynamicznie (DLL), która składa się z funkcji, które odbierają wiadomości ze i wysyłanie komunikatów do środowiska CLR przy użyciu profilowania interfejsu API. Program profilujący DLL jest ładowany przez środowisko CLR w czasie wykonywania.  
  
 Tradycyjne narzędzie profilowania skupia się na pomiarze wykonania aplikacji. To znaczy służą do pomiaru czasu spędzonego w każdej funkcji lub użycia pamięci przez aplikację wraz z upływem czasu. Profilowania API jest przeznaczone dla szerszej klasy narzędzi diagnostycznych, takich jak narzędzia pokrycia kodu i nawet zaawansowane debugowanie pomocne. Te zastosowania są wszystkie diagnostyczne w naturze. Profilowanie API nie tylko mierzy, ale również monitoruje wykonywanie aplikacji. Z tego powodu, profilowanie API nie mogą być używane przez samą aplikację, a wykonywanie aplikacji nie powinna zależeć od (lub doświadczyć działania) programu profilującego.  
  
 Profilowanie aplikacji CLR wymaga obsługi więcej obsługi niż profilowanie konwencjonalnie skompilowanego kodu maszynowego. Jest to spowodowane CLR wprowadza takie pojęcia jak domeny aplikacji, wyrzucanie elementów bezużytecznych zarządzane obsługę wyjątków, just-in-time (JIT) kompilacja kodu (Konwersja języka Microsoft intermediate language lub MSIL kod do kodu macierzystego komputera) i podobnych zastosowaniach funkcje. Mechanizmy konwencjonalnego profilowania nie można zidentyfikować lub dostarczyć przydatnych informacji o tych funkcjach. Profilowanie API dostarcza brakujących informacji skutecznie, z minimalnym wpływem na wydajność środowiska CLR i profilowanej aplikacji.  
  
 Kompilacja JIT w czasie wykonywania zapewnia dobre możliwości profilowania. Profilowania API umożliwia programowi profilującemu zmianę strumienia kodu MSIL w pamięci dla procedury, zanim zostanie skompilowany JIT. W ten sposób program profilujący może dynamicznie dodawać kod Instrumentacji do szczególnych procedur, które wymagają głębszego zbadania. Chociaż to podejście jest możliwe w scenariuszach konwencjonalnych, jest znacznie łatwiejsze do wdrożenia dla środowiska CLR przy użyciu profilowania interfejsu API.  
  
 To omówienie składa się z następujących sekcji:  
  
-   [API profilowania](#profiling_api)  
  
-   [Obsługiwane funkcje](#support)  
  
-   [Wątki powiadomień](#notification_threads)  
  
-   [Zabezpieczenia](#security)  
  
-   [Łączenie kodu zarządzanego i niezarządzanego w Profiler kodu](#combining_managed_unmanaged)  
  
-   [Profilowanie niezarządzanego kodu](#unmanaged)  
  
-   [Korzystając z modelu COM](#com)  
  
-   [Stosy wywołań](#call_stacks)  
  
-   [Wywołania zwrotne i głębokość stosu](#callbacks)  
  
-   [Tematy pokrewne](#related_topics)  
  
<a name="profiling_api"></a>   
## <a name="the-profiling-api"></a>API profilowania  
 Zazwyczaj profilowania API jest używany do zapisywania *program profilujący*, czyli program, który monitoruje wykonanie zarządzanej aplikacji.  
  
 Profilowania API jest używany przez program profilujący DLL, który jest ładowany do tego samego procesu co aplikacja, która jest profilowana. Program profilujący biblioteki DLL implementuje interfejs wywołania zwrotnego ([ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) w .NET Framework w wersji 1.0 i 1.1, [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) w wersji 2.0 lub nowszej). Środowisko CLR wywołania metody, w tym interfejsie powiadomić profiler wydarzeń w profilowanym procesie. Program profilujący wywołania zwrotnego w czasie wykonywania przy przy użyciu metod w [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) i [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interfejsy w celu uzyskania informacji na temat stanu profilowanej aplikacji.  
  
> [!NOTE]
>  Tylko część gromadzenia danych rozwiązania profilera powinna być uruchomiona w tym samym procesie co profilowana aplikacja. Wszystkich użytkowników interfejsu i przeprowadzać analizę danych powinno być przeprowadzone w oddzielnym procesie.  
  
 Poniższa ilustracja przedstawia, jak profiler DLL współdziała z aplikacji, która jest profilowana i środowiska CLR.  
  
 ![Profilowanie architektury](../../../../docs/framework/unmanaged-api/profiling/media/profilingarch.png "ProfilingArch")  
Profilowanie architektury  
  
### <a name="the-notification-interfaces"></a>Interfejsy powiadomień  
 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) jest uznawana za interfejsy powiadomień. Interfejsy te składają się z metody takie jak [ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md), i [JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Każdorazowo CLR ładuje i zwalnia klasy, kompiluje funkcję i itd., wywołuje odpowiedniej metody w profilerze `ICorProfilerCallback` lub `ICorProfilerCallback2` interfejsu.  
  
 Na przykład program profilujący może zmierzyć wydajność kodu przez dwie funkcje powiadomień: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) i [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Aplikacja sygnatury czasowe Każde powiadomienie, gromadzi wyniki i wyświetla listę, która wskazuje, które funkcje używane najwięcej procesora CPU lub zgodnie z zegarem czasu podczas wykonywania aplikacji.  
  
### <a name="the-information-retrieval-interfaces"></a>Interfejsy wyszukiwania informacji  
 Inne główny interfejsy, zaangażowany w profilowanie to [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) i [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Program profilujący wywołuje te interfejsy zgodnie z wymaganiami, aby uzyskać więcej informacji na temat ich analizy. Na przykład, gdy środowisko CLR wywołuje [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) funkcji, dostarcza mu identyfikator funkcji. Program profilujący może uzyskać więcej informacji na temat tej funkcji przez wywołanie metody [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody umożliwiającej odnajdowanie funkcji klasy nadrzędnej, jej nazwa i tak dalej.  
  
 [Powrót do początku](#top)  
  
<a name="support"></a>   
## <a name="supported-features"></a>Obsługiwane funkcje  
 Profilowania API zawiera informacje o różnych zdarzeniach i działaniach, które występują w środowisko uruchomieniowe języka wspólnego. Te informacje służą do monitorowania wewnętrznego działania procesów i analizowania wydajność aplikacji .NET Framework.  
  
 API profilowania pobiera informacje o następujących działaniach i zdarzeniach, które wystąpiły w CLR:  
  
-   Zdarzenia uruchamiania i zamykania CLR.  
  
-   Zdarzenia tworzenia i zamykania aplikacji domeny.  
  
-   Ładowanie zestawów i wyładowywanie zdarzeń.  
  
-   Ładowanie modułów i wyładowywanie zdarzeń.  
  
-   Zdarzenia tworzenia i niszczenia COM vtable.  
  
-   Just-in-time (JIT) kompilacja i zdarzenia poziomowania kodu.  
  
-   Klasa ładowania i wyładowywanie zdarzeń.  
  
-   Wątek zdarzenia tworzenia i niszczenia.  
  
-   Zdarzenia wejścia i wyjścia funkcji.  
  
-   Liczba wyjątków.  
  
-   Przejścia między wykonywaniem kodu zarządzanego i niezarządzanego.  
  
-   Przejścia między środowiskiem uruchomieniowym w różnych kontekstach.  
  
-   Informacje o zawieszeniach środowiska uruchomieniowego.  
  
-   Informacje na temat środowiska uruchomieniowego pamięci sterty i wyrzucania elementów kolekcji działania.  
  
 Profilowania API można wywołać z dowolnego języka zgodnego z COM. (niezarządzany).  
  
 Interfejs API jest skuteczny w odniesieniu do zużycia procesora CPU i pamięci. Profilowania może obejmować zmian profilowanej aplikacji, które są na tyle znaczące spowodować wyświetlenie nieprawdziwych wyników.  
  
 Profilowania API jest przydatne do pobierania próbek i -pobierania próbek profilowania. A *próbkowania profilera* przeprowadza inspekcję profilu przy regularnych taktach zegara, powiedz, co 5 milisekund. A *profilujący niezwiązany* jest informowany o zdarzeniu synchronicznie z wątkiem, który powoduje to zdarzenie.  
  
### <a name="unsupported-functionality"></a>Nieobsługiwana funkcja  
 Profilowanie API nie obsługuje następujące funkcje:  
  
-   Niezarządzany kod, który musi być profilowany za pomocą konwencjonalnych metod Win32. Jednakże program profilujący CLR zawiera zdarzenia przejścia do określenia granic między kodem zarządzanym i niezarządzanym.  
  
-   Własne modyfikowanie aplikacji, które modyfikują swój własny kod do celów takich jak programowanie zorientowanego na aspekt.  
  
-   Sprawdzanie granic, ponieważ profilowanie API nie dostarcza tych informacji. Środowisko CLR zapewnia wsparcie wewnętrznej sprawdzanie wszystkich zarządzanych kodów granic.  
  
-   Zdalne profilowanie, który nie jest obsługiwany w następujących sytuacjach:  
  
    -   Zdalne profilowanie rozszerza czas wykonania. Korzystając z interfejsów profilowania, można zminimalizować czas wykonywania, aby wyniki profilowania nie będą nadmiernie zmieniane. Jest to szczególnie istotne w przypadku, gdy wykonanie wydajności jest monitorowane. Jednakże, zdalne profilowanie nie jest to ograniczenie, gdy interfejsy profilujące są używane do monitorowania wykorzystania pamięci lub uzyskać informacje czasu wykonywania ramki stosu, obiektów i tak dalej.  
  
    -   Profiler kodu CLR musi zarejestrować jeden lub więcej interfejsów wywołania zwrotnego do aparatu plików wykonywalnych na komputerze lokalnym, na którym jest uruchomiona profilowana aplikacja. Ogranicza to możliwość tworzenia profilerów kodu zdalnego.  
  
-   Profilowanie w środowiskach produkcyjnych z wymogami wysokiej dostępności. API profilowania zostało utworzone do obsługi rozwoju diagnostycznego. Nie przeszedł rygorystycznych testów wymaganych do obsługi środowisk produkcyjnych.  
  
 [Powrót do początku](#top)  
  
<a name="notification_threads"></a>   
## <a name="notification-threads"></a>Wątki powiadomień  
 W większości przypadków wątek, który generuje zdarzenie także wykonuje powiadomienia. Takie powiadomienia (na przykład [functionenter —](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) i [functionleave —](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) nie muszą podawać jawnie `ThreadID`. Program profilujący może też użyć magazynu wątków lokalnych do przechowywania i aktualizowania swoich bloków analizy zamiast indeksowania bloków analizy w globalnej pamięci masowej, na podstawie `ThreadID` wątku, do których to dotyczy.  
  
 Należy pamiętać, że te wywołania zwrotne nie są serializowane. Dlatego też należy chronić swój kod poprzez tworzenie struktur danych wątków oraz blokowanie kodu profilera, gdy jest to konieczne w celu zapobieżenia dostępowi równolegle z wielu wątków. W związku z tym w niektórych przypadkach można otrzymać nietypowe sekwencję wywołań zwrotnych. Na przykład załóżmy, że aplikację zarządzaną namnaża dwa wątki, które realizują ten sam kod. W tym przypadku jest możliwe, aby otrzymać [icorprofilercallback::jitcompilationstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) zdarzeń dla niektórych funkcji z jednego wątku i `FunctionEnter` wywołania zwrotnego z innego wątku przed otrzymaniem [ Icorprofilercallback::jitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) wywołania zwrotnego. W takim przypadku użytkownik otrzyma `FunctionEnter` wywołania zwrotnego dla funkcji, która może nie zostać w pełni just-in-time (JIT) jeszcze skompilowany.  
  
 [Powrót do początku](#top)  
  
<a name="security"></a>   
## <a name="security"></a>Zabezpieczenia  
 Program profilujący DLL jest niezarządzaną biblioteką DLL, która działa jako część aparat wykonywania środowiska uruchomieniowego języka wspólnego. W rezultacie kodu w programie profilującym DLL nie jest przedmiotem ograniczeń zarządzanego zabezpieczenia dostępu kodu. Jedynymi ograniczeniami profilera biblioteki DLL są ograniczenia nałożone przez system operacyjny na użytkownika, który uruchomił profilowaną aplikację.  
  
 Autorzy Profiler należy podjąć odpowiednie środki ostrożności, aby uniknąć problemów związanych z zabezpieczeniami. Na przykład podczas instalacji, program profilujący DLL powinien można dodać do listy kontroli dostępu (ACL), aby złośliwy użytkownik nie mógł go modyfikować.  
  
 [Powrót do początku](#top)  
  
<a name="combining_managed_unmanaged"></a>   
## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Łączenie kodu zarządzanego i niezarządzanego w Profiler kodu  
 Nieprawidłowo napisany program profilujący może powodować własne odwołania cykliczne, powodując nieprzewidywalne zachowanie.  
  
 Przegląd środowiska CLR profilowania API może stworzyć wrażenie, że piszesz program profilujący, który zawiera zarządzane i niezarządzane komponenty, wywołujące siebie wzajemnie za pośrednictwem wywołania COM interop lub pośredniego.  
  
 Mimo że jest to możliwe z technicznego punktu widzenia, API profilowania nie obsługuje składników zarządzanych. Program profilujący CLR musi być całkowicie niezarządzany. Próby połączenia kodu zarządzanego i niezarządzanego w programie profilującym CLR mogą spowodować naruszenia zasad dostępu, awarię programu lub zakleszczenie. Składniki zarządzane profilera nastąpi ich elementów niezarządzanych, które wywołają składniki zarządzane ponownie, wynikiem odwołań cyklicznych zdarzeń.  
  
 Jedyną lokalizacją, gdzie CLR profiler może wywoływać kod zarządzany bezpiecznie jest w treści firmy Microsoft intermediate language (MSIL) metody. Zalecana praktyka modyfikacji ciała MSIL jest użycie metod rekompilacji JIT w [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu.  
  
 Istnieje również możliwość użycia starszych metod oprzyrządowania do modyfikowania MSIL. Przed zakończeniem kompilacji just-in-time (JIT) funkcji, program profilujący może wstawić zarządzane wywołania w treści MSIL metody, a następnie skompilować wg JIT go (zobacz [icorprofilerinfo::getilfunctionbody —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) metody). Ta technika może pomyślnie służyć do selektywnej Instrumentacji kodu zarządzanego lub do zbierania statystyk i wydajności danych dotyczących JIT.  
  
 Alternatywnie program profilujący kodu może wstawiać haki macierzyste w ciele MSIL każdej funkcji zarządzanej, która wywołuje kod niezarządzany. Ta technika może zostać użyta do Instrumentacji i zasięgu. Na przykład program profilujący kodu może wstawiać zaczepy Instrumentacji po każdym bloku MSIL, aby upewnić się, że blokada została wykonana. Modyfikacja treści MSIL metody to bardzo delikatna operacja, a istnieje wiele czynników, które należy wziąć pod uwagę.  
  
 [Powrót do początku](#top)  
  
<a name="unmanaged"></a>   
## <a name="profiling-unmanaged-code"></a>Profilowanie niezarządzanego kodu  
 Środowisko uruchomieniowe języka wspólnego (CLR) profilowania API zapewnia minimalną obsługę dla profilowania kodu niezarządzanego. Następująca funkcjonalność została zapewniona:  
  
-   Wyliczenie łańcuchów stosu. Ta funkcja umożliwia programowi profilującemu kodu określenie granic między kodem zarządzanym i niezarządzanym kodzie.  
  
-   Określenie tego, czy łańcuch stosu odnosi się do kodu zarządzanego lub kodu natywnego.  
  
 W wersjach programu .NET Framework 1.0 i 1.1 metody te są dostępne poprzez wewnątrzprocesowy podzbiór debugowania CLR interfejsu API. Są one zdefiniowane w pliku CorDebug.idl.  
  
 W programie .NET Framework 2.0 i nowszych możesz użyć [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody dla tej funkcji.  
  
 [Powrót do początku](#top)  
  
<a name="com"></a>   
## <a name="using-com"></a>Korzystając z modelu COM  
 Chociaż interfejsy profilowania są zdefiniowane jako interfejsy COM, środowisko uruchomieniowe języka wspólnego (CLR) nie inicjuje w rzeczywistości COM do użycia tych interfejsów. Przyczyną jest, aby uniknąć konieczności ustawiania modelu wątku za pomocą [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) funkcja zarządzaną aplikacją miała szansę, aby określić swój żądany model wątku. Podobnie, sam program profilujący nie powinien wywoływać `CoInitialize`, ponieważ może wybrać model wątku, który jest niezgodny z profilowaną aplikacją i może spowodować awarię aplikacji.  
  
 [Powrót do początku](#top)  
  
<a name="call_stacks"></a>   
## <a name="call-stacks"></a>Stosy wywołań  
 Profilowania API umożliwia uzyskanie stosów wywołań na dwa sposoby: metoda migawki stosu, która umożliwia gromadzenie rzadkich stosów wywołań, oraz metodę stosu w tle, która śledzi stos wywołań w każdej chwili.  
  
### <a name="stack-snapshot"></a>Migawka stosu  
 Migawka stosu jest śladem stosu wątku na moment w czasie. Profilowania API obsługuje śledzenie zarządzanej funkcji na stosie, ale pozostawia śledzenia funkcji niezarządzanych do własnego profiler walker stosu.  
  
 Aby uzyskać więcej informacji na temat sposobu programowania programu profilującego do przejścia przez stosy zarządzane, zobacz [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody, w tym zestawie dokumentacji i [Profiler stosu zalet w programie .NET Framework 2.0: Podstawy i](https://go.microsoft.com/fwlink/?LinkId=73638).
  
### <a name="shadow-stack"></a>Stos cieni  
 Przy użyciu metody migawki zbyt często można szybko utworzyć problemu z wydajnością. Jeśli chcesz śledzić stos często Twój program profilujący w zamian powinien skompilować cień stosu za pomocą [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md), i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) wywołań zwrotnych wyjątków. Stos cienia jest zawsze aktualny i szybko może być kopiowany do magazynu, ilekroć migawka stosu jest potrzebna.  
  
 Stos cieni może uzyskać argumenty funkcji, wartości zwracane i informacje dotyczące ogólnych instancji. Te informacje są dostępne tylko za pośrednictwem stosu w tle i można ją uzyskać podczas przekazywania kontroli do funkcji. Jednak te informacje mogą nie być dostępne później podczas wykonywania funkcji.  
  
 [Powrót do początku](#top)  
  
<a name="callbacks"></a>   
## <a name="callbacks-and-stack-depth"></a>Wywołania zwrotne i głębokość stosu  
 Wywołania zwrotne Profiler mogą być wydawane w okolicznościach bardzo ograniczonych stosu a przepełnienie stosu w wywołaniu zwrotnym profilera doprowadzi do natychmiastowego wyjścia procesu. Program profilujący powinien upewnij się, że używa tak mały stos, jak to możliwe w odpowiedzi na wywołania zwrotne. Jeśli program profilujący jest przeznaczony do użycia wobec procesów, które są odporne na przepełnienie stosu, sam program profilujący powinien również unikać wyzwolenia przepełnienia stosu.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Konfigurowanie środowiska profilowania](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Wyjaśnia sposób inicjowania programu profilującego, ustawiania powiadomień zdarzeń i profilowania usługi Windows.|  
|[Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|W tym artykule opisano niezarządzane interfejsy, których używa interfejs profilowania API.|  
|[Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Opisuje niezarządzane globalne funkcje statyczne, których używa interfejs profilowania API.|  
|[Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Opisuje niezarządzane wyliczenia, których używa interfejs profilowania API.|  
|[Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Opisuje niezarządzane struktury, których używa interfejs profilowania API.|
