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
ms.openlocfilehash: 36851ac4573d0d65caffaa3f82a1f6fc8440a2d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092752"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a>ICLRRuntimeInfo::SetDefaultStartupFlags — Metoda
Ustawia flagi uruchamiania i plik konfiguracji hosta, który zostanie użyty do uruchomienia środowiska uruchomieniowego. Ta metoda zastępuje użycie parametru `startupFlags` w funkcjach [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i [CorBindToRuntimeHost —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwStartupFlags`  
 podczas Flagi uruchamiania hosta do ustawienia. Użyj tych samych flag co w przypadku funkcji [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) i [CorBindToRuntimeHost —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) .  
  
 `pwzHostConfigFile`  
 podczas Ścieżka katalogu pliku konfiguracji hosta do ustawienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT, a także błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Host wielowątkowy powinien synchronizować wywołania z tą metodą. W przeciwnym razie wątek A może wywoływać metodę `SetStartupFlags` po wykonaniu przez wątek B wywołania do `SetStartupFlags` i zanim wątek B uruchomi środowisko uruchomieniowe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
