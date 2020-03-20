---
title: CorDebugInterfaceVersion — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
ms.openlocfilehash: 5ebbbf01bc27974850c7e0bb3591b8f050fd0579
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179274"
---
# <a name="cordebuginterfaceversion-enumeration"></a>CorDebugInterfaceVersion — Wyliczenie
Określa interfejs, wersję programu .NET Framework lub wersję programu .NET Framework, w której wprowadzono interfejs.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 Poniższa tabela zawiera łącza z każdej wartości wyliczenia do odpowiedniego interfejsu. Ponadto tabela wskazuje pierwszą wersję programu .NET Framework, w których interfejs był obsługiwany.  
  
|Członek|Określa|Wersja programu .NET Framework|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|Wersja programu .NET Framework jest nieprawidłowa.|-|  
|`CorDebugVersion_1_0`|Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 1.0.|1.0|  
|`CorDebugVersion_1_1`|Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 1.1.|1.1|  
|`CorDebugVersion_2_0`|Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 2.0.|2.0|  
|`CorDebugVersion_4_0`|Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 4.|4|  
|`CorDebugVersion_4_5`|Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest 4.5.|4.5|  
|`ver_ICorDebugManagedCallback`|[ICorDebugManagedCallback (Powrót do łączenia)](icordebugmanagedcallback-interface.md)|1.0|  
|`ver_ICorDebugUnmanagedCallback`|[ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)|1.0|  
|`ver_ICorDebug`|[Icordebug](icordebug-interface.md)|1.0|  
|`ver_ICorDebugController`|[Kontroler ICorDebug](icordebugcontroller-interface.md)|1.0|  
|`ver_ICorDebugAppDomain`|[Domena ICorDebugApp](icordebugappdomain-interface.md)|1.0|  
|`ver_ICorDebugAssembly`|[ICorDebugAssembly](icordebugassembly-interface.md)|1.0|  
|`ver_ICorDebugProcess`|[Icordebugprocess](icordebugprocess-interface.md)|1.0|  
|`ver_ICorDebugBreakpoint`|[Icordebugbreakpoint](icordebugbreakpoint-interface.md)|1.0|  
|`ver_ICorDebugFunctionBreakpoint`|[ICorDebugFunctionBreakpoint (Punkt przerwania)](icordebugfunctionbreakpoint-interface.md)|1.0|  
|`ver_ICorDebugModuleBreakpoint`|[ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)|1.0|  
|`ver_ICorDebugValueBreakpoint`|[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)|1.0|  
|`ver_ICorDebugStepper`|[ICorDebugStepper (ICorDebugStepper)](icordebugstepper-interface.md)|1.0|  
|`ver_ICorDebugRegisterSet`|[Zestaw rejestrów ICorDebug](icordebugregisterset-interface.md)|1.0|  
|`ver_ICorDebugThread`|[Icordebugthread](icordebugthread-interface.md)|1.0|  
|`ver_ICorDebugChain`|[ICorDebugChain (ICorDebugChain)](icordebugchain-interface.md)|1.0|  
|`ver_ICorDebugFrame`|[Icordebugframe](icordebugframe-interface.md)|1.0|  
|`ver_ICorDebugILFrame`|[Ramka ICorDebugILFrame](icordebugilframe-interface.md)|1.0|  
|`ver_ICorDebugNativeFrame`|[Ramka ICorDebugNativeFrame](icordebugnativeframe-interface.md)|1.0|  
|`ver_ICorDebugModule`|[ICorDebugModule](icordebugmodule-interface.md)|1.0|  
|`ver_ICorDebugFunction`|[Icordebugfunction](icordebugfunction-interface1.md)|1.0|  
|`ver_ICorDebugCode`|[Icordebugcode](icordebugcode-interface1.md)|1.0|  
|`ver_ICorDebugClass`|[Icordebugclass](icordebugclass-interface.md)|1.0|  
|`ver_ICorDebugEval`|[ICorDebugZawal](icordebugeval-interface.md)|1.0|  
|`ver_ICorDebugValue`|[Icordebugvalue](icordebugvalue-interface.md)|1.0|  
|`ver_ICorDebugGenericValue`|[ICorDebugGenericValue](icordebuggenericvalue-interface.md)|1.0|  
|`ver_ICorDebugReferenceValue`|[ICorDebugReferenceValue](icordebugreferencevalue-interface.md)|1.0|  
|`ver_ICorDebugHeapValue`|[ICorDebugHeapValue](icordebugheapvalue-interface.md)|1.0|  
|`ver_ICorDebugObjectValue`|[ICorDebugObjectValue](icordebugobjectvalue-interface.md)|1.0|  
|`ver_ICorDebugBoxValue`|[ICorDebugBoxValue](icordebugboxvalue-interface.md)|1.0|  
|`ver_ICorDebugStringValue`|[ICorDebugStringValue](icordebugstringvalue-interface.md)|1.0|  
|`ver_ICorDebugArrayValue`|[ICorDebugArrayValue](icordebugarrayvalue-interface.md)|1.0|  
|`ver_ICorDebugContext`|[ICorDebugKontekst](icordebugcontext-interface.md)|1.0|  
|`ver_ICorDebugEnum`|[Icordebugenum](icordebugenum-interface1.md)|1.0|  
|`ver_ICorDebugObjectEnum`|[ICorDebugObjectEnum](icordebugobjectenum-interface.md)|1.0|  
|`ver_ICorDebugBreakpointEnum`|[ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)|1.0|  
|`ver_ICorDebugStepperEnum`|[ICorDebugStepperEnum](icordebugstepperenum-interface.md)|1.0|  
|`ver_ICorDebugProcessEnum`|[ICorDebugProcessEnum](icordebugprocessenum-interface.md)|1.0|  
|`ver_ICorDebugThreadEnum`|[ICorDebugThreadEnum](icordebugthreadenum-interface1.md)|1.0|  
|`ver_ICorDebugFrameEnum`|[ICorDebugFrameEnum ( ICorDebugFrameEnum )](icordebugframeenum-interface.md)|1.0|  
|`ver_ICorDebugChainEnum`|[ICorDebugChainEnum](icordebugchainenum-interface.md)|1.0|  
|`ver_ICorDebugModuleEnum`|[ICorDebugModuleEnum](icordebugmoduleenum-interface.md)|1.0|  
|`ver_ICorDebugValueEnum`|[ICorDebugValueEnum](icordebugvalueenum-interface.md)|1.0|  
|`ver_ICorDebugCodeEnum`|[Kod ICorDebug](icordebugcodeenum-interface.md)|1.0|  
|`ver_ICorDebugTypeEnum`|[ICorDebugTypeEnum ( ICorDebugTypeEnum )](icordebugtypeenum-interface.md)|1.0|  
|`ver_ICorDebugErrorInfoEnum`|[ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)|1.0|  
|`ver_ICorDebugAppDomainEnum`|[ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)|1.0|  
|`ver_ICorDebugAssemblyEnum`|[ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)|1.0|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)|1.0|  
|`ver_ICorDebugEditAndContinueSnapshot`|[ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)|1.0|  
|`ver_ICorDebugManagedCallback2`|[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)|2.0|  
|`ver_ICorDebugAppDomain2`|[Domena ICorDebugApp2](icordebugappdomain2-interface.md)|2.0|  
|`ver_ICorDebugProcess2`|[ICorDebugProcess2](icordebugprocess2-interface1.md)|2.0|  
|`ver_ICorDebugStepper2`|[ICorDebugStepper2](icordebugstepper2-interface1.md)|2.0|  
|`ver_ICorDebugRegisterSet2`|[ICorDebugRegisterSet2](icordebugregisterset2-interface.md)|2.0|  
|`ver_ICorDebugThread2`|[ICorDebugNastawa2](icordebugthread2-interface.md)|2.0|  
|`ver_ICorDebugILFrame2`|[Klatka ICorDebugIL2](icordebugilframe2-interface.md)|2.0|  
|`ver_ICorDebugModule2`|[ICorDebugModule2](icordebugmodule2-interface.md)|2.0|  
|`ver_ICorDebugFunction2`|[ICorDebugFunction2](icordebugfunction2-interface.md)|2.0|  
|`ver_ICorDebugCode2`|[Kod ICorDebugCode2](icordebugcode2-interface.md)|2.0|  
|`ver_ICorDebugClass2`|"ICorDebugClass2"|2.0|  
|`ver_ICorDebugValue2`|"ICorDebugValue2"|2.0|  
|`ver_ICorDebugEval2`|"ICorDebugEval2".|2.0|  
|`ver_ICorDebugObjectValue2`|"ICorDebugObjectValue2"|2.0|  
|`ver_ICorDebugThread3`|[ICorDebugNastawa3](icordebugthread3-interface.md)|4|  
|`ver_ICorDebugThread4`|[ICorDebugNajuż](icordebugthread4-interface.md)|4|  
|`ver_ICorDebugStackWalk`|[Icordebugstackwalk](icordebugstackwalk-interface.md)|4|  
|`ver_ICorDebugNativeFrame2`|[Ramka ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)|4|  
|`ver_ICorDebugInternalFrame2`|[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)|4|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[ICorDebugRuntimeUnwindableFrame](icordebugruntimeunwindableframe-interface.md)|4|  
|`ver_ICorDebugHeapValue3`|[ICorDebugHeapValue3, interfejs](icordebugheapvalue3-interface.md)|4|  
|`ver_ICorDebugBlockingObjectEnum`|[ICorDebugBlockingObjectEnum, interfejs](icordebugblockingobjectenum-interface.md)|4|  
|`ver_ICorDebugValue3`|[ICorDebugValue3](icordebugvalue3-interface.md)|4|  
|`ver_ICorDebugComObjectValue`|[ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)|4.5|  
|`ver_ICorDebugAppDomain3`|[Domena ICorDebugAppDomain3](icordebugappdomain3-interface.md)|4.5|  
|`ver_ICorDebugCode3`|[Kod ICorDebugCode3](icordebugcode3-interface.md)|4.5|  
|`ver_ICorDebugILFrame3`|[ICorDebugILFrame3](icordebugilframe3-interface.md)|4.5|  
|`CorDebugLatestVersion`|Wersja programu .NET Framework, w tym wszystkie dodatki Service Pack, jest najnowszą wersją.|-|  
  
## <a name="remarks"></a>Uwagi  
 Debuger może użyć `CorDebugInterfaceVersion` wyliczenia w [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkcji, aby określić najwyższą wersję .NET Framework, który obsługuje debuger.  
  
## <a name="interface-names"></a>Nazwy interfejsów  
 Numer, który pojawia się na końcu nazw interfejsu w debugowaniu interfejsu API `ICorDebugThread3`(na przykład "3" w ) określa wersję interfejsu, a nie wersję .NET Framework. Wszystkie nazwy interfejsów w debugowaniu interfejsu API zawierają numery wersji z wyjątkiem interfejsów, które zostały wprowadzone w wersji .NET Framework w wersji 1. Wszelka korespondencja między numerami wersji interfejsu and.NET numerami wersji Framework są przypadkowe.  
  
- Interfejsy, które zostały wprowadzone w .NET Framework w wersji 1.0 nie zawierają liczby, ponieważ wszystkie są one niejawnie w wersji 1.  
  
- Program .NET Framework w wersji 1.1 używa interfejsów w wersji 1.0 i nie wprowadza żadnych nowych interfejsów debugowania.  
  
- 14 interfejsów debugowania wprowadzonych w wersji .NET Framework 2.0 są logicznymi rozszerzeniami ich odpowiedników w wersji 1 i zawierają liczbę "2" w ich nazwach.  
  
- Program .NET Framework w wersjach 3.0 i 3.5 korzysta z istniejących interfejsów .NET Framework 2.0 i nie wprowadza żadnych nowych interfejsów.  
  
- .NET Framework 4 wprowadza kombinację wersji interfejsu. Na przykład `ICorDebugThread3` zarówno `ICorDebugThread4` i pojawiają się jako `ICorDebugThread` trzecia i czwarta wersja interfejsu. .NET Framework 4 wprowadza również pierwszą `ICorDebugStackWalk` wersję interfejsu i `ICorDebugNativeFrame` drugą`ICorDebugNativeFrame2`wersję interfejsu ( ).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie, wyliczenia](debugging-enumerations.md)
