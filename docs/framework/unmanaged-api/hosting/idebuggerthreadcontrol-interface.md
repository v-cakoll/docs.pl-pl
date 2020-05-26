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
ms.openlocfilehash: 82c6113f4df3334500128df22f7e9ce8d4bf151f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805280"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl — Interfejs
Zapewnia metody powiadamiania hosta o blokowaniu i odblokowywaniu wątków przez usługi debugowania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger, metoda](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|Powiadamia hosta, że wątek wysyłający to wywołanie zwrotne ma zostać zablokowany w ramach usług debugowania.|  
|[ReleaseAllRuntimeThreads, metoda](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|Powiadamia hosta o wydaniu wszystkich zablokowanych wątków przez usługi debugowania.|  
|[StartBlockingForDebugger, metoda](idebuggerthreadcontrol-startblockingfordebugger-method.md)|Powiadamia hosta o konieczności rozpoczęcia blokowania wszystkich wątków przez usługi debugowania.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, interfejsy](hosting-interfaces.md)
