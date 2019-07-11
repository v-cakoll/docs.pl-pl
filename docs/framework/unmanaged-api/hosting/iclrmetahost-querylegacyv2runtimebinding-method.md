---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7312a50137ab8a5c066d5e140a1742ee1918b44
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776559"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda
Zwraca interfejs, który reprezentuje środowiska uruchomieniowego, do którego zasady starszych aktywacji została powiązana, na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu na [ \<uruchamiania > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) wpis w pliku konfiguracji, przy użyciu bezpośredniego Aktywacja starszych interfejsów API lub przez wywołanie metody [iclrruntimeinfo::bindaslegacyv2runtime —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 [in] Jedyna prawidłowa wartość dla tego parametru to Required.Currently `IID_ICLRRuntimeInfo`.  
  
 `ppUnk`  
 [out] Wymagane. Po powrocie z tej metody zawiera wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który reprezentuje powiązanej z zasad aktywacji starszej wersji środowiska uruchomieniowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie i zwrócony środowiska uruchomieniowego, który był powiązany z zasad aktywacji starszej wersji.|  
|S_FALSE|Metoda została ukończona pomyślnie, ale starszej wersji środowiska uruchomieniowego nie została jeszcze powiązana.|  
|E_NOINTERFACE|Metoda znaleziono środowiska uruchomieniowego, który był powiązany z zasad aktywacji starszej wersji, ale `riid` nie jest obsługiwany przez ten program obsługi.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMetaHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
