---
title: ICLRRuntimeInfo::GetRuntimeDirectory — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
ms.openlocfilehash: b0a2e5f259fe1ee566f9cc25152b2d2a1f740bea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120341"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a>ICLRRuntimeInfo::GetRuntimeDirectory — Metoda
Pobiera katalog instalacyjny środowiska uruchomieniowego języka wspólnego (CLR) skojarzonego z tym interfejsem.  
  
 Ta metoda zastępuje funkcję [GetCORSystemDirectory —](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) w .NET Framework wersje 2,0, 3,0 i 3,5.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzBuffer`  
 określoną Zwraca katalog instalacji środowiska CLR. Ścieżka instalacji jest w pełni kwalifikowana; na przykład "c:\Windows\Microsoft.NET\Framework\v1.0.3705\\".  
  
 `pchBuffer`  
 [in. out] Określa rozmiar `pwzBuffer`, aby uniknąć przekroczeń buforu. Jeśli `pwzBuffer` ma wartość null, `pchBuffer` zwraca wymagany rozmiar `pwzBuffer`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pwzBuffer` lub `pchBuffer` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
