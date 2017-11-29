---
title: "Debugowanie — Interfejsy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de2469d15eef40b9ef283d67aeca429d9d96a7ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-interfaces"></a>Debugowanie — Interfejsy
W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRDataEnumMemoryRegions — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.  
  
 [ICLRDataEnumMemoryRegionsCallback — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 Zapewnia metodę wywołania zwrotnego `EnumMemoryRegions` zgłoszenia do debugera, wynik próby wyliczenia określonego regionu pamięci.  
  
 [ICLRDataTarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 Zapewnia metody interakcji z obiektem docelowym procesu CLR.  
  
 [ICLRDataTarget2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 Podklasa `ICLRDataTarget` używany przez warstwę usługi dostępu do danych do manipulowania regiony pamięci wirtualnej w procesie docelowym.  
  
 [Iclrdatatarget3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 Podklasa [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , który zapewnia dostęp do informacji o wyjątku.  
  
 [ICLRDebugging — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.  
  
 [Iclrdebugginglibraryprovider — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 Obejmuje [ProvideLibrary — metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) metodę, która pobiera dostawcę biblioteki interfejsu wywołania zwrotnego, który umożliwia języka wspólnego bibliotek debugowania określonej wersji środowiska uruchomieniowego należy odnaleźć i załadować na żądanie.  
  
 [ICLRMetadataLocator — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.  
  
 [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.  
  
 [ICorDebugAppDomain Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 Dostarcza metody do debugowania domen aplikacji.  
  
 [ICorDebugAppDomain2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef. Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` interfejsu.  
  
 [ICorDebugAppDomain3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 Udostępnia metody do pracy z [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy w domenie aplikacji. Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` i `ICorDebugAppDomain2` interfejsów.  
  
 [Icordebugappdomain4 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 Rozszerza logicznie [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interfejs do pobierania obiektu zarządzanych z wywoływana otoka COM.  
  
 [ICorDebugAppDomainEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 Udostępnia metodę, która zwraca określoną liczbę `ICorDebugAppDomain` wartości, zaczynając od następnej lokalizacji w wyliczeniu.  
  
 [ICorDebugArrayValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 Podklasa `ICorDebugHeapValue` reprezentujący tablicy jednowymiarowej lub wielowymiarowych.  
  
 [ICorDebugAssembly Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 Reprezentuje zestaw.  
  
 [ICorDebugAssembly2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 Reprezentuje zestaw. Ten interfejs jest rozszerzeniem `ICorDebugAssembly` interfejsu.  
  
 [Interfejs ICorDebugAssembly3](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 Rozszerza logicznie [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interfejsu, aby zapewnić obsługę dla zestawów kontenera i ich zawartych w niej zestawów. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugAssemblyEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugAssembly` tablic.  
  
 [ICorDebugBlockingObjectEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 Udostępnia moduł wyliczający listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.  
  
 [ICorDebugBoxValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 Podklasa `ICorDebugHeapValue` reprezentujący obiekt klasy wartości spakowanej.  
  
 [ICorDebugBreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.  
  
 [ICorDebugBreakpointEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugBreakpoint` tablic.  
  
 [ICorDebugChain Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 Reprezentuje segment stosu wywołań fizycznych lub logicznych.  
  
 [ICorDebugChainEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugChain` tablic.  
  
 [ICorDebugClass Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest rodzajowy, `ICorDebugClass` reprezentuje bez wystąpień typu ogólnego.  
  
 [ICorDebugClass2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 Reprezentuje klasy ogólnej lub klasie z parametrem metody typu <xref:System.Type>. Ten interfejs stanowi rozszerzenie `ICorDebugClass`.  
  
 [ICorDebugCode Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.  
  
 [ICorDebugCode2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 Udostępnia metody, które rozszerzają możliwości `ICorDebugCode`.  
  
 [Icordebugcode3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 Udostępnia metodę, która rozszerza [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) i [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) aby podać informacje o zarządzanych wartości zwracanej.  
  
 [Interfejs ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 Udostępnia metodę umożliwiającą debugera wyliczyć zmiennych lokalnych i argumenty w funkcji.  
  
 [ICorDebugCodeEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugCode` tablic.  
  
 [ICorDebugComObjectValue — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.  
  
 [ICorDebugContext Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 Reprezentuje obiekt kontekstu. Ten Interfejs nie został jeszcze implementowany.  
  
 [ICorDebugController Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, których wykonanie kodu mogą być kontrolowane kontekstu.  
  
 [ICorDebugDataTarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.  
  
 [Interfejs ICorDebugDataTarget2](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 Rozszerza logicznie [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu. **Dostępne na tylko platforma .NET Native.**  
  
 [Icordebugdatatarget3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 Rozszerza logicznie [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów. **Dostępne na tylko platforma .NET Native.**  
  
 [Interfejs ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 Definiuje interfejs podstawowy, z którym wszystkie `ICorDebug` pochodzi zdarzeń debugowania. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugEditAndContinueErrorInfo — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEditAndContinueSnapshot Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.  
  
 [ICorDebugErrorInfoEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEval Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.  
  
 [ICorDebugEval2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 Rozszerza `ICorDebugEval` zapewnienie wsparcia dla typów ogólnych.  
  
 [Interfejs ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejs do obsługi zdarzeń wyjątków. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugExceptionObjectCallStackEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.  
  
 [ICorDebugExceptionObjectValue — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 Rozszerza [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interfejsu, aby podać informacje śledzenia stosu z obiektem zarządzanym wyjątku.  
  
 [ICorDebugFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 Reprezentuje ramkę na bieżącym stosie.  
  
 [ICorDebugFrameEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugFrame` tablic.  
  
 [ICorDebugFunction Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 Reprezentuje zarządzaną funkcję lub metodę.  
  
 [ICorDebugFunction2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 Rozszerza logicznie `ICorDebugFunction` zapewnia obsługę tylko mój kod krokowym debugowania.  
  
 [Interfejs ICorDebugFunction3](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 Rozszerza logicznie [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interfejsu w celu zapewnienia dostępu do kodu z żądania ReJIT.  
  
 [ICorDebugFunctionBreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w funkcjach.  
  
 [ICorDebugGCReferenceEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.  
  
 [ICorDebugGenericValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 Podklasa `ICorDebugValue` dotyczy wszystkich wartości. Ten interfejs zapewnia metody Get i Set dla wartości.  
  
 [ICorDebugGuidToTypeEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 Udostępnia moduł wyliczający dla obiekt, który mapuje identyfikatorów GUID i odpowiednie `ICorDebugType` obiektów.  
  
 [ICorDebugHandleValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 Podklasa `ICorDebugReferenceValue` reprezentujący wartość odwołania, do których debuger został utworzony obsługę wyrzucanie elementów bezużytecznych.  
  
 [ICorDebugHeapEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.  
  
 [ICorDebugHeapSegmentEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.  
  
 [ICorDebugHeapValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 Podklasa `ICorDebugValue` reprezentujący obiekt, które zostały zebrane przez moduł garbage collector środowiska CLR.  
  
 [ICorDebugHeapValue2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 Rozszerzenie `ICorDebugHeapValue` który zapewnia obsługę środowiska uruchomieniowego uchwytów.  
  
 [ICorDebugHeapValue3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 Udostępnia właściwości blokady monitora obiektów.  
  
 [Interfejs ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 Reprezentuje segment kodu w języku pośrednim (IL).  
  
 [Interfejs ICorDebugILCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 Rozszerza logicznie [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interfejsu podania metod tokenem podpisu lokalnego zmiennej funkcji, które zwracają, oraz że mapowanie profilera instrumentowanych język pośredni (IL) przesuwa się do oryginalnej metody IL przesunięcia.  
  
 [ICorDebugILFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 Reprezentuje ramkę stosu kodu MSIL.  
  
 [ICorDebugILFrame2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 Rozszerzenie logicznej `ICorDebugILFrame`.  
  
 [Icordebugilframe3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.  
  
 [Interfejs ICorDebugILFrame4](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu w języku pośrednim (IL). Parametr określa, czy debuger ma dostęp do zmiennych i kodzie dodanym w ReJIT Instrumentacji profilera.  
  
 [Interfejs ICorDebugInstanceFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 Reprezentuje informacje symbolu debugowania dla pola wystąpienia. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugInternalFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 Identyfikuje typy ramek dla debugera.  
  
 [ICorDebugInternalFrame2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 Informacje na temat wewnętrznej ramki, w tym adresu stosu i pozycji w odniesieniu do [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) obiektów.  
  
 [Icordebugloadedmodule — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 Udostępnia informacje na temat załadować modułu. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugManagedCallback — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 Dostarcza metody do przetwarzania wywołań zwrotnych debugera.  
  
 [ICorDebugManagedCallback2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA). `ICorDebugManagedCallback2`jest logiczną rozszerzenie `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.  
  
 [ICorDebugMDA — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).  
  
 [Interfejs ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 Reprezentuje buforów w pamięci. **Dostępne na tylko platforma .NET Native.**  
  
 [Interfejs ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 Zawiera informacje o zestawie scalone. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugMetaDataLocator — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 Dostarcza informacje o metadanych do debugera.  
  
 [ICorDebugModule Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.  
  
 [ICorDebugModule2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 Służy jako logiczne rozszerzenia `ICorDebugModule`.  
  
 [ICorDebugModule3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 Tworzy czytnik symbolu dla modułu dynamicznego.  
  
 [ICorDebugModuleBreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 Rozszerza `ICorDebugBreakpoint` umożliwia dostęp do określonych modułów.  
  
 [Interfejs ICorDebugModuleDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejs do obsługi zdarzenia na poziomie modułu. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugModuleEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugModule` tablic.  
  
 [Interfejs ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 Rozszerza [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejs do obsługi danych modyfikowalne elementy docelowe.  
  
 [ICorDebugNativeFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 Specjalne implementacja `ICorDebugFrame` używany dla ramek natywnych.  
  
 [ICorDebugNativeFrame2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.  
  
 [ICorDebugObjectEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza tablice obiektów przez względną wirtualnych adresów (RVAs).  
  
 [ICorDebugObjectValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 Podklasa `ICorDebugValue` reprezentujący wartość, która zawiera obiekt.  
  
 [ICorDebugObjectValue2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastąpień.  
  
 [ICorDebugProcess Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 Reprezentuje proces, który wykonuje kod zarządzany.  
  
 [ICorDebugProcess2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 Rozszerzenie logicznej `ICorDebugProcess`.  
  
 [ICorDebugProcess3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 Steruje niestandardowymi powiadomieniami debugera.  
  
 [ICorDebugProcess5 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 Rozszerza [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejs do obsługi dostępu do sterty zarządzanej, aby podać informacje o wyrzucanie elementów bezużytecznych zarządzanych obiektów i ustalenie, czy debuger ładuje obrazów z aplikacji do lokalnego pamięć podręczna obrazu macierzystego.  
  
 [Interfejs ICorDebugProcess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 Rozszerza logicznie [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejsu, aby włączyć funkcje, takie jak dekodowania zdarzenia debugowania zarządzanego, które są zakodowane w zdarzenia debugowania natywnego wyjątków i dzielenia wirtualnych modułu. **Dostępne na tylko platforma .NET Native.**  
  
 [Interfejs ICorDebugProcess7](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 Udostępnia metodę, która konfiguruje debugera do obsługi aktualizacji metadanych w pamięci w procesie docelowym.  
  
 [Icordebugprocess8 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 Rozszerza logicznie [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interfejsu, aby włączyć lub wyłączyć niektórych typów [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) wyjątek wywołań zwrotnych.  
  
 [ICorDebugProcessEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugProcess` tablic.  
  
 [ICorDebugReferenceValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 Podklasa `ICorDebugValue` obsługuje typy referencyjne.  
  
 [ICorDebugRegisterSet — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.  
  
 [ICorDebugRegisterSet2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają ponad 64 rejestrów.  
  
 [ICorDebugRemote — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.  
  
 [ICorDebugRemoteTarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.  
  
 [Icordebugruntimeunwindableframe — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.  
  
 [ICorDebugStackWalk — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.  
  
 [Interfejs ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 Reprezentuje informacje symbolu debugowania dla pola statycznego. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugStepper — Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
 [ICorDebugStepper2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 Zapewnia obsługę debugowania Tylko mój kod (JMC).  
  
 [ICorDebugStepperEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugStepper` tablic.  
  
 [ICorDebugStringValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 Podklasa `ICorDebugHeapValue` dotyczący wartości ciągu.  
  
 [Interfejs ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 Udostępnia metody, które mogą służyć do pobierania informacji o symbolach debugowania. **Dostępne na tylko platforma .NET Native.**  
  
 [Interfejs ICorDebugSymbolProvider2](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 Rozszerza logicznie [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interfejsu można pobrać informacji o symbolach dodatkowe debugowania. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugThread Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 Reprezentuje wątek w procesie. Okres istnienia `ICorDebugThread` wystąpienie jest taki sam jak okres istnienia reprezentuje wątku.  
  
 [ICorDebugThread2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 Służy jako logiczne rozszerzenia `ICorDebugThread`.  
  
 [ICorDebugThread3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 Zapewnia punkt wejścia do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) i odpowiednie interfejsy.  
  
 [ICorDebugThread4 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 Dostarcza informacje o blokowaniu wątku.  
  
 [ICorDebugThreadEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugThread` tablic.  
  
 [ICorDebugType Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest rodzajowy, `ICorDebugType` reprezentuje wystąpień typu ogólnego.  
  
 [Interfejs ICorDebugType2](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 Rozszerza [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interfejsu można pobrać identyfikatora typu podstawowego typu lub typu złożonego (zdefiniowane przez użytkownika).  
  
 [ICorDebugTypeEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugType` tablic.  
  
 [ICorDebugUnmanagedCallback — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.  
  
 "ICorDebugValue"  
 Reprezentuje wartość odczytu lub zapisu w procesie debugowania.  
  
 "ICorDebugValue2"  
 Rozszerza `ICorDebugValue` aby zapewnić obsługę `ICorDebugType`.  
  
 [ICorDebugValue3 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 Rozszerza interfejsów "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę dla tablic, które są większe niż 2 GB.  
  
 "ICorDebugValueBreakpoint"  
 Rozszerza `ICorDebugBreakpoint` do zapewniania dostępu do określonej wartości.  
  
 "ICorDebugValueEnum"  
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugValue` tablic.  
  
 [Interfejs ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 Reprezentuje lokalnej zmiennej lub argumentu funkcji.  
  
 [Interfejs ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 Udostępnia moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.  
  
 [Interfejs ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 Pobiera informacje o symbolu debugowania dla zmiennej. **Dostępne na tylko platforma .NET Native.**  
  
 [Icordebugvirtualunwinder — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 Udostępnia metody, aby pomóc w odwijanie stosu. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorPublish — interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 Służy jako ogólny interfejs dla procesów publikowania.  
  
 [ICorPublishAppDomain — interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.  
  
 [ICorPublishAppDomainEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 Udostępnia metody przechodzących przez kolekcję `ICorPublishAppDomain` obiekty znajdujące się obecnie w ramach procesu.  
  
 [ICorPublishEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.  
  
 [ICorPublishProcess — interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 Dostarcza metody, które mają dostęp do informacji dotyczących procesu.  
  
 [ICorPublishProcessEnum — interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 Udostępnia metody przechodzących przez kolekcję `ICorPublishProcess` obiektów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Statyczne funkcje globalne debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Debugowanie — wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
