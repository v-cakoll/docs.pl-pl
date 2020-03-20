---
title: Debugowanie — wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: c37b6ff42b428184d301d63b6dbbd9d80a72bf3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179138"
---
# <a name="debugging-enumerations"></a>Debugowanie — wyliczenia
W tej sekcji opisano niezarządzane wyliczenia używane przez debugowanie interfejsu API.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [CLR_DEBUGGING_PROCESS_FLAGS, wyliczenie](clr-debugging-process-flags-enumeration.md)  
 Zawiera wartości, które są używane przez [metodę ICLRDebugging::OpenVirtualProcess.](iclrdebugging-openvirtualprocess-method.md)  
  
 [CLRDataEnumMemoryFlags — Wyliczenie](clrdataenummemoryflags-enumeration.md)  
 Wskazuje, które regiony pamięci wywołać [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) metoda powinna zawierać.  
  
 [COR_PUB_ENUMPROCESS, wyliczenie](cor-pub-enumprocess-enumeration.md)  
 Identyfikuje typ procesu, który ma być wyliczony.  
  
 [CorDebugBlockingReason, wyliczenie](cordebugblockingreason-enumeration.md)  
 Określa powody, dla których wątek może zostać zablokowany na danym obiekcie.  
  
 CorDebugChainReason  
 Wskazuje przyczynę lub przyczyny rozpoczęcia łańcucha wywołań.  
  
 [Wyliczenie CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md)  
 W tym artykule opisano, jak wyeksportowana funkcja wywołuje kod zarządzany.  
  
 [CorDebugCodeInvokePurpose, wyliczenie](cordebugcodeinvokepurpose-enumeration.md)  
 Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.  
  
 CorDebugCreateProcessFlags  
 Udostępnia dodatkowe opcje debugowania, które mogą być używane w wywołaniu [metody ICorDebug::CreateProcess.](icordebug-createprocess-method.md)  
  
 [CorDebugDebugEventKind, wyliczenie](cordebugdebugeventkind-enumeration.md)  
 Wskazuje typ zdarzenia, którego informacje są dekodowane przez [DecodeEvent](icordebugprocess6-decodeevent-method.md) metody.  
  
 [Wyliczenie CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md)  
 Zawiera dodatkowe informacje dotyczące zdarzeń debugowania na platformie Windows.  
  
 CorDebugExceptionCallbackType  
 Wskazuje typ wywołania zwrotnego, który jest wykonany ze zdarzenia [ICorDebugManagedCallback2::Exception.](icordebugmanagedcallback2-exception-method.md)  
  
 [CorDebugExceptionFlags — Wyliczenie](cordebugexceptionflags-enumeration.md)  
 Zawiera dodatkowe informacje o wyjątku.  
  
 CorDebugExceptionUnwindCallbackType  
 Wskazuje zdarzenie, które jest sygnalizowane przez wywołanie zwrotne podczas fazy unwind.  
  
 [CorDebugGCType, wyliczenie](cordebuggctype-enumeration.md)  
 Wskazuje, czy moduł zbierający elementy bezużyteczne jest uruchomiony na stacji roboczej lub serwera.  
  
 [CorDebugGenerationTypes, wyliczenie](cordebuggenerationtypes-enumeration.md)  
 Określa generowanie regionu pamięci na zarządzanym stosie.  
  
 CorDebugHandleType  
 Wskazuje typ uchwytu.  
  
 [CorDebugIlToNativeMappingTypes, wyliczenie](cordebugiltonativemappingtypes-enumeration.md)  
 Wskazuje, czy określony zakres instrukcji natywnych odpowiada specjalnemu regionowi kodu.  
  
 CorDebugIntercept  
 Wskazuje typy kodu, do których można wejść.  
  
 [CorDebugInterfaceVersion, wyliczenie](cordebuginterfaceversion-enumeration.md)  
 Określa wersję programu .NET Framework lub wersję programu .NET Framework, w której wprowadzono interfejs.  
  
 CorDebugInternalFrameType  
 Identyfikuje typ ramki stosu.  
  
 [CorDebugJITCompilerFlags, wyliczenie](cordebugjitcompilerflags-enumeration.md)  
 Zawiera wartości, które wpływają na zachowanie kompilatora zarządzanego just-in-time (JIT).  
  
 [CorDebugJITCompilerFlagsDeprecated, wyliczenie](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Nieaktualne. Zamiast `CORDEBUG_JIT_DEFAULT` tego należy użyć elementu członkowskiego [wyliczenia CorDebugJITCompilerFlags.](cordebugjitcompilerflags-enumeration.md)  
  
 CorDebugMappingResult  
 Zawiera szczegółowe informacje o tym, jak uzyskano wartość wskaźnika instrukcji (IP).  
  
 [CorDebugMDAFlags — Wyliczenie](cordebugmdaflags-enumeration.md)  
 Określa stan wątku, na którym jest uruchamiany asystent debugowania zarządzanego (MDA).  
  
 [CorDebugNGenPolicy, wyliczenie](cordebugngenpolicy-enumeration.md)  
 Zapewnia wartość, która określa, czy debuger ładuje natywne obrazy (NGen) z pamięci podręcznej obrazu macierzystego.  
  
 [CorDebugPlatform, wyliczenie](cordebugplatform-enumeration.md)  
 Zawiera wartości platformy docelowej, które są używane przez [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) metody.  
  
 [Wyliczenie CorDebugRecordFormat](cordebugrecordformat-enumeration.md)  
 Opisuje format danych w tablicy bajtów, który zawiera informacje o zdarzeniu debugowania wyjątków natywnych.  
  
 Rejestr CorDebug  
 Określa rejestry skojarzone z daną architekturą procesora.  
  
 [CorDebugSetContextFlag, wyliczenie](cordebugsetcontextflag-enumeration.md)  
 Wskazuje, czy kontekst pochodzi z aktywnej (lub liścia) ramki na stosie lub został obliczony przez odwijanie z innej ramki.  
  
 [CorDebugStateChange, wyliczenie](cordebugstatechange-enumeration.md)  
 W tym artykule opisano ilość danych w pamięci podręcznej, które muszą zostać odrzucone na podstawie zmian w procesie.  
  
 CorDebugStepReason  
 Wskazuje wynik pojedynczego kroku.  
  
 CorDebugStan  
 Określa stan wątku do debugowania.  
  
 \>CorDebugUnmappedStop  
 Określa typ niezamapowanego kodu, który może wyzwolić zatrzymanie w wykonaniu kodu przez stepper.  
  
 Stan CorDebugUser  
 Wskazuje stan użytkownika wątku.  
  
 [CorGCReferenceType, wyliczenie](corgcreferencetype-enumeration.md)  
 Identyfikuje źródło obiektu, który ma być zbierany z modułem.  
  
 [ILCodeKind, wyliczenie](ilcodekind-enumeration.md)  
 Zawiera wartości, które określają, czy debuger jest w stanie uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w profiler Instrumentacji ReJIT.  
  
 [LoggingLevelEnum — Wyliczenie](logginglevelenum-enumeration.md)  
 Wskazuje poziom ważności opisowego komunikatu, który jest zapisywany w dzienniku zdarzeń, gdy zarządzany wątek rejestruje zdarzenie.  
  
 [LogSwitchCallReason, wyliczenie](logswitchcallreason-enumeration.md)  
 Wskazuje operację, która została wykonana na debugowania/śledzenia przełącznika.  
  
 [VariableLocationType, wyliczenie](variablelocationtype-enumeration.md)  
 Wskazuje natywny typ lokalizacji zmiennej.  
  
 [Wyliczenie WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md)  
 Zawiera wartości, które określają, czy aktualizacje metadane w pamięci są widoczne dla debugera.

 [Wyliczanie clrDataSourceType](clrdatasourcetype-enumeration.md) Zawiera wartości, które są używane przez CLRDATA_IL_ADDRESS_MAP struktury.

## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](debugging-coclasses.md)  
  
 [Debugowanie — Interfejsy](debugging-interfaces.md)  
  
 [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)  
  
 [Struktury debugowania](debugging-structures.md)
