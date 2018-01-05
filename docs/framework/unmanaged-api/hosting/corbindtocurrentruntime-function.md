---
title: "CorBindToCurrentRuntime — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: HeaderDef
f1_keywords: CorBindToCurrentRuntime
helpviewer_keywords: CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9568d9420c686d5a906fb7f90570fe6a1d12046d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime — Funkcja
Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu za pomocą wersji informacje przechowywane w pliku XML. Format pliku XML jest modelowane pliku konfiguracji standardowej aplikacji. Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [schemat pliku konfiguracji](../../../../docs/framework/configure-apps/file-schema/index.md).  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Zobacz [ładowania środowiska CLR do procesu](http://msdn.microsoft.com/en-us/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFileName`  
 [in] Nazwa określająca wersję środowiska CLR, aby załadować plik konfiguracyjny aplikacji. Jeśli nazwa pliku nie jest w pełni kwalifikowana, zakłada się w tym samym katalogu co plik wykonywalny wywołania.  
  
 Wersja środowiska uruchomieniowego do załadowania jest opisane przez atrybut version w [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elementu w pliku konfiguracji.  
  
 Jeśli wersja nie jest określona lub `<requiredRuntime>` nie można znaleźć elementu, jest ładowany najnowszą wersję środowiska CLR, która jest zainstalowana na komputerze.  
  
 `rclsid`  
 [in] `CLSID` Klasy coclass, który implementuje albo [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu. Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] `IID` Interfejsu żądania dostępu. Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Wskaźnik interfejsu zwrócony.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [CorBindToRuntimeHost, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
