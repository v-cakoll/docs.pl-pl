---
title: ICLRIoCompletionManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: 822b51531b7afc1c824c74b9580d9208e347e13b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703555"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager — Interfejs
Implementuje metodę wywołania zwrotnego, która umożliwia hostowi powiadamianie środowiska uruchomieniowego języka wspólnego (CLR) o stanie określonych żądań we/wy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[OnComplete, metoda](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|Powiadamia CLR o stanie żądania we/wy, które zostało wykonane przy użyciu wywołania metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .|  
  
## <a name="remarks"></a>Uwagi  
 Host implementuje abstrakcję ukończenia we/wy przy użyciu interfejsu [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) . Środowisko CLR wykonuje żądania we/wy za pośrednictwem tego interfejsu, a host powiadamia środowisko uruchomieniowe o wyniku takich żądań za pomocą `ICLRIoCompletionManager` interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostIoCompletionManager, interfejs](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager, interfejs](ihostthreadpoolmanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
