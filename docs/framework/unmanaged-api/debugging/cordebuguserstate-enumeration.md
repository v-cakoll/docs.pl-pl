---
title: CorDebugUserState — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: d0394d511197c8d0aaa366ce7b791216a3d226bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120190"
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState — Wyliczenie
Wskazuje stan użytkownika wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|Zażądano zakończenia wątku.|  
|`USER_SUSPEND_REQUESTED`|Zażądano zawieszenia wątku.|  
|`USER_BACKGROUND`|Wątek działa w tle.|  
|`USER_UNSTARTED`|Nie rozpoczęto wykonywania wątku.|  
|`USER_STOPPED`|Wątek został zakończony.|  
|`USER_WAIT_SLEEP_JOIN`|Wątek oczekuje na ukończenie zadania przez inny wątek.|  
|`USER_SUSPENDED`|Wątek został zawieszony.|  
|`USER_UNSAFE_POINT`|Wątek znajduje się w niebezpiecznym punkcie. Oznacza to, że wątek jest w miejscu wykonywania, gdzie może blokować odzyskiwanie pamięci.<br /><br /> Zdarzenia debugowania mogą być wysyłane z niebezpiecznych punktów, ale zawieszenie wątku w niebezpiecznym punkcie prawdopodobnie spowoduje zakleszczenie do momentu wznowienia wątku. Bezpieczne i niebezpieczne punkty są określane przez implementację just-in-Time (JIT) i wyrzucania elementów bezużytecznych.|  
|`USER_THREADPOOL`|Wątek pochodzi z puli wątków.|  
  
## <a name="remarks"></a>Uwagi  
 Stanem użytkownika wątku jest stan, w którym wątek jest badany przez debuger. Wątek może mieć kombinację Stanów użytkownika.  
  
 Użyj metody [ICorDebugThread:: GetUserState —](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) , aby pobrać stan użytkownika wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
