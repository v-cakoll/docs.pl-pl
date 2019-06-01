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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dfad184e30ec94c8add265db2ef8131d0d34396f
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457230"
---
# <a name="setting-up-a-profiling-environment"></a>Konfigurowanie środowiska profilowania
> [!NOTE]
>  Były istotne zmiany do profilowania w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
 Po rozpoczęciu procesu zarządzanego (aplikacji lub usługi), ładuje środowisko uruchomieniowe języka wspólnego (CLR). Po zainicjowaniu środowiska CLR, ocenia ono następujące dwie zmienne środowiskowe do określania, czy proces należy się połączyć program profilujący:  
  
- COR_ENABLE_PROFILING: Środowisko CLR łączy do profilera tylko wtedy, gdy ta zmienna środowiskowa istnieje i jest ustawiona na 1.  
  
- COR_PROFILER: Jeśli COR_ENABLE_PROFILING sprawdzać przebiegów, CLR łączy się z programem profilującym, które ma identyfikator CLSID lub ProgID, które muszą być uprzednio przechowywane w rejestrze. Zmienna środowiskowa COR_PROFILER jest zdefiniowana jako ciąg znaków, jak pokazano w poniższych dwóch przykładach.  
  
    ```  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Aby profilować aplikację CLR, należy ustawić zmienne środowiskowe COR_ENABLE_PROFILING i COR_PROFILER przed uruchomieniem aplikacji. Również należy się upewnić, że profiler DLL jest zarejestrowany.  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 4, profilowania nie trzeba być zarejestrowane.  
  
> [!NOTE]
>  Aby użyć .NET Framework w wersji 2.0, 3.0 i 3.5 profilowania w .NET Framework 4 i nowsze wersje, należy ustawić zmiennej środowiskowej COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Zakres zmiennej środowiskowej.  
 Jak ustawić zmienne środowiskowe COR_ENABLE_PROFILING i COR_PROFILER określa zakres wpływu. Można ustawić te zmienne na jeden z następujących sposobów:  
  
- Jeśli ustawisz zmienne w [icordebug::CreateProcess —](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) wywołanie, będą one dotyczyć tylko aplikacji, które są uruchomione w czasie. (Będą one również dotyczyć innych aplikacji, uruchomione przez tę aplikację, dziedziczy środowisko.)  
  
- Jeśli ustawisz zmienne w oknie wiersza polecenia, będą one dotyczyć wszystkich aplikacji, które są uruchamiane z tego okna.  
  
- Jeśli ustawisz zmienne na poziomie użytkownika, będą one dotyczyć wszystkich aplikacji, które są uruchamiane przy użyciu Eksploratora plików. Okno wiersza polecenia otwarte po ustawieniu zmiennych będzie miało te właściwości środowiska i dlatego będzie każda aplikacja uruchamiana z tego okna. Aby ustawić zmienne środowiskowe na poziomie użytkownika, kliknij prawym przyciskiem myszy **Mój komputer**, kliknij przycisk **właściwości**, kliknij przycisk **zaawansowane** kliknij pozycję **środowiska Zmienne**i Dodaj zmienne do **zmienne użytkownika** listy.  
  
- Jeśli ustawisz zmienne na poziomie komputera, będą one dotyczyć wszystkich aplikacji, które są uruchomione na tym komputerze. Okno wiersza polecenia, które można otworzyć na tym komputerze będzie miało te właściwości środowiska i będzie więc każda aplikacja uruchamiana z tego okna. Oznacza to, że każdy proces zarządzany na tym komputerze rozpoczyna się od swojego programu profilującego. Aby ustawić zmienne środowiskowe na poziomie komputera, kliknij prawym przyciskiem myszy **Mój komputer**, kliknij przycisk **właściwości**, kliknij przycisk **zaawansowane** kliknij pozycję **środowiska Zmienne**, Dodaj zmienne do **zmiennych systemowych** listy, a następnie ponownie uruchom komputer. Po ponownym uruchomieniu komputera, zmienne będą dostępne systemowo.  
  
 Czy profilowanie usługi Windows, należy ponownie uruchomić komputer po ustawieniu zmiennych środowiskowych i zarejestrowaniu programu profilującego DLL. Aby uzyskać więcej informacji dotyczących tych rozważań, zobacz sekcję [profilowanie usługi Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Dodatkowe zagadnienia  
  
- Implementuje klasy programu profilującego [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfejsów. W programie .NET Framework 2.0, program profilujący musi zaimplementować `ICorProfilerCallback2`. Jeśli nie, `ICorProfilerCallback2` nie zostanie załadowany.  
  
- Tylko jeden profiler można profilować proces w tym samym czasie w danym środowisku. Można zarejestrować dwa różne profilowania w różnych środowiskach, ale każdy musi profilować oddzielnych procesach. Program profilujący musi zostać wdrożony jako serwera COM DLL, która jest mapowana do tej samej przestrzeni adresowej jako proces, która jest profilowana w procesie. Oznacza to, że profiler jest uruchamiany w procesie. .NET Framework nie obsługuje żadnego rodzaju serwera COM. Na przykład jeśli program profilujący chce monitorować aplikacje z komputera zdalnego, jego musi implementować agentów kolektora na każdym komputerze. Agenci będą grupowały wyniki i przekazywały je do centralnego komputera zbierania danych.  
  
- Ponieważ program profilujący jest obiektem COM, który jest tworzony w procesie, każda profilowana aplikacja posiada własną kopię programu profilującego. Dlatego wystąpienie pojedynczego profilera nie ma obsługi danych z wielu aplikacji. Jednak trzeba będzie dodać logikę do programu profilującego rejestrowania kodu, aby zapobiec pliku dziennika zastępuje z innych aplikacji profilowanych.  
  
## <a name="initializing-the-profiler"></a>Inicjowanie Profiler  
 Gdy oba zmiennej środowiskowej zostały wykryte, CLR tworzy instancję programu profilującego w sposób podobny do COM `CoCreateInstance` funkcji. Program profilujący nie jest załadowany poprzez bezpośrednie wywołanie `CoCreateInstance`. W związku z tym, wywołanie `CoInitialize`, które wymaga utworzenia modelu wątku, jest unikane. Środowisko CLR następnie wywołuje [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) metodę w programie profiler. Podpis tej metody jest następujący.  
  
```  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Program profilujący musi wykonać zapytanie `pICorProfilerInfoUnk` dla [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) lub [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interfejsu wskaźnika i zapisać go tak, aby go zażądać więcej informacji później podczas profilowania.  
  
## <a name="setting-event-notifications"></a>Ustawianie powiadomień o zdarzeniach  
 Następnie program profilujący wywołuje [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby określić, którymi kategoriami powiadomień jest zainteresowany. Na przykład jeśli program profilujący zajmuje się tylko wprowadzeniem funkcji i pozostawia powiadomienia i powiadomienia dotyczące odzyskiwania pamięci, określa poniższe.  
  
```  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Ustawiając maskę powiadomień w ten sposób, program profilujący może ograniczyć powiadomienia, które otrzyma. To podejście pozwala użytkownikowi na tworzenie prostego lub specjalnego narzędzia profiler. Zmniejsza to także czas CPU, który zostałby zmarnowany na wysyłanie powiadomień, które program profilujący po prostu zignoruje.  
  
 Niektóre zdarzenia programu profilującego są niezmienne. Oznacza to, że jak tylko te zdarzenia zostaną ustawione `ICorProfilerCallback::Initialize` wywołanie zwrotne, nie można jej wyłączyć i nowe zdarzenia nie może być włączona. Próby zmiany niezmiennego zdarzenia będą skutkować `ICorProfilerInfo::SetEventMask` zwracanie HRESULT nie powiodło się.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Profilowanie usługi Windows  
 Profilowanie usługi Windows jest podobne do profilowania typowych aplikacji środowiska wykonawczego języka. Obie operacje profilowania są włączone za pomocą zmiennych środowiskowych. Ponieważ usługa Windows jest uruchamiana, gdy system operacyjny zostanie uruchomiony, zmienne środowiskowe omówione wcześniej w tym temacie muszą już być obecne i ustawione na wartości wymagane przed uruchomieniem systemu. Ponadto profilowanie DLL musi być już zarejestrowany w systemie.  
  
 Po ustawieniu zmiennych środowiskowych COR_ENABLE_PROFILING i COR_PROFILER i zarejestrowaniu programu profilującego DLL, dzięki czemu usługa Windows mogła wykryć te zmiany należy ponownie uruchomić komputer docelowy.  
  
 Należy pamiętać, że zmiany te umożliwią profilowanie na podstawie całego systemu. Aby zapobiec każda zarządzana aplikacja kolejno poddawanego profilowaniu unika, należy usunąć zmienne środowiskowe systemu po ponownym uruchomieniu komputera docelowego.  
  
 Technika ta prowadzi do każdego procesu CLR profilowany. Program profilujący powinien dodać logikę do jej [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego do wykrywania, czy bieżący proces jest przedmiotem zainteresowania. Jeśli nie jest dostępne, program profilujący może zawieść wywołanie zwrotne bez przeprowadzenia inicjalizacji.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
