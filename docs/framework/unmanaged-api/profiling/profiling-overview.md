---
title: "Omówienie profilowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d7918a369b5a5656fa2e059bdaaf6c211bd022c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-overview"></a>Omówienie profilowania
<a name="top"></a>Profiler to narzędzie, które monitoruje wykonywanie innej aplikacji. Typowe profiler środowiska uruchomieniowego (języka wspólnego CLR) języka jest biblioteki dołączanej (dynamicznie DLL), która składa się z funkcji, które odbierać komunikaty z i wysyłać wiadomości do środowiska CLR za pomocą interfejsu API profilowania. Biblioteki DLL profilera jest ładowany przez środowisko CLR w czasie wykonywania.  
  
 Tradycyjne narzędzia profilowania skupić się na mierzeniu wykonywania aplikacji. Oznacza to pomiaru ich czasu poświęcana w każdej funkcji lub użycie pamięci aplikacji w czasie. Interfejsu API profilowania dotyczy szerszego klasy narzędzi diagnostycznych, takich jak narzędzia pokrycia kodu i nawet zaawansowane debugowania pomocy. Te ustawienia są wszystkie diagnostycznych charakter. Interfejsu API profilowania nie tylko miary, ale również monitoruje wykonywania aplikacji. Z tego powodu interfejsu API profilowania nie mogą być używane przez samą aplikację, a nie należy uwzględniać wykonywania aplikacji (lub dotyczy) profilera.  
  
 Profilowanie aplikacji CLR wymaga więcej możliwości niż profilowania tradycyjnie skompilowany kod maszyny. Jest to spowodowane CLR wprowadza pojęcia, takie jak obsługa wyjątków zarządzanych domeny aplikacji, wyrzucanie elementów bezużytecznych just-in-time (JIT) kompilacji kodu (konwertowanie język pośredni firmy Microsoft lub MSIL, kod do kodu macierzystego maszyny) i podobnych funkcje. Konwencjonalne mechanizmów profilowania nie można zidentyfikować lub dostarczające przydatnych informacji o tych funkcjach. Interfejsu API profilowania zapewnia brakujących informacji wydajnie, minimalny wpływ na wydajność środowiska CLR i profilowana aplikacja.  
  
 Kompilacja JIT w czasie wykonywania zapewnia dobre możliwości do profilowania. Interfejsu API profilowania umożliwia profilera zmienić strumienia kodu MSIL w pamięci dla procedury, zanim zostanie skompilowany JIT. W ten sposób profilera można dynamicznie dodać kod Instrumentacji do określonej procedury, które wymagają głębsza analiza. Takie podejście jest możliwe w scenariuszach z konwencjonalnej, jest znacznie łatwiejsze do wdrożenia dla środowiska CLR za pomocą interfejsu API profilowania.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Interfejsu API profilowania](#profiling_api)  
  
-   [Obsługiwane funkcje](#support)  
  
-   [Wątki powiadomień](#notification_threads)  
  
-   [Zabezpieczeń](#security)  
  
-   [Łączenie zarządzanych i niezarządzanych kodu w profilera kodu](#combining_managed_unmanaged)  
  
-   [Niezarządzany kod profilowania](#unmanaged)  
  
-   [Przy użyciu modelu COM](#com)  
  
-   [Stosy wywołań](#call_stacks)  
  
-   [Wywołania zwrotne i głębokość stosu](#callbacks)  
  
-   [Tematy pokrewne](#related_topics)  
  
<a name="profiling_api"></a>   
## <a name="the-profiling-api"></a>Interfejsu API profilowania  
 Zazwyczaj interfejsu API profilowania służy do zapisywania *program profilujący*, który jest program, który monitoruje wykonywanie zarządzanej aplikacji.  
  
 Interfejsu API profilowania jest używany przez profiler biblioteki DLL, który jest ładowany do tego samego procesu jak aplikacja, która jest poddawany profilowaniu. Biblioteki DLL profilera implementuje interfejs wywołania zwrotnego ([ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) w programie .NET Framework w wersji 1.0, 1.1, [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) w wersji 2.0 lub nowszy). Środowisko CLR wywołuje metody tego interfejsu do powiadamiania profilera zdarzenia PROFILOWANEGO procesu. Profiler może wywołania zwrotnego w czasie wykonywania przez przy użyciu metod w [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) i [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interfejsów, aby uzyskać informacje o stanie profilowana aplikacja.  
  
> [!NOTE]
>  W tym samym procesie jako profilowana aplikacja powinna być uruchomiona tylko częścią gromadzenia danych rozwiązania profilera. Wszystkich użytkowników interface i analizy danych, należy wykonać w ramach osobnej operacji.  
  
 Na poniższej ilustracji przedstawiono, jak biblioteki DLL profilera współdziała z aplikacji, która jest PROFILOWANEGO i środowiska CLR.  
  
 ![Profilowanie architektury](../../../../docs/framework/unmanaged-api/profiling/media/profilingarch.png "ProfilingArch")  
Profilowanie architektury  
  
### <a name="the-notification-interfaces"></a>Interfejsy powiadomień  
 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) mogą zostać uwzględnione interfejsy powiadomień. Te interfejsy składają się z metody takie jak [ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md), i [JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Za każdym razem CLR ładuje lub zwalnia klasy kompiluje funkcji i itd., wywołuje odpowiedniej metody w profilera `ICorProfilerCallback` lub `ICorProfilerCallback2` interfejsu.  
  
 Na przykład profiler może pomiaru wydajności kodu za pomocą dwóch funkcji powiadomień: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) i [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Go tylko sygnatury czasowe akumuluje wyniki każdego powiadomienia i wyświetla listę, która wskazuje, które funkcje używane najwięcej procesora CPU lub tablicy zegara czasu podczas uruchamiania aplikacji.  
  
### <a name="the-information-retrieval-interfaces"></a>Interfejsy pobierania informacji  
 Inne objętego profilowania głównego interfejsy są [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) i [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Profiler wywołuje te interfejsy zgodnie z wymaganiami, aby uzyskać więcej informacji na temat jego analizy. Na przykład, gdy środowisko CLR wywołuje [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) funkcji, podaje identyfikator funkcji. Profiler można uzyskać więcej informacji na temat tej funkcji, wywołując [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody odnajdywania przez funkcję klasy nadrzędnej, jego nazwa i tak dalej.  
  
 [Powrót do początku](#top)  
  
<a name="support"></a>   
## <a name="supported-features"></a>Obsługiwane funkcje  
 Interfejsu API profilowania zawiera informacje o różnych zdarzeń i akcje, które występują w środowisko uruchomieniowe języka wspólnego. Monitorowanie przebiega procesów oraz analizowanie wydajności aplikacji .NET Framework, można użyć tych informacji.  
  
 Interfejsu API profilowania pobiera informacje o następujące akcje i zdarzenia występujące w środowisku CLR:  
  
-   Zdarzenia uruchamiania i wyłączania CLR.  
  
-   Zdarzenia tworzenia i zamykania aplikacji domeny.  
  
-   Zestaw ładowanie i zwalnianie zdarzenia.  
  
-   Moduł ładowanie i zwalnianie zdarzenia.  
  
-   COM vtable tworzenie i likwidacja zdarzenia.  
  
-   Just-in-time (JIT) kompilacji i zdarzenia pitching kodu.  
  
-   Klasa zdarzeń ładowania i zwalniania.  
  
-   Tworzenie i likwidacja zdarzenia wątków.  
  
-   Wejście i wyjście z zdarzenia funkcji.  
  
-   Wyjątki.  
  
-   Przejścia między wykonanie kodu zarządzane i niezarządzane.  
  
-   Przejścia między runtime różnych kontekstach.  
  
-   Informacje o zawieszeniu środowiska wykonawczego.  
  
-   Informacje na temat środowiska uruchomieniowego pamięci sterty i odzyskiwanie kolekcji działania.  
  
 Z dowolnego języka zgodny z modelu COM (niezarządzany) można wywołać interfejsu API profilowania.  
  
 Interfejs API jest efektywne względem zużycie procesora CPU i pamięci. Profilowanie nie obejmują zmiany do PROFILOWANEGO aplikacji, które są istotne, błędne wyniki.  
  
 Interfejsu API profilowania przydaje się do profilowania pobierania próbek i z systemem innym niż próbkowania. A *próbkowania profilera* przeprowadzający profilu przy Takty zegara regularne powiedzieć, w milisekundach 5 od siebie. A *z systemem innym niż próbkowania profilera* zostanie poinformowany o zdarzenie synchronicznie przy użyciu wątku, który powoduje, że zdarzenie.  
  
### <a name="unsupported-functionality"></a>Nieobsługiwanych funkcji  
 Interfejsu API profilowania nie obsługuje następujące funkcje:  
  
-   Niezarządzany kod, który musi być profilowane konwencjonalnej metodami Win32. Jednak CLR profiler zawiera zdarzenia przejścia do określenia granicę między zarządzanymi i niezarządzanymi kodu.  
  
-   Modyfikowanie własnym aplikacje, które modyfikują własny kod do celów, takich jak programowanie zorientowane na proporcji.  
  
-   Sprawdzanie, ponieważ interfejsu API profilowania nie dostarcza informacji granic. Środowisko CLR zapewnia obsługę wewnętrzne granice sprawdzanie wszystkich kodu zarządzanego.  
  
-   Zdalne profilowania, która nie jest obsługiwana w następujących sytuacjach:  
  
    -   Profilowanie zdalne rozszerza czasu wykonywania. Gdy używasz interfejsy profilowania, można zminimalizować czas wykonania tak, aby wyniki profilowania nie ma negatywnego wpływu. Jest to szczególnie istotne podczas wykonywania wydajności jest monitorowany. Jednak profilowanie zdalne nie jest to ograniczenie podczas profilowania interfejsy są używane do monitorowania wykorzystania pamięci lub Aby uzyskać informacje czasu wykonywania ramki stosu, obiekty i tak dalej.  
  
    -   Profiler CLR kod należy zarejestrować co najmniej jeden interfejs wywołania zwrotnego ze środowiskiem uruchomieniowym na komputerze lokalnym, na którym działa profilowana aplikacja. To ogranicza możliwość tworzenia profilera zdalnego kodu.  
  
-   Profilowanie w środowisku produkcyjnym wymagania wysokiej dostępności. Interfejsu API profilowania został utworzony w celu obsługi diagnostyki w czasie opracowywania. Nie przeszły rygorystyczne testy wymagane do obsługi środowisk produkcyjnych.  
  
 [Powrót do początku](#top)  
  
<a name="notification_threads"></a>   
## <a name="notification-threads"></a>Wątki powiadomień  
 W większości przypadków wątku, który generuje zdarzenie wykonuje powiadomienia. Powiadomienia (na przykład [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) i [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) nie trzeba podać jawne `ThreadID`. Ponadto profilera zdecydować się na używane magazynu wątków lokalnych do przechowywania i zaktualizuj jego bloków analizy zamiast indeksowania bloków analizy w globalnej pamięci masowej, na podstawie `ThreadID` dotyczy wątku.  
  
 Należy pamiętać, że te wywołania zwrotne nie są serializowane. Użytkownicy muszą chronić ich kodu przez utworzenie struktury danych wątkowo i blokowanie kodu profilera, gdzie jest to konieczne w celu zapobieżenia równoległych dostęp wiele wątków. Dlatego w niektórych przypadkach może odbierać nietypowe sekwencję wywołań zwrotnych. Na przykład przypuśćmy, że zarządzanej aplikacji jest duplikowanie dwóch wątków, które są wykonywane w taki sam kod. W takim przypadku użytkownik może odbierać [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) zdarzenia dla niektórych funkcji z jednego wątku i `FunctionEnter` wywołania zwrotnego z wątku przed odbieranie [ ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) wywołania zwrotnego. W takim przypadku użytkownik otrzyma `FunctionEnter` wywołania zwrotnego dla funkcji, które mogły nie zostać całkowicie just-in-time (JIT) jeszcze skompilowana.  
  
 [Powrót do początku](#top)  
  
<a name="security"></a>   
## <a name="security"></a>Zabezpieczenia  
 Profiler biblioteki DLL jest niezarządzany biblioteki DLL, która działa jako część aparat wykonywania środowiska uruchomieniowego języka wspólnego. W związku z tym kod w profilera, które biblioteki DLL nie podlega ograniczeniom zarządzane zabezpieczenia dostępu kodu. Jedynymi ograniczeniami profilera biblioteki DLL są nakładane przez system operacyjny na użytkownika, który działa profilowana aplikacja.  
  
 Autorzy profilera należy podjąć odpowiednie środki ostrożności, aby uniknąć problemów związanych z zabezpieczeniami. Na przykład podczas instalacji, biblioteki DLL profilera powinien można dodać do listy kontroli dostępu (ACL), aby złośliwy użytkownik nie można go modyfikować.  
  
 [Powrót do początku](#top)  
  
<a name="combining_managed_unmanaged"></a>   
## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Łączenie zarządzanych i niezarządzanych kodu w profilera kodu  
 Niepoprawnie napisany profilera może spowodować cykliczne odwołanie do samej siebie, co w sposób nieprzewidywalny.  
  
 Przegląd profilowania API środowiska CLR może tworzyć wrażenie, który może zapisać profilera, zawierający składniki zarządzane i niezarządzane, wywołujące wzajemnie za pośrednictwem wywołania COM interop lub pośrednie.  
  
 Jest to możliwe z punktu widzenia projektu, interfejsu API profilowania nie obsługuje składników zarządzanych. CLR profiler muszą być całkowicie niezarządzane. Próbuje połączyć kod zarządzane i niezarządzane w CLR profiler może spowodować naruszenia zasad dostępu, program awarii lub zakleszczenia. Zarządzane składniki profilera będą wyzwalać zdarzeń do ich niezarządzane składniki, które następnie wywołać składników zarządzanych do ponownie, co powoduje odwołań cyklicznych.  
  
 Tylko gdy CLR profiler mogą wywoływać kodu zarządzanego bezpiecznie znajduje się w treści metody język pośredni (MSIL) firmy Microsoft. Zalecanym działaniem w przypadku modyfikowania treści MSIL jest użycie metody ponownej kompilacji JIT w [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfejsu.  
  
 Istnieje również możliwość użycia starsze metody Instrumentacji do modyfikowania MSIL. Przed ukończeniem kompilacji just-in-time (JIT) funkcji profilera można wstawić wywołań zarządzanych w treści metody, a następnie kompilacji JIT MSIL go (zobacz [ICorProfilerInfo::GetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) metody). Ta technika pomyślnie może służyć do selektywnego Instrumentacji kodu zarządzanego lub w celu zbierania statystyk i wydajności dane dotyczące JIT.  
  
 Alternatywnie profilera kodu można wstawić natywnego punkty zaczepienia w treści MSIL każdego zarządzanego funkcji, który odwołuje się do kodu niezarządzanego. Ta technika może służyć do Instrumentacji i pokrycie. Na przykład profilera kodu można wstawić punkty zaczepienia w Instrumentacji po każdym bloku MSIL, aby upewnić się, że wykonano bloku. Modyfikacja MSIL treści metody jest bardzo delikatny operację, i istnieje wiele czynników, które należy wziąć pod uwagę.  
  
 [Powrót do początku](#top)  
  
<a name="unmanaged"></a>   
## <a name="profiling-unmanaged-code"></a>Niezarządzany kod profilowania  
 Środowisko uruchomieniowe języka wspólnego (CLR) interfejsu API profilowania zapewnia obsługę minimalnego profilowania kodu niezarządzanego. Podano następujące funkcje:  
  
-   Wyliczenie łańcuchów stosu. Ta funkcja umożliwia profilera kod określić granicę między kodu zarządzanego i kodu niezarządzanego.  
  
-   Oznaczanie czy łańcuch stosu odnosi się do kodu zarządzanego i kodu natywnego.  
  
 W wersji systemu .NET Framework 1.0 i 1.1 te metody są dostępne w trakcie podzbiór CLR debugowanie interfejsu API. Są one zdefiniowane w pliku CorDebug.idl.  
  
 W .NET Framework 2.0 lub nowszej, można użyć [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodę dla tej funkcji.  
  
 [Powrót do początku](#top)  
  
<a name="com"></a>   
## <a name="using-com"></a>Przy użyciu modelu COM  
 Mimo że profilowania interfejsy są zdefiniowane jako interfejsy modelu COM, środowisko uruchomieniowe języka wspólnego (CLR) nie faktycznie zainicjować modelu COM w celu użycia tych interfejsów. Przyczyną jest aby uniknąć konieczności ustawiania modelu wątkowości przy użyciu [CoInitialize](http://msdn.microsoft.com/library/windows/desktop/ms678543\(v=vs.85\).aspx) funkcji przed zarządzanej aplikacji miał możliwość określić jego żądanego modelu wątkowości. Podobnie, nie powinny wywoływać profilera sam `CoInitialize`, ponieważ może wybierz model wątków, która jest niezgodna z aplikacją PROFILOWANEGO i może spowodować awarię aplikacji.  
  
 [Powrót do początku](#top)  
  
<a name="call_stacks"></a>   
## <a name="call-stacks"></a>Stosy wywołań  
 Interfejsu API profilowania udostępnia dwa sposoby uzyskania stosy wywołań: metoda migawki stosu, co umożliwia gromadzenie rozrzedzonych stosy wywołań, i metodę stosu w tle, który śledzi stos wywołań w każdej chwili.  
  
### <a name="stack-snapshot"></a>Migawki stosu  
 Migawki stosu jest śladu stosu wątku w chwili w czasie. Interfejsu API profilowania obsługuje śledzenie zarządzanego funkcji na stosie, ale pozostawia śledzenie niezarządzanych funkcji do własnych profilera walkera stosu.  
  
 Aby uzyskać więcej informacji na temat programu profiler do przeszukania zarządzane stosy, zobacz [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody w tym zestawie dokumentacji i [profilera stosu przejście w .NET Framework 2.0: Podstawy i poza](http://go.microsoft.com/fwlink/?LinkId=73638).
  
### <a name="shadow-stack"></a>Stos w tle  
 Przy użyciu metody migawki zbyt często może szybko utworzyć problem z wydajnością. Jeśli chcesz wykonać często ślady stosu, profilera powinno zamiast tego utworzyć stosu tle przy użyciu [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md), i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) wyjątek wywołań zwrotnych. Stos tle zawsze jest aktualny i szybko można skopiować do magazynu w każdym przypadku, gdy wymagane jest migawki stosu.  
  
 Stos tle może uzyskać argumenty funkcji zwracanych wartości i informacji na temat ogólnych utworzonych wystąpieniach. Te informacje są dostępne tylko za pośrednictwem stosu w tle i mogą być uzyskane, gdy formant jest przekazywany do funkcji. Jednak te informacje mogą nie można później, podczas wykonywania funkcji.  
  
 [Powrót do początku](#top)  
  
<a name="callbacks"></a>   
## <a name="callbacks-and-stack-depth"></a>Wywołania zwrotne i głębokość stosu  
 Wywołania zwrotne Profiler może być wystawiony w sytuacji bardzo ograniczone stosu i przepełnienie stosu w wywołaniu zwrotnym profilera doprowadzi do zakończenia procesu bezpośrednim. Profiler powinien upewnij się, że używany jako mały stos możliwie w odpowiedzi na wywołania zwrotne. Jeśli profiler jest przeznaczony do użycia dla procesów, które są odporna przepełnienie stosu, profilera się również unikać wyzwalania przepełnienia stosu.  
  
 [Powrót do początku](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Konfigurowanie środowiska profilowania](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Wyjaśniono, jak zainicjować profilera, ustawienie powiadomień o zdarzeniach i profilu usługi systemu Windows.|  
|[Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|W tym artykule opisano niezarządzane interfejsy, które używa interfejsu API profilowania.|  
|[Statyczne funkcje globalne profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Opisuje niezarządzane statyczne funkcje globalne, które używa interfejsu API profilowania.|  
|[Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|W tym artykule opisano niezarządzane wyliczenia, które używa interfejsu API profilowania.|  
|[Struktury profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|W tym artykule opisano niezarządzane struktury, których używa interfejsu API profilowania.|
