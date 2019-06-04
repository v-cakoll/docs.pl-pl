---
title: EClrFailure — Wyliczenie
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb19f950122f7b0db66830e9ed5dff44ccd370c2
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490440"
---
# <a name="eclrfailure-enumeration"></a>EClrFailure — Wyliczenie
W tym artykule opisano zestaw awarie, dla których hosta można ustawić akcje dotyczące zasad.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|Wystąpił błąd podczas próby przydzielenia zasobu (na przykład wątku, blok pamięci lub blokadę) w regionie niekrytyczne kodu.|  
|`FAIL_CriticalResource`|Wystąpił błąd podczas próby przydzielenia zasobu (na przykład wątku, blok pamięci lub blokady) krytyczne obszar kodu.|  
|`FAIL_FatalRuntime`|Środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do uruchomienia kodu zarządzanego w procesie. Odtąd wywołania wszystkie funkcje hostingu zwraca wartość HRESULT HOST_E_CLRNOTAVAILABLE.|  
|`FAIL_OrphanedLock`|Wątek nie udało się zwolnić blokady po powrocie z <xref:System.AppDomain> obiektu. Host nie można ustawić tego błędu, aby spowodować, że wątek przerwać.|  
|`FAIL_StackOverflow`|Wystąpiło przepełnienie stosu.|  
|`FAIL_AccessViolation`|Nastąpiła próba odczytu lub zapisu pamięci chronionej. Nie są obsługiwane w programie .NET Framework 4.|  
|`FAIL_CodeContract`|Wystąpił błąd kodu kontraktu. Zobacz [kodu umów](../../../../docs/framework/debug-trace-profile/code-contracts.md).|  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [iclrpolicymanager::setactiononfailure —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metody, aby uzyskać listę [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości hosta można użyć do określenia akcje zasad warunki błędu. Aby uzyskać więcej informacji na temat regionów krytyczne i niekrytyczne kodu, zobacz [eclroperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetActionOnFailure, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
