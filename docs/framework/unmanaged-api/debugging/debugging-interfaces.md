---
title: Debugowanie — Interfejsy
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d939063aaefb00d4db3de604df0dbd1b2175bf95
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981611"
---
# <a name="debugging-interfaces"></a>Debugowanie — Interfejsy
W tej sekcji opisano niezarządzane interfejsy obsługujące debugowanie programu wykonywanego w środowisku uruchomieniowym języka wspólnego (CLR).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Iclrdataenummemoryregions — interfejs](iclrdataenummemoryregions-interface.md)\
 Zapewnia metodę pozwalającą wyliczyć obszary pamięci, które są określone przez obiekty wywołujące.  
  
 [Iclrdataenummemoryregionscallback — interfejs](iclrdataenummemoryregionscallback-interface.md)\
 Zapewnia metodę wywołania zwrotnego dla `EnumMemoryRegions` do zgłaszania do debugera wyniku próby wyliczenia określonego regionu pamięci.  
  
 [Iclrdatatarget — interfejs](iclrdatatarget-interface.md)\
 Zapewnia metody interakcji z obiektem docelowym procesu CLR.  
  
 [Iclrdatatarget2 — interfejs](iclrdatatarget2-interface.md)\
 Podklasa klasy `ICLRDataTarget` używany przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.  
  
 [ICLRDataTarget3, interfejs](iclrdatatarget3-interface.md)\
 Podklasa klasy [ICLRDataTarget2](iclrdatatarget2-interface.md) , który zapewnia dostęp do informacji o wyjątku.  
  
 [Iclrdebugging — interfejs](iclrdebugging-interface.md)\
 Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.  
  
 [Iclrdebugginglibraryprovider — interfejs](iclrdebugginglibraryprovider-interface.md)\
 Obejmuje [providelibrary — metoda](iclrdebugginglibraryprovider-providelibrary-method.md) metody, która pobiera interfejs wywołania zwrotnego, która umożliwia języka wspólnego bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego lokalizowanie i ładowanie na żądanie dostawcy biblioteki.  
  
 [Iclrmetadatalocator — interfejs](iclrmetadatalocator-interface.md)\
 Interfejs używany przez warstwę usług dostępu do danych do lokalizowania metadane zestawów w procesie docelowym.  
  
 [Icordebug — interfejs](icordebug-interface.md)\
 Dostarcza metody, które umożliwiają programistom debugowanie aplikacji w środowisku CLR.  
  
 [ICorDebugAppDomain Interface](icordebugappdomain-interface.md)\
 Dostarcza metody do debugowania domen aplikacji.  
  
 [ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\
 Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami ByRef. Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` interfejsu.  
  
 [ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\
 Dostarcza metody do pracy z [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy w domenie aplikacji. Ten interfejs jest rozszerzeniem `ICorDebugAppDomain` i `ICorDebugAppDomain2` interfejsów.  
  
 [ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\
 Rozszerza logicznie [ICorDebugAppDomain](icordebugappdomain-interface.md) interfejsu można pobrać obiektu zarządzanego z wywołalne opakowanie COM.  
  
 [Icordebugappdomainenum — interfejs](icordebugappdomainenum-interface.md)\
 Dostarcza metodę, która zwraca określoną liczbę `ICorDebugAppDomain` wartości, zaczynając od następnej pozycji w wyliczeniu.  
  
 [Icordebugarrayvalue — interfejs](icordebugarrayvalue-interface.md)\
 Podklasa klasy `ICorDebugHeapValue` reprezentująca tablicę jednowymiarową lub wielowymiarową.  
  
 [Icordebugassembly — interfejs](icordebugassembly-interface.md)\
 Reprezentuje zestaw.  
  
 [Icordebugassembly2 — interfejs](icordebugassembly2-interface.md)\
 Reprezentuje zestaw. Ten interfejs jest rozszerzeniem `ICorDebugAssembly` interfejsu.  
  
 [ICorDebugAssembly3, interfejs](icordebugassembly3-interface.md)\
 Rozszerza logicznie [ICorDebugAssembly](icordebugassembly-interface.md) interfejs w celu zapewnienia obsługi kontenerów zestawów i ich zestawy zawarte. **Dostępne na tylko platforma .NET Native.**  
  
 [Icordebugassemblyenum — interfejs](icordebugassemblyenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugAssembly` tablic.  
  
 [Icordebugblockingobjectenum — interfejs](icordebugblockingobjectenum-interface.md)\
 Dostarcza moduł wyliczający listę [CorDebugBlockingObject](cordebugblockingobject-structure.md) struktury.  
  
 [Icordebugboxvalue — interfejs](icordebugboxvalue-interface.md)\
 Podklasa klasy `ICorDebugHeapValue` reprezentująca spakowany obiekt klasy wartości.  
  
 [Icordebugbreakpoint — interfejs](icordebugbreakpoint-interface.md)\
 Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.  
  
 [Icordebugbreakpointenum — interfejs](icordebugbreakpointenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugBreakpoint` tablic.  
  
 [Icordebugchain — interfejs](icordebugchain-interface.md)\
 Reprezentuje segment stosu wywołań fizycznych lub logicznych.  
  
 [Icordebugchainenum — interfejs](icordebugchainenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugChain` tablic.  
  
 [ICorDebugClass Interface](icordebugclass-interface.md)\
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.  
  
 [ICorDebugClass2 Interface](icordebugclass2-interface.md)\
 Reprezentuje klasą rodzajową lub klasy z parametrem metody typu <xref:System.Type>. Ten interfejs rozszerza `ICorDebugClass`.  
  
 [Icordebugcode — interfejs](icordebugcode-interface1.md)\
 Reprezentuje segment kodu języka pośredniego firmy Microsoft (MSIL) lub kodu natywnego.  
  
 [Icordebugcode2 — interfejs](icordebugcode2-interface.md)\
 Udostępnia metody, które rozszerzają możliwości `ICorDebugCode`.  
  
 [ICorDebugCode3, interfejs](icordebugcode3-interface.md)\
 Dostarcza metodę, która rozszerza [ICorDebugCode](icordebugcode-interface1.md) i [ICorDebugCode2](icordebugcode2-interface.md) aby podać informacje o zarządzaniu wartością zwracaną.  
  
 [ICorDebugCode4, interfejs](icordebugcode4-interface.md)\
 Dostarcza metodę, która umożliwia debugera wyliczanie zmiennych lokalnych i argumenty w funkcji.  
  
 [Icordebugcodeenum — interfejs](icordebugcodeenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugCode` tablic.  
  
 [ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\
 Dostarcza metody pobierania obiektów interfejsu w pamięci podręcznej.  
  
 [Icordebugcontext — interfejs](icordebugcontext-interface.md)\
 Reprezentuje obiekt kontekstu. Ten Interfejs nie został jeszcze implementowany.  
  
 [ICorDebugController Interface](icordebugcontroller-interface.md)\
 Reprezentuje zakres, albo <xref:System.Diagnostics.Process> lub <xref:System.AppDomain>, wykonanie kodu, które mogą być kontrolowane kontekstu.  
  
 [Icordebugdatatarget — interfejs](icordebugdatatarget-interface.md)\
 Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.  
  
 [ICorDebugDataTarget2, interfejs](icordebugdatatarget2-interface.md)\
 Rozszerza logicznie [icordebugdatatarget —](icordebugdatatarget-interface.md) interfejsu. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\
 Rozszerza logicznie [icordebugdatatarget —](icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugDebugEvent, interfejs](icordebugdebugevent-interface.md)\
 Definiuje interfejs podstawowy, z którym wszystkie `ICorDebug` pochodzić zdarzeń debugowania. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)\
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [Icordebugenum — interfejs](icordebugenum-interface1.md)\
 Służy jako abstrakcyjny interfejs podstawowy do debugowania modułów wyliczających.  
  
 [Icordebugerrorinfoenum — interfejs](icordebugerrorinfoenum-interface.md)\
 Nieaktualne. Nie używaj tego interfejsu.  
  
 [Icordebugeval — interfejs](icordebugeval-interface.md)\
 Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.  
  
 [Icordebugeval2 — interfejs](icordebugeval2-interface.md)\
 Rozszerza `ICorDebugEval` celu zapewnienia obsługi typów ogólnych.  
  
 [ICorDebugExceptionDebugEvent, interfejs](icordebugexceptiondebugevent-interface.md)\
 Rozszerza [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń dotyczących wyjątków. **Dostępne na tylko platforma .NET Native.**  
  
 [Icordebugexceptionobjectcallstackenum — interfejs](icordebugexceptionobjectcallstackenum-interface.md)\
 Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.  
  
 [Icordebugexceptionobjectvalue — interfejs](icordebugexceptionobjectvalue-interface.md)\
 Rozszerza [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interfejsu, aby zapewnić informacje śledzenia stosu z zarządzanego obiektu wyjątku.  
  
 [ICorDebugFrame Interface](icordebugframe-interface.md)\
 Reprezentuje ramkę na bieżącym stosie.  
  
 [Icordebugframeenum — interfejs](icordebugframeenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugFrame` tablic.  
  
 [ICorDebugFunction — interfejs](icordebugfunction-interface1.md)\
 Reprezentuje zarządzaną funkcję lub metodę.  
  
 [ICorDebugFunction2 Interface](icordebugfunction2-interface.md)\
 Rozszerza logicznie `ICorDebugFunction` zapewnia obsługę debugowania tylko mój kod krokowym.  
  
 [ICorDebugFunction3 Interface](icordebugfunction3-interface.md)\
 Rozszerza logicznie [ICorDebugFunction](icordebugfunction-interface1.md) interfejsu, aby zapewnić dostęp do kodu z żądaniem ReJIT.  
  
 [ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)\
 Rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w obrębie funkcji.  
  
 [Icordebuggcreferenceenum — interfejs](icordebuggcreferenceenum-interface.md)\
 Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.  
  
 [Icordebuggenericvalue — interfejs](icordebuggenericvalue-interface.md)\
 Podklasa klasy `ICorDebugValue` która odnosi się do wszystkich wartości. Ten interfejs zapewnia metody Get i Set dla wartości.  
  
 [Icordebugguidtotypeenum — interfejs](icordebugguidtotypeenum-interface.md)\
 Dostarcza moduł wyliczający dla obiektu, który mapuje identyfikatory GUID i odpowiednie `ICorDebugType` obiektów.  
  
 [Icordebughandlevalue — interfejs](icordebughandlevalue-interface.md)\
 Podklasa klasy `ICorDebugReferenceValue` reprezentująca wartość odniesienia, do której debuger utworzył procedurę obsługi do wyrzucania elementów bezużytecznych.  
  
 [Icordebugheapenum — interfejs](icordebugheapenum-interface.md)\
 Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie.  
  
 [Icordebugheapsegmentenum — interfejs](icordebugheapsegmentenum-interface.md)\
 Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty.  
  
 [Icordebugheapvalue — interfejs](icordebugheapvalue-interface.md)\
 Podklasa klasy `ICorDebugValue` reprezentująca obiekt, który został zebrany przez moduł odśmiecania pamięci CLR.  
  
 [Icordebugheapvalue2 — interfejs](icordebugheapvalue2-interface1.md)\
 Rozszerzenie `ICorDebugHeapValue` który zapewnia obsługę dla obsługi środowiska uruchomieniowego.  
  
 [Icordebugheapvalue3 — interfejs](icordebugheapvalue3-interface.md)\
 Udostępnia właściwości blokady monitora obiektów.  
  
 [ICorDebugILCode Interface](icordebugilcode-interface.md)\
 Reprezentuje segment kodu języka pośredniego (IL).  
  
 [ICorDebugILCode2 Interface](icordebugilcode2-interface.md)\
 Rozszerza logicznie [ICorDebugILCode](icordebugilcode-interface.md) interfejsu podania metod, które zwracają token do funkcji lokalnej zmiennej podpisu i mapy, program profilujący instrumentowanych języka pośredniego (IL) przesuwa się do oryginalnej metody IL przesunięcia.  
  
 [ICorDebugILFrame Interface](icordebugilframe-interface.md)\
 Reprezentuje ramkę stosu kodu MSIL.  
  
 [ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)\
 Logiczne rozszerzenie `ICorDebugILFrame`.  
  
 [ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)\
 Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.  
  
 [ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\
 Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu języka pośredniego (IL). Parametr określa, czy narzędzie debuger ma dostęp do zmiennych i kodzie dodanym w profilerze ReJIT instrumentacji.  
  
 [ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\
 Reprezentuje informacji dotyczących symboli debugowania dla pola wystąpienia. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)\
 Identyfikuje typy ramek dla debugera.  
  
 [ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\
 Zawiera informacje o ramkach wewnętrznych, łącznie z adresem stosu i pozycją w odniesieniu do [ICorDebugFrame](icordebugframe-interface.md) obiektów.  
  
 [ICorDebugLoadedModule, interfejs](icordebugloadedmodule-interface.md)\
 Zawiera informacje dotyczące załadowanym module. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)\
 Dostarcza metody do przetwarzania wywołań zwrotnych debugera.  
  
 [ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\
 Dostarcza metody umożliwiające obsługę wyjątków debugera i obsługujące asystentów zarządzanego debugowania (MDA). `ICorDebugManagedCallback2` jest logicznym rozszerzeniem `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\
 Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.  
  
 [ICorDebugMDA Interface](icordebugmda-interface.md)\
 Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).  
  
 [ICorDebugMemoryBuffer, interfejs](icordebugmemorybuffer-interface.md)\
 Reprezentuje buforów w pamięci. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugMergedAssemblyRecord, interfejs](icordebugmergedassemblyrecord-interface.md)\
 Zawiera informacje o zestawie scalone. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\
 Dostarcza informacje o metadanych do debugera.  
  
 [Icordebugmodule — interfejs](icordebugmodule-interface.md)\
 Reprezentuje moduł CLR, który jest albo plikiem wykonywalnym lub biblioteką DLL.  
  
 [Icordebugmodule2 — interfejs](icordebugmodule2-interface.md)\
 Służy jako logiczne rozszerzenie `ICorDebugModule`.  
  
 [Icordebugmodule3 — interfejs](icordebugmodule3-interface.md)\
 Tworzy czytnik symbolu dla modułu dynamicznego.  
  
 [ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\
 Rozszerza `ICorDebugBreakpoint` zapewnienie dostępu do konkretnych modułów.  
  
 [ICorDebugModuleDebugEvent, interfejs](icordebugmoduledebugevent-interface.md)\
 Rozszerza [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń na poziomie modułu. **Dostępne na tylko platforma .NET Native.**  
  
 [Icordebugmoduleenum — interfejs](icordebugmoduleenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugModule` tablic.  
  
 [ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\
 Rozszerza [icordebugdatatarget —](icordebugdatatarget-interface.md) interfejsu do obsługi danych modyfikowalnych elementów docelowych.  
  
 [ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)\
 Wyspecjalizowana implementacja `ICorDebugFrame` wykorzystywana do ramek natywnych.  
  
 [ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\
 Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.  
  
 [Icordebugobjectenum — interfejs](icordebugobjectenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza tablice obiektów według ich względnych adresów wirtualnych (RVA).  
  
 [Icordebugobjectvalue — interfejs](icordebugobjectvalue-interface.md)\
 Podklasa klasy `ICorDebugValue` reprezentująca wartość, która zawiera obiekt.  
  
 [Icordebugobjectvalue2 — interfejs](icordebugobjectvalue2-interface.md)\
 Rozszerza `ICorDebugObjectValue` do obsługi dziedziczenia i zastępowania.  
  
 [Icordebugprocess — interfejs](icordebugprocess-interface.md)\
 Reprezentuje proces, który wykonuje kod zarządzany.  
  
 [Icordebugprocess2 — interfejs](icordebugprocess2-interface1.md)\
 Logiczne rozszerzenie `ICorDebugProcess`.  
  
 [ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\
 Steruje niestandardowymi powiadomieniami debugera.

 [ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\
 Zapewnia obsługę poza Kontrola wykonywania procesu.
  
 [ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\
 Rozszerza [ICorDebugProcess](icordebugprocess-interface.md) obsługiwany dostęp do zarządzanej sterty, do dostarczania informacji dotyczących wyrzucania elementów bezużytecznych obiektów zarządzanych i określenia, czy debuger wczytuje obrazy z aplikacji przez interfejs użytkownika lokalnego pamięci podręcznej obrazów natywnych.  
  
 [ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\
 Rozszerza logicznie [ICorDebugProcess](icordebugprocess-interface.md) interfejsu, aby włączyć funkcje, takie jak dekodowanie zdarzenia debugowania zarządzanego, które są kodowane w zdarzeń debugowania natywnych wyjątków oraz wirtualnego modułu dzielenia. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugProcess7, interfejs](icordebugprocess7-interface.md)\
 Dostarcza metodę, która umożliwia skonfigurowanie debuger mógł obsłużyć aktualizacji metadanych w pamięci w procesie docelowym.  
  
 [ICorDebugProcess8, interfejs](icordebugprocess8-interface.md)\
 Rozszerza logicznie [ICorDebugProcess](icordebugprocess-interface.md) interfejsu, aby włączyć lub wyłączyć niektórych rodzajów [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) wywołań zwrotnych wyjątków.  
  
 [Icordebugprocessenum — interfejs](icordebugprocessenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugProcess` tablic.  
  
 [Icordebugreferencevalue — interfejs](icordebugreferencevalue-interface.md)\
 Podklasa klasy `ICorDebugValue` obsługuje typy odwołań.  
  
 [Icordebugregisterset — interfejs](icordebugregisterset-interface.md)\
 Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.  
  
 [Icordebugregisterset2 — interfejs](icordebugregisterset2-interface.md)\
 Rozszerza możliwości `ICorDebugRegisterSet` dla platform sprzętowych, które mają więcej niż 64 rejestrów.  
  
 [Icordebugremote — interfejs](icordebugremote-interface.md)\
 Zapewnia zdalnemu procesowi docelowemu możliwość uruchamiania lub dołączenia zarządzanych debugerów.  
  
 [Icordebugremotetarget — interfejs](icordebugremotetarget-interface.md)\
 Dostarcza metody, które umożliwiają debugowania aplikacji opartych na dodatku Silverlight w środowisku CLR.  
  
 [ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)\
 Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.  
  
 [ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)\
 Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.  
  
 [ICorDebugStaticFieldSymbol, interfejs](icordebugstaticfieldsymbol-interface.md)\
 Reprezentuje informacji dotyczących symboli debugowania dla pola statyczne. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugStepper — interfejs](icordebugstepper-interface.md)\
 Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
 [Icordebugstepper2 — interfejs](icordebugstepper2-interface1.md)\
 Zapewnia obsługę debugowania Tylko mój kod (JMC).  
  
 [Icordebugstepperenum — interfejs](icordebugstepperenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugStepper` tablic.  
  
 [Icordebugstringvalue — interfejs](icordebugstringvalue-interface.md)\
 Podklasa klasy `ICorDebugHeapValue` która odnosi się do wartości ciągu.  
  
 [ICorDebugSymbolProvider, interfejs](icordebugsymbolprovider-interface.md)\
 Udostępnia metody, które mogą służyć do pobierania informacji dotyczących symboli debugowania. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugSymbolProvider2, interfejs](icordebugsymbolprovider2-interface.md)\
 Rozszerza logicznie [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interfejsu można pobrać informacji dotyczących symboli debugowania dodatkowe. **Dostępne na tylko platforma .NET Native.**  
  
 [Icordebugthread — interfejs](icordebugthread-interface.md)\
 Reprezentuje wątek w procesie. Okres istnienia `ICorDebugThread` wystąpienie jest taki sam, jak okres istnienia wątku, który reprezentuje.  
  
 [Icordebugthread2 — interfejs](icordebugthread2-interface.md)\
 Służy jako logiczne rozszerzenie `ICorDebugThread`.  
  
 [Icordebugthread3 — interfejs](icordebugthread3-interface.md)\
 Zapewnia punkt wejścia do [ICorDebugStackWalk](icordebugstackwalk-interface.md) i odpowiednich interfejsów.  
  
 [Icordebugthread4 — interfejs](icordebugthread4-interface.md)\
 Dostarcza informacje o blokowaniu wątku.  
  
 [Icordebugthreadenum — interfejs](icordebugthreadenum-interface1.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugThread` tablic.  
  
 [Icordebugtype — interfejs](icordebugtype-interface.md)\
 Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ ogólny, `ICorDebugType` reprezentuje typ ogólny z wystąpieniami.  
  
 [ICorDebugType2, interfejs](icordebugtype2-interface.md)\
 Rozszerza [ICorDebugType](icordebugtype-interface.md) interfejsu, aby pobrać identyfikator typu Typ podstawowy lub złożony (typ zdefiniowany przez użytkownika).  
  
 [Icordebugtypeenum — interfejs](icordebugtypeenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugType` tablic.  
  
 [ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)\
 Zapewnia powiadomienie macierzystych zdarzeń, które nie dotyczą bezpośrednio środowiska CLR.  
  
 [ICorDebugValue](icordebugvalue-interface.md)\
 Reprezentuje wartość odczytu lub zapisu w procesie debugowania.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 Rozszerza `ICorDebugValue` aby zapewnić obsługę `ICorDebugType`.  
  
 [Icordebugvalue3 — interfejs](icordebugvalue3-interface.md)\
 Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic, które są większe niż 2 GB.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Rozszerza `ICorDebugBreakpoint` zapewniać dostęp do określonych wartości.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 Implementuje `ICorDebugEnum` metod i wylicza `ICorDebugValue` tablic.  
  
 [ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\
 Reprezentuje zmiennej lokalnej lub argumentu funkcji.  
  
 [ICorDebugVariableHomeEnum, interfejs](icordebugvariablehomeenum-interface.md)\
 Dostarcza moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.  
  
 [ICorDebugVariableSymbol, interfejs](icordebugvariablesymbol-interface.md)\
 Umożliwia pobranie informacji dotyczących symboli debugowania dla zmiennej. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorDebugVirtualUnwinder, interfejs](icordebugvirtualunwinder-interface.md)\
 Dostarcza metody pomagające w wykonywania operacji odwijania stosu. **Dostępne na tylko platforma .NET Native.**  
  
 [ICorPublish — interfejs](icorpublish-interface.md)\
 Służy jako ogólny interfejs dla procesów publikowania.  
  
 [Icorpublishappdomain — interfejs](icorpublishappdomain-interface.md)\
 Reprezentuje i dostarcza informacje dotyczące domeny aplikacji.  
  
 [Icorpublishappdomainenum — interfejs](icorpublishappdomainenum-interface.md)\
 Udostępnia metody, które przemierzają kolekcję `ICorPublishAppDomain` obiekty, które obecnie istnieją w ramach procesu.  
  
 [Icorpublishenum — interfejs](icorpublishenum-interface.md)\
 Służy jako abstrakcyjna podstawowa do publikowania modułów wyliczających.  
  
 [Icorpublishprocess — interfejs](icorpublishprocess-interface.md)\
 Dostarcza metody, które mają dostęp do informacji dotyczących procesu.  
  
 [Icorpublishprocessenum — interfejs](icorpublishprocessenum-interface.md)\
 Udostępnia metody, które przemierzają kolekcję `ICorPublishProcess` obiektów.  

 [Interfejs ISOSDacInterface](isosdacinterface-interface.md)\
 Udostępnia metody pomocnicze na dostęp do danych z `SOS`.

 [Interfejs IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)\
 Udostępnia metody do wykonywania zapytań o definicję metody.
 
 [Interfejs IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)\
 Udostępnia metody do wykonywania zapytań o wystąpienie metody.
 
 [Interfejs IXCLRDataModule](ixclrdatamodule-interface.md)\
 Udostępnia metody do wykonywania zapytań o załadowanym module.
 
 [Interfejs IXCLRDataProcess](ixclrdataprocess-interface.md)\
 Udostępnia metody do wykonywania zapytań informacji dotyczących procesu.
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](debugging-coclasses.md)\
 [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)\
 [Debugowanie — wyliczenia](debugging-enumerations.md)\
 [Struktury debugowania](debugging-structures.md)\
