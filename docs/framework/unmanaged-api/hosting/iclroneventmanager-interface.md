---
title: ICLROnEventManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f927cece9997c78a75b1edecdb0a671203c3dd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646896"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager — Interfejs
Udostępnia metody, które umożliwiają hosta rejestrować i wyrejestrowywać wywołania zwrotne dla typowych zdarzeń środowiska uruchomieniowego (języka wspólnego CLR) języka.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[RegisterActionOnEvent, metoda](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|Rejestruje wywołanie zwrotne wskaźnik dla określonego zdarzenia.|  
|[UnregisterActionOnEvent, metoda](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|Wyrejestrowuje wskaźnik wcześniej zarejestrowanego wywołania zwrotnego dla określonego zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Aby rejestrować i wyrejestrowywać wywołania zwrotne zdarzeń, host pobiera odwołanie do `ICLROnEventManager` przez wywołanie metody [iclrcontrol::getclrmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.  
  
> [!NOTE]
>  Zdarzenie opisane przez [eclrevent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) uruchamiane więcej niż jeden raz i inne wątki w celu sygnalizowania, że zwolnienie lub wyłączenie środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [EClrEvent, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
