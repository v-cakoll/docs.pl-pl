---
title: Debugowanie — wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5edd6dfb3dac05ce4614c43949f2ec4c19b5f742
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698515"
---
# <a name="debugging-enumerations"></a>Debugowanie — wyliczenia
W tej sekcji opisano niezarządzane wyliczenia, których używa interfejsu API debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [CLR_DEBUGGING_PROCESS_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Zawiera wartości, które są używane przez [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.  
  
 [CLRDataEnumMemoryFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Wskazuje, które regiony pamięci wywołanie [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) powinna zawierać metodę.  
  
 [COR_PUB_ENUMPROCESS, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Identyfikuje typ procesu do wyliczenia.  
  
 [CorDebugBlockingReason, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Określa przyczyny, dlaczego wątek może stać się zablokowany dla danego obiektu.  
  
 CorDebugChainReason  
 Wskazuje powód lub powody do rozpoczęcia łańcuch wywołań.  
  
 [CorDebugCodeInvokeKind, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 W tym artykule opisano, jak eksportowanych funkcji wywołuje kod zarządzany.  
  
 [CorDebugCodeInvokePurpose, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 W tym artykule opisano, dlaczego eksportowanych funkcji wywołuje kod zarządzany.  
  
 CorDebugCreateProcessFlags  
 Zapewnia dodatkowe opcje debugowania, które mogą być używane w wywołaniu [icordebug::CreateProcess —](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.  
  
 [CorDebugDebugEventKind, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 Określa typ zdarzenia, o których informacje jest dekodowana przy [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.  
  
 [CorDebugDecodeEventFlagsWindows, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.  
  
 CorDebugExceptionCallbackType  
 Wskazuje typ wywołanie zwrotne, które zostało wprowadzone przy użyciu [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) zdarzeń.  
  
 [CorDebugExceptionFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Zawiera dodatkowe informacje o wyjątku.  
  
 CorDebugExceptionUnwindCallbackType  
 Określa zdarzenie, które jest jest sygnalizowane przez wywołania zwrotnego w fazie unwind.  
  
 [CorDebugGCType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Wskazuje, czy moduł garbage collector jest uruchomiona na serwerze lub stacji roboczej.  
  
 [CorDebugGenerationTypes, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Określa Generowanie region pamięci na stosie zarządzanym.  
  
 CorDebugHandleType  
 Wskazuje typ uchwytu.  
  
 [CorDebugIlToNativeMappingTypes, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Wskazuje, czy określony zakres natywne instrukcje odnosi się do regionu specjalny kod.  
  
 CorDebugIntercept  
 Wskazuje typy kodu, który może być zmieniana w.  
  
 [CorDebugInterfaceVersion, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 Określa wersję programu .NET Framework lub wersji programu .NET Framework, w której wprowadzono interfejs.  
  
 CorDebugInternalFrameType  
 Określa typ ramki stosu.  
  
 [CorDebugJITCompilerFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Zawiera wartości, które wpływają na zachowanie zarządzanych kompilator just-in-time (JIT).  
  
 [CorDebugJITCompilerFlagsDeprecated, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Nieaktualne. Użyj `CORDEBUG_JIT_DEFAULT` członkiem [cordebugjitcompilerflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenia zamiast tego.  
  
 CorDebugMappingResult  
 Zawiera szczegółowe informacje, jak uzyskać była wartość wskaźnika instrukcji (IP).  
  
 [CorDebugMDAFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Określa stan wątku, na którym jest uruchamiany zarządzanego Asystenta debugowania (MDA).  
  
 [CorDebugNGenPolicy, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Zawiera wartość określającą, czy debuger wczytuje obrazów macierzystych (NGen) z pamięci podręcznej obrazów natywnych.  
  
 [CorDebugPlatform, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Udostępnia wartości platformy docelowe, które są używane przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.  
  
 [CorDebugRecordFormat, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 W tym artykule opisano format danych w tablicy bajtowej, zawierający informacje o zdarzeniu debugowania natywnych wyjątku.  
  
 CorDebugRegister  
 Określa rejestrów związane z architekturą procesora w danym.  
  
 [CorDebugSetContextFlag, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Wskazuje, czy kontekst jest z aktywnej (lub liścia) ramek na stosie lub obliczeniu, odwijanie od innej ramki.  
  
 [CorDebugStateChange, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.  
  
 CorDebugStepReason  
 Wskazuje wynik pojedynczego kroku.  
  
 CorDebugThreadState  
 Określa stan wątku do debugowania.  
  
 \>CorDebugUnmappedStop  
 Określa typ niezamapowane kod, który możesz wyzwolić stepper zatrzymania wykonywania kodu.  
  
 CorDebugUserState  
 Wskazuje stan wątku użytkownika.  
  
 [CorGCReferenceType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Określa źródło obiektu zebranych elementów bezużytecznych.  
  
 [ILCodeKind, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Zawiera wartości, które określają, czy debuger jest w stanie uzyskać dostęp do zmiennych lokalnych lub kodzie dodanym w profilerze ReJIT instrumentacji.  
  
 [LoggingLevelEnum, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Wskazuje poziom ważności opisowy komunikat, który jest zapisywany w dzienniku zdarzeń, gdy wątków zarządzanych rejestruje zdarzenie.  
  
 [LogSwitchCallReason, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Określa operację, która została wykonana w przełączniku debugowanie śledzenia.  
  
 [VariableLocationType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Wskazuje typ lokalizacji natywnych zmienną.  
  
 [WriteableMetadataUpdateMode, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Zawiera wartości, które określają, czy aktualizacje metadanych w pamięci są widoczne dla debugera. 

 [Wyliczenie ClrDataSourceType](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) zawiera wartości, które są używane przez strukturę CLRDATA_IL_ADDRESS_MAP.

## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
