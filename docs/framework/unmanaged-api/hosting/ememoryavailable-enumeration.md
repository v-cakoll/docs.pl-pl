---
title: EMemoryAvailable — Wyliczenie
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
ms.openlocfilehash: 0073a532f680d8764ec9e76ea22326a630457043
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176438"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable — Wyliczenie
Zawiera wartości wskazujące ilość wolnej pamięci fizycznej na komputerze. Wartości te logicznie mapują zdarzenia dla wysokiej `CreateMemoryResourceNotification` i małej ilości pamięci zwróconej z funkcji w interfejsie API systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|Dostępnych jest mnóstwo pamięci fizycznej.|  
|`eMemoryAvailableLow`|Dostępna jest bardzo mała pamięć fizyczna.|  
|`eMemoryAvailableNeutral`|Dostępna pamięć fizyczna jest neutralna.|  
  
## <a name="remarks"></a>Uwagi  
 Ta wartość jest przekazywana przez hosta do środowiska wykonawczego języka wspólnego (CLR) przy użyciu wywołania [metody ICLRMemoryNotificationCallback::OnMemoryNotification.](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting — Wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
