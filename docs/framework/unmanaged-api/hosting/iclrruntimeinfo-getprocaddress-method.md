---
title: ICLRRuntimeInfo::GetProcAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a95b6b7e20bbcd86dedf187c932f2cf74d37cdab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199183"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a>ICLRRuntimeInfo::GetProcAddress — Metoda
Pobiera adres określonej funkcji, która została wyeksportowana z środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z tym interfejsem.  
  
 Ta metoda zastępuje [getrealprocaddress —](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a>Parametry  
 `pszProcName`  
 [in] Nazwa eksportowanych funkcji.  
  
 `ppProc`  
 [out] Adres eksportowanych funkcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pszProcName` lub `ppProc` ma wartość null.|  
|CLR_E_SHIM_RUNTIMEEXPORT|Określona funkcja nie jest eksportowanych funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje, że CLR do załadowane, ale nie zainicjowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
