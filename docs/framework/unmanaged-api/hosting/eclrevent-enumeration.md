---
title: EClrEvent — Wyliczenie
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: ee749fd40f440e92f1d1b09c2ea5e7bdd51f1cbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131134"
---
# <a name="eclrevent-enumeration"></a>EClrEvent — Wyliczenie
Opisuje zdarzenia środowiska uruchomieniowego języka wspólnego (CLR), dla których host może rejestrować wywołania zwrotne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`Event_ClrDisabled`|Określa krytyczny błąd CLR.|  
|`Event_DomainUnload`|Określa wyładowywanie określonego <xref:System.AppDomain>.|  
|`Event_MDAFired`|Określa, że został wygenerowany komunikat Asystent debugowania zarządzanego (MDA).|  
|`Event_StackOverflow`|Określa, że wystąpił błąd przepełnienia stosu.|  
  
## <a name="remarks"></a>Uwagi  
 Host może rejestrować wywołania zwrotne dla dowolnego typu zdarzenia opisanego przez `EClrEvent` przez wywoływanie metod interfejsu [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) . Host Pobiera wskaźnik do tego interfejsu, wywołując metodę [ICLRControl:: GetCLRManager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .  
  
 Zdarzenia `Event_CLRDisabled` i `Event_DomainUnload` mogą być wywoływane więcej niż jeden raz i z różnych wątków, aby sygnalizować zwolnienie lub wyłączenie środowiska CLR.  
  
 Zdarzenie `Event_MDAFired` wywołuje Tworzenie wystąpienia [MDAInfo —](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) zawierającego szczegóły komunikatu MDA. Aby uzyskać więcej informacji na temat MDA, zobacz [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IActionOnCLREvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
