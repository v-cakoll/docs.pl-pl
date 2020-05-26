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
ms.openlocfilehash: 428e4cf8997713b08e40d9376c34ae5eee8cfa32
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804856"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager — Interfejs
Dostarcza metody, które powiadamiają hosta zdarzeń w mechanizmie wyrzucania elementów bezużytecznych zaimplementowane przez środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|[SuspensionEnding, metoda](ihostgcmanager-suspensionending-method.md)|Powiadamia hosta, że środowisko CLR wznawia wykonywanie zadań w wątkach, które zostały zawieszone na wyrzucanie elementów bezużytecznych.|  
|[SuspensionStarting, metoda](ihostgcmanager-suspensionstarting-method.md)|Powiadamia hosta o wstrzymaniu wykonywania zadań przez środowisko CLR w celu wykonania wyrzucania elementów bezużytecznych.|  
|[ThreadIsBlockingForSuspension, metoda](ihostgcmanager-threadisblockingforsuspension-method.md)|Powiadamia hosta, że wątek, z którego wykonano wywołanie metody, ma zablokować na wyrzucanie elementów bezużytecznych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRTask — Interfejs](iclrtask-interface.md)
- [ICLRTaskManager, interfejs](iclrtaskmanager-interface.md)
- [IHostTask, interfejs](ihosttask-interface.md)
- [IHostTaskManager, interfejs](ihosttaskmanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
