---
title: EClrOperation — Wyliczenie
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d5f24d7415ff7ecceba6b0a5fbd3098d70dcd0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190356"
---
# <a name="eclroperation-enumeration"></a>EClrOperation — Wyliczenie
W tym artykule opisano zestaw operacji, dla których hostem akcje można zastosować zasad.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|Hosta można określić zasady akcje do wykonania, kiedy <xref:System.AppDomain> zwalnianie w sposób łagodne (prosta).|  
|`OPR_AppDomainUnload`|Hosta można określić zasady akcje do wykonania, kiedy <xref:System.AppDomain> jest zwalniana.|  
|`OPR_FinalizerRun`|Hosta można określić zasady akcje do wykonania po uruchomieniu finalizatorów.|  
|`OPR_ProcessExit`|Hosta można określić zasady akcje do wykonania, gdy kończy proces.|  
|`OPR_ThreadAbort`|Hosta można określić zasady akcje do wykonania, gdy wątek został przerwany.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|Hosta można określić zasady akcje do wykonania, gdy przerwanie wątku prosta odbywa się na krytyczny obszar kodu.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|Hosta można określić akcje zasad podjęcie sytuacji przerwanie wątku prosta w regionie niekrytyczne kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Wspólnej infrastruktury języka wspólnego (CLR) niezawodność rozróżnia przerwań i zasobów błędów alokacji, występujących w regionach krytycznego kodu, i te, które występują w niekrytyczne regiony kodu. Ta różnica jest przeznaczony do Zezwalaj na hostach w celu ustawienia zasad różne w zależności od tego, gdzie występuje błąd w kodzie.  
  
 A *krytyczne obszar kodu* dowolnego miejsca, gdzie środowisko CLR nie może zagwarantować tego przerywanie zadania lub nieukończone żądania dla zasobów wpłynie na bieżące zadanie. Na przykład, jeśli zadanie jest blokada, otrzymuje wartość HRESULT, który wskazuje niepowodzenie podczas żądania alokacji pamięci jest za mała, aby przerwać to zadanie, aby upewnić się, stabilności, po prostu <xref:System.AppDomain>, ponieważ <xref:System.AppDomain> mogą zawierać inne Oczekiwanie na blokadę tego samego zadania. Aby wstrzymać bieżącą zadanie może spowodować, te inne zadania przestać odpowiadać (lub odłożyć) na czas nieokreślony. W takim przypadku host wymaga możliwości można zwolnić całej <xref:System.AppDomain> zamiast niestabilności potencjalne ryzyko.  
  
 A *niekrytyczne obszar kodu*, z drugiej strony, to region, w którym środowiska CLR może zagwarantować, że przerwania lub awarii będzie mieć wpływ na zadania, na którym występuje błąd.  
  
 Środowisko CLR rozróżnia również bezpiecznie i łagodne przerwań (prosta). Ogólnie rzecz biorąc przerwania normalne lub łagodne dokłada wszelkich starań, aby uruchomić procedury obsługi wyjątków i finalizatory przed przerwaniem zadania, natomiast prosta przerwania nie gwarantuje takie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
