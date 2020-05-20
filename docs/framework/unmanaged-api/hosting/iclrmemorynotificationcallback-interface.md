---
title: ICLRMemoryNotificationCallback — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: 52fc21044d345998ad72c045cdf5e80a8a03a38e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703800"
---
# <a name="iclrmemorynotificationcallback-interface"></a>ICLRMemoryNotificationCallback — Interfejs
Umożliwia hostowi zgłaszanie warunków ciśnienia pamięci przy użyciu podejścia podobnego do `CreateMemoryResourceNotification` funkcji Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[OnMemoryNotification, metoda](iclrmemorynotificationcallback-onmemorynotification-method.md)|Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o załadowaniu pamięci na komputerze.|  
  
## <a name="remarks"></a>Uwagi  
 Host używa `ICLRMemoryNotificationCallback` interfejsu do żądania zasobów wolnej pamięci środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostMemoryManager, interfejs](ihostmemorymanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
