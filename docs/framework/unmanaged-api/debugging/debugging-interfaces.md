---
title: Debugowanie — Interfejsy
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 07b39666637628102e9ffafd2c059ba0d4b51b92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097199"
---
# <a name="debugging-interfaces"></a>Debugowanie — Interfejsy
W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRDataEnumMemoryRegions\ interfejsu](iclrdataenummemoryregions-interface.md)
 Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.  
  
 [ICLRDataEnumMemoryRegionsCallback\ interfejsu](iclrdataenummemoryregionscallback-interface.md)
 Zapewnia metodę wywołania zwrotnego dla `EnumMemoryRegions`, aby zgłosić do debugera, wynik próby wyliczenia określonego regionu pamięci.  
  
 [ICLRDataTarget\ interfejsu](iclrdatatarget-interface.md)
 Zapewnia metody interakcji z obiektem docelowym procesu CLR.  
  
 [ICLRDataTarget2\ interfejsu](iclrdatatarget2-interface.md)
 Podklasa `ICLRDataTarget`, która jest używana przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.  
  
 [ICLRDataTarget3\ interfejsu](iclrdatatarget3-interface.md)
 Podklasa elementu [ICLRDataTarget2](iclrdatatarget2-interface.md) , która zapewnia dostęp do informacji o wyjątku.  
  
 [ICLRDebugging\ interfejsu](iclrdebugging-interface.md)
 Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.  
  
 [ICLRDebuggingLibraryProvider\ interfejsu](iclrdebugginglibraryprovider-interface.md)
 Obejmuje metodę [metody ProvideLibrary —](iclrdebugginglibraryprovider-providelibrary-method.md) , która pobiera interfejs wywołania zwrotnego dostawcy biblioteki, który umożliwia zlokalizowanie i załadowanie bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego języka wspólnego na żądanie.  
  
 [ICLRMetadataLocator\ interfejsu](iclrmetadatalocator-interface.md)
 Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.  
  
 [ICorDebug\ interfejsu](icordebug-interface.md)
 Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.  
  
 [ICorDebugAppDomain\ interfejsu](icordebugappdomain-interface.md)
 Dostarcza metody do debugowania domen aplikacji.  
  
 [ICorDebugAppDomain2\ interfejsu](icordebugappdomain2-interface.md)
 Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef. Ten interfejs jest rozszerzeniem interfejsu `ICorDebugAppDomain`.  
  
 [ICorDebugAppDomain3\ interfejsu](icordebugappdomain3-interface.md)
 Zapewnia metody do pracy z typami środowisko wykonawcze systemu Windows w domenie aplikacji. Ten interfejs jest rozszerzeniem interfejsów `ICorDebugAppDomain` i `ICorDebugAppDomain2`.  
  
 [ICorDebugAppDomain4\ interfejsu](icordebugappdomain4-interface.md)
 Logicznie rozszerza interfejs [ICorDebugAppDomain](icordebugappdomain-interface.md) w celu uzyskania obiektu zarządzanego z przywywoływanej otoki com.  
  
 [ICorDebugAppDomainEnum\ interfejsu](icordebugappdomainenum-interface.md)
 Zapewnia metodę, która zwraca określoną liczbę `ICorDebugAppDomain` wartości, rozpoczynając od następnej lokalizacji w wyliczeniu.  
  
 [ICorDebugArrayValue\ interfejsu](icordebugarrayvalue-interface.md)
 Podklasa `ICorDebugHeapValue`, która reprezentuje tablicę jednowymiarową lub wielowymiarową.  
  
 [ICorDebugAssembly\ interfejsu](icordebugassembly-interface.md)
 Reprezentuje zestaw.  
  
 [ICorDebugAssembly2\ interfejsu](icordebugassembly2-interface.md)
 Reprezentuje zestaw. Ten interfejs jest rozszerzeniem interfejsu `ICorDebugAssembly`.  
  
 [ICorDebugAssembly3\ interfejsu](icordebugassembly3-interface.md)
 Logicznie rozszerza interfejs [ICorDebugAssembly](icordebugassembly-interface.md) w celu zapewnienia obsługi zestawów kontenerów i zawartych w nich zestawów. **Dostępne tylko .NET Native.**  
  
 [ICorDebugAssemblyEnum\ interfejsu](icordebugassemblyenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugAssembly` tablice.  
  
 [ICorDebugBlockingObjectEnum\ interfejsu](icordebugblockingobjectenum-interface.md)
 Dostarcza moduł wyliczający listę struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .  
  
 [ICorDebugBoxValue\ interfejsu](icordebugboxvalue-interface.md)
 Podklasa `ICorDebugHeapValue`, która reprezentuje obiekt klasy wartości w ramce.  
  
 [ICorDebugBreakpoint\ interfejsu](icordebugbreakpoint-interface.md)
 Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.  
  
 [ICorDebugBreakpointEnum\ interfejsu](icordebugbreakpointenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugBreakpoint` tablice.  
  
 [ICorDebugChain\ interfejsu](icordebugchain-interface.md)
 Reprezentuje segment stosu wywołań fizycznych lub logicznych.  
  
 [ICorDebugChainEnum\ interfejsu](icordebugchainenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugChain` tablice.  
  
 [ICorDebugClass\ interfejsu](icordebugclass-interface.md)
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.  
  
 [ICorDebugClass2\ interfejsu](icordebugclass2-interface.md)
 Reprezentuje klasę generyczną lub klasę z parametrem metody typu <xref:System.Type>. Ten interfejs rozszerza `ICorDebugClass`.  
  
 [ICorDebugCode\ interfejsu](icordebugcode-interface1.md)
 Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.  
  
 [ICorDebugCode2\ interfejsu](icordebugcode2-interface.md)
 Dostarcza metody, które zwiększają możliwości `ICorDebugCode`.  
  
 [ICorDebugCode3\ interfejsu](icordebugcode3-interface.md)
 Zapewnia metodę, która rozszerza [ICorDebugCode](icordebugcode-interface1.md) i [ICorDebugCode2](icordebugcode2-interface.md) , aby zapewnić informacje o zarządzanej wartości zwracanej.  
  
 [ICorDebugCode4\ interfejsu](icordebugcode4-interface.md)
 Zapewnia metodę, która umożliwia debugerowi Wyliczenie zmiennych lokalnych i argumentów w funkcji.  
  
 [ICorDebugCodeEnum\ interfejsu](icordebugcodeenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugCode` tablice.  
  
 [ICorDebugComObjectValue\ interfejsu](icordebugcomobjectvalue-interface.md)
 Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.  
  
 [Icordebugcontext —\ interfejsu](icordebugcontext-interface.md)
 Reprezentuje obiekt kontekstu. Ten Interfejs nie został jeszcze implementowany.  
  
 [ICorDebugController\ interfejsu](icordebugcontroller-interface.md)
 Reprezentuje zakres, <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, w którym można kontrolować kontekst wykonywania kodu.  
  
 [ICorDebugDataTarget\ interfejsu](icordebugdatatarget-interface.md)
 Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.  
  
 [Metoda icordebugdatatarget2\ interfejsu](icordebugdatatarget2-interface.md)
 Logicznie rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) . **Dostępne tylko .NET Native.**  
  
 [ICorDebugDataTarget3\ interfejsu](icordebugdatatarget3-interface.md)
 Logicznie rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) w celu dostarczenia informacji o załadowanych modułach. **Dostępne tylko .NET Native.**  
  
 [ICorDebugDebugEvent\ interfejsu](icordebugdebugevent-interface.md)
 Definiuje interfejs podstawowy, z którego pochodzą wszystkie zdarzenia debugowania `ICorDebug`. **Dostępne tylko .NET Native.**  
  
 [ICorDebugEditAndContinueErrorInfo\ interfejsu](icordebugeditandcontinueerrorinfo-interface.md)
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEditAndContinueSnapshot\ interfejsu](icordebugeditandcontinuesnapshot-interface.md)
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEnum\ interfejsu](icordebugenum-interface1.md)
 Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.  
  
 [ICorDebugErrorInfoEnum\ interfejsu](icordebugerrorinfoenum-interface.md)
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEval\ interfejsu](icordebugeval-interface.md)
 Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.  
  
 [ICorDebugEval2\ interfejsu](icordebugeval2-interface.md)
 Rozszerza `ICorDebugEval`, aby zapewnić obsługę typów ogólnych.  
  
 [ICorDebugExceptionDebugEvent\ interfejsu](icordebugexceptiondebugevent-interface.md)
 Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) w celu obsługi zdarzeń wyjątków. **Dostępne tylko .NET Native.**  
  
 [ICorDebugExceptionObjectCallStackEnum\ interfejsu](icordebugexceptionobjectcallstackenum-interface.md)
 Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.  
  
 [ICorDebugExceptionObjectValue\ interfejsu](icordebugexceptionobjectvalue-interface.md)
 Rozszerza interfejs [ICorDebugObjectValue](icordebugobjectvalue-interface.md) w celu udostępnienia informacji o śledzeniu stosu z obiektu wyjątku zarządzanego.  
  
 [ICorDebugFrame\ interfejsu](icordebugframe-interface.md)
 Reprezentuje ramkę na bieżącym stosie.  
  
 [ICorDebugFrameEnum\ interfejsu](icordebugframeenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugFrame` tablice.  
  
 [ICorDebugFunction\ interfejsu](icordebugfunction-interface1.md)
 Reprezentuje zarządzaną funkcję lub metodę.  
  
 [ICorDebugFunction2\ interfejsu](icordebugfunction2-interface.md)
 Logicznie rozszerza `ICorDebugFunction`, aby zapewnić obsługę Tylko mój kod debugowania krok po kroku.  
  
 [ICorDebugFunction3\ interfejsu](icordebugfunction3-interface.md)
 Logicznie rozszerza interfejs [ICorDebugFunction](icordebugfunction-interface1.md) w celu zapewnienia dostępu do kodu z żądania ReJIT.  
  
 [ICorDebugFunctionBreakpoint\ interfejsu](icordebugfunctionbreakpoint-interface.md)
 Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w funkcjach.  
  
 [ICorDebugGCReferenceEnum\ interfejsu](icordebuggcreferenceenum-interface.md)
 Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.  
  
 [ICorDebugGenericValue\ interfejsu](icordebuggenericvalue-interface.md)
 Podklasa `ICorDebugValue`, która ma zastosowanie do wszystkich wartości. Ten interfejs zapewnia metody Get i Set dla wartości.  
  
 [ICorDebugGuidToTypeEnum\ interfejsu](icordebugguidtotypeenum-interface.md)
 Dostarcza moduł wyliczający dla obiektu, który mapuje identyfikatory GUID i odpowiadające im obiekty `ICorDebugType`.  
  
 [ICorDebugHandleValue\ interfejsu](icordebughandlevalue-interface.md)
 Podklasa `ICorDebugReferenceValue`, która reprezentuje wartość odniesienia, do której debuger utworzył dojście do wyrzucania elementów bezużytecznych.  
  
 [ICorDebugHeapEnum\ interfejsu](icordebugheapenum-interface.md)
 Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.  
  
 [ICorDebugHeapSegmentEnum\ interfejsu](icordebugheapsegmentenum-interface.md)
 Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.  
  
 [ICorDebugHeapValue\ interfejsu](icordebugheapvalue-interface.md)
 Podklasa `ICorDebugValue`, która reprezentuje obiekt, który został zebrany przez moduł wyrzucania elementów bezużytecznych CLR.  
  
 [ICorDebugHeapValue2\ interfejsu](icordebugheapvalue2-interface1.md)
 Rozszerzenie `ICorDebugHeapValue`, które zapewnia obsługę uchwytów środowiska uruchomieniowego.  
  
 [ICorDebugHeapValue3\ interfejsu](icordebugheapvalue3-interface.md)
 Udostępnia właściwości blokady monitora obiektów.  
  
 [ICorDebugILCode\ interfejsu](icordebugilcode-interface.md)
 Reprezentuje segment kodu języka pośredniego (IL).  
  
 [ICorDebugILCode2\ interfejsu](icordebugilcode2-interface.md)
 Logicznie rozszerza interfejs [ICorDebugILCode](icordebugilcode-interface.md) w celu zapewnienia metod, które zwracają token dla sygnatury zmiennej lokalnej funkcji, i mapuje przesunięcia języka pośredniego (IL) narzędzia profilera do oryginalnej metody do przesunięcia Il.  
  
 [ICorDebugILFrame\ interfejsu](icordebugilframe-interface.md)
 Reprezentuje ramkę stosu kodu MSIL.  
  
 [ICorDebugILFrame2\ interfejsu](icordebugilframe2-interface.md)
 Logiczne rozszerzenie `ICorDebugILFrame`.  
  
 [ICorDebugILFrame3\ interfejsu](icordebugilframe3-interface.md)
 Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.  
  
 [Metoda icordebugilframe4\ interfejsu](icordebugilframe4-interface.md)
 Zapewnia metody umożliwiające dostęp do zmiennych lokalnych i kodu w ramce stosu kodu języka pośredniego (IL). Parametr określa, czy debuger ma dostęp do zmiennych i kodu dodanych w Instrumentacji ReJIT profilera.  
  
 [ICorDebugInstanceFieldSymbol\ interfejsu](icordebuginstancefieldsymbol-interface.md)
 Przedstawia informacje o symbolu debugowania dla pola wystąpienia. **Dostępne tylko .NET Native.**  
  
 [ICorDebugInternalFrame\ interfejsu](icordebuginternalframe-interface.md)
 Identyfikuje typy ramek dla debugera.  
  
 [ICorDebugInternalFrame2\ interfejsu](icordebuginternalframe2-interface.md)
 Zawiera informacje o ramkach wewnętrznych, łącznie z adresem stosu i pozycją w odniesieniu do obiektów [ICorDebugFrame](icordebugframe-interface.md) .  
  
 [ICorDebugLoadedModule\ interfejsu](icordebugloadedmodule-interface.md)
 Zawiera informacje o załadowanym module. **Dostępne tylko .NET Native.**  
  
 [ICorDebugManagedCallback\ interfejsu](icordebugmanagedcallback-interface.md)
 Dostarcza metody do przetwarzania wywołań zwrotnych debugera.  
  
 [ICorDebugManagedCallback2\ interfejsu](icordebugmanagedcallback2-interface.md)
 Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA). `ICorDebugManagedCallback2` jest logicznym rozszerzeniem `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3\ interfejsu](icordebugmanagedcallback3-interface.md)
 Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.  
  
 [ICorDebugMDA\ interfejsu](icordebugmda-interface.md)
 Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).  
  
 [ICorDebugMemoryBuffer\ interfejsu](icordebugmemorybuffer-interface.md)
 Reprezentuje bufor w pamięci. **Dostępne tylko .NET Native.**  
  
 [ICorDebugMergedAssemblyRecord\ interfejsu](icordebugmergedassemblyrecord-interface.md)
 Zawiera informacje o scalonym zestawie. **Dostępne tylko .NET Native.**  
  
 [ICorDebugMetaDataLocator\ interfejsu](icordebugmetadatalocator-interface.md)
 Dostarcza informacje o metadanych do debugera.  
  
 [ICorDebugModule\ interfejsu](icordebugmodule-interface.md)
 Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.  
  
 [ICorDebugModule2\ interfejsu](icordebugmodule2-interface.md)
 Służy jako logiczne rozszerzenie do `ICorDebugModule`.  
  
 [ICorDebugModule3\ interfejsu](icordebugmodule3-interface.md)
 Tworzy czytnik symbolu dla modułu dynamicznego.  
  
 [ICorDebugModuleBreakpoint\ interfejsu](icordebugmodulebreakpoint-interface.md)
 Rozszerza `ICorDebugBreakpoint`, aby zapewnić dostęp do określonych modułów.  
  
 [ICorDebugModuleDebugEvent\ interfejsu](icordebugmoduledebugevent-interface.md)
 Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) w celu obsługi zdarzeń na poziomie modułu. **Dostępne tylko .NET Native.**  
  
 [ICorDebugModuleEnum\ interfejsu](icordebugmoduleenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugModule` tablice.  
  
 [ICorDebugMutableDataTarget\ interfejsu](icordebugmutabledatatarget-interface.md)
 Rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) w celu obsługi modyfikowalnych obiektów docelowych danych.  
  
 [ICorDebugNativeFrame\ interfejsu](icordebugnativeframe-interface.md)
 Wyspecjalizowana implementacja `ICorDebugFrame` używana w przypadku ramek natywnych.  
  
 [ICorDebugNativeFrame2\ interfejsu](icordebugnativeframe2-interface.md)
 Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.  
  
 [ICorDebugObjectEnum\ interfejsu](icordebugobjectenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).  
  
 [ICorDebugObjectValue\ interfejsu](icordebugobjectvalue-interface.md)
 Podklasa `ICorDebugValue`, która reprezentuje wartość, która zawiera obiekt.  
  
 [ICorDebugObjectValue2\ interfejsu](icordebugobjectvalue2-interface.md)
 Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastąpień.  
  
 [ICorDebugProcess\ interfejsu](icordebugprocess-interface.md)
 Reprezentuje proces, który wykonuje kod zarządzany.  
  
 [ICorDebugProcess2\ interfejsu](icordebugprocess2-interface1.md)
 Logiczne rozszerzenie `ICorDebugProcess`.  
  
 [ICorDebugProcess3\ interfejsu](icordebugprocess3-interface.md)
 Steruje niestandardowymi powiadomieniami debugera.

 [ICorDebugProcess4\ interfejsu](icordebugprocess4-interface.md)
 Zapewnia obsługę kontroli wykonywania poza procesem.
  
 [ICorDebugProcess5\ interfejsu](icordebugprocess5-interface.md)
 Rozszerza interfejs [ICorDebugProcess](icordebugprocess-interface.md) w celu obsługi dostępu do zarządzanej sterty, zapewnia informacje o wyrzucaniu elementów bezużytecznych obiektów zarządzanych i określa, czy debuger ładuje obrazy z lokalnej pamięci podręcznej obrazów natywnych aplikacji.  
  
 [Metoda icordebugprocess6\ interfejsu](icordebugprocess6-interface.md)
 Logicznie rozszerza interfejs [ICorDebugProcess](icordebugprocess-interface.md) w celu włączenia takich funkcji, jak dekodowanie zdarzeń debugowania zarządzanego, które są kodowane w natywnych zdarzeniach debugowania wyjątków i dzielenia modułu wirtualnego. **Dostępne tylko .NET Native.**  
  
 [ICorDebugProcess7\ interfejsu](icordebugprocess7-interface.md)
 Zapewnia metodę, która umożliwia skonfigurowanie debugera do obsługi aktualizacji metadanych w pamięci w procesie docelowym.  
  
 [ICorDebugProcess8\ interfejsu](icordebugprocess8-interface.md)
 Logicznie rozszerza interfejs [ICorDebugProcess](icordebugprocess-interface.md) w celu włączenia lub wyłączenia niektórych typów wywołań zwrotnych wyjątków [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
 [ICorDebugProcessEnum\ interfejsu](icordebugprocessenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugProcess` tablice.  
  
 [ICorDebugReferenceValue\ interfejsu](icordebugreferencevalue-interface.md)
 Podklasa `ICorDebugValue`, która obsługuje typy odwołań.  
  
 [ICorDebugRegisterSet\ interfejsu](icordebugregisterset-interface.md)
 Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.  
  
 [ICorDebugRegisterSet2\ interfejsu](icordebugregisterset2-interface.md)
 Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają więcej niż 64 rejestrów.  
  
 [ICorDebugRemote\ interfejsu](icordebugremote-interface.md)
 Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.  
  
 [ICorDebugRemoteTarget\ interfejsu](icordebugremotetarget-interface.md)
 Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.  
  
 [ICorDebugRuntimeUnwindableFrame\ interfejsu](icordebugruntimeunwindableframe-interface.md)
 Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.  
  
 [ICorDebugStackWalk\ interfejsu](icordebugstackwalk-interface.md)
 Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.  
  
 [ICorDebugStaticFieldSymbol\ interfejsu](icordebugstaticfieldsymbol-interface.md)
 Przedstawia informacje o symbolu debugowania dla pola statycznego. **Dostępne tylko .NET Native.**  
  
 [ICorDebugStepper\ interfejsu](icordebugstepper-interface.md)
 Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
 [ICorDebugStepper2\ interfejsu](icordebugstepper2-interface1.md)
 Zapewnia obsługę debugowania Tylko mój kod (JMC).  
  
 [ICorDebugStepperEnum\ interfejsu](icordebugstepperenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugStepper` tablice.  
  
 [ICorDebugStringValue\ interfejsu](icordebugstringvalue-interface.md)
 Podklasa `ICorDebugHeapValue`, która ma zastosowanie do wartości ciągu.  
  
 [ICorDebugSymbolProvider\ interfejsu](icordebugsymbolprovider-interface.md)
 Dostarcza metody, których można użyć do pobrania informacji o symbolach debugowania. **Dostępne tylko .NET Native.**  
  
 [ICorDebugSymbolProvider2\ interfejsu](icordebugsymbolprovider2-interface.md)
 Logicznie rozszerza interfejs [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) w celu pobrania dodatkowych informacji o symbolach debugowania. **Dostępne tylko .NET Native.**  
  
 [ICorDebugThread\ interfejsu](icordebugthread-interface.md)
 Reprezentuje wątek w procesie. Okres istnienia wystąpienia `ICorDebugThread` jest taki sam jak okres istnienia wątku, który reprezentuje.  
  
 [ICorDebugThread2\ interfejsu](icordebugthread2-interface.md)
 Służy jako logiczne rozszerzenie do `ICorDebugThread`.  
  
 [ICorDebugThread3\ interfejsu](icordebugthread3-interface.md)
 Udostępnia punkt wejścia do [ICorDebugStackWalk](icordebugstackwalk-interface.md) i odpowiednich interfejsów.  
  
 [ICorDebugThread4\ interfejsu](icordebugthread4-interface.md)
 Dostarcza informacje o blokowaniu wątku.  
  
 [ICorDebugThreadEnum\ interfejsu](icordebugthreadenum-interface1.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugThread` tablice.  
  
 [ICorDebugType\ interfejsu](icordebugtype-interface.md)
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest ogólny, `ICorDebugType` reprezentuje typ ogólny wystąpienia.  
  
 [ICorDebugType2\ interfejsu](icordebugtype2-interface.md)
 Rozszerza interfejs [ICorDebugType](icordebugtype-interface.md) w celu pobrania identyfikatora typu podstawowego lub złożonego (zdefiniowanego przez użytkownika).  
  
 [ICorDebugTypeEnum\ interfejsu](icordebugtypeenum-interface.md)
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugType` tablice.  
  
 [ICorDebugUnmanagedCallback\ interfejsu](icordebugunmanagedcallback-interface.md)
 Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.  
  
 [ICorDebugValue](icordebugvalue-interface.md)\
 Reprezentuje wartość odczytu lub zapisu w procesie debugowania.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 Rozszerza `ICorDebugValue`, aby zapewnić obsługę `ICorDebugType`.  
  
 [ICorDebugValue3\ interfejsu](icordebugvalue3-interface.md)
 Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic o rozmiarze większym niż 2 GB.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Rozszerza `ICorDebugBreakpoint`, aby zapewnić dostęp do określonych wartości.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 Implementuje metody `ICorDebugEnum` i wylicza `ICorDebugValue` tablice.  
  
 [ICorDebugVariableHome\ interfejsu](icordebugvariablehome-interface.md)
 Reprezentuje zmienną lokalną lub argument funkcji.  
  
 [ICorDebugVariableHomeEnum\ interfejsu](icordebugvariablehomeenum-interface.md)
 Dostarcza moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.  
  
 [ICorDebugVariableSymbol\ interfejsu](icordebugvariablesymbol-interface.md)
 Pobiera informacje o symbolach debugowania dla zmiennej. **Dostępne tylko .NET Native.**  
  
 [ICorDebugVirtualUnwinder\ interfejsu](icordebugvirtualunwinder-interface.md)
 Zapewnia metody pomagające w rozwinięcia stosu. **Dostępne tylko .NET Native.**  
  
 [ICorPublish\ interfejsu](icorpublish-interface.md)
 Służy jako ogólny interfejs dla procesów publikowania.  
  
 [ICorPublishAppDomain\ interfejsu](icorpublishappdomain-interface.md)
 Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.  
  
 [ICorPublishAppDomainEnum\ interfejsu](icorpublishappdomainenum-interface.md)
 Dostarcza metody, które przechodzą przez kolekcję `ICorPublishAppDomain` obiektów, które aktualnie istnieją w ramach procesu.  
  
 [ICorPublishEnum\ interfejsu](icorpublishenum-interface.md)
 Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.  
  
 [ICorPublishProcess\ interfejsu](icorpublishprocess-interface.md)
 Dostarcza metody, które mają dostęp do informacji dotyczących procesu.  
  
 [ICorPublishProcessEnum\ interfejsu](icorpublishprocessenum-interface.md)
 Dostarcza metody, które przechodzą przez kolekcję obiektów `ICorPublishProcess`.  

 [ISOSDacInterface\ interfejsu](isosdacinterface-interface.md)
 Zapewnia metody pomocnika do uzyskiwania dostępu do danych z `SOS`.

 [IXCLRDataMethodDefinition\ interfejsu](ixclrdatamethoddefinition-interface.md)
 Zapewnia metody wykonywania zapytań dotyczących informacji o definicji metody.
 
 [IXCLRDataMethodInstance\ interfejsu](ixclrdatamethodinstance-interface.md)
 Zapewnia metody wykonywania zapytań dotyczących informacji o wystąpieniu metody.
 
 [IXCLRDataModule\ interfejsu](ixclrdatamodule-interface.md)
 Zapewnia metody wykonywania zapytania o informacje o załadowanym module.
 
 [IXCLRDataProcess\ interfejsu](ixclrdataprocess-interface.md)
 Dostarcza metody do wykonywania zapytań dotyczących informacji o procesie.
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](debugging-coclasses.md)\
 [Debugowanie globalnych funkcji statycznych](debugging-global-static-functions.md)\
 \ [wyliczeń debugowania](debugging-enumerations.md)
 [Struktury debugowania](debugging-structures.md)\
