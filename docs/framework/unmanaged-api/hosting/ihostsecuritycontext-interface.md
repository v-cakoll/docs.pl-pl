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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c2500f013584ef4722ceaaaee91d5db54991639
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439302"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext — Interfejs
Umożliwia środowisko uruchomieniowe języka wspólnego (CLR), aby zachować informacje kontekstu zabezpieczeń zaimplementowana przez hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Capture, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|Pobiera Sklonowanie `IHostSecurityContext` wystąpienia zwrócone w wyniku wywołania [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).|  
  
## <a name="remarks"></a>Uwagi  
 Hosta można kontrolować kod dostęp do tokenów wątku przez kod zarówno CLR, jak i użytkownika. Zapewnia również Zabezpieczenia pełne informacje o kontekście jest przekazywany przez operacje asynchroniczne lub punktów kodowych z ograniczeniami kod dostępu. `IHostSecurityContext` hermetyzuje informacje kontekstu zabezpieczeń, które jest nieprzezroczysta dla środowiska uruchomieniowego. Środowisko uruchomieniowe przechwytuje te informacje przy użyciu `Capture`, i przenosi ją wysyłania elementu roboczego puli wątków, wykonanie finalizatora i konstruktory moduł i klasy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRHostProtectionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
