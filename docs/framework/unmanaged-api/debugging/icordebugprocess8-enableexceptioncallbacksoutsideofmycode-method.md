---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: b6bfd258f35f19719be5e5169a1edc22a358371c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123376"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda
[Obsługiwane w .NET Framework 4,6 i nowszych wersjach]  
  
 Włącza lub wyłącza określone typy wywołań zwrotnych wyjątków [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enableExceptionsOutsideOfJMC`  
 podczas  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `enableExceptionsOutsideOfJMC` jest `false`:  
  
- Wyjątek DEBUG_EXCEPTION_FIRST_CHANCE nie powoduje wywołania zwrotnego debugera.  
  
- Wyjątek DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nie powoduje wywołania zwrotnego debugera, jeśli wyjątek nigdy nie wyjdzie do kodu użytkownika (oznacza to, że ścieżka ze źródła wyjątku do procedury obsługi wyjątku nie ma metod oznaczonych jako JustMyCode lub JMC).  
  
 Wartość domyślna `enableExceptionsOutsideOfJMC` jest `true`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess8, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
