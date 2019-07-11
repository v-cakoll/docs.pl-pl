---
title: ICLRRuntimeInfo::SetDefaultStartupFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2996acd9678557b08fcfa543ecc7648ed639b143
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748340"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a>ICLRRuntimeInfo::SetDefaultStartupFlags — Metoda
Ustawia flagi uruchamiania i pliku konfiguracyjnego hosta, która będzie służyć do uruchomienia w środowisku uruchomieniowym. Ta metoda zastępuje użycia `startupFlags` parametru w [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i [corbindtoruntimehost —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwStartupFlags`  
 [in] Flagi uruchamiania hosta można ustawić. Za pomocą tego samego flag jako za pomocą [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i [corbindtoruntimehost —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkcji.  
  
 `pwzHostConfigFile`  
 [in] Ścieżka katalogu pliku konfiguracyjnego hosta, aby ustawić.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące HRESULT określonych oraz błędów HRESULT, wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Wielowątkowe hosta należy synchronizować wywołania tej metody. W przeciwnym razie wątek A mogą wywołać `SetStartupFlags` metody, gdy wątek B zakończy się po wywołaniu `SetStartupFlags` i przed wątku B uruchamia środowisko wykonawcze.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
