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
ms.openlocfilehash: 86720cb1739e3f193cd1d5081577d69bca1cf0f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427054"
---
# <a name="setting-up-a-profiling-environment"></a>Konfigurowanie środowiska profilowania
> [!NOTE]
> W .NET Framework 4 wprowadzono istotne zmiany profilowania.  
  
 Gdy uruchamiany jest proces zarządzany (aplikacja lub usługa), ładuje on środowisko uruchomieniowe języka wspólnego (CLR). Po zainicjowaniu środowiska CLR program oblicza następujące dwie zmienne środowiskowe, aby zdecydować, czy proces powinien łączyć się z profilerem:  
  
- COR_ENABLE_PROFILING: środowisko CLR nawiązuje połączenie z profilerem tylko wtedy, gdy ta zmienna środowiskowa istnieje i ma ustawioną wartość 1.  
  
- COR_PROFILER: Jeśli sprawdzanie COR_ENABLE_PROFILING przebiega, środowisko CLR łączy się z profilerem, który ma ten identyfikator CLSID lub ProgID, który musi być zapisany wcześniej w rejestrze. Zmienna środowiskowa COR_PROFILER jest definiowana jako ciąg, jak pokazano w poniższych dwóch przykładach.  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Aby profilować aplikację CLR, należy ustawić zmienne środowiskowe COR_ENABLE_PROFILING i COR_PROFILER przed uruchomieniem aplikacji. Należy również upewnić się, że plik DLL profilera jest zarejestrowany.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, nie musi być zarejestrowany.  
  
> [!NOTE]
> Aby użyć .NET Framework w wersji 2,0, 3,0 i 3,5 do prekoderów w .NET Framework 4 i nowszych wersjach, należy ustawić zmienną środowiskową COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Zakres zmiennej środowiskowej  
 Sposób ustawiania zmiennych środowiskowych COR_ENABLE_PROFILING i COR_PROFILER określi ich zakres. Można ustawić te zmienne w jeden z następujących sposobów:  
  
- Jeśli ustawisz zmienne w wywołaniu [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) , zostaną one zastosowane tylko do aplikacji, która jest uruchomiona w danym momencie. (Zostaną one również zastosowane do innych aplikacji uruchomionych przez aplikację, która dziedziczy środowisko).  
  
- Jeśli ustawisz zmienne w oknie wiersza polecenia, zostaną one zastosowane do wszystkich aplikacji, które są uruchamiane z tego okna.  
  
- Jeśli ustawisz zmienne na poziomie użytkownika, zostaną one zastosowane do wszystkich aplikacji, które zaczynają się od Eksploratora plików. Okno wiersza polecenia otwarte po ustawieniu zmiennych będzie miało te ustawienia środowiska, a więc każda aplikacja uruchamiana z tego okna. Aby ustawić zmienne środowiskowe na poziomie użytkownika, kliknij prawym przyciskiem myszy pozycję **mój komputer**, kliknij pozycję **Właściwości**, kliknij kartę **Zaawansowane** , kliknij przycisk **zmienne środowiskowe**i Dodaj zmienne do listy **zmiennych użytkownika** .  
  
- Jeśli ustawisz zmienne na poziomie komputera, zostaną one zastosowane do wszystkich aplikacji uruchomionych na tym komputerze. Okno wiersza polecenia otwarte na tym komputerze będzie miało te ustawienia środowiska, a więc każda aplikacja uruchamiana z tego okna. Oznacza to, że każdy proces zarządzany na tym komputerze zacznie od profilera. Aby ustawić zmienne środowiskowe na poziomie komputera, kliknij prawym przyciskiem myszy pozycję **mój komputer**, kliknij pozycję **Właściwości**, kliknij kartę **Zaawansowane** , kliknij przycisk **zmienne środowiskowe**, Dodaj zmienne do listy **zmienne systemowe** , a następnie uruchom ponownie komputer. Po ponownym uruchomieniu zmienne będą dostępne dla całego systemu.  
  
 W przypadku profilowania usługi systemu Windows należy ponownie uruchomić komputer po ustawieniu zmiennych środowiskowych i zarejestrowaniu biblioteki DLL profilera. Aby uzyskać więcej informacji na temat tych zagadnień, zobacz sekcję [profilowanie usługi systemu Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Dodatkowe zagadnienia  
  
- Klasa profilera implementuje interfejsy [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) . W .NET Framework w wersji 2,0, profiler musi implementować `ICorProfilerCallback2`. Jeśli tak nie jest, `ICorProfilerCallback2` nie zostanie załadowany.  
  
- Tylko jeden profiler może jednocześnie profilować proces w danym środowisku. W różnych środowiskach można rejestrować dwa różne, ale muszą one profilować oddzielne procesy. Profiler musi być zaimplementowany jako biblioteka DLL serwera COM w procesie, która jest mapowana na tę samą przestrzeń adresową co proces, który jest profilowany. Oznacza to, że profiler jest uruchamiany w procesie. .NET Framework nie obsługuje żadnego innego typu serwera COM. Na przykład, jeśli profiler chce monitorować aplikacje z komputera zdalnego, musi zaimplementować agentów modułu zbierającego na każdym komputerze. Ci agenci będą przekazywać wyniki wsadowe i komunikować się z centralnym komputerem zbierania danych.  
  
- Ponieważ Profiler jest obiektem COM, który jest tworzony w procesie, każda profilowana aplikacja będzie miała własną kopię profilera. W związku z tym pojedyncze wystąpienie profilera nie musi obsługiwać danych z wielu aplikacji. Należy jednak dodać logikę do kodu rejestrowania profilera, aby zapobiec zastępowaniu pliku dziennika z innych profilowanych aplikacji.  
  
## <a name="initializing-the-profiler"></a>Inicjowanie profilera  
 Gdy obie zmienne środowiskowe sprawdzają przebieg, środowisko CLR tworzy wystąpienie profilera w podobny sposób do funkcji COM `CoCreateInstance`. Profiler nie jest ładowany przez bezpośrednie wywołanie do `CoCreateInstance`. W związku z tym, wywołanie do `CoInitialize`, które wymaga ustawienia modelu wątkowości, jest unikane. Środowisko CLR następnie wywołuje metodę [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) w profilera. Sygnatura tej metody jest następująca.  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profiler musi zbadać `pICorProfilerInfoUnk` dla wskaźnika interfejsu [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) lub [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) i zapisać go, aby można było zażądać dalszych informacji później podczas profilowania.  
  
## <a name="setting-event-notifications"></a>Ustawianie powiadomień o zdarzeniach  
 Profiler wywołuje następnie metodę [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) , aby określić, które kategorie powiadomień interesują. Na przykład, jeśli Profiler jest interesujący tylko funkcja wprowadzanie i pozostawianie powiadomień i powiadomień o wyrzucaniu elementów bezużytecznych, określa następujące kwestie.  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Ustawiając maskę powiadomień w ten sposób, profiler może ograniczyć liczbę otrzymywanych powiadomień. Takie podejście ułatwia użytkownikowi tworzenie prostego lub specjalnego profilera. Skraca to również czas procesora, który mógłby być tracony przez program Profiler.  
  
 Niektóre zdarzenia profilera są niezmienne. Oznacza to, że zaraz po ustawieniu tych zdarzeń w `ICorProfilerCallback::Initialize` wywołaniu zwrotnym nie można ich wyłączyć i nie będzie można włączyć nowych zdarzeń. Próby zmiany niezmiennego zdarzenia spowodują, że `ICorProfilerInfo::SetEventMask` zwracać wynik HRESULT zakończony niepowodzeniem.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Profilowanie usługi systemu Windows  
 Profilowanie usługi systemu Windows przypomina Profilowanie aplikacji środowiska uruchomieniowego języka wspólnego. Obie operacje profilowania są włączane za poorednictwem zmiennych środowiskowych. Ponieważ usługa systemu Windows jest uruchamiana podczas uruchamiania systemu operacyjnego, zmienne środowiskowe omówione wcześniej w tym temacie muszą być już obecne i ustawione na wartości wymagane przed uruchomieniem systemu. Ponadto biblioteka DLL profilowania musi być już zarejestrowana w systemie.  
  
 Po ustawieniu zmiennych środowiskowych COR_ENABLE_PROFILING i COR_PROFILER i zarejestrowaniu biblioteki DLL profilera należy ponownie uruchomić komputer docelowy, aby usługa systemu Windows mogła wykryć te zmiany.  
  
 Należy pamiętać, że te zmiany spowodują profilowanie na podstawie całego systemu. Aby zapobiec przetwarzaniu przez każdą aplikację zarządzaną, która następnie jest uruchamiana, należy usunąć systemowe zmienne środowiskowe po ponownym uruchomieniu komputera docelowego.  
  
 Ta technika prowadzi również do każdego procesu CLR, w którym zawarto pliki. Profiler powinien dodać logikę do jej [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego w celu wykrycia, czy bieżący proces jest interesujący. Jeśli tak nie jest, profiler może zakończyć wywołanie zwrotne bez wykonywania inicjalizacji.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
