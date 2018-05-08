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
ms.openlocfilehash: b81e7c2ffabdee78af34d00c48fb29c7525dea08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-enumerations"></a>Debugowanie — wyliczenia
W tej sekcji opisano niezarządzane wyliczenia, które używa interfejsu API debugowania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [CLR_DEBUGGING_PROCESS_FLAGS, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Udostępnia wartości, które są używane przez [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.  
  
 [CLRDataEnumMemoryFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Wskazuje, które regiony pamięci wywołanie [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) metoda powinna zawierać.  
  
 [COR_PUB_ENUMPROCESS, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Określa typ procesu, które mają zostać wyliczone.  
  
 [CorDebugBlockingReason, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Określa przyczyny, dlaczego wątek może stać się zablokowane na dany obiekt.  
  
 CorDebugChainReason  
 Wskazuje powód lub powody rozpoczęcia łańcuch wywołań.  
  
 [CorDebugCodeInvokeKind, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 W tym artykule opisano, jak wyeksportowanej funkcji wywołuje kodu zarządzanego.  
  
 [CorDebugCodeInvokePurpose, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Opisuje, dlaczego wyeksportowanej funkcji wywołania kodu zarządzanego.  
  
 CorDebugCreateProcessFlags  
 Udostępnia dodatkowe opcje debugowania, które mogą być używane w wywołaniu [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.  
  
 [CorDebugDebugEventKind, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 Wskazuje typ zdarzenia, których dane są dekodowane przez [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.  
  
 [CorDebugDecodeEventFlagsWindows, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Zawiera dodatkowe informacje o zdarzeniach debugowania na platformie systemu Windows.  
  
 CorDebugExceptionCallbackType  
 Wskazuje typ wywołania zwrotnego, które zostało utworzone z [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) zdarzeń.  
  
 [CorDebugExceptionFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Zawiera dodatkowe informacje o wyjątku.  
  
 CorDebugExceptionUnwindCallbackType  
 Wskazuje sygnalizowane trwa przez wywołanie zwrotne w fazie unwind zdarzenie.  
  
 [CorDebugGCType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Wskazuje, czy moduł zbierający elementy bezużyteczne jest uruchomiona na serwerze lub stacji roboczej.  
  
 [CorDebugGenerationTypes, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Określa Generowanie obszaru pamięci na stercie zarządzanej.  
  
 CorDebugHandleType  
 Wskazuje typ dojścia.  
  
 [CorDebugIlToNativeMappingTypes, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Wskazuje, czy określony zakres natywnego instrukcje odpowiada specjalne kodu regionu.  
  
 CorDebugIntercept  
 Wskazuje typy kodu, które można podjąć w.  
  
 [CorDebugInterfaceVersion, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 Określa wersję systemu .NET Framework lub wersji programu .NET Framework, w którym wprowadzono interfejs.  
  
 CorDebugInternalFrameType  
 Określa typ ramki stosu.  
  
 [CorDebugJITCompilerFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Zawiera wartości, które wpływają na zachowanie zarządzanych kompilatora just in time (JIT).  
  
 [CorDebugJITCompilerFlagsDeprecated, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Nieaktualne. Użyj `CORDEBUG_JIT_DEFAULT` członkiem [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenie zamiast tego.  
  
 CorDebugMappingResult  
 Zawiera szczegółowe informacje o sposobie uzyskano wartość wskaźnika instrukcji (IP).  
  
 [CorDebugMDAFlags, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Określa stan wątku, na którym jest uruchamiany zarządzany Asystent debugowania (MDA).  
  
 [CorDebugNGenPolicy, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Zawiera wartość, która określa, czy debuger ładuje obrazów natywnych (NGen) z pamięci podręcznej obrazów natywnych.  
  
 [CorDebugPlatform, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Udostępnia wartości platform docelowych, które są używane przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.  
  
 [CorDebugRecordFormat, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Opisuje format danych w tablicy bajtów, który zawiera informacje dotyczące zdarzenia debugowania natywnego wyjątek.  
  
 CorDebugRegister  
 Określa, rejestruje skojarzony z danym procesor.  
  
 [CorDebugSetContextFlag, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Wskazuje, czy kontekst jest z aktywnego (lub typu liść) ramek na stosie lub został obliczony przy odwijanie od innej ramki.  
  
 [CorDebugStateChange, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.  
  
 CorDebugStepReason  
 Wskazuje wynik pojedynczego kroku.  
  
 CorDebugThreadState  
 Określa stan wątku do debugowania.  
  
 \>CorDebugUnmappedStop  
 Określa typ Niemapowane kodu, które mogą wyzwalać zatrzymania wykonywania kodu przez stepper.  
  
 CorDebugUserState  
 Wskazuje stan użytkownika wątku.  
  
 [CorGCReferenceType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Określa źródło obiektu być zbierane z pamięci.  
  
 [ILCodeKind, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Zawiera wartości, które określają, czy debuger jest w stanie uzyskać dostęp do zmiennych lokalnych lub kodzie dodanym w ReJIT Instrumentacji profilera.  
  
 [LoggingLevelEnum, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Wskazuje poziom ważności opisowym komunikatem, które są zapisywane w dzienniku zdarzeń, gdy zarządzanego wątku rejestruje zdarzenie.  
  
 [LogSwitchCallReason, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Wskazuje działanie zostało wykonane na przełączniku debugowania śledzenia.  
  
 [VariableLocationType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Wskazuje typ macierzysty lokalizacji zmiennej.  
  
 [WriteableMetadataUpdateMode, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Zawiera wartości, które określają, czy aktualizacje metadanych w pamięci są widoczne dla debugera.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
