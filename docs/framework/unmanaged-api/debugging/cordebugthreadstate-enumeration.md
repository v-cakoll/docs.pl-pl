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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efb7f5b8e63742471123a0e0a38cebe605f3696f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092451"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState — Wyliczenie
Określa stan wątku do debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`THREAD_RUN`|Wątek uruchamia się za darmo, chyba że wystąpi zdarzenie debugowania.|  
|`THREAD_SUSPEND`|Nie można uruchomić wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Debuger używa `CorDebugThreadState` wyliczeniu, aby kontrolować wykonywanie wątku. Stan wątku można ustawić za pomocą [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) lub [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) metody.  
  
 Wywołanie zwrotne udostępniane [hostującego interfejs API](../../../../docs/framework/unmanaged-api/hosting/index.md) umożliwia przekazywanie wiadomości, przerwane stanu nie jest potrzebna.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDegug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
