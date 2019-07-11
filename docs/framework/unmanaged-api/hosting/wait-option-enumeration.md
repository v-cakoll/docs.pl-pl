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
ms.openlocfilehash: eda866c1a1f1f69f0d042ccfde3dfad293df9b37
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776508"
---
# <a name="waitoption-enumeration"></a>WAIT_OPTION — Wyliczenie
Zawiera wartości, które wskazują, że akcja hosta powinno zająć, jeśli operacji wymaganej przez bloki języka, aby środowisko uruchomieniowe (języka wspólnego CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|Powiadamia hosta, że zadanie powinno wznowione, jeśli środowisko CLR wywołuje [ihosttask::alert —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) metody.|  
|`WAIT_MSGPUMP`|Powiadamia hosta, należy go pompy komunikatów dla bieżącego wątku systemu operacyjnego Jeśli wątek zostanie zablokowane. Środowisko wykonawcze określa tę wartość tylko na <xref:System.Threading.ApartmentState.STA> wątku.|  
|`WAIT_NOTINDEADLOCK`|Powiadamia hosta, że żądanie synchronizacji określonego nie można podzielić przez hosta. Oznacza to, że host nie może zwracać `HOST_E_DEADLOCK`.|  
  
## <a name="remarks"></a>Uwagi  
 [Ihosttaskmanager::Sleep —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) i [ihosttaskmanager::switchtotask —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) metody przyjmować parametr tego typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
