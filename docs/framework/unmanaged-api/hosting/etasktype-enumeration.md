---
title: "ETaskType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ETaskType
api_location: mscoree.dll
api_type: COM
f1_keywords: ETaskType
helpviewer_keywords: ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 52e027c5d2ead70bbd624fafe3021121557cd261
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="etasktype-enumeration"></a>ETaskType — Wyliczenie
Zawiera wartości, które wskazują na typ task, która jest reprezentowana przez albo [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) lub [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`TT_ADUNLOAD`|Interfejs reprezentuje zadania zwalniania domeny aplikacji.|  
|`TT_DEBUGGERHELPER`|Interfejs reprezentuje zadania pomocnika debugera.|  
|`TT_FINALIZER`|Interfejs reprezentuje zadania finalizatora.|  
|`TT_GC`|Interfejs reprezentuje zadanie odzyskiwania pamięci.|  
|`TT_THREADPOOL_GATE`|Interfejs reprezentuje zadania wątku bramy.|  
|`TT_THREADPOOL_IOCOMPLETION`|Interfejs reprezentuje zadania wątków We/Wy lub wątku portu ukończenia zadania.|  
|`TT_THREADPOOL_TIMER`|Interfejs reprezentuje zadanie czasomierza wątku.|  
|`TT_THREADPOOL_WAIT`|Interfejs reprezentuje oczekiwania wątku zadania.|  
|`TT_THREADPOOL_WORKER`|Interfejs reprezentuje zadania wątku roboczego.|  
|`TT_UNKNOWN`|Zadanie jest nieznany.|  
|`TT_USER`|Interfejs reprezentuje zadanie użytkownika.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
