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
ms.openlocfilehash: d502b4098016fb14793bccd6feb641e92e3c2611
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795641"
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
  
 Użyj metody [ICorDebugThread:: GetUserState —](icordebugthread-getuserstate-method.md) , aby pobrać stan użytkownika wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — wyliczenia](debugging-enumerations.md)
