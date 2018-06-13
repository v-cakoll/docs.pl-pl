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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5cf7e17989f3c083c7c4e52fa8cfc09c00bc7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431522"
---
# <a name="iclrmemorynotificationcallback-interface"></a>ICLRMemoryNotificationCallback — Interfejs
Umożliwia hostowi warunków braku pamięci raportu w sposób podobny do środowiska Win32 `CreateMemoryResourceNotification` funkcji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[OnMemoryNotification, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) obciążenia pamięci na komputerze.|  
  
## <a name="remarks"></a>Uwagi  
 Host używa `ICLRMemoryNotificationCallback` interfejsu na żądanie, że środowisko CLR zwolnienia zasobów pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
