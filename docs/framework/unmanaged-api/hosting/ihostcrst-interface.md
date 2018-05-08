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
ms.openlocfilehash: 88f2ef8299911905d651ad5c3076dc9c74f397f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 `IHostCrst` Umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do bezpośredniego komunikowania się z hosta reprezentację sekcja krytyczna, a nie przy użyciu funkcji Win32, takich jak `EnterCriticalSection` lub `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
