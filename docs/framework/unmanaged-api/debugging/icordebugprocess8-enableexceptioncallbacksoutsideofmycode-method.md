---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52a58f75ca7abd1bd1f871bcf4637bfd7eb7bdcd
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300545"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode — metoda
[Obsługiwane w programie .NET Framework 4.6 lub nowszy]  
  
 Włącza lub wyłącza niektóre rodzaje [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) wywołań zwrotnych wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enableExceptionsOutsideOfJMC`  
 [in]  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `enableExceptionsOutsideOfJMC` jest `false`:  
  
- Wyjątek DEBUG_EXCEPTION_FIRST_CHANCE nie spowoduje wywołanie zwrotne do debugera.  
  
- Wyjątek DEBUG_EXCEPTION_CATCH_HANDLER_FOUND nie powoduje wywołanie zwrotne do debugera w przypadku wyjątku, nigdy nie specjalne w kodzie użytkownika (oznacza to ścieżki ze źródła wyjątku do obsługi wyjątków nie zawiera metod oznaczonego jako JustMyCode lub JMC).  
  
 Wartość domyślna `enableExceptionsOutsideOfJMC` jest `true`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess8, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
