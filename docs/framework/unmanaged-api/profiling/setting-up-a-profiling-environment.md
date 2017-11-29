---
title: "Konfigurowanie środowiska profilowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ff2c57be82166ecf5eb8a012491044eb2cb79d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="setting-up-a-profiling-environment"></a>Konfigurowanie środowiska profilowania
> [!NOTE]
>  Wprowadzono znaczne zmiany do profilowania w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
 Podczas uruchamiania procesu zarządzanego (aplikacji lub usługi), ładuje środowisko uruchomieniowe języka wspólnego (CLR). Po zainicjowaniu środowiska CLR, wynikiem następujących dwóch zmiennych środowiskowych zdecydować, czy proces ma nawiązać profilera:  
  
-   COR_ENABLE_PROFILING: CLR łączy się z profilera tylko wtedy, gdy ta zmienna środowiskowa istnieje i jest ustawiona na 1.  
  
-   COR_PROFILER: Jeśli wyboru COR_ENABLE_PROFILING zakończy się pomyślnie, CLR łączy się z profilera, który ma ten identyfikator CLSID lub ProgID, które muszą być przechowywane wcześniej w rejestrze. COR_PROFILER — zmienna środowiskowa zdefiniowano jako ciąg, jak pokazano w poniższych dwóch przykładach.  
  
    ```  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Profilowanie aplikacji CLR, należy ustawić zmiennych środowiskowych COR_ENABLE_PROFILING i COR_PROFILER przed uruchomieniem aplikacji. Należy również upewnić się, że biblioteki DLL profilera jest zarejestrowany.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], profilery nie musi być zarejestrowana.  
  
> [!NOTE]
>  Aby użyć środowiska .NET Framework w wersji 2.0, 3.0 i 3.5 profilowania w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] i nowszych wersjach, należy ustawić zmiennej środowiskowej COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Zakres zmiennej środowiskowej  
 Ustawienia zmiennych środowiskowych COR_ENABLE_PROFILING i COR_PROFILER określi ich obowiązywania. Te zmienne można ustawić w jednym z następujących sposobów:  
  
-   Jeśli ustawienie zmiennych [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) wywołanie, będą stosować tylko do aplikacji, które są uruchomione w czasie. (Będzie również stosują do innych aplikacji uruchomiona przez tę aplikację, które dziedziczą środowiska.)  
  
-   Jeśli ustawisz zmienne w oknie wiersza polecenia, będzie dotyczyć wszystkich aplikacji, które są uruchamiane z tego okna.  
  
-   Jeśli ustawisz zmienne na poziomie użytkownika będzie dotyczyć wszystkich aplikacji, które zaczynają się Eksploratora plików. Okno wiersza polecenia otwierania po ustawieniu zmienne środowiskowe ustawienia zostaną, a więc będzie dowolnej aplikacji, która zostanie uruchomione z tego okna. Aby ustawić zmiennych środowiskowych na poziomie użytkownika, kliknij prawym przyciskiem myszy **Mój komputer**, kliknij przycisk **właściwości**, kliknij przycisk **zaawansowane** , kliknij pozycję **środowiska Zmienne**i Dodaj zmienne, które mają **zmienne użytkownika** listy.  
  
-   Jeśli ustawisz zmienne na poziomie komputera będzie dotyczyć wszystkich aplikacji, które są uruchamiane na tym komputerze. Okno wiersza polecenia, które można otworzyć na tym komputerze tych ustawień środowiska, a więc będzie dowolnej aplikacji, która zostanie uruchomione z tego okna. Oznacza to, że każdy proces zarządzane na tym komputerze rozpoczyna się od profilera. Aby ustawić zmiennych środowiskowych na poziomie komputera, kliknij prawym przyciskiem myszy **Mój komputer**, kliknij przycisk **właściwości**, kliknij przycisk **zaawansowane** , kliknij pozycję **środowiska Zmienne**, dodać zmienne, które mają **zmienne systemowe** listy, a następnie ponownie uruchom komputer. Po ponownym uruchomieniu, zmienne będą dostępne całego systemu.  
  
 Usługa systemu Windows są profilowania, należy ponownie uruchomić komputer po Ustaw zmienne środowiskowe i rejestrowanie biblioteki DLL profilera. Aby uzyskać więcej informacji na temat tych zagadnień, zobacz sekcję [profilowania usługi systemu Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Dodatkowe uwagi  
  
-   Implementuje klasy profilera [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) i [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfejsów. W programie .NET Framework w wersji 2.0, musi implementować profiler `ICorProfilerCallback2`. Jeśli nie, `ICorProfilerCallback2` nie zostanie załadowany.  
  
-   Tylko jeden profiler może profilu procesu w tym samym czasie w danym środowisku. Możesz zarejestrować dwóch różnych profilowania w różnych środowiskach, ale musi każdego profilu osobne procesy. Profiler musi być implementowana jako serwer COM wewnątrzprocesowe biblioteki DLL, która jest mapowana do tej samej przestrzeni adresowej jako proces jest poddawany profilowaniu. Oznacza to, że profiler jest uruchamiana w procesie. .NET Framework nie obsługuje żadnego innego typu serwer COM. Na przykład jeśli chce profiler do monitorowania aplikacji z komputera zdalnego, musi on implementować agentów zbierających na każdym komputerze. Tych agentów zostanie partii wyników i przekazywać je do komputera kolekcji danych centralnej.  
  
-   Ponieważ profiler jest obiekt COM, który jest w trakcie wystąpień, każdy profilowana aplikacja ma własną kopię profilera. W związku z tym wystąpieniem pojedynczego profilera nie ma obsługiwać danych z wielu aplikacji. Jednak należy dodać zastępuje logiki do kodu rejestrowania profilera, aby zapobiec pliku dziennika z innych aplikacji PROFILOWANEGO.  
  
## <a name="initializing-the-profiler"></a>Podczas inicjowania profilera  
 Gdy zarówno środowiska zmiennej testów, CLR tworzy wystąpienie profilera w sposób podobny do modelu COM `CoCreateInstance` funkcji. Profiler nie został załadowany poprzez bezpośrednie wywołanie `CoCreateInstance`. W związku z tym wywołaniu `CoInitialize`, który wymaga ustawienia modelu wątkowości jest unikać. Następnie wywołuje CLR [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) metoda profilera. Podpis tej metody ma następującą składnię.  
  
```  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Zapytanie musi profilera `pICorProfilerInfoUnk` dla [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) lub [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interfejsu wskaźnik i zapisz go, dzięki czemu można zażądać więcej informacji później podczas profilowania.  
  
## <a name="setting-event-notifications"></a>Ustawienie powiadomień o zdarzeniach  
 Następnie wywołuje profilera [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodę, aby określić kategorie, które powiadomienia o jego jest zainteresowana. Na przykład, jeśli profiler jest tylko funkcja wprowadź i pozostaw powiadomień i powiadomienia dotyczące odzyskiwania pamięci, określa następujące.  
  
```  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Przez ustawienie maski powiadomienia w ten sposób, profilera można ograniczyć które odbiera powiadomienia. Takie podejście ułatwia użytkownikom tworzenie prostego lub specjalnych profilera. Zmniejsza czas procesora CPU, który będzie występować wysyłanie powiadomień, które profilera czy po prostu zignoruj.  
  
 Określone zdarzenia profilera są niezmienne. Oznacza to, że gdy tylko te zdarzenia są ustawiane w `ICorProfilerCallback::Initialize` wywołania zwrotnego, nie można jej wyłączyć i nie może być włączona nowych zdarzeń. Próby zmiany zdarzenie niezmienne spowoduje `ICorProfilerInfo::SetEventMask` zwracanie HRESULT nie powiodło się.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Profilowanie usługi systemu Windows  
 Profilowanie usługi systemu Windows jest podobne do profilowania typowych aplikacji środowiska wykonawczego języka. Obie profilowania operacje są włączone w zmiennych środowiskowych. Ponieważ usługa systemu Windows jest uruchomiony, gdy zostanie uruchomiony system operacyjny, zmienne środowiskowe omówionych wcześniej w tym temacie musi już być istnieje i ustaw wartości wymaganych przed uruchomieniem systemu. Ponadto DLL profilowania musi już być zarejestrowany w systemie.  
  
 Po ustawieniu zmiennych środowiskowych COR_ENABLE_PROFILING i COR_PROFILER i zarejestrować biblioteki DLL profilera, dzięki czemu usługa systemu Windows wykrywa te zmiany należy ponownie uruchomić komputer docelowy.  
  
 Należy pamiętać, że te zmiany spowoduje włączenie profilowania na poziomie systemu. Aby zapobiec co zarządzanych aplikację, która następnie działa z profilowanego, należy usunąć zmiennych środowiskowych systemu po ponownym uruchomieniu komputera docelowego.  
  
 Ta technika również prowadzi do każdego procesu CLR pobierania profilowaniu. Profiler należy dodać logikę do swojej [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołanie zwrotne, aby wykryć, czy bieżący proces jest przydatne. Jeśli nie, profiler może zakończyć się niepowodzeniem wywołania zwrotnego bez wykonywania inicjowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
