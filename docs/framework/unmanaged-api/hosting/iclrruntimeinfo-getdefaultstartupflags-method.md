---
title: "ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73ad12e99a1ba98f6ea61775155cf1389118f754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda
Pobiera flagi uruchamiania i pliku konfiguracji hosta, który będzie używany do uruchomienia środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwStartupFlags`  
 [out] Wskaźnik do aktualnie ustawionych flag uruchomienia hosta.  
  
 `pwzHostConfigFile`  
 [out] Wskaźnik do ścieżki katalogu bieżącego pliku konfiguracji hosta.  
  
 `pcchHostConfigFile`  
 [w, out] W danych wejściowych, rozmiar `pwzHostConfigFile`, aby uniknąć przepełnienia buforu. Jeśli `pwzHostConfigFile` jest wartość null, metoda zwraca wymagany rozmiar `pwzHostConfigFile` wstępnej alokacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące HRESULT określonych oraz HRESULT błędów, które wskazuje niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca domyślne wartości flag (`STARTUP_CONCURRENT_GC` i `NULL`), lub wartości podane przez poprzednie wywołanie [ICLRRuntimeInfo::SetDefaultStartupFlags — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), i wartościami ustawionymi przez `CorBind*` metody, jeśli są one powiązane z tego środowiska wykonawczego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRRuntimeInfo — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
