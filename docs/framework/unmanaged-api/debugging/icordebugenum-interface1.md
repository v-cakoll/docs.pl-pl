---
title: ICorDebugEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: 59dcb7ae6f27f8d049cd4dc2d313f7f1130fc503
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085264"
---
# <a name="icordebugenum-interface"></a>ICorDebugEnum — Interfejs

Służy jako abstrakcyjny interfejs podstawowy dla modułów wyliczających, które są używane przez aplikację do debugowania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|Tworzy kopię tego obiektu `ICorDebugEnum`.|  
|[GetCount, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|Pobiera liczbę elementów w wyliczeniu.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|Przenosi kursor do początku wyliczenia.|  
|[Skip, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|Przenosi kursor do przodu w wyliczeniu o określoną liczbę elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące moduły wyliczające pochodzą z `ICorDebugEnum`:  
  
- ICorDebugAppDomainEnum  
  
- ICorDebugAssemblyEnum  
  
- [ICorDebugBlockingObjectEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- ICorDebugBreakpointEnum  
  
- ICorDebugChainEnum  
  
- ICorDebugCodeEnum  
  
- ICorDebugErrorInfoEnum  
  
- [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- ICorDebugFrameEnum  
  
- [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- ICorDebugModuleEnum  
  
- ICorDebugObjectEnum  
  
- ICorDebugProcessEnum  
  
- ICorDebugStepperEnum  
  
- ICorDebugThreadEnum  
  
- ICorDebugTypeEnum  
  
- ICorDebugValueEnum  
  
- [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
