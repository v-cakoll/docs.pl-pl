---
title: Debugowanie — wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: a83b1aa0b2cc068ed2f73dca04083b1085d45201
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789160"
---
# <a name="debugging-enumerations"></a>Debugowanie — wyliczenia
W tej sekcji opisano niezarządzane wyliczenia używane przez interfejs API debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [CLR_DEBUGGING_PROCESS_FLAGS, wyliczenie](clr-debugging-process-flags-enumeration.md)  
 Dostarcza wartości, które są używane przez metodę [ICLRDebugging:: OpenVirtualProcess —](iclrdebugging-openvirtualprocess-method.md) .  
  
 [CLRDataEnumMemoryFlags, wyliczenie](clrdataenummemoryflags-enumeration.md)  
 Wskazuje, które regiony pamięci są wywoływane przez wywołanie metody [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](iclrdataenummemoryregions-enummemoryregions-method.md) .  
  
 [COR_PUB_ENUMPROCESS, wyliczenie](cor-pub-enumprocess-enumeration.md)  
 Identyfikuje typ procesu do wyliczenia.  
  
 [CorDebugBlockingReason, wyliczenie](cordebugblockingreason-enumeration.md)  
 Określa przyczyny, dla których wątek może zostać zablokowany dla danego obiektu.  
  
 CorDebugChainReason  
 Wskazuje przyczynę lub przyczyny inicjacji łańcucha wywołań.  
  
 [CorDebugCodeInvokeKind, wyliczenie](cordebugcodeinvokekind-enumeration.md)  
 Opisuje sposób, w jaki wyeksportowana funkcja wywołuje kod zarządzany.  
  
 [CorDebugCodeInvokePurpose, wyliczenie](cordebugcodeinvokepurpose-enumeration.md)  
 Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.  
  
 CorDebugCreateProcessFlags  
 Zapewnia dodatkowe opcje debugowania, których można użyć w wywołaniu metody [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) .  
  
 [CorDebugDebugEventKind, wyliczenie](cordebugdebugeventkind-enumeration.md)  
 Wskazuje typ zdarzenia, którego informacje są dekodowane przez metodę [DecodeEvent](icordebugprocess6-decodeevent-method.md) .  
  
 [CorDebugDecodeEventFlagsWindows, wyliczenie](cordebugdecodeeventflagswindows-enumeration.md)  
 Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.  
  
 CorDebugExceptionCallbackType  
 Wskazuje typ wywołania zwrotnego, które jest wykonywane z [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) zdarzenia.  
  
 [CorDebugExceptionFlags, wyliczenie](cordebugexceptionflags-enumeration.md)  
 Zawiera dodatkowe informacje o wyjątku.  
  
 CorDebugExceptionUnwindCallbackType  
 Wskazuje zdarzenie, które jest sygnalizowane przez wywołanie zwrotne w fazie unwind.  
  
 [CorDebugGCType, wyliczenie](cordebuggctype-enumeration.md)  
 Wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.  
  
 [CorDebugGenerationTypes, wyliczenie](cordebuggenerationtypes-enumeration.md)  
 Określa generowanie regionu pamięci na zarządzanym stosie.  
  
 CorDebugHandleType  
 Wskazuje typ dojścia.  
  
 [CorDebugIlToNativeMappingTypes, wyliczenie](cordebugiltonativemappingtypes-enumeration.md)  
 Wskazuje, czy konkretny zakres instrukcji macierzystych odpowiada specjalnemu regionowi kodu.  
  
 CorDebugIntercept  
 Wskazuje typy kodu, do którego można wykonać te działania.  
  
 [CorDebugInterfaceVersion, wyliczenie](cordebuginterfaceversion-enumeration.md)  
 Określa wersję .NET Framework lub wersję .NET Framework, w której został wprowadzony interfejs.  
  
 CorDebugInternalFrameType  
 Identyfikuje typ ramki stosu.  
  
 [CorDebugJITCompilerFlags, wyliczenie](cordebugjitcompilerflags-enumeration.md)  
 Zawiera wartości wpływające na zachowanie kompilatora zarządzanego (just-in-Time).  
  
 [CorDebugJITCompilerFlagsDeprecated, wyliczenie](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 {1&gt;Nieaktualne.&lt;1} Zamiast tego użyj `CORDEBUG_JIT_DEFAULT` elementu członkowskiego wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) .  
  
 CorDebugMappingResult  
 Zawiera szczegółowe informacje o sposobie uzyskiwania wartości wskaźnika instrukcji (IP).  
  
 [CorDebugMDAFlags, wyliczenie](cordebugmdaflags-enumeration.md)  
 Określa stan wątku, w którym jest uruchamiany Asystent debugowania zarządzanego (MDA).  
  
 [CorDebugNGenPolicy, wyliczenie](cordebugngenpolicy-enumeration.md)  
 Zapewnia wartość określającą, czy debuger ładuje obrazy natywne (NGen) z pamięci podręcznej obrazów natywnych.  
  
 [CorDebugPlatform, wyliczenie](cordebugplatform-enumeration.md)  
 Zapewnia wartości platformy docelowej, które są używane przez metodę [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .  
  
 [CorDebugRecordFormat, wyliczenie](cordebugrecordformat-enumeration.md)  
 Opisuje format danych w tablicy bajtów, który zawiera informacje na temat natywnego zdarzenia debugowania wyjątku.  
  
 CorDebugRegister  
 Określa rejestry skojarzone z daną architekturą procesora.  
  
 [CorDebugSetContextFlag, wyliczenie](cordebugsetcontextflag-enumeration.md)  
 Wskazuje, czy kontekst pochodzi z aktywnej ramki (lub liściowej) na stosie czy został obliczony przez odróżnienie od innej ramki.  
  
 [CorDebugStateChange, wyliczenie](cordebugstatechange-enumeration.md)  
 Opisuje ilość danych buforowanych, które muszą zostać odrzucone na podstawie zmian w procesie.  
  
 CorDebugStepReason  
 Wskazuje wynik pojedynczego kroku.  
  
 CorDebugThreadState  
 Określa stan wątku do debugowania.  
  
 \>CorDebugUnmappedStop  
 Określa typ niezamapowanego kodu, który może wyzwolić zatrzymanie w wykonaniu kodu przez stepper.  
  
 CorDebugUserState  
 Wskazuje stan użytkownika wątku.  
  
 [CorGCReferenceType, wyliczenie](corgcreferencetype-enumeration.md)  
 Określa źródło obiektu, które ma zostać pobrane jako elementy bezużyteczne.  
  
 [ILCodeKind, wyliczenie](ilcodekind-enumeration.md)  
 Zawiera wartości, które określają, czy debuger może uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w instrumentacji profilera ReJIT.  
  
 [LoggingLevelEnum, wyliczenie](logginglevelenum-enumeration.md)  
 Wskazuje poziom ważności komunikatu opisowego, który jest zapisywana w dzienniku zdarzeń, gdy zarządzany wątek rejestruje zdarzenie.  
  
 [LogSwitchCallReason, wyliczenie](logswitchcallreason-enumeration.md)  
 Wskazuje operację wykonywaną na przełączniku debugowania/śledzenia.  
  
 [VariableLocationType, wyliczenie](variablelocationtype-enumeration.md)  
 Wskazuje typ lokalizacji natywnej zmiennej.  
  
 [WriteableMetadataUpdateMode, wyliczenie](writeablemetadataupdatemode-enumeration.md)  
 Zawiera wartości, które określają, czy aktualizacje w pamięci mają być widoczne dla debugera. 

 [ClrDataSourceType, Wyliczenie](clrdatasourcetype-enumeration.md) Dostarcza wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.

## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](debugging-coclasses.md)  
  
 [Debugowanie, interfejsy](debugging-interfaces.md)  
  
 [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)  
  
 [Struktury debugowania](debugging-structures.md)
