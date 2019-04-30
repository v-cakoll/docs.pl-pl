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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54b2af6e7a200db89bfd7335868a629d7a886fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61724112"
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState — Wyliczenie
Wskazuje stan wątku użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`USER_SUSPEND_REQUESTED`|Wysłano żądanie zawieszenia wątku.|  
|`USER_BACKGROUND`|Wątek jest uruchomiony w tle.|  
|`USER_UNSTARTED`|Wątek się nie rozpoczęła wykonywanie.|  
|`USER_STOPPED`|Wątek został zakończony.|  
|`USER_WAIT_SLEEP_JOIN`|Wątek czeka, aż inny wątek do ukończenia zadania.|  
|`USER_SUSPENDED`|Wątek zostało zawieszone.|  
|`USER_UNSAFE_POINT`|Ten wątek jest niebezpieczne w punkcie. Wątek jest w momencie wykonywania gdzie mogą blokować wyrzucania elementów bezużytecznych.<br /><br /> Debugowanie zdarzeń mogą być wysyłane z punktów niebezpieczne, ale zawieszanie wątków niebezpiecznych w punkcie najprawdopodobniej spowoduje zakleszczenia aż wątek zostanie wznowione. Bezpieczne i niebezpieczne punkty są określane przez just-in-time (JIT) i implementacji kolekcji wyrzucania elementów.|  
|`USER_THREADPOOL`|Ten wątek jest z puli wątków.|  
  
## <a name="remarks"></a>Uwagi  
 Stan użytkownika wątek jest stan, który ma wątku, gdy debuger bada go. Wątek może być kombinacją stanów użytkowników.  
  
 Użyj [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) metodę, aby pobrać stan użytkownika dla wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
