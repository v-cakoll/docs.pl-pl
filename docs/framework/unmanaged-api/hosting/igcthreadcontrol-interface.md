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
ms.openlocfilehash: 9296aedf24979624c3d7357a4d51be835716a16f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438031"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl — Interfejs
Udostępnia metody do uczestnictwa w planowaniu wątków, które można zablokować dla wyrzucania elementów bezużytecznych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SuspensionEnding, metoda](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|Powiadamia host środowiska uruchomieniowego Trwa wznawianie wątków po wyrzucania elementów bezużytecznych lub innych zawieszenia.|  
|[SuspensionStarting, metoda](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|Powiadamia hosta rozpoczyna środowiska uruchomieniowego zawieszeniu wątku wyrzucania elementów bezużytecznych lub innych zawieszenie.|  
|[ThreadIsBlockingForSuspension, metoda](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|Powiadamia hosta wątku wywołania o zbliżającym się zablokować, być może do wyrzucania elementów bezużytecznych lub innych zawieszenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
