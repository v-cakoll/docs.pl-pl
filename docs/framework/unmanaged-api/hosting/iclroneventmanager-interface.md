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
ms.openlocfilehash: 30312e6e09535cee2968b1f9e8ac87b461c5ff40
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703520"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager — Interfejs
Zapewnia metody, które pozwalają hostowi rejestrować i wyrejestrować wywołania zwrotne dla zdarzeń środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[RegisterActionOnEvent, metoda](iclroneventmanager-registeractiononevent-method.md)|Rejestruje wskaźnik wywołania zwrotnego dla określonego zdarzenia.|  
|[UnregisterActionOnEvent, metoda](iclroneventmanager-unregisteractiononevent-method.md)|Wyrejestrowuje wcześniej zarejestrowany wskaźnik wywołania zwrotnego dla określonego zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Aby zarejestrować i wyrejestrować wywołania zwrotne zdarzeń, Host pobiera odwołanie do, `ICLROnEventManager` wywołując metodę [ICLRControl:: GetCLRManager —](iclrcontrol-getclrmanager-method.md) .  
  
> [!NOTE]
> Zdarzenia opisane przez [EClrEvent —](eclrevent-enumeration.md) mogą być wywoływane więcej niż jeden raz i z różnych wątków, aby sygnalizować zwolnienie lub wyłączenie środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrEvent, wyliczenie](eclrevent-enumeration.md)
- [IActionOnCLREvent — Interfejs](iactiononclrevent-interface.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
