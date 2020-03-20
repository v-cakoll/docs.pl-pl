---
title: CorBindToRuntimeByCfg — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: 4fbc6e7ea531f65a6b1cd0ec93f4847ab8e4fe83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178248"
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg — Funkcja
Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu przy użyciu informacji o wersji, który jest odczytywany z pliku XML.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCfgStream`  
 [w] Wskaźnik do `IStream` obiektu, który odczytuje plik XML.  
  
 `reserved`  
 [w] Zarezerwowane do wykorzystania w przyszłości. Użyj 0 (zero) jako wartości.  
  
 `startupFlags`  
 [w] Wartość wyliczenia [STARTUP_FLAGS,](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) która określa zachowanie uruchamiania programu CLR.  
  
 `rclsid`  
 [w] Coclass, `CLSID` który implementuje interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) Obsługiwane wartości są CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 [w] Interfejs `IID` `ICorRuntimeHost` lub `ICLRRuntimeHost` interfejs. Obsługiwane wartości są IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 [na zewnątrz] Wskaźnik do adresu zwracanego interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Format pliku XML jest modelowany według standardowego pliku konfiguracyjnego aplikacji. Aby uzyskać więcej informacji o plikach XML, zobacz [Schemat pliku konfiguracji](../../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost — Funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
