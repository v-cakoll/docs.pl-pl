---
title: EPolicyAction — Wyliczenie
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75bd7da67cbac958f0b34c8295454a719962c7ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201731"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction — Wyliczenie
W tym artykule opisano akcje zasad hosta można ustawić dla operacji opisanych przez [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) i awarie opisanego przez [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eAbortThread`|Określa, że środowisko uruchomieniowe języka wspólnego (CLR) należy przerwać bez problemu zmieniała wątku. Łagodne przerwania obejmuje próbuje uruchomić wszystkie `finally` blokach dowolny `catch` bloków związanych z wątku przerwań i finalizatorów.|  
|`eDisableRuntime`|Określa, że środowisko CLR należy wprowadzić w stanie wyłączenia. Żadne dodatkowe zarządzanego kodu mogą być wykonywane w procesie zainfekowanego i możliwość wprowadzania środowiska CLR są blokowane wątki.|  
|`eExitProcess`|Określa, że środowisko CLR powinien podejmować próbę Łagodne wyjście procesu, łącznie z systemem finalizatory i oczyszczania i operacji rejestrowania.|  
|`eFastExitProcess`|Określa środowisko CLR powinien natychmiast zakończyć proces bez uruchamiania finalizatory i oczyszczania i operacji rejestrowania. Jednak powiadomienie jest wysyłane do debugera.|  
|`eNoAction`|Określa, czy podjęta żadna akcja.|  
|`eRudeAbortThread`|Określa, że przerwanie wątku prosta powinno być wykonywane przez środowisko CLR. Tylko te `catch` i `finally` bloki oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.|  
|`eRudeExitProcess`|Określa środowisko CLR powinna zakończyć proces bez uruchamiania finalizatory i rejestrowanie operacji.|  
|`eRudeUnloadAppDomain`|Określa, że prosta zwolnienie powinno być wykonywane przez środowisko CLR <xref:System.AppDomain>. Finalizatory tylko oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane. Podobnie wszystkie wątki w tym <xref:System.AppDomain> w stosie ich odbierania `ThreadAbortException`, a jedynie tych `catch` i `finally` bloki oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute> są wykonywane.|  
|`eThrowException`|Określa, że odpowiednie do warunku, takie jak braku pamięci, przepełnienie buforu i tak dalej, należy zgłosić wyjątek.|  
|`eUnloadAppDomain`|Określa, że <xref:System.AppDomain> powinny zostać zwolniony. Środowisko CLR podejmie próbę uruchomienia finalizatorów.|  
  
## <a name="remarks"></a>Uwagi  
 Host ustawia akcje zasad przez wywołanie metody [iclrpolicymanager —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interfejsu. Aby o prosta i płynnego przerwań, zobacz [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wyliczenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure — Wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [ICLRPolicyManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Hosting — Wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
