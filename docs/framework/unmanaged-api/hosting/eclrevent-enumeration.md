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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13d564be68d6b49a1616be97710312f33f828d48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176348"
---
# <a name="eclrevent-enumeration"></a>EClrEvent — Wyliczenie
Zawiera opis typowych zdarzeń środowiska uruchomieniowego (języka wspólnego CLR) języka, dla których hosta mogą rejestrować wywołania zwrotne.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`Event_ClrDisabled`|Określa krytyczny błąd środowiska CLR.|  
|`Event_DomainUnload`|Określa zwolnienie określonego <xref:System.AppDomain>.|  
|`Event_MDAFired`|Określa komunikat zarządzane debugowanie Asystenta ustawień (MDA) został wygenerowany.|  
|`Event_StackOverflow`|Określa, że wystąpił błąd przepełnienia stosu.|  
  
## <a name="remarks"></a>Uwagi  
 Hosta można zarejestrować wywołania zwrotne dla każdego z typów zdarzeń, opisanego przez `EClrEvent` przez wywołanie metody [iclroneventmanager —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interfejsu. Host pobiera wskaźnik do tego interfejsu, wywołując [iclrcontrol::getclrmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.  
  
 `Event_CLRDisabled` i `Event_DomainUnload` zdarzenia można podnieść więcej niż jeden raz i inne wątki w celu sygnalizowania, że zwolnienie lub wyłączenie środowiska CLR.  
  
 `Event_MDAFired` Zdarzeń wywołuje tworzenie [mdainfo —](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) wystąpienia, które zawiera szczegóły komunikatu MDA. Aby uzyskać więcej informacji na temat mda zobacz [diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IActionOnCLREvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
