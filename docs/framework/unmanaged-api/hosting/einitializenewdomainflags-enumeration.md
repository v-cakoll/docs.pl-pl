---
title: EInitializeNewDomainFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 3693285e13d0650f7662e2187471027cc4c40704
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129421"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags — Wyliczenie
Umożliwia hostowi zapewnienie środowiska uruchomieniowego z informacjami o inicjalizacji domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|Brak flag.|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|Informuje środowisko uruchomieniowe języka wspólnego (CLR), że host nie wprowadzi zmian w stanie zabezpieczeń domeny aplikacji w metodzie <xref:System.AppDomainManager.InitializeNewDomain%2A>.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda [ICLRDomainManager:: SetAppDomainManagerType —](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) przyjmuje parametr typu `EInitializeNewDomainFlags`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [SetAppDomainManagerType, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
