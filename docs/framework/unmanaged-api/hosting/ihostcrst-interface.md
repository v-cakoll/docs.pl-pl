---
title: IHostCrst — Interfejs
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 108492ba298e9f8429b2acd890ab3404365bc602
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130524"
---
# <a name="ihostcrst-interface"></a>IHostCrst — Interfejs
Służy jako reprezentacja hosta sekcji krytycznej dla wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Enter, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Wprowadza sekcję krytyczną.|  
|[Leave, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Pozostawia sekcję krytyczną.|  
|[SetSpinCount, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Ustawia liczbę obrotów dla sekcji krytycznej.|  
|[TryEnter, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Próbuje wprowadzić sekcję krytyczną i natychmiast raportuje powodzenie lub niepowodzenie.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostCrst` umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do bezpośredniego komunikowania się z reprezentacją sekcji krytycznej hosta, a nie za pomocą funkcji Win32, takich jak `EnterCriticalSection` lub `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
