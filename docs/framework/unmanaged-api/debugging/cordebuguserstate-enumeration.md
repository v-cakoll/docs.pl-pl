---
title: "CorDebugUserState — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUserState
helpviewer_keywords: CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57fd9df27b1911c90bd11712b67e6e64588c2b5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState — Wyliczenie
Wskazuje stan użytkownika wątku.  
  
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
|`USER_SUSPEND_REQUESTED`|Zażądano zawieszenia wątku.|  
|`USER_BACKGROUND`|Wątek jest uruchomiony w tle.|  
|`USER_UNSTARTED`|Wątek nie została uruchomiona, wykonywania.|  
|`USER_STOPPED`|Wątek został zakończony.|  
|`USER_WAIT_SLEEP_JOIN`|Wątek oczekuje na inny wątek w celu wykonania zadania.|  
|`USER_SUSPENDED`|Wątek zostało zawieszone.|  
|`USER_UNSAFE_POINT`|Wątek znajduje się w niebezpiecznego punktu. Wątek jest w momencie wykonywania gdzie może blokować wyrzucanie elementów bezużytecznych.<br /><br /> Debugowanie zdarzeń mogą być wysyłane z niebezpiecznych punkty, ale wstrzymywania wątku w niebezpiecznego punktu najprawdopodobniej spowoduje zakleszczenie dopóki nie zostanie wznowione wątku. Bezpieczne i niebezpieczny punkty są określane przez just-in-time (JIT) i odzyskiwanie kolekcji implementacji.|  
|`USER_THREADPOOL`|Wątek znajduje się w puli wątków.|  
  
## <a name="remarks"></a>Uwagi  
 Stan użytkownika wątek jest w stanie, zawierający wątku, gdy debuger bada go. Wątek może mieć kombinację stanów użytkownika.  
  
 Użyj [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) metoda pobierania stanu użytkownika dla wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
