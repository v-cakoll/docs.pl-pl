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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c39ad4638c7db45c481bd3dfccb0a82759397aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072586"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda
Pobiera flagi uruchamiania i pliku konfiguracyjnego hosta, która będzie służyć do uruchomienia w środowisku uruchomieniowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwStartupFlags`  
 [out] Wskaźnik flagi uruchamiania hosta, które są ustawione.  
  
 `pwzHostConfigFile`  
 [out] Wskaźnik do ścieżkę katalogu bieżącego pliku konfiguracji hosta.  
  
 `pcchHostConfigFile`  
 [out w] W danych wejściowych, rozmiar `pwzHostConfigFile`, aby uniknąć przepełnienia buforu. Jeśli `pwzHostConfigFile` jest wartość null, metoda zwraca wymagany rozmiar `pwzHostConfigFile` wstępnej alokacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące HRESULT określonych oraz błędów HRESULT, wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartości domyślne flagi (`STARTUP_CONCURRENT_GC` i `NULL`), lub wartości, dostarczone przez poprzednie wywołanie [iclrruntimeinfo::setdefaultstartupflags — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), lub wartości ustawione przez żaden z `CorBind*` metody, jeśli są one powiązane z tym środowisku uruchomieniowym.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
