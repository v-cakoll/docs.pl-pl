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
ms.openlocfilehash: a1b22e77fe20d5e2d755efcd7a63c8f2bdc781e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140843"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager — Interfejs
Zapewnia metody, które pozwalają hostowi rejestrować i wyrejestrować wywołania zwrotne dla zdarzeń środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[RegisterActionOnEvent, metoda](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|Rejestruje wskaźnik wywołania zwrotnego dla określonego zdarzenia.|  
|[UnregisterActionOnEvent, metoda](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|Wyrejestrowuje wcześniej zarejestrowany wskaźnik wywołania zwrotnego dla określonego zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Aby zarejestrować i wyrejestrować wywołania zwrotne zdarzeń, Host pobiera odwołanie do `ICLROnEventManager` przez wywołanie metody [ICLRControl:: GetCLRManager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .  
  
> [!NOTE]
> Zdarzenia opisane przez [EClrEvent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) mogą być wywoływane więcej niż jeden raz i z różnych wątków, aby sygnalizować zwolnienie lub wyłączenie środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrEvent, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
