---
title: CorDebugThreadState — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 1ff36e8ef6b7c02eea5b02bc22587bc3889df093
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133694"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState — Wyliczenie
Określa stan wątku do debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`THREAD_RUN`|Wątek działa swobodnie, chyba że wystąpi zdarzenie debugowania.|  
|`THREAD_SUSPEND`|Nie można uruchomić wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Debuger używa wyliczenia `CorDebugThreadState`, aby sterować wykonywaniem wątku. Stan wątku można ustawić za pomocą metody [ICorDebugThread:: SetDebugState —](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) lub [ICorDebugController:: SetAllThreadsDebugState —](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) .  
  
 Wywołanie zwrotne obsługiwane w [interfejsie API hostingu](../../../../docs/framework/unmanaged-api/hosting/index.md) umożliwia pompowanie komunikatów, dlatego nie jest wymagany stan przerwania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
