---
title: ICorRuntimeHost::GetConfiguration — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1a044d1600f7e21e3abfbf704daef5213617b4c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780047"
---
# <a name="icorruntimehostgetconfiguration-method"></a>ICorRuntimeHost::GetConfiguration — Metoda
Pobiera obiekt, który zezwala hostów do określenia konfiguracji wywołania zwrotnego środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pConfiguration`  
 [out] Wskaźnik na adres [icorconfiguration —](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) obiekt, który może służyć do konfigurowania środowiska CLR.  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR musi być skonfigurowany przed inicjacji; w przeciwnym razie `GetConfiguration` metoda zwraca wartość HRESULT wskazująca na wystąpienie błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Zobacz także

- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
