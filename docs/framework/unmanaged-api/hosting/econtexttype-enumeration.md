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
ms.openlocfilehash: b93b27957cc715a5b4718dd9ef61cd11f4a39914
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493422"
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
  
|Członek|Opis|  
|------------|-----------------|  
|`eCurrentContext`|Wskazuje kontekst bieżącego wątku w czasie, gdy środowisko uruchomieniowe języka wspólnego (CLR) wywołuje metodę [IHostSecurityManager:: GetSecurityContext —](ihostsecuritymanager-getsecuritycontext-method.md) lub kontekst żądany przez środowisko CLR w wywołaniu metody [IHostSecurityManager:: SetSecurityContext —](ihostsecuritymanager-setsecuritycontext-method.md) .|  
|`eRestrictedContext`|Wskazuje kontekst, w którym host ma niższe uprawnienia, takie jak moduł wyrzucania elementów bezużytecznych lub konstruktory klas lub modułów.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR dostarcza jedną z `EContextType` wartości jako wartość parametru w wywołaniach `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` metod i.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostSecurityContext — Interfejs](ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interfejs](ihostsecuritymanager-interface.md)
- [Hosting — Wyliczenia](hosting-enumerations.md)
