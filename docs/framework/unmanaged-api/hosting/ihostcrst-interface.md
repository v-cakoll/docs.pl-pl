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
ms.openlocfilehash: e8cb1486ccea11ba6edcf7bbb781a9bf210b496d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804903"
---
# <a name="ihostcrst-interface"></a>IHostCrst — Interfejs
Służy jako reprezentacja hosta sekcji krytycznej dla wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Enter, metoda](ihostcrst-enter-method.md)|Wprowadza sekcję krytyczną.|  
|[Leave, metoda](ihostcrst-leave-method.md)|Pozostawia sekcję krytyczną.|  
|[SetSpinCount, metoda](ihostcrst-setspincount-method.md)|Ustawia liczbę obrotów dla sekcji krytycznej.|  
|[TryEnter, metoda](ihostcrst-tryenter-method.md)|Próbuje wprowadzić sekcję krytyczną i natychmiast raportuje powodzenie lub niepowodzenie.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostCrst`zezwala, aby środowisko uruchomieniowe języka wspólnego (CLR) komunikować się bezpośrednio z reprezentacją w sekcji krytycznej hosta, a nie przy użyciu funkcji Win32, takich jak `EnterCriticalSection` lub `LeaveCriticalSection` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRSyncManager — Interfejs](iclrsyncmanager-interface.md)
- [IHostSyncManager, interfejs](ihostsyncmanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
