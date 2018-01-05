---
title: "EClrEvent — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrEvent
helpviewer_keywords: EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d453cf7d3c7613397890c2d49a2dbe81a2e5d81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="eclrevent-enumeration"></a>EClrEvent — Wyliczenie
W tym artykule opisano typowe zdarzenia środowiska uruchomieniowego (języka wspólnego CLR) języka, dla których hosta można zarejestrować wywołań zwrotnych.  
  
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
|`Event_DomainUnload`|Określa zwalnianie określonego <xref:System.AppDomain>.|  
|`Event_MDAFired`|Określa wygenerowania wiadomości zarządzane debugowania Asystenta (MDA).|  
|`Event_StackOverflow`|Określa, że wystąpił błąd przepełnienia stosu.|  
  
## <a name="remarks"></a>Uwagi  
 Hosta można zarejestrować wywołań zwrotnych dla każdego z typów zdarzeń opisanego przez `EClrEvent` przez wywołanie metody [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interfejsu. Host pobiera wskaźnik do tego interfejsu, wywołując [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.  
  
 `Event_CLRDisabled` i `Event_DomainUnload` zdarzenia można podnieść więcej niż jeden raz i inne wątki sygnalizują zwolnienie lub wyłączenie środowiska CLR.  
  
 `Event_MDAFired` Tworzenie wywołuje zdarzenie [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) wystąpienia, które zawiera szczegóły komunikat MDA. Aby uzyskać więcej informacji o mda, zobacz [diagnozowanie problemów z Asystenci zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IActionOnCLREvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
