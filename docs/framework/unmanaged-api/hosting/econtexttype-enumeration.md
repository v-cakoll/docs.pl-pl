---
title: EContextType — Wyliczenie
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: 5e82f542bdc364a52fc558e582134a7d8d554ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131143"
---
# <a name="econtexttype-enumeration"></a>EContextType — Wyliczenie
Opisuje kontekst zabezpieczeń aktualnie wykonywanego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eCurrentContext`|Wskazuje kontekst bieżącego wątku w czasie, gdy środowisko uruchomieniowe języka wspólnego (CLR) wywołuje metodę [IHostSecurityManager:: GetSecurityContext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) lub kontekst żądany przez środowisko CLR w wywołaniu [IHostSecurityManager:: SetSecurityContext — ](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)Metoda.|  
|`eRestrictedContext`|Wskazuje kontekst, w którym host ma niższe uprawnienia, takie jak moduł wyrzucania elementów bezużytecznych lub konstruktory klas lub modułów.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR dostarcza jedną z wartości `EContextType` jako wartość parametru w wywołaniach metody `IHostSecurityManager::GetSecurityContext` i `IHostSecurityManager::SetSecurityContext`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostSecurityContext, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
