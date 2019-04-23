---
title: IDebuggerThreadControl — Interfejs
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a551d3cc6ab3dd3887f232018f8201de4036d1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096839"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl — Interfejs
Zawiera metody służące do powiadamiania hosta dotyczące blokowania i odblokowywania wątków przez usług debugowania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger, metoda](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|Powiadamia hosta, którego dotyczy wątku, który wysyła to wywołanie zwrotne do bloku, w ramach usług debugowania.|  
|[ReleaseAllRuntimeThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|Powiadamia hosta, że usług debugowania zamiar Zwolnij wszystkie wątki, które są blokowane.|  
|[StartBlockingForDebugger, metoda](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|Powiadamia hosta, że usług debugowania zamiar start blokuje wszystkie wątki.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
