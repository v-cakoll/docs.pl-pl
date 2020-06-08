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
ms.openlocfilehash: 2f83bc5b114b746958f936c311efa823d88441d1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503890"
---
# <a name="wait_option-enumeration"></a>WAIT_OPTION — Wyliczenie
Zawiera wartości wskazujące akcję, którą host powinien wykonać, jeśli operacja zażądała bloków środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|Powiadamia hosta, że zadanie powinno zostać wznowione, jeśli środowisko CLR wywoła metodę [IHostTask:: Alert](ihosttask-alert-method.md) .|  
|`WAIT_MSGPUMP`|Powiadamia hosta, że musi pompować komunikaty w bieżącym wątku systemu operacyjnego, jeśli wątek zostanie zablokowany. Środowisko uruchomieniowe określa tę wartość tylko w <xref:System.Threading.ApartmentState.STA> wątku.|  
|`WAIT_NOTINDEADLOCK`|Powiadamia hosta, że nie można rozbić określonego żądania synchronizacji przez hosta. Oznacza to, że host nie może zwrócić `HOST_E_DEADLOCK` .|  
  
## <a name="remarks"></a>Uwagi  
 Metody [IHostTaskManager:: Sleep](ihosttaskmanager-sleep-method.md) i [IHostTaskManager:: SwitchToTask —](ihosttaskmanager-switchtotask-method.md) przyjmują parametr tego typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — Wyliczenia](hosting-enumerations.md)
