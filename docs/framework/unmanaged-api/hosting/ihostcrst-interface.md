---
title: "IHostCrst — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a9ed2b390ad741d90f9179ef5101d328d3b639d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrst-interface"></a>IHostCrst — Interfejs
Służy jako hosta reprezentację sekcja krytyczna dla wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Enter, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Wprowadza sekcja krytyczna.|  
|[Leave, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Pozostawia sekcja krytyczna.|  
|[SetSpinCount, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Ustawia liczbę pokrętła dla sekcji krytycznych.|  
|[TryEnter, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Próbuje natychmiast wprowadź sekcja krytyczna i raporty powodzenie lub niepowodzenie.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostCrst`Umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do bezpośredniego komunikowania się z hosta reprezentację sekcja krytyczna, a nie przy użyciu funkcji Win32, takich jak `EnterCriticalSection` lub `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
