---
title: ICLRMetaHost::EnumerateLoadedRuntimes — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0e1213128f5728f17225fbf6906d877dc64e86d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106616"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a>ICLRMetaHost::EnumerateLoadedRuntimes — Metoda
Zwraca wyliczenie, które zawiera prawidłową [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) wskaźnika interfejsu dla każdej wersji programu środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w danym procesie. Ta metoda zastępuje [getversionfromprocess —](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hndProcess`  
 [in] Uchwyt procesu do wglądu dla środowisk uruchomieniowych załadowane.  
  
 `ppEnumerator`  
 [out] <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> Wyliczenie [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsów odpowiadający każdej CLR, który jest ładowany przez proces.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`ppEnumerator` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest załadowany Wyświetla wszystkie środowiska uruchomieniowe, nawet wtedy, gdy zostały przestarzałe funkcje takie jak załadowane [CorBindToRuntime —](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMetaHost — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
