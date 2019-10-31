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
ms.openlocfilehash: eaba6b2166a82cfe825ffb98db515e24d4656462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138231"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction — Wyliczenie
Opisuje akcje zasad, które host może ustawić dla operacji opisanych przez [EClrOperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) i błędy opisane przez [EClrFailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`eAbortThread`|Określa, że środowisko uruchomieniowe języka wspólnego (CLR) powinno bezpiecznie przerwać wątek. Bezpieczne przerwanie obejmuje próby uruchomienia wszystkich bloków `finally`, wszelkich bloków `catch` związanych z przerwami wątku i finalizatorami.|  
|`eDisableRuntime`|Określa, że środowisko CLR ma wejść w stan wyłączony. Żaden kod zarządzany nie może być wykonywany w odpowiednim procesie, a wątki są blokowane przed wprowadzeniem środowiska CLR.|  
|`eExitProcess`|Określa, że środowisko CLR ma próbować bezpiecznie wyjść z procesu, w tym uruchamiania finalizatorów i wykonywania operacji czyszczenia i rejestrowania.|  
|`eFastExitProcess`|Określa, że środowisko CLR powinno zakończyć proces natychmiast, bez uruchamiania finalizatorów lub wykonywania operacji czyszczenia i rejestrowania. Powiadomienia są jednak wysyłane do debugera.|  
|`eNoAction`|Określa, że żadna akcja nie powinna być wykonywana.|  
|`eRudeAbortThread`|Określa, że środowisko CLR ma wykonać przerwanie wątku prosta. Wykonywane są tylko te `catch` i bloki `finally` oznaczone jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute>.|  
|`eRudeExitProcess`|Określa, że środowisko CLR ma wyjść z procesu bez uruchamiania finalizatorów lub operacji rejestrowania.|  
|`eRudeUnloadAppDomain`|Określa, że środowisko CLR ma wykonać prosta Unload <xref:System.AppDomain>. Wykonywane są tylko finalizatory oznaczone <xref:System.EnterpriseServices.MustRunInClientContextAttribute>. Podobnie wszystkie wątki z tym <xref:System.AppDomain> w stosie odbierają `ThreadAbortException`, ale są wykonywane tylko te bloki `catch` i `finally` oznaczone jako <xref:System.EnterpriseServices.MustRunInClientContextAttribute>.|  
|`eThrowException`|Określa, że wyjątek odpowiedni dla warunku, taki jak braku pamięci, przepełnienie buforu i tak dalej, powinien zostać wygenerowany.|  
|`eUnloadAppDomain`|Określa, że <xref:System.AppDomain> powinny być zwolnione. Środowisko CLR próbuje uruchomić finalizatorów.|  
  
## <a name="remarks"></a>Uwagi  
 Host ustawia akcje zasad przez wywołanie metod interfejsu [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) . Aby uzyskać informacje na temat prosta i łagodnego przerwania, zobacz Wyliczenie [EClrOperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
