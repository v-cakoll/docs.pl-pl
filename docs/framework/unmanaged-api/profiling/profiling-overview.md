---
title: Przegląd profilowania
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
ms.openlocfilehash: 3836b562d969726a6587d702d3edf45abb147d10
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588502"
---
# <a name="profiling-overview"></a>Przegląd profilowania

Profiler jest narzędziem, które monitoruje wykonywanie innej aplikacji. Profiler środowiska wykonawczego języka wspólnego (CLR) jest biblioteka łączy dynamicznych (DLL), który składa się z funkcji, które odbierają wiadomości z i wysyłać wiadomości do CLR przy użyciu interfejsu API profilowania. Biblioteka DLL profilera jest ładowana przez clr w czasie wykonywania.

Tradycyjne narzędzia do profilowania koncentrują się na pomiarze wykonania aplikacji. Oznacza to, że mierzą czas spędzony w każdej funkcji lub użycie pamięci aplikacji w czasie. Profilowanie interfejsu API jest przeznaczony dla szerszej klasy narzędzi diagnostycznych, takich jak narzędzia pokrycia kodu, a nawet zaawansowane pomoce debugowania. Wszystkie te zastosowania mają charakter diagnostyczny. Profilowanie interfejsu API nie tylko mierzy, ale także monitoruje wykonanie aplikacji. Z tego powodu interfejsu API profilowania nigdy nie powinny być używane przez samą aplikację, a wykonanie aplikacji nie powinno zależeć od (lub mieć na nie wpływ) profilera.

Profilowanie aplikacji CLR wymaga więcej obsługi niż profilowanie konwencjonalnie skompilowany kod maszyny. Dzieje się tak, ponieważ program CLR wprowadza pojęcia, takie jak domeny aplikacji, wyrzucanie elementów bezużytecznych, obsługa wyjątków zarządzanych, kompilacja kodu just-in-time (JIT) (konwersja języka pośredniego firmy Microsoft lub MSIL, kod na natywny kod maszynowy) i podobne funkcje. Konwencjonalne mechanizmy profilowania nie mogą zidentyfikować ani dostarczyć przydatnych informacji na temat tych funkcji. Interfejs API profilowania zapewnia te brakujące informacje skutecznie, z minimalnym wpływem na wydajność CLR i profilowane aplikacji.

Kompilacja JIT w czasie wykonywania zapewnia dobre możliwości profilowania. Profilowanie interfejsu API umożliwia profiler zmienić strumień kodu MSIL w pamięci dla procedury, zanim zostanie skompilowany JIT. W ten sposób profiler można dynamicznie dodać kod instrumentacji do określonych procedur, które wymagają głębszego badania. Chociaż takie podejście jest możliwe w konwencjonalnych scenariuszach, jest znacznie łatwiejsze do zaimplementowania dla programu CLR przy użyciu interfejsu API profilowania.

## <a name="the-profiling-api"></a>Interfejs API profilowania

Zazwyczaj profilowanie interfejsu API jest używany do pisania *profiler kodu*, który jest programem, który monitoruje wykonanie aplikacji zarządzanej.

Interfejs API profilowania jest używany przez bibliotekę DLL profilera, która jest ładowana do tego samego procesu co aplikacja, która jest profilowana. Biblioteka DLL profilera implementuje interfejs wywołania zwrotnego[(ICorProfilerCallback](icorprofilercallback-interface.md) w wersji .NET Framework 1.0 i 1.1, [ICorProfilerCallback2](icorprofilercallback2-interface.md) w wersji 2.0 i nowszej). CLR wywołuje metody w tym interfejsie, aby powiadomić profiler zdarzeń w procesie profilowanym. Profiler można wywołać z powrotem do środowiska wykonawczego przy użyciu metod w [interfejsach ICorProfilerInfo](icorprofilerinfo-interface.md) i [ICorProfilerInfo2,](icorprofilerinfo2-interface.md) aby uzyskać informacje o stanie profilowanej aplikacji.

> [!NOTE]
> Tylko część zbierająca dane rozwiązania profilera powinna być uruchomiona w tym samym procesie co profilowana aplikacja. Cały interfejs użytkownika i analiza danych powinny być wykonywane w oddzielnym procesie.

Na poniższej ilustracji pokazano, jak biblioteka DLL profilera współdziała z aplikacją, która jest profilowana i CLR.

![Zrzut ekranu przedstawiający architekturę profilowania.](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>Interfejsy powiadomień

[ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback2](icorprofilercallback2-interface.md) można uznać za interfejsy powiadomień. Interfejsy te składają się z metod, takich jak [ClassLoadStarted](icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](icorprofilercallback-classloadfinished-method.md)i [JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md). Za każdym razem, gdy CLR ładuje lub zwalnia klasę, kompiluje funkcję i tak dalej, wywołuje odpowiednią metodę w profilura `ICorProfilerCallback` lub `ICorProfilerCallback2` interfejsu.

Na przykład profiler może mierzyć wydajność kodu za pomocą dwóch funkcji powiadomień: [FunctionEnter2](functionenter2-function.md) i [FunctionLeave2](functionleave2-function.md). To tylko sygnatury czasowe każdego powiadomienia, gromadzi wyniki i wyprowadza listę, która wskazuje, które funkcje używane najwięcej czasu procesora CPU lub zegara ściennego podczas wykonywania aplikacji.

### <a name="the-information-retrieval-interfaces"></a>Interfejsy pobierania informacji

Inne główne interfejsy zaangażowane w profilowanie są [ICorProfilerInfo](icorprofilerinfo-interface.md) i [ICorProfilerInfo2](icorprofilerinfo2-interface.md). Profiler wywołuje te interfejsy, zgodnie z wymaganiami, aby uzyskać więcej informacji, aby pomóc w jego analizie. Na przykład za każdym razem, gdy CLR wywołuje [functionenter2](functionenter2-function.md) funkcja, dostarcza identyfikator funkcji. Profiler można uzyskać więcej informacji na temat tej funkcji, wywołując [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) metody odnajdywać funkcji klasy nadrzędnej, jego nazwę i tak dalej.

## <a name="supported-features"></a>Obsługiwane funkcje

Interfejs API profilowania zawiera informacje o różnych zdarzeń i akcji, które występują w czasie wykonywania języka wspólnego. Te informacje można użyć do monitorowania wewnętrznego funkcjonowania procesów i analizowania wydajności aplikacji .NET Framework.

Interfejs API profilowania pobiera informacje o następujących akcjach i zdarzeniach występujących w programie CLR:

- Zdarzenia uruchamiania i zamykania programu CLR.

- Zdarzenia tworzenia i zamykania domeny aplikacji.

- Zdarzenia załadunku i rozładunku zestawu.

- Zdarzenia załadunku i rozładunku modułów.

- Zdarzenia tworzenia i niszczenia w trybie wirtualnym COM.

- Kompilacja just-in-time (JIT) i zdarzenia tworzenia kodu.

- Zdarzenia załadunku i rozładunku klasy.

- Zdarzenia tworzenia i niszczenia wątków.

- Zdarzenia wprowadzania i zamykania funkcji.

- Wyjątki.

- Przejścia między wykonaniem kodu zarządzanego i niezarządzanego.

- Przejścia między różnymi kontekstami środowiska uruchomieniowego.

- Informacje o zawieszeniach czasu wykonywania.

- Informacje o stercie pamięci środowiska wykonawczego i działania wyrzucania elementów bezużytecznych.

Interfejs API profilowania można wywołać z dowolnego (niezarządzego) języka zgodnego z com.

Interfejs API jest wydajny w odniesieniu do zużycia procesora i pamięci. Profilowanie nie obejmuje zmian w profilowanych aplikacjach, które są wystarczająco istotne, aby spowodować mylące wyniki.

Profilowanie interfejsu API jest przydatne zarówno dla próbkowania i profilowania bez próbkowania. *Profiler próbkowania* sprawdza profil w regularnych znaczników zegara, powiedzmy, w 5 milisekund od siebie. Profiler *bez próbkowania* jest informowany o zdarzeniu synchronicznie z wątku, który powoduje zdarzenie.

### <a name="unsupported-functionality"></a>Nieobsługiwana funkcja

Interfejs API profilowania nie obsługuje następujących funkcji:

- Kod niezarządzany, który musi być profilowane przy użyciu konwencjonalnych metod Win32. Jednak profiler CLR zawiera zdarzenia przejścia w celu określenia granic między kodem zarządzanym i niezarządzanym.

- Samomodyfikujące aplikacje, które modyfikują własny kod do celów, takich jak programowanie zorientowane na aspekt.

- Sprawdzanie granic, ponieważ interfejs API profilowania nie zawiera tych informacji. CLR zapewnia wewnętrzna obsługa sprawdzania granic całego kodu zarządzanego.

- Profilowanie zdalne, które nie jest obsługiwane z następujących powodów:

  - Zdalne profilowanie wydłuża czas wykonywania. Korzystając z interfejsów profilowania, należy zminimalizować czas wykonywania, tak aby wyniki profilowania nie będzie nadmiernie wpływa. Jest to szczególnie ważne, gdy wydajność wykonywania jest monitorowany. Jednak profilowanie zdalne nie jest ograniczeniem, gdy interfejsy profilowania są używane do monitorowania użycia pamięci lub w celu uzyskania informacji w czasie wykonywania ramek stosu, obiektów i tak dalej.

  - Profiler kodu CLR musi zarejestrować jeden lub więcej interfejsów wywołania zwrotnego ze środowiska wykonawczego na komputerze lokalnym, na którym jest uruchomiona profilowana aplikacja. Ogranicza to możliwość tworzenia zdalnego profilera kodu.

## <a name="notification-threads"></a>Wątki powiadomień

W większości przypadków wątek, który generuje zdarzenie wykonuje również powiadomienia. Takie powiadomienia (na przykład [FunctionEnter](functionenter-function.md) i [FunctionLeave)](functionleave-function.md)nie `ThreadID`muszą podawać jawnego . Ponadto profiler może zdecydować się na użycie magazynu lokalnego wątku do przechowywania i aktualizowania swoich bloków `ThreadID` analizy zamiast indeksowania bloków analizy w magazynie globalnym, na podstawie wątku, którego dotyczy problem.

Należy zauważyć, że te wywołania zwrotne nie są serializowane. Użytkownicy muszą chronić swój kod, tworząc struktury danych bezpiecznych dla wątków i blokując kod profilera, jeśli jest to konieczne, aby zapobiec dostępowi równoległemu z wielu wątków. W związku z tym w niektórych przypadkach można otrzymać nietypową sekwencję wywołań zwrotnych. Na przykład załóżmy, że aplikacja zarządzana jest tarło dwa wątki, które wykonują identyczny kod. W takim przypadku jest możliwe, aby otrzymać [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) zdarzenie dla `FunctionEnter` niektórych funkcji z jednego wątku i wywołania zwrotnego z innego wątku przed odebraniem [ICorProfilerCallback::JITCompilationFinished wywołania](icorprofilercallback-jitcompilationfinished-method.md) zwrotnego. W takim przypadku użytkownik otrzyma `FunctionEnter` wywołanie zwrotne dla funkcji, która może nie być w pełni just-in-time (JIT) skompilowany jeszcze.

## <a name="security"></a>Zabezpieczenia

Biblioteka DLL profilera jest niezarządzaną biblioteką DLL, która działa jako część aparatu wykonywania środowiska wykonawczego języka wspólnego. W rezultacie kod w biblioteki DLL profilera nie podlega ograniczeniom zabezpieczeń dostępu do kodu zarządzanego. Jedynymi ograniczeniami biblioteki DLL profilera są te nałożone przez system operacyjny na użytkownika, który uruchamia profilowane aplikacji.

Autorzy profilera powinni podjąć odpowiednie środki ostrożności, aby uniknąć problemów związanych z zabezpieczeniami. Na przykład podczas instalacji biblioteki DLL profilera powinny zostać dodane do listy kontroli dostępu (ACL), tak aby złośliwy użytkownik nie mógł go zmodyfikować.

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Łączenie kodu zarządzanego i niezarządzanego w programie Profiler kodu

Niepoprawnie napisany profiler może powodować odwołania cykliczne do siebie, co powoduje nieprzewidywalne zachowanie.

Przegląd interfejsu API profilowania CLR może stworzyć wrażenie, że można napisać profiler, który zawiera składniki zarządzane i niezarządzane, które wywołują się wzajemnie za pośrednictwem com interop lub pośrednich wywołań.

Chociaż jest to możliwe z punktu widzenia projektu, profilowanie interfejsu API nie obsługuje składników zarządzanych. Profiler CLR musi być całkowicie niezarządzane. Próby połączenia kodu zarządzanego i niezarządzanego w profilu CLR może spowodować naruszenia dostępu, błąd programu lub zakleszczenia. Zarządzane składniki profilera będą uruchamiać zdarzenia z powrotem do ich składników niezarządzanych, które następnie wywołać składniki zarządzane ponownie, co powoduje odwołania cykliczne.

Jedyną lokalizacją, w której profiler CLR można bezpiecznie wywołać kod zarządzany jest w treści języka pośredniego firmy Microsoft (MSIL) metody. Zalecaną praktyką modyfikowania treści MSIL jest użycie metod ponownej kompilacji JIT w interfejsie [ICorProfilerCallback4.](icorprofilercallback4-interface.md)

Istnieje również możliwość użycia starszych metod instrumentacji do modyfikowania MSIL. Przed kompilacji just-in-time (JIT) funkcji jest zakończona, profiler można wstawić wywołania zarządzane w treści MSIL metody, a następnie JIT-skompilować go (zobacz [ICorProfilerInfo::GetILFunctionBody](icorprofilerinfo-getilfunctionbody-method.md) metody). Technika ta może być z powodzeniem używana do selektywnego instrumentacji kodu zarządzanego lub do zbierania danych statystycznych i danych dotyczących wydajności JIT.

Alternatywnie profiler kodu można wstawić natywne haki w treści MSIL każdej funkcji zarządzanej, która wywołuje do kodu niezarządzanego. Technika ta może być stosowana do oprzyrządowania i pokrycia. Na przykład profiler kodu można wstawić haki instrumentacji po każdym bloku MSIL, aby upewnić się, że blok został wykonany. Modyfikacja treści MSIL metody jest bardzo delikatną operacją i istnieje wiele czynników, które należy wziąć pod uwagę.

## <a name="profiling-unmanaged-code"></a>Profilowanie niezarządzanego kodu

Interfejs API profilowania środowiska wykonawczego języka wspólnego (CLR) zapewnia minimalną obsługę profilowania kodu niezarządzanego. Dostępne są następujące funkcje:

- Wyliczenie łańcuchów stosu. Ta funkcja umożliwia profiler kodu, aby określić granicę między kodem zarządzanym i kod niezarządzane.

- Określenie, czy łańcuch stosu odpowiada kodowi zarządzanemu lub kodowi macierzystemu.

W programie .NET Framework w wersjach 1.0 i 1.1 te metody są dostępne za pośrednictwem podzbioru w procesie interfejsu API debugowania programu CLR. Są one zdefiniowane w pliku CorDebug.idl.

W .NET Framework 2.0 i nowszych, można użyć [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metody dla tej funkcji.

## <a name="using-com"></a>Korzystanie z com

Mimo że interfejsy profilowania są zdefiniowane jako interfejsy COM, środowisko wykonawcze języka wspólnego (CLR) w rzeczywistości nie inicjuje COM do korzystania z tych interfejsów. Powodem jest, aby uniknąć konieczności ustawiania modelu wątkowego przy użyciu [Funkcji CoInitialize,](/windows/desktop/api/objbase/nf-objbase-coinitialize) zanim aplikacja zarządzana miała szansę określić jego pożądanego modelu wątkowego. Podobnie profiler sam nie należy `CoInitialize`wywołać , ponieważ może wybrać model wątków, który jest niezgodny z aplikacją jest profilowane i może spowodować niepowodzenie aplikacji.

## <a name="call-stacks"></a>Stosy połączeń

Interfejs API profilowania zapewnia dwa sposoby uzyskania stosów wywołań: metoda migawki stosu, która umożliwia rzadkie zbieranie stosów wywołań i metoda stosu cieni, która śledzi stos wywołań w każdej chwili.

### <a name="stack-snapshot"></a>Migawka stosu

Migawka stosu jest ślad stosu wątku w jednej chwili w czasie. Profilowanie interfejsu API obsługuje śledzenie funkcji zarządzanych na stosie, ale pozostawia śledzenie funkcji niezarządzanych do własnego stosu profilera walker.

Aby uzyskać więcej informacji na temat programowania profiler chodzić zarządzanych stosów, zobacz [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metody w tym zestawie dokumentacji i [Profiler Stack Walking w .NET Framework 2.0: Podstawy i poza nią](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10)).

### <a name="shadow-stack"></a>Stos cieni

Korzystanie z metody migawki zbyt często można szybko utworzyć problem z wydajnością. Jeśli chcesz często przyjmować ślady stosu, profiler powinien zamiast tego utworzyć stos cieni przy użyciu [functionenter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), [FunctionTailcall2](functiontailcall2-function.md)i [ICorProfilerCallback2](icorprofilercallback2-interface.md) wywołania zwrotne wyjątków. Stos cieni jest zawsze aktualny i można szybko skopiować do magazynu, gdy wymagana jest migawka stosu.

Stos cieni może uzyskać argumenty funkcji, zwracanie wartości i informacje o ogólnych wystąpieniach. Te informacje są dostępne tylko za pośrednictwem stosu cieni i mogą być uzyskane, gdy kontrola jest przekazywana do funkcji. Jednak te informacje mogą nie być dostępne później podczas uruchamiania funkcji.

## <a name="callbacks-and-stack-depth"></a>Wywołania zwrotne i głębokość stosu

Wywołania zwrotne profilera mogą być wydawane w bardzo ograniczonych warunkach stosu, a przepełnienie stosu w wywołaniu zwrotnym profilera doprowadzi do natychmiastowego zakończenia procesu. Profiler należy upewnić się, aby używać jak najmniejszego stosu, jak to możliwe w odpowiedzi na wywołania zwrotne. Jeśli profiler jest przeznaczony do użycia w przypadku procesów, które są niezawodne względem przepełnienia stosu, profiler sam należy również unikać wyzwalania przepełnienia stosu.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Konfigurowanie środowiska profilowania](setting-up-a-profiling-environment.md)|W tym artykule wyjaśniono, jak zainicjować profiler, ustawić powiadomienia o zdarzeniach i profilu usługi systemu Windows.|
|[Interfejsy profilowania](profiling-interfaces.md)|W tym artykule opisano interfejsy niezarządzane, których używa interfejs api profilowania.|
|[Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)|W tym artykule opisano niezarządzane globalne funkcje statyczne używane przez interfejs API profilowania.|
|[Profilowanie — wyliczenia](profiling-enumerations.md)|W tym artykule opisano niezarządzane wyliczenia używane przez interfejs API profilowania.|
|[Profiling — struktury](profiling-structures.md)|W tym artykule opisano struktury niezarządzane, które używa interfejsu API profilowania.|
