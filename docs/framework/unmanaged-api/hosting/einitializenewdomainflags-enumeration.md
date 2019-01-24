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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 826e02789f6940923538f3e01744345dacf4b2ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705287"
---
# <a name="einitializenewdomainflags-enumeration"></a>EInitializeNewDomainFlags — Wyliczenie
Umożliwia hosta zapewnienie środowiska uruchomieniowego informacje dotyczące inicjowania domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|Bez flag.|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|Środowisko uruchomieniowe języka wspólnego (CLR) informuje, że host nie wprowadzi zmiany stanu zabezpieczeń domeny aplikacji w <xref:System.AppDomainManager.InitializeNewDomain%2A> metody.|  
  
## <a name="remarks"></a>Uwagi  
 [Iclrdomainmanager::setappdomainmanagertype —](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) metoda przyjmuje parametr typu `EInitializeNewDomainFlags`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [SetAppDomainManagerType, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
