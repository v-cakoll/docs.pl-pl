---
title: ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: 0ce822533b0699f3467dc08044aa4dab59285a77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120314"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda
Pobiera flagi uruchamiania i plik konfiguracji hosta, który zostanie użyty do uruchomienia środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwStartupFlags`  
 określoną Wskaźnik do ustawionych obecnie flag uruchamiania hosta.  
  
 `pwzHostConfigFile`  
 określoną Wskaźnik do ścieżki katalogu bieżącego pliku konfiguracji hosta.  
  
 `pcchHostConfigFile`  
 [in. out] Na wejściu rozmiar `pwzHostConfigFile`, aby uniknąć przekroczeń buforu. Jeśli `pwzHostConfigFile` ma wartość null, metoda zwraca wymagany rozmiar `pwzHostConfigFile` do wstępnego przydzielenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT, a także błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartości domyślnych flag (`STARTUP_CONCURRENT_GC` i `NULL`) albo wartości dostarczonych przez poprzednie wywołanie [metody ICLRRuntimeInfo:: SetDefaultStartupFlags —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)lub wartości ustawionych przy użyciu dowolnej metody `CorBind*`, jeśli są one powiązane z tym środowiskiem uruchomieniowym.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
