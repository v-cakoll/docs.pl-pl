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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26bee605724fd69d972a7e07c6fe6be2fbcabfa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563863"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a>ICLRRuntimeInfo::GetRuntimeDirectory — Metoda
Pobiera katalogu instalacji zestawu środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z tym interfejsem.  
  
 Ta metoda zastępuje [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) funkcja udostępniana w .NET Framework w wersji 2.0, 3.0 i 3.5.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzBuffer`  
 [out] Zwraca katalog instalacyjny środowiska CLR. Ścieżka instalacji jest w pełni kwalifikowany; na przykład "c:\windows\microsoft.net\framework\v1.0.3705\\".  
  
 `pchBuffer`  
 [out w] Określa rozmiar `pwzBuffer` w celu uniknięcia przepełnienia buforu. Jeśli `pwzBuffer` ma wartość null, `pchBuffer` zwraca wymagany rozmiar `pwzBuffer`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pwzBuffer` lub `pchBuffer` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
