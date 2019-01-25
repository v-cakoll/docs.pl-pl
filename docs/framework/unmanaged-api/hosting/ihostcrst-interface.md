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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34a911668db09b255282833cec3e6272b315373b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618662"
---
# <a name="ihostcrst-interface"></a>IHostCrst — Interfejs
Służy jako hosta reprezentacja sekcję krytyczną dla wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Enter, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Wprowadza sekcję krytyczną.|  
|[Leave, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Pozostawia sekcję krytyczną.|  
|[SetSpinCount, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Ustawia liczbę pokrętła sekcję krytyczną.|  
|[TryEnter, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Próbuje wprowadzić sekcję krytyczną i raporty o powodzeniu lub niepowodzeniu natychmiast.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostCrst` Umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do bezpośredniego komunikowania się z hosta reprezentacja sekcję krytyczną, a nie przy użyciu funkcji środowiska Win32, takich jak `EnterCriticalSection` lub `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
