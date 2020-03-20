---
title: Debugowanie — Interfejsy
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179164"
---
# <a name="debugging-interfaces"></a>Debugowanie — Interfejsy
W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\
 Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.  
  
 [Interfejs ICLRDataEnemoryMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)\
 Zawiera metodę wywołania `EnumMemoryRegions` zwrotnego do raportu do debugera, wynik próby wyliczenia określonego regionu pamięci.  
  
 [Interfejs ICLRDataTarget](iclrdatatarget-interface.md)\
 Zapewnia metody interakcji z obiektem docelowym procesu CLR.  
  
 [Interfejs ICLRDataTarget2](iclrdatatarget2-interface.md)\
 Podklasa, `ICLRDataTarget` która jest używana przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.  
  
 [Interfejs ICLRDataTarget3](iclrdatatarget3-interface.md)\
 Podklasa [ICLRDataTarget2,](iclrdatatarget2-interface.md) która zapewnia dostęp do informacji o wyjątkach.  
  
 [Interfejs ICLRDebugging](iclrdebugging-interface.md)\
 Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.  
  
 [Interfejs ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)\
 Zawiera [Metodę ProvideLibrary,](iclrdebugginglibraryprovider-providelibrary-method.md) która pobiera interfejs wywołania zwrotnego dostawcy biblioteki, który umożliwia zlokalizowanie i załadowanie bibliotek debugowania specyficzne dla środowiska wykonawczego języka wspólnego języka.  
  
 [Interfejs ICLRMetadataLocator](iclrmetadatalocator-interface.md)\
 Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.  
  
 [Interfejs ICorDebug](icordebug-interface.md)\
 Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.  
  
 [Interfejs ICorDebugAppDomain](icordebugappdomain-interface.md)\
 Dostarcza metody do debugowania domen aplikacji.  
  
 [Interfejs ICorDebugAppDomain2](icordebugappdomain2-interface.md)\
 Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef. Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` interfejsu.  
  
 [Interfejs ICorDebugAppDomain3](icordebugappdomain3-interface.md)\
 Udostępnia metody do pracy z typami środowiska wykonawczego systemu Windows w domenie aplikacji. Ten interfejs jest `ICorDebugAppDomain` rozszerzeniem `ICorDebugAppDomain2` i interfejsów.  
  
 [Interfejs ICorDebugAppDomain4](icordebugappdomain4-interface.md)\
 Logicznie rozszerza interfejs [ICorDebugAppDomain,](icordebugappdomain-interface.md) aby uzyskać obiekt zarządzany z otoki wywoływanej przez COM.  
  
 [Interfejs ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)\
 Zawiera metodę, która zwraca `ICorDebugAppDomain` określoną liczbę wartości, począwszy od następnej lokalizacji w wyliczeniu.  
  
 [Interfejs ICorDebugArrayValue](icordebugarrayvalue-interface.md)\
 Podklasa, `ICorDebugHeapValue` która reprezentuje tablicę jednowymiarową lub wielowymiarową.  
  
 [Interfejs ICorDebugAssembly](icordebugassembly-interface.md)\
 Reprezentuje zestaw.  
  
 [Interfejs ICorDebugAssembly2](icordebugassembly2-interface.md)\
 Reprezentuje zestaw. Ten interfejs jest rozszerzeniem `ICorDebugAssembly` interfejsu.  
  
 [Interfejs ICorDebugAssembly3](icordebugassembly3-interface.md)\
 Logicznie rozszerza interfejs [ICorDebugAssembly,](icordebugassembly-interface.md) aby zapewnić obsługę zestawów kontenerów i ich zestawów zawartych. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugAssembly` tablice.  
  
 [Interfejs ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)\
 Zawiera wyliczenie listy [CorDebugBlockingObject](cordebugblockingobject-structure.md) struktur.  
  
 [Interfejs ICorDebugBoxValue](icordebugboxvalue-interface.md)\
 Podklasa, `ICorDebugHeapValue` która reprezentuje obiekt klasy wartości w pudełku.  
  
 [Interfejs ICorDebugBreakpoint](icordebugbreakpoint-interface.md)\
 Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.  
  
 [Interfejs ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugBreakpoint` tablice.  
  
 [Interfejs ICorDebugChain](icordebugchain-interface.md)\
 Reprezentuje segment stosu wywołań fizycznych lub logicznych.  
  
 [Interfejs ICorDebugChainEnum](icordebugchainenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugChain` tablice.  
  
 [Interfejs ICorDebugClass](icordebugclass-interface.md)\
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest `ICorDebugClass` ogólny, reprezentuje nieustannego typu ogólnego.  
  
 [Interfejs ICorDebugClass2](icordebugclass2-interface.md)\
 Reprezentuje klasę rodzajową lub klasę z <xref:System.Type>parametrem metody typu . Ten interfejs `ICorDebugClass`rozszerza .  
  
 [Interfejs ICorDebugCode](icordebugcode-interface1.md)\
 Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.  
  
 [Interfejs ICorDebugCode2](icordebugcode2-interface.md)\
 Zawiera metody, które rozszerzają możliwości . `ICorDebugCode`  
  
 [Interfejs ICorDebugCode3](icordebugcode3-interface.md)\
 Zawiera metodę, która rozszerza [ICorDebugCode](icordebugcode-interface1.md) i [ICorDebugCode2,](icordebugcode2-interface.md) aby zapewnić informacje o wartości zarządzanej zwracanej.  
  
 [Interfejs ICorDebugCode4](icordebugcode4-interface.md)\
 Udostępnia metodę, która umożliwia debugerowi wyliczyć zmienne lokalne i argumenty w funkcji.  
  
 [Interfejs ICorDebugCodeEnum](icordebugcodeenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugCode` tablice.  
  
 [Interfejs ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)\
 Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.  
  
 [Interfejs ICorDebugContext](icordebugcontext-interface.md)\
 Reprezentuje obiekt kontekstu. Ten Interfejs nie został jeszcze implementowany.  
  
 [Interfejs ICorDebugController](icordebugcontroller-interface.md)\
 Reprezentuje zakres, a <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, w którym można kontrolować kontekst wykonywania kodu.  
  
 [Interfejs ICorDebugDataTarget](icordebugdatatarget-interface.md)\
 Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.  
  
 [Interfejs ICorDebugDataTarget2](icordebugdatatarget2-interface.md)\
 Logicznie rozszerza interfejs [ICorDebugDataTarget.](icordebugdatatarget-interface.md) **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugDataTarget3](icordebugdatatarget3-interface.md)\
 Logicznie rozszerza interfejs [ICorDebugDataTarget,](icordebugdatatarget-interface.md) aby zapewnić informacje o załadowanych modułach. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugDebugEvent](icordebugdebugevent-interface.md)\
 Definiuje interfejs podstawowy, z `ICorDebug` którego pochodzą wszystkie zdarzenia debugowania. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)\
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [Interfejs ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)\
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [Interfejs ICorDebugEnum](icordebugenum-interface1.md)\
 Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.  
  
 [Interfejs ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)\
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [Interfejs ICorDebugEval](icordebugeval-interface.md)\
 Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.  
  
 [Interfejs ICorDebugEval2](icordebugeval2-interface.md)\
 `ICorDebugEval` Rozszerza, aby zapewnić obsługę typów ogólnych.  
  
 [Interfejs ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)\
 Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) do obsługi zdarzeń wyjątków. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)\
 Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.  
  
 [Interfejs ICorDebugExceptionObjectValue](icordebugexceptionobjectvalue-interface.md)\
 Rozszerza interfejs [ICorDebugObjectValue,](icordebugobjectvalue-interface.md) aby zapewnić informacje śledzenia stosu z zarządzanego obiektu wyjątku.  
  
 [Interfejs ICorDebugFrame](icordebugframe-interface.md)\
 Reprezentuje ramkę na bieżącym stosie.  
  
 [Interfejs ICorDebugFrameEnum](icordebugframeenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugFrame` tablice.  
  
 [Interfejs ICorDebugFunction](icordebugfunction-interface1.md)\
 Reprezentuje zarządzaną funkcję lub metodę.  
  
 [Interfejs ICorDebugFunction2](icordebugfunction2-interface.md)\
 Logicznie `ICorDebugFunction` rozszerza, aby zapewnić obsługę debugowania krok po kroku tylko mój kod.  
  
 [Interfejs ICorDebugFunction3](icordebugfunction3-interface.md)\
 Logicznie rozszerza interfejs [ICorDebugFunction,](icordebugfunction-interface1.md) aby zapewnić dostęp do kodu z żądania ReJIT.  
  
 [Interfejs ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)\
 Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w ramach funkcji.  
  
 [Interfejs ICorDebugCReferenceEnum](icordebuggcreferenceenum-interface.md)\
 Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.  
  
 [Interfejs ICorDebugGenericValue](icordebuggenericvalue-interface.md)\
 Podklasa, `ICorDebugValue` która ma zastosowanie do wszystkich wartości. Ten interfejs zapewnia metody Get i Set dla wartości.  
  
 [Interfejs ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)\
 Zawiera wyliczenie obiektu, który mapuje identyfikatory `ICorDebugType` GUID i odpowiadające im obiekty.  
  
 [Interfejs ICorDebugHandleValue](icordebughandlevalue-interface.md)\
 Podklasa, `ICorDebugReferenceValue` która reprezentuje wartość odwołania, do której debuger utworzył dojście do wyrzucania elementów bezużytecznych.  
  
 [Interfejs ICorDebugHeapEnum](icordebugheapenum-interface.md)\
 Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.  
  
 [Interfejs ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)\
 Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.  
  
 [Interfejs ICorDebugHeapValue](icordebugheapvalue-interface.md)\
 Podklasa, `ICorDebugValue` która reprezentuje obiekt, który został zebrany przez moduł zbierający elementy bezużyteczne CLR.  
  
 [Interfejs ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)\
 `ICorDebugHeapValue` Rozszerzenie, które zapewnia obsługę dojść w czasie wykonywania.  
  
 [Interfejs ICorDebugHeapValue3](icordebugheapvalue3-interface.md)\
 Udostępnia właściwości blokady monitora obiektów.  
  
 [Interfejs ICorDebugILCode](icordebugilcode-interface.md)\
 Reprezentuje segment kodu języka pośredniego (IL).  
  
 [Interfejs ICorDebugILCode2](icordebugilcode2-interface.md)\
 Logicznie rozszerza interfejs [ICorDebugILCode,](icordebugilcode-interface.md) aby zapewnić metody, które zwracają token dla sygnatury zmiennej lokalnej funkcji i które mapują przesunięcia języka pośredniego (IL) oprzyrządowania profilera do przesunięć oryginalnej metody IL.  
  
 [Interfejs ICorDebugILFrame](icordebugilframe-interface.md)\
 Reprezentuje ramkę stosu kodu MSIL.  
  
 [Interfejs ICorDebugILFrame2](icordebugilframe2-interface.md)\
 Logiczne rozszerzenie `ICorDebugILFrame`.  
  
 [Interfejs ICorDebugILFrame3](icordebugilframe3-interface.md)\
 Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.  
  
 [Interfejs ICorDebugILFrame4](icordebugilframe4-interface.md)\
 Zawiera metody, które umożliwiają dostęp do zmiennych lokalnych i kodu w ramce stosu kodu języka pośredniego (IL). Parametr określa, czy debuger ma dostęp do zmiennych i kodu dodanego w instrumentacji ReJIT profilera.  
  
 [Interfejs ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)\
 Reprezentuje informacje o symbolu debugowania dla pola wystąpienia. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugInternalFrame](icordebuginternalframe-interface.md)\
 Identyfikuje typy ramek dla debugera.  
  
 [Interfejs ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)\
 Zawiera informacje o ramkach wewnętrznych, w tym adres stosu i położenie w odniesieniu do obiektów [ICorDebugFrame.](icordebugframe-interface.md)  
  
 [Interfejs ICorDebugLoadedModule](icordebugloadedmodule-interface.md)\
 Zawiera informacje o załadowanym module. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)\
 Dostarcza metody do przetwarzania wywołań zwrotnych debugera.  
  
 [Interfejs ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)\
 Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA). `ICorDebugManagedCallback2`jest logicznym `ICorDebugManagedCallback`rozszerzeniem .  
  
 [Interfejs ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)\
 Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.  
  
 [Interfejs ICorDebugMDA](icordebugmda-interface.md)\
 Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).  
  
 [Interfejs ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)\
 Reprezentuje bufor w pamięci. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)\
 Zawiera informacje o scalonym zestawie. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugMetaDataLocator](icordebugmetadatalocator-interface.md)\
 Dostarcza informacje o metadanych do debugera.  
  
 [Interfejs ICorDebugModule](icordebugmodule-interface.md)\
 Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.  
  
 [Interfejs ICorDebugModule2](icordebugmodule2-interface.md)\
 Służy jako logiczne `ICorDebugModule`rozszerzenie do .  
  
 [Interfejs ICorDebugModule3](icordebugmodule3-interface.md)\
 Tworzy czytnik symbolu dla modułu dynamicznego.  
  
 [Interfejs ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)\
 `ICorDebugBreakpoint` Rozszerza, aby zapewnić dostęp do określonych modułów.  
  
 [Interfejs ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)\
 Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) do obsługi zdarzeń na poziomie modułu. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugModuleEnum](icordebugmoduleenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugModule` tablice.  
  
 [Interfejs ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)\
 Rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) do obsługi docelowych danych modyfikowalnych.  
  
 [Interfejs ICorDebugNativeFrame](icordebugnativeframe-interface.md)\
 Specjalistyczna implementacja `ICorDebugFrame` używana dla ram natywnych.  
  
 [Interfejs ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)\
 Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.  
  
 [Interfejs ICorDebugObjectEnum](icordebugobjectenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).  
  
 [Interfejs ICorDebugObectValue](icordebugobjectvalue-interface.md)\
 Podklasa, `ICorDebugValue` która reprezentuje wartość, która zawiera obiekt.  
  
 [Interfejs ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)\
 Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastąpienia.  
  
 [Interfejs ICorDebugProcess](icordebugprocess-interface.md)\
 Reprezentuje proces, który wykonuje kod zarządzany.  
  
 [Interfejs ICorDebugProcess2](icordebugprocess2-interface1.md)\
 Logiczne rozszerzenie `ICorDebugProcess`.  
  
 [Interfejs ICorDebugProcess3](icordebugprocess3-interface.md)\
 Steruje niestandardowymi powiadomieniami debugera.

 [Interfejs ICorDebugProcess4](icordebugprocess4-interface.md)\
 Zapewnia obsługę poza kontrolą wykonywania procesu.
  
 [Interfejs ICorDebugProcess5](icordebugprocess5-interface.md)\
 Rozszerza interfejs [ICorDebugProcess](icordebugprocess-interface.md) do obsługi dostępu do zarządzanego stosu, aby zapewnić informacje o wyrzucaniu elementów bezużytecznych obiektów zarządzanych i określić, czy debuger ładuje obrazy z lokalnej pamięci podręcznej obrazu macierzystego aplikacji.  
  
 [Interfejs ICorDebugProcess6](icordebugprocess6-interface.md)\
 Logicznie rozszerza interfejs [ICorDebugProcess,](icordebugprocess-interface.md) aby włączyć funkcje, takie jak dekodowanie zarządzanych zdarzeń debugowania, które są zakodowane w natywnych zdarzeń debugowania wyjątków i dzielenia modułu wirtualnego. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugProcess7](icordebugprocess7-interface.md)\
 Udostępnia metodę, która konfiguruje debugera do obsługi aktualizacji metadanych w pamięci w procesie docelowym.  
  
 [Interfejs ICorDebugProcess8](icordebugprocess8-interface.md)\
 Logicznie rozszerza interfejs [ICorDebugProcess,](icordebugprocess-interface.md) aby włączyć lub wyłączyć niektóre typy wywołań zwrotnych wyjątków [ICorDebugManagedCallback2.](icordebugmanagedcallback2-interface.md)  
  
 [Interfejs ICorDebugProcessEnum](icordebugprocessenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugProcess` tablice.  
  
 [Interfejs ICorDebugReferenceValue](icordebugreferencevalue-interface.md)\
 Podklasa, `ICorDebugValue` która obsługuje typy odwołań.  
  
 [Interfejs ICorDebugRegisterSet](icordebugregisterset-interface.md)\
 Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.  
  
 [Interfejs ICorDebugRegisterSet2](icordebugregisterset2-interface.md)\
 Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają więcej niż 64 rejestrów.  
  
 [Interfejs ICorDebugRemote](icordebugremote-interface.md)\
 Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.  
  
 [Interfejs ICorDebugRemoteTarget](icordebugremotetarget-interface.md)\
 Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.  
  
 [Interfejs ICorDebugRuntimeUnwindableFrame](icordebugruntimeunwindableframe-interface.md)\
 Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.  
  
 [Interfejs ICorDebugStackWalk](icordebugstackwalk-interface.md)\
 Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.  
  
 [Interfejs ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)\
 Reprezentuje informacje o symbolu debugowania dla pola statycznego. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugStepper](icordebugstepper-interface.md)\
 Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
 [Interfejs ICorDebugStepper2](icordebugstepper2-interface1.md)\
 Zapewnia obsługę debugowania Tylko mój kod (JMC).  
  
 [Interfejs ICorDebugStepperEnum](icordebugstepperenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugStepper` tablice.  
  
 [Interfejs ICorDebugStringValue](icordebugstringvalue-interface.md)\
 Podklasa, `ICorDebugHeapValue` która ma zastosowanie do wartości ciągu.  
  
 [Interfejs ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)\
 Zawiera metody, które mogą służyć do pobierania informacji o symbolu debugowania. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)\
 Logicznie rozszerza interfejs [ICorDebugSymbolProvider,](icordebugsymbolprovider-interface.md) aby pobrać dodatkowe informacje o symbolu debugowania. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugThread](icordebugthread-interface.md)\
 Reprezentuje wątek w procesie. Okres istnienia `ICorDebugThread` wystąpienia jest taki sam jak okres istnienia wątku, który reprezentuje.  
  
 [Interfejs ICorDebugThread2](icordebugthread2-interface.md)\
 Służy jako logiczne `ICorDebugThread`rozszerzenie do .  
  
 [Interfejs ICorDebugThread3](icordebugthread3-interface.md)\
 Zawiera punkt wejścia do [ICorDebugStackWalk](icordebugstackwalk-interface.md) i odpowiednich interfejsów.  
  
 [Interfejs ICorDebugThread4](icordebugthread4-interface.md)\
 Dostarcza informacje o blokowaniu wątku.  
  
 [Interfejs ICorDebugThreadEnum](icordebugthreadenum-interface1.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugThread` tablice.  
  
 [Interfejs ICorDebugType](icordebugtype-interface.md)\
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest `ICorDebugType` ogólny, reprezentuje smowany typ ogólny.  
  
 [Interfejs ICorDebugType2](icordebugtype2-interface.md)\
 Rozszerza interfejs [ICorDebugType,](icordebugtype-interface.md) aby pobrać identyfikator typu typu podstawowego lub typu złożonego (zdefiniowanego przez użytkownika).  
  
 [Interfejs ICorDebugTypeEnum](icordebugtypeenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugType` tablice.  
  
 [Interfejs ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)\
 Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.  
  
 [Icordebugvalue](icordebugvalue-interface.md)\
 Reprezentuje wartość odczytu lub zapisu w procesie debugowania.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 `ICorDebugValue` Rozszerza, aby zapewnić `ICorDebugType`wsparcie dla .  
  
 [Interfejs ICorDebugValue3](icordebugvalue3-interface.md)\
 Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic, które są większe niż 2 GB.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 `ICorDebugBreakpoint` Rozszerza, aby zapewnić dostęp do określonych wartości.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 Implementuje `ICorDebugEnum` metody i wylicza `ICorDebugValue` tablice.  
  
 [Interfejs ICorDebugVariableHome](icordebugvariablehome-interface.md)\
 Reprezentuje zmienną lokalną lub argument funkcji.  
  
 [Interfejs ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)\
 Zawiera wyliczenia do zmiennych lokalnych i argumentów w funkcji.  
  
 [Interfejs ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)\
 Pobiera informacje o symbolu debugowania dla zmiennej. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)\
 Zawiera metody, które pomogą w odwijaniu stosu. **Dostępne tylko w programie .NET Native.**  
  
 [Interfejs ICorPublish](icorpublish-interface.md)\
 Służy jako ogólny interfejs dla procesów publikowania.  
  
 [Interfejs ICorPublishAppDomain](icorpublishappdomain-interface.md)\
 Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.  
  
 [Interfejs ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)\
 Zawiera metody, które przechodzą `ICorPublishAppDomain` przez kolekcję obiektów, które obecnie istnieją w ramach procesu.  
  
 [Interfejs ICorPublishEnum](icorpublishenum-interface.md)\
 Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.  
  
 [Interfejs ICorPublishProcess](icorpublishprocess-interface.md)\
 Dostarcza metody, które mają dostęp do informacji dotyczących procesu.  
  
 [Interfejs ICorPublishProcessEnum](icorpublishprocessenum-interface.md)\
 Zawiera metody, które przechodzą `ICorPublishProcess` przez kolekcję obiektów.  

 [Interfejs ISOSDacInterface](isosdacinterface-interface.md)\
 Udostępnia metody pomocnicze dostępu `SOS`do danych z programu .

 [Interfejs ixclrdataMethodDefinition](ixclrdatamethoddefinition-interface.md)\
 Zawiera metody wykonywania zapytań o definicję metody.

 [Interfejs IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)\
 Zawiera metody wykonywania zapytań o wystąpienie metody.

 [Interfejs IXCLRDataModule](ixclrdatamodule-interface.md)\
 Zawiera metody wykonywania zapytań o załadowany moduł.

 [Interfejs IXCLRDataProcess](ixclrdataprocess-interface.md)\
 Zawiera metody wykonywania zapytań o proces.
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Coclasses debugowania](debugging-coclasses.md)\
 [Debugowanie globalnych funkcji statycznych](debugging-global-static-functions.md)\
 [Wyliczenia debugowania](debugging-enumerations.md)\
 [Struktury debugowania](debugging-structures.md)\
