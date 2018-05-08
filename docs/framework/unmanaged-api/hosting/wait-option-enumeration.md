---
title: WAIT_OPTION — Wyliczenie
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb37394799db39baa406ef332066d5ebb2dbf19d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="waitoption-enumeration"></a>WAIT_OPTION — Wyliczenie
Zawiera wartości, które wskazują, że akcja hosta może pobierać operacji wymaganej przez wspólne bloki środowiska uruchomieniowego (języka wspólnego CLR) języka.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|Powiadamia hosta, czy zadanie powinno wznowione wywołuje CLR [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) metody.|  
|`WAIT_MSGPUMP`|Powiadamia hosta, że musi on pompa wiadomości w bieżącym wątku systemu operacyjnego, jeśli wątek zostanie zablokowane. Środowisko uruchomieniowe określa tę wartość tylko dla <xref:System.Threading.ApartmentState.STA> wątku.|  
|`WAIT_NOTINDEADLOCK`|Powiadamia hosta, że nie mogą być podzielone żądanie synchronizacji określonej przez hosta. Oznacza to, że host nie może zwracać `HOST_E_DEADLOCK`.|  
  
## <a name="remarks"></a>Uwagi  
 [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) i [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) metody zarówno przyjmują parametr tego typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
