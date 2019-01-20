---
title: Debugowanie — Interfejsy
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b6d00d17615769a5d03d58e0eda5af62ca58368
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415965"
---
# <a name="debugging-interfaces"></a>Debugowanie — Interfejsy
W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRDataEnumMemoryRegions, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.  
  
 [ICLRDataEnumMemoryRegionsCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 Zapewnia metodę wywołania zwrotnego dla `EnumMemoryRegions` do zgłaszania do debugera wyniku próby wyliczenia określonego regionu pamięci.  
  
 [ICLRDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 Zapewnia metody interakcji z obiektem docelowym procesu CLR.  
  
 [ICLRDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 Podklasa klasy `ICLRDataTarget` używany przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.  
  
 [ICLRDataTarget3, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 Podklasa klasy [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , który zapewnia dostęp do informacji o wyjątku.  
  
 [ICLRDebugging, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.  
  
 [ICLRDebuggingLibraryProvider, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 Obejmuje [providelibrary — metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metody, która pobiera interfejs wywołania zwrotnego, która umożliwia języka wspólnego bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego lokalizowanie i ładowanie na żądanie dostawcy biblioteki.  
  
 [ICLRMetadataLocator, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.  
  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.  
  
 [ICorDebugAppDomain, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 Dostarcza metody do debugowania domen aplikacji.  
  
 [ICorDebugAppDomain2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef. Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` interfejsu.  
  
 [ICorDebugAppDomain3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 Dostarcza metody do pracy z [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy w domenie aplikacji. Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` i `ICorDebugAppDomain2` interfejsów.  
  
 [ICorDebugAppDomain4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 Rozszerza logicznie [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interfejsu można pobrać obiektu zarządzanego z wywołalne opakowanie COM.  
  
 [ICorDebugAppDomainEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 Dostarcza metodę, która zwraca określoną liczbę `ICorDebugAppDomain` wartości, zaczynając od następnej pozycji w wyliczeniu.  
  
 [ICorDebugArrayValue, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 Podklasa klasy `ICorDebugHeapValue` reprezentująca tablicę jednowymiarową lub wielowymiarową.  
  
 [ICorDebugAssembly, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 Reprezentuje zestaw.  
  
 [ICorDebugAssembly2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 Reprezentuje zestaw. Ten interfejs jest rozszerzeniem `ICorDebugAssembly` interfejsu.  
  
 [ICorDebugAssembly3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 Rozszerza logicznie [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interfejs w celu zapewnienia obsługi kontenerów zestawów i ich zestawy zawarte. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugAssemblyEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugAssembly` tablic.  
  
 [ICorDebugBlockingObjectEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 Dostarcza moduł wyliczający listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.  
  
 [ICorDebugBoxValue, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 Podklasa klasy `ICorDebugHeapValue` reprezentująca spakowany obiekt klasy wartości.  
  
 [ICorDebugBreakpoint, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.  
  
 [ICorDebugBreakpointEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugBreakpoint` tablic.  
  
 [ICorDebugChain, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 Reprezentuje segment stosu wywołań fizycznych lub logicznych.  
  
 [ICorDebugChainEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugChain` tablic.  
  
 [ICorDebugClass, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.  
  
 [ICorDebugClass2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 Reprezentuje klasą rodzajową lub klasy z parametrem metody typu <xref:System.Type>. Ten interfejs rozszerza `ICorDebugClass`.  
  
 [ICorDebugCode, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.  
  
 [ICorDebugCode2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 Udostępnia metody, które rozszerzają możliwości `ICorDebugCode`.  
  
 [ICorDebugCode3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 Dostarcza metodę, która rozszerza [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) i [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) aby podać informacje o zarządzaniu wartością zwracaną.  
  
 [ICorDebugCode4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 Dostarcza metodę, która umożliwia debugera wyliczanie zmiennych lokalnych i argumenty w funkcji.  
  
 [ICorDebugCodeEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugCode` tablic.  
  
 [ICorDebugComObjectValue, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.  
  
 [ICorDebugContext, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 Reprezentuje obiekt kontekstu. Ten Interfejs nie został jeszcze implementowany.  
  
 [ICorDebugController, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, wykonanie kodu, które mogą być kontrolowane kontekstu.  
  
 [ICorDebugDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.  
  
 [ICorDebugDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 Rozszerza logicznie [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugDataTarget3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 Rozszerza logicznie [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugDebugEvent, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 Definiuje interfejs podstawowy, z którym wszystkie `ICorDebug` pochodzić zdarzeń debugowania. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugEditAndContinueErrorInfo, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEditAndContinueSnapshot, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.  
  
 [ICorDebugErrorInfoEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEval, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.  
  
 [ICorDebugEval2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 Rozszerza `ICorDebugEval` celu zapewnienia obsługi typów ogólnych.  
  
 [ICorDebugExceptionDebugEvent, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń dotyczących wyjątków. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugExceptionObjectCallStackEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.  
  
 [ICorDebugExceptionObjectValue, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 Rozszerza [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interfejsu, aby zapewnić informacje śledzenia stosu z zarządzanego obiektu wyjątku.  
  
 [ICorDebugFrame, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 Reprezentuje ramkę na bieżącym stosie.  
  
 [ICorDebugFrameEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugFrame` tablic.  
  
 [ICorDebugFunction, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 Reprezentuje zarządzaną funkcję lub metodę.  
  
 [ICorDebugFunction2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 Rozszerza logicznie `ICorDebugFunction` zapewnia obsługę debugowania tylko mój kod krokowym.  
  
 [ICorDebugFunction3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 Rozszerza logicznie [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interfejsu, aby zapewnić dostęp do kodu z żądaniem ReJIT.  
  
 [ICorDebugFunctionBreakpoint, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w obrębie funkcji.  
  
 [ICorDebugGCReferenceEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.  
  
 [ICorDebugGenericValue, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 Podklasa klasy `ICorDebugValue` która odnosi się do wszystkich wartości. Ten interfejs zapewnia metody Get i Set dla wartości.  
  
 [ICorDebugGuidToTypeEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 Dostarcza moduł wyliczający dla obiektu, który mapuje identyfikatory GUID i odpowiednie `ICorDebugType` obiektów.  
  
 [ICorDebugHandleValue, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 Podklasa klasy `ICorDebugReferenceValue` reprezentująca wartość odniesienia, do której debuger utworzył procedurę obsługi do wyrzucania elementów bezużytecznych.  
  
 [ICorDebugHeapEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.  
  
 [ICorDebugHeapSegmentEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.  
  
 [ICorDebugHeapValue, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 Podklasa klasy `ICorDebugValue` reprezentująca obiekt, który został zebrany przez moduł odśmiecania pamięci CLR.  
  
 [ICorDebugHeapValue2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 Rozszerzenie `ICorDebugHeapValue` który zapewnia obsługę dla obsługi środowiska uruchomieniowego.  
  
 [ICorDebugHeapValue3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 Udostępnia właściwości blokady monitora obiektów.  
  
 [ICorDebugILCode, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 Reprezentuje segment kodu języka pośredniego (IL).  
  
 [ICorDebugILCode2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 Rozszerza logicznie [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interfejsu podania metod, które zwracają token do funkcji lokalnej zmiennej podpisu i mapy, program profilujący instrumentowanych języka pośredniego (IL) przesuwa się do oryginalnej metody IL przesunięcia.  
  
 [ICorDebugILFrame, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 Reprezentuje ramkę stosu kodu MSIL.  
  
 [ICorDebugILFrame2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 Logiczne rozszerzenie `ICorDebugILFrame`.  
  
 [ICorDebugILFrame3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.  
  
 [ICorDebugILFrame4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu języka pośredniego (IL). Parametr określa, czy narzędzie debuger ma dostęp do zmiennych i kodzie dodanym w profilerze ReJIT instrumentacji.  
  
 [ICorDebugInstanceFieldSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 Reprezentuje informacji dotyczących symboli debugowania dla pola wystąpienia. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugInternalFrame, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 Identyfikuje typy ramek dla debugera.  
  
 [ICorDebugInternalFrame2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 Zawiera informacje o ramkach wewnętrznych, łącznie z adresem stosu i pozycją w odniesieniu do [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) obiektów.  
  
 [ICorDebugLoadedModule, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 Zawiera informacje dotyczące załadowanym module. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 Dostarcza metody do przetwarzania wywołań zwrotnych debugera.  
  
 [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA). `ICorDebugManagedCallback2` jest logicznym rozszerzeniem `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.  
  
 [ICorDebugMDA, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).  
  
 [ICorDebugMemoryBuffer, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 Reprezentuje buforów w pamięci. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugMergedAssemblyRecord, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 Zawiera informacje o zestawie scalone. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugMetaDataLocator, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 Dostarcza informacje o metadanych do debugera.  
  
 [ICorDebugModule, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.  
  
 [ICorDebugModule2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 Służy jako logiczne rozszerzenie `ICorDebugModule`.  
  
 [ICorDebugModule3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 Tworzy czytnik symbolu dla modułu dynamicznego.  
  
 [ICorDebugModuleBreakpoint, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 Rozszerza `ICorDebugBreakpoint` zapewnienie dostępu do konkretnych modułów.  
  
 [ICorDebugModuleDebugEvent, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń na poziomie modułu. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugModuleEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugModule` tablic.  
  
 [ICorDebugMutableDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 Rozszerza [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu do obsługi danych modyfikowalnych elementów docelowych.  
  
 [ICorDebugNativeFrame, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 Wyspecjalizowana implementacja `ICorDebugFrame` wykorzystywana do ramek natywnych.  
  
 [ICorDebugNativeFrame2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.  
  
 [ICorDebugObjectEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).  
  
 [ICorDebugObjectValue, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 Podklasa klasy `ICorDebugValue` reprezentująca wartość, która zawiera obiekt.  
  
 [ICorDebugObjectValue2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastępowania.  
  
 [ICorDebugProcess, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 Reprezentuje proces, który wykonuje kod zarządzany.  
  
 [ICorDebugProcess2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 Logiczne rozszerzenie `ICorDebugProcess`.  
  
 [ICorDebugProcess3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 Steruje niestandardowymi powiadomieniami debugera.  
  
 [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 Rozszerza [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) obsługiwany dostęp do zarządzanej sterty, do dostarczania informacji dotyczących wyrzucania elementów bezużytecznych obiektów zarządzanych i określenia, czy debuger wczytuje obrazy z aplikacji przez interfejs użytkownika lokalnego pamięci podręcznej obrazów natywnych.  
  
 [ICorDebugProcess6, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 Rozszerza logicznie [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejsu, aby włączyć funkcje, takie jak dekodowanie zdarzenia debugowania zarządzanego, które są kodowane w zdarzeń debugowania natywnych wyjątków oraz wirtualnego modułu dzielenia. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugProcess7, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 Dostarcza metodę, która umożliwia skonfigurowanie debuger mógł obsłużyć aktualizacji metadanych w pamięci w procesie docelowym.  
  
 [ICorDebugProcess8, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 Rozszerza logicznie [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejsu, aby włączyć lub wyłączyć niektórych rodzajów [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) wywołań zwrotnych wyjątków.  
  
 [ICorDebugProcessEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugProcess` tablic.  
  
 [ICorDebugReferenceValue, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 Podklasa klasy `ICorDebugValue` obsługuje typy odwołań.  
  
 [ICorDebugRegisterSet, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.  
  
 [ICorDebugRegisterSet2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają więcej niż 64 rejestrów.  
  
 [ICorDebugRemote, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.  
  
 [ICorDebugRemoteTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.  
  
 [ICorDebugRuntimeUnwindableFrame, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.  
  
 [ICorDebugStackWalk, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.  
  
 [ICorDebugStaticFieldSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 Reprezentuje informacji dotyczących symboli debugowania dla pola statyczne. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugStepper, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
 [ICorDebugStepper2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 Zapewnia obsługę debugowania Tylko mój kod (JMC).  
  
 [ICorDebugStepperEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugStepper` tablic.  
  
 [ICorDebugStringValue, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 Podklasa klasy `ICorDebugHeapValue` która odnosi się do wartości ciągu.  
  
 [ICorDebugSymbolProvider, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 Udostępnia metody, które mogą służyć do pobierania informacji dotyczących symboli debugowania. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugSymbolProvider2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 Rozszerza logicznie [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interfejsu można pobrać informacji dotyczących symboli debugowania dodatkowe. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugThread, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 Reprezentuje wątek w procesie. Okres istnienia `ICorDebugThread` wystąpienie jest taki sam, jak okres istnienia wątku, który reprezentuje.  
  
 [ICorDebugThread2, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 Służy jako logiczne rozszerzenie `ICorDebugThread`.  
  
 [ICorDebugThread3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 Zapewnia punkt wejścia do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) i odpowiednich interfejsów.  
  
 [ICorDebugThread4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 Dostarcza informacje o blokowaniu wątku.  
  
 [ICorDebugThreadEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugThread` tablic.  
  
 [ICorDebugType, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ ogólny, `ICorDebugType` reprezentuje typ ogólny z wystąpieniami.  
  
 [ICorDebugType2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 Rozszerza [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interfejsu, aby pobrać identyfikator typu Typ podstawowy lub złożony (typ zdefiniowany przez użytkownika).  
  
 [ICorDebugTypeEnum, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugType` tablic.  
  
 [ICorDebugUnmanagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.  
  
 "ICorDebugValue"  
 Reprezentuje wartość odczytu lub zapisu w procesie debugowania.  
  
 "ICorDebugValue2"  
 Rozszerza `ICorDebugValue` aby zapewnić obsługę `ICorDebugType`.  
  
 [ICorDebugValue3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic, które są większe niż 2 GB.  
  
 "ICorDebugValueBreakpoint"  
 Rozszerza `ICorDebugBreakpoint` zapewniać dostęp do określonych wartości.  
  
 "ICorDebugValueEnum"  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugValue` tablic.  
  
 [ICorDebugVariableHome, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 Reprezentuje zmiennej lokalnej lub argumentu funkcji.  
  
 [ICorDebugVariableHomeEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 Dostarcza moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.  
  
 [ICorDebugVariableSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 Umożliwia pobranie informacji dotyczących symboli debugowania dla zmiennej. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugVirtualUnwinder, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 Dostarcza metody pomagające w wykonywania operacji odwijania stosu. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorPublish, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 Służy jako ogólny interfejs dla procesów publikowania.  
  
 [ICorPublishAppDomain, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.  
  
 [ICorPublishAppDomainEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 Udostępnia metody, które przemierzają kolekcję `ICorPublishAppDomain` obiekty, które obecnie istnieją w ramach procesu.  
  
 [ICorPublishEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.  
  
 [ICorPublishProcess, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 Dostarcza metody, które mają dostęp do informacji dotyczących procesu.  
  
 [ICorPublishProcessEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 Udostępnia metody, które przemierzają kolekcję `ICorPublishProcess` obiektów.  

 [Interfejs ISOSDacInterface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) zapewnia metody pomocnika dostępu do danych z `SOS`.

 [Interfejs IXCLRDataMethodDefinition](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) udostępnia metody do wykonywania zapytań o definicję metody.
 
 [Interfejs IXCLRDataMethodInstance](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) udostępnia metody do wykonywania zapytań o wystąpienie metody.
 
 [Interfejs IXCLRDataModule](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) udostępnia metody do wykonywania zapytań o załadowanym module.
 
 [Interfejs IXCLRDataProcess](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) udostępnia metody do wykonywania zapytań informacji dotyczących procesu.
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
