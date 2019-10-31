---
title: IHostGCManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
ms.openlocfilehash: 6f7158bcac7ad22647104e2041da959285d2be8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130479"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager — Interfejs
Dostarcza metody, które powiadamiają hosta zdarzeń w mechanizmie wyrzucania elementów bezużytecznych zaimplementowane przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[SuspensionEnding, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|Powiadamia hosta, że środowisko CLR wznawia wykonywanie zadań w wątkach, które zostały zawieszone na wyrzucanie elementów bezużytecznych.|  
|[SuspensionStarting, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|Powiadamia hosta o wstrzymaniu wykonywania zadań przez środowisko CLR w celu wykonania wyrzucania elementów bezużytecznych.|  
|[ThreadIsBlockingForSuspension, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|Powiadamia hosta, że wątek, z którego wykonano wywołanie metody, ma zablokować na wyrzucanie elementów bezużytecznych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
