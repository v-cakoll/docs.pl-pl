---
title: Debugowanie — wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 7948b78da1db5267ce53364af1e4a26ff73801e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124328"
---
# <a name="debugging-enumerations"></a>Debugowanie — wyliczenia
W tej sekcji opisano niezarządzane wyliczenia używane przez interfejs API debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [CLR_DEBUGGING_PROCESS_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Dostarcza wartości, które są używane przez metodę [ICLRDebugging:: OpenVirtualProcess —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) .  
  
 [CLRDataEnumMemoryFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Wskazuje, które regiony pamięci są wywoływane przez wywołanie metody [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) .  
  
 [COR_PUB_ENUMPROCESS, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Identyfikuje typ procesu do wyliczenia.  
  
 [CorDebugBlockingReason, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Określa przyczyny, dla których wątek może zostać zablokowany dla danego obiektu.  
  
 CorDebugChainReason —  
 Wskazuje przyczynę lub przyczyny inicjacji łańcucha wywołań.  
  
 [CorDebugCodeInvokeKind, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Opisuje sposób, w jaki wyeksportowana funkcja wywołuje kod zarządzany.  
  
 [CorDebugCodeInvokePurpose, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.  
  
 CorDebugCreateProcessFlags —  
 Zapewnia dodatkowe opcje debugowania, których można użyć w wywołaniu metody [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) .  
  
 [CorDebugDebugEventKind, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 Wskazuje typ zdarzenia, którego informacje są dekodowane przez metodę [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) .  
  
 [CorDebugDecodeEventFlagsWindows, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.  
  
 CorDebugExceptionCallbackType —  
 Wskazuje typ wywołania zwrotnego, które jest wykonywane z [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) zdarzenia.  
  
 [CorDebugExceptionFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Zawiera dodatkowe informacje o wyjątku.  
  
 CorDebugExceptionUnwindCallbackType —  
 Wskazuje zdarzenie, które jest sygnalizowane przez wywołanie zwrotne w fazie unwind.  
  
 [CorDebugGCType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Wskazuje, czy moduł wyrzucania elementów bezużytecznych jest uruchomiony na stacji roboczej lub na serwerze.  
  
 [CorDebugGenerationTypes, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Określa generowanie regionu pamięci na zarządzanym stosie.  
  
 CorDebugHandleType —  
 Wskazuje typ dojścia.  
  
 [CorDebugIlToNativeMappingTypes, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Wskazuje, czy konkretny zakres instrukcji macierzystych odpowiada specjalnemu regionowi kodu.  
  
 CorDebugIntercept —  
 Wskazuje typy kodu, do którego można wykonać te działania.  
  
 [CorDebugInterfaceVersion, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 Określa wersję .NET Framework lub wersję .NET Framework, w której został wprowadzony interfejs.  
  
 CorDebugInternalFrameType —  
 Identyfikuje typ ramki stosu.  
  
 [CorDebugJITCompilerFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Zawiera wartości wpływające na zachowanie kompilatora zarządzanego (just-in-Time).  
  
 [CorDebugJITCompilerFlagsDeprecated, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Nieaktualne. Zamiast tego użyj `CORDEBUG_JIT_DEFAULT` elementu członkowskiego wyliczenia [CorDebugJITCompilerFlags —](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .  
  
 CorDebugMappingResult —  
 Zawiera szczegółowe informacje o sposobie uzyskiwania wartości wskaźnika instrukcji (IP).  
  
 [CorDebugMDAFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Określa stan wątku, w którym jest uruchamiany Asystent debugowania zarządzanego (MDA).  
  
 [CorDebugNGenPolicy, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Zapewnia wartość określającą, czy debuger ładuje obrazy natywne (NGen) z pamięci podręcznej obrazów natywnych.  
  
 [CorDebugPlatform, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Zapewnia wartości platformy docelowej, które są używane przez metodę [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .  
  
 [CorDebugRecordFormat, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Opisuje format danych w tablicy bajtów, który zawiera informacje na temat natywnego zdarzenia debugowania wyjątku.  
  
 CorDebugRegister —  
 Określa rejestry skojarzone z daną architekturą procesora.  
  
 [CorDebugSetContextFlag, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Wskazuje, czy kontekst pochodzi z aktywnej ramki (lub liściowej) na stosie czy został obliczony przez odróżnienie od innej ramki.  
  
 [CorDebugStateChange, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 Opisuje ilość danych buforowanych, które muszą zostać odrzucone na podstawie zmian w procesie.  
  
 CorDebugStepReason —  
 Wskazuje wynik pojedynczego kroku.  
  
 CorDebugThreadState —  
 Określa stan wątku do debugowania.  
  
 \>CorDebugUnmappedStop —  
 Określa typ niezamapowanego kodu, który może wyzwolić zatrzymanie w wykonaniu kodu przez stepper.  
  
 CorDebugUserState —  
 Wskazuje stan użytkownika wątku.  
  
 [CorGCReferenceType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Określa źródło obiektu, które ma zostać pobrane jako elementy bezużyteczne.  
  
 [ILCodeKind, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Zawiera wartości, które określają, czy debuger może uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w instrumentacji profilera ReJIT.  
  
 [LoggingLevelEnum, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Wskazuje poziom ważności komunikatu opisowego, który jest zapisywana w dzienniku zdarzeń, gdy zarządzany wątek rejestruje zdarzenie.  
  
 [LogSwitchCallReason, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Wskazuje operację wykonywaną na przełączniku debugowania/śledzenia.  
  
 [VariableLocationType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Wskazuje typ lokalizacji natywnej zmiennej.  
  
 [WriteableMetadataUpdateMode, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Zawiera wartości, które określają, czy aktualizacje w pamięci mają być widoczne dla debugera. 

 [ClrDataSourceType, Wyliczenie](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Dostarcza wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.

## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
