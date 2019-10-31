---
title: IHostSecurityContext — Interfejs
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: 993d16818b25dfefe1f53c7afd06bc9857d9eb24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121521"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext — Interfejs
Umożliwia środowisko uruchomieniowe języka wspólnego (CLR), aby zachować informacje kontekstu zabezpieczeń zaimplementowane przez hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Capture, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|Pobiera klon wystąpienia `IHostSecurityContext` zwróconego przez wywołanie [IHostSecurityManager:: GetSecurityContext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).|  
  
## <a name="remarks"></a>Uwagi  
 Host może kontrolować cały dostęp kodu do tokenów wątków przez środowisko CLR i kod użytkownika. Może także zapewnić, że pełne informacje kontekstu zabezpieczeń są przesyłane przez operacje asynchroniczne lub punkty kodowe z ograniczonym dostępem do kodu. `IHostSecurityContext` hermetyzuje informacje kontekstu zabezpieczeń, nieprzezroczyste dla środowiska uruchomieniowego. Środowisko uruchomieniowe przechwytuje te informacje przy użyciu `Capture`i przenosi je między elementami roboczymi puli wątków, wykonywaniem finalizatorów oraz konstruktorami modułów i klas.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostProtectionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
