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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d98a0c1c3187b81c44fae6eee91d975169a40045
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072809"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable — Wyliczenie
Zawiera wartości, które wskazują ilość wolnej pamięci fizycznej na komputerze. Te wartości logicznie mapowania na zdarzenia dla wysokim i niskim pamięci zwróciło `CreateMemoryResourceNotification` funkcji w interfejsie API Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|Dużej ilości pamięci fizycznej jest dostępna.|  
|`eMemoryAvailableLow`|Bardzo mała ilość pamięci fizycznej jest dostępna.|  
|`eMemoryAvailableNeutral`|Dostępnej pamięci fizycznej jest neutralna.|  
  
## <a name="remarks"></a>Uwagi  
 Ta wartość jest przekazywana przez hosta do wykonywalnych języka wspólnego (CLR), przy użyciu wywołania do [iclrmemorynotificationcallback::onmemorynotification —](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — Wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
