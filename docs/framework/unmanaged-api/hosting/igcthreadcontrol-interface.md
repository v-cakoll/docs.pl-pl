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
ms.openlocfilehash: 78e667acf1573769a1a67b4c964d7801f11838fe
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805128"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl — Interfejs
Zapewnia metody uczestnictwa w planowaniu wątków, które w przeciwnym razie byłyby blokowane na wyrzucanie elementów bezużytecznych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SuspensionEnding, metoda](igcthreadcontrol-suspensionending-method.md)|Powiadamia hosta, że środowisko uruchomieniowe wznawia wątki po wyrzucaniu elementów bezużytecznych lub innym zawieszeniu.|  
|[SuspensionStarting, metoda](igcthreadcontrol-suspensionstarting-method.md)|Powiadamia hosta, że środowisko uruchomieniowe rozpoczyna zawieszenie wątku na wyrzucanie elementów bezużytecznych lub inne zawieszenie.|  
|[ThreadIsBlockingForSuspension, metoda](igcthreadcontrol-threadisblockingforsuspension-method.md)|Powiadamia hosta, że wątek wywołujący wywołanie ma być blokowany, prawdopodobnie na wyrzucanie elementów bezużytecznych lub innym zawieszeniu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, interfejsy](hosting-interfaces.md)
