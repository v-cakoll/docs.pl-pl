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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a261d9164e8714531eab1fe9fc8148304e6d5bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432885"
---
# <a name="econtexttype-enumeration"></a>EContextType — Wyliczenie
W tym artykule opisano wątku aktualnie wykonywane w kontekście zabezpieczeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eCurrentContext`|Wskazuje kontekstu w bieżącym wątku w momencie wywołania środowisko uruchomieniowe języka wspólnego (CLR) [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metody lub kontekstu żądanego przez środowisko CLR w wywołaniu [ IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) metody.|  
|`eRestrictedContext`|Wskazuje kontekst, w odniesieniu do której host ma niższe uprawnienia, takie jak moduł zbierający elementy bezużyteczne lub klasę lub moduł konstruktorów.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR udostępnia jeden z `EContextType` wartości jako wartości parametru w wywołaniach `IHostSecurityManager::GetSecurityContext` i `IHostSecurityManager::SetSecurityContext` metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostSecurityContext, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
