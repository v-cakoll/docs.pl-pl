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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d59506b522e1c225912da4bc3bd62ca19d32eb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556089"
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg — Funkcja
Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu za pomocą informacji o wersji, które są odczytywane z pliku XML.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCfgStream`  
 [in] Wskaźnik do `IStream` obiekt, który odczytuje plik XML.  
  
 `reserved`  
 [in] Zarezerwowane do użytku w przyszłości. Użyj wartości 0 (zero) jako wartość.  
  
 `startupFlags`  
 [in] Wartość [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wyliczenia, która określa zachowanie uruchamiania środowiska CLR.  
  
 `rclsid`  
 [in] `CLSID` z koklas, która implementuje [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu. Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] `IID` Albo `ICorRuntimeHost` lub `ICLRRuntimeHost` interfejsu. Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Wskaźnik na adres zwrócony interfejs.  
  
## <a name="remarks"></a>Uwagi  
 Format pliku XML jest modelowane pliku konfiguracji standardowej aplikacji. Aby uzyskać więcej informacji na temat plików XML, zobacz [schemat pliku konfiguracji](../../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
