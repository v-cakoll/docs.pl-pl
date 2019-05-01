---
title: IGCThreadControl — Interfejs
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c00f401bedc1a2810c4e9b3046a45e53a79f1ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992774"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl — Interfejs
Udostępnia metody do uczestnictwa w planowaniu wątki, które w przeciwnym razie zostałby zablokowany dla wyrzucania elementów bezużytecznych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SuspensionEnding, metoda](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|Powiadamia hosta, czy środowisko uruchomieniowe jest wznawianie wątków po wyrzucania elementów bezużytecznych lub innych zawieszenia.|  
|[SuspensionStarting, metoda](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|Powiadamia hosta, rozpoczyna środowiska uruchomieniowego zawieszeniu wątku wyrzucania elementów bezużytecznych lub innych zawieszenia.|  
|[ThreadIsBlockingForSuspension, metoda](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|Powiadamia hosta, że wątek wywołania się zablokować, być może do wyrzucania elementów bezużytecznych lub innych zawieszenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
