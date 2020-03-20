---
title: Konfigurowanie środowiska profilowania
ms.date: 03/30/2017
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
ms.openlocfilehash: 32ebb868ea64a24fba80133b1a0eb539f51cb411
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176971"
---
# <a name="setting-up-a-profiling-environment"></a>Konfigurowanie środowiska profilowania
> [!NOTE]
> Wprowadzono istotne zmiany w profilowaniu w programie .NET Framework 4.  
  
 Po uruchomieniu procesu zarządzanego (aplikacji lub usługi) ładuje środowisko uruchomieniowe języka wspólnego (CLR). Po zainicjowaniu clr, ocenia następujące dwie zmienne środowiskowe, aby zdecydować, czy proces powinien łączyć się z profilera:  
  
- COR_ENABLE_PROFILING: ŚRODOWISKO CLR łączy się z profilerem tylko wtedy, gdy ta zmienna środowiskowa istnieje i jest ustawiona na 1.  
  
- COR_PROFILER: Jeśli sprawdzanie COR_ENABLE_PROFILING przebiega pomyślnie, clr łączy się z profilerem, który ma ten identyfikator CLSID lub ProgID, który musi być wcześniej przechowywany w rejestrze. COR_PROFILER zmienna środowiskowa jest zdefiniowana jako ciąg, jak pokazano w poniższych dwóch przykładach.  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Aby profilować aplikację CLR, należy ustawić COR_ENABLE_PROFILING i COR_PROFILER zmiennych środowiskowych przed uruchomieniem aplikacji. Należy również upewnić się, że biblioteka DLL profilera jest zarejestrowana.  
  
> [!NOTE]
> Począwszy od .NET Framework 4 profileers nie muszą być rejestrowane.  
  
> [!NOTE]
> Aby używać programów .NET Framework w wersjach 2.0, 3.0 i 3.5 profilerów w .NET Framework 4 i nowszych wersjach, należy ustawić zmienną środowiskową COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Zakres zmiennej środowiskowej  
 Sposób ustawienia COR_ENABLE_PROFILING i COR_PROFILER zmiennych środowiskowych określi ich zakres wpływu. Te zmienne można ustawić w jeden z następujących sposobów:  
  
- Jeśli ustawisz zmienne w wywołaniu [ICorDebug::CreateProcess,](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) będą one stosowane tylko do aplikacji, która jest uruchomiona w tym czasie. (Będą one również stosowane do innych aplikacji uruchomionych przez tę aplikację, które dziedziczą środowisko.)  
  
- Jeśli ustawisz zmienne w oknie wiersza polecenia, będą one stosowane do wszystkich aplikacji, które są uruchamiane z tego okna.  
  
- Jeśli ustawisz zmienne na poziomie użytkownika, będą one stosowane do wszystkich aplikacji, które można uruchomić z Eksploratora plików. Okno wiersza polecenia, które zostanie otwarte po ustawieniu zmiennych, będzie miało te ustawienia środowiska, podobnie jak każda aplikacja uruchamiana od tego okna. Aby ustawić zmienne środowiskowe na poziomie użytkownika, kliknij prawym przyciskiem myszy **pozycję Mój komputer**, kliknij polecenie **Właściwości**, kliknij kartę **Zaawansowane,** kliknij pozycję **Zmienne środowiskowe**i dodaj zmienne do listy **Zmienne użytkownika.**  
  
- Jeśli ustawisz zmienne na poziomie komputera, będą one stosowane do wszystkich aplikacji, które są uruchamiane na tym komputerze. Okno wiersza polecenia, które zostanie otwarte na tym komputerze, będzie miało te ustawienia środowiska, podobnie jak każda aplikacja uruchamiana od tego okna. Oznacza to, że każdy proces zarządzany na tym komputerze rozpocznie się od profilera. Aby ustawić zmienne środowiskowe na poziomie komputera, kliknij prawym przyciskiem myszy **pozycję Mój komputer**, kliknij polecenie **Właściwości**, kliknij kartę **Zaawansowane,** kliknij pozycję **Zmienne środowiskowe**, dodaj zmienne do listy **Zmienne systemowe,** a następnie uruchom ponownie komputer. Po ponownym uruchomieniu zmienne będą dostępne w całym systemie.  
  
 W przypadku profilowania usługi systemu Windows należy ponownie uruchomić komputer po ustawieniu zmiennych środowiskowych i zarejestrowaniu biblioteki DLL profilera. Aby uzyskać więcej informacji na temat tych zagadnień, zobacz [sekcję Profilowanie usługi systemu Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Dodatkowe uwagi  
  
- Klasa profilera implementuje interfejsy [ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback2.](icorprofilercallback2-interface.md) W programie .NET Framework w wersji 2.0 profiler musi zaimplementować `ICorProfilerCallback2`. Jeśli tak nie `ICorProfilerCallback2` jest, nie zostanie załadowany.  
  
- Tylko jeden profiler może profilować proces w tym czasie w danym środowisku. Można zarejestrować dwa różne profilera w różnych środowiskach, ale każdy musi profilować oddzielne procesy. Profiler musi być zaimplementowany jako biblioteka DLL serwera COM w toku, która jest mapowana na tę samą przestrzeń adresową, co proces, który jest profilowany. Oznacza to, że profiler działa w procesie. Program .NET Framework nie obsługuje żadnego innego typu serwera COM. Na przykład jeśli profiler chce monitorować aplikacje z komputera zdalnego, musi implementować agentów modułu zbierającego na każdym komputerze. Agenci ci będą wsadować wyniki i przekazywać je do centralnego komputera zbierającego dane.  
  
- Ponieważ profiler jest obiektem COM, który jest tworzone w procesie, każda profilowana aplikacja będzie miała własną kopię profilera. W związku z tym wystąpienie pojedynczego profilera nie musi obsługiwać danych z wielu aplikacji. Jednak trzeba będzie dodać logikę do kodu rejestrowania profilera, aby zapobiec zastąpieniu pliku dziennika z innych profilowanych aplikacji.  
  
## <a name="initializing-the-profiler"></a>Inicjowanie profilera  
 Gdy oba kontrole zmiennej środowiskowej przechodzą, CLR tworzy wystąpienie profilera w sposób podobny do funkcji COM. `CoCreateInstance` Profiler nie jest ładowany `CoCreateInstance`za pośrednictwem bezpośredniego wywołania . W związku z `CoInitialize`tym unika się wywołania , który wymaga ustawienia modelu wątkowego. Następnie clr wywołuje [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) metody w profilera. Podpis tej metody jest następujący.  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profiler musi `pICorProfilerInfoUnk` kwerendy dla [ICorProfilerInfo](icorprofilerinfo-interface.md) lub [ICorProfilerInfo2](icorprofilerinfo2-interface.md) wskaźnik interfejsu i zapisać go, dzięki czemu można zażądać więcej informacji później podczas profilowania.  
  
## <a name="setting-event-notifications"></a>Ustawianie powiadomień o zdarzeniach  
 Profiler następnie wywołuje [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) metody, aby określić, które kategorie powiadomień jest zainteresowany. Na przykład jeśli profiler jest zainteresowany tylko funkcji enter i pozostawić powiadomienia i powiadomienia wyrzucania elementów bezużytecznych, określa następujące.  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Ustawiając maskę powiadomień w ten sposób, profiler może ograniczyć otrzymywane powiadomienia. Takie podejście pomaga użytkownikowi tworzyć profiler proste lub specjalnego przeznaczenia. Zmniejsza również czas procesora CPU, który zostanie zmarnowany wysyłanie powiadomień, które profiler będzie po prostu ignorować.  
  
 Niektóre zdarzenia profilera są niezmienne. Oznacza to, że jak tylko te `ICorProfilerCallback::Initialize` zdarzenia są ustawione w wywołaniu zwrotnym, nie można ich wyłączyć i nie można włączyć nowych zdarzeń. Próby zmiany zdarzenia niezmienne spowoduje `ICorProfilerInfo::SetEventMask` zwrócenie nie powiodło się HRESULT.  
  
<a name="windows_service"></a>
## <a name="profiling-a-windows-service"></a>Profilowanie usługi systemu Windows  
 Profilowanie usługi systemu Windows jest jak profilowanie aplikacji środowiska wykonawczego języka wspólnego. Obie operacje profilowania są włączone za pomocą zmiennych środowiskowych. Ponieważ usługa systemu Windows jest uruchomiona po uruchomieniu systemu operacyjnego, zmienne środowiskowe omówione wcześniej w tym temacie muszą być już obecne i ustawione na wymagane wartości przed uruchomieniem systemu. Ponadto biblioteka DLL profilowania musi być już zarejestrowana w systemie.  
  
 Po ustawieniu COR_ENABLE_PROFILING i COR_PROFILER zmiennych środowiskowych i zarejestrowaniu biblioteki DLL profilera należy ponownie uruchomić komputer docelowy, aby usługa systemu Windows mogła wykryć te zmiany.  
  
 Należy pamiętać, że te zmiany umożliwi profilowania na podstawie całego systemu. Aby zapobiec profilowaniu każdej zarządzanej aplikacji, która następnie uruchamia się, należy usunąć zmienne środowiska systemowego po ponownym uruchomieniu komputera docelowego.  
  
 Ta technika prowadzi również do każdego procesu CLR coraz profilowane. Profiler należy dodać logikę do jego [ICorProfilerCallback::Initialize wywołania](icorprofilercallback-initialize-method.md) zwrotnego, aby wykryć, czy bieżący proces jest przedmiotem zainteresowania. Jeśli nie jest, profiler może zakończyć się niepowodzeniem wywołania zwrotnego bez wykonywania inicjowania.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd profilowania](profiling-overview.md)
