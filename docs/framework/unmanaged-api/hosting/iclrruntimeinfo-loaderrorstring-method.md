---
title: ICLRRuntimeInfo::LoadErrorString — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b485811b0e7d2f657ff2d2c1d7a2aa135e48a335
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154690"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a>ICLRRuntimeInfo::LoadErrorString — Metoda
Tłumaczy wartość HRESULT do odpowiedniego komunikatu o błędzie dla określonej kultury.  
  
 Ta metoda zastępuje następujące funkcje:  
  
-   [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a>Parametry  
 `iResourceID`  
 [in] Wartość HRESULT do translacji.  
  
 `pwzBuffer`  
 [out] Ciąg komunikatu skojarzonego z danym elementem HRESULT.  
  
 `pcchBuffer`  
 [out w] Rozmiar `pwzbuffer` w celu uniknięcia przepełnienia buforu. Jeśli `pwzbuffer` ma wartość null, `pcchBuffer` zawiera oczekiwanego rozmiaru `pwzbuffer` umożliwia wstępne przydzielanie.  
  
 `iLocaleID`  
 [in] Identyfikator kultury. Aby użyć domyślnej kultury, należy określić -1.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pcchBuffer` ma wartość null.|  
|E_INVALIDARG|`pwzBuffer` ma wartość null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
