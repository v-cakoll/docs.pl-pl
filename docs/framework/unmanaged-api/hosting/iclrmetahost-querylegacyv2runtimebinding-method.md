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
ms.openlocfilehash: 90474a61b16d65565889bd69ef75616804d8bc60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140882"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda
Zwraca interfejs, który reprezentuje środowisko uruchomieniowe, do którego powiązano starsze zasady aktywacji, na przykład przy użyciu atrybutu `useLegacyV2RuntimeActivationPolicy` w wpisie pliku konfiguracji [elementu > start\<](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , przez bezpośrednie użycie starszych interfejsów API aktywacji lub wywołując metodę [ICLRRuntimeInfo:: BindAsLegacyV2Runtime —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 podczas Wymagane. obecnie jedyną prawidłową wartością tego parametru jest `IID_ICLRRuntimeInfo`.  
  
 `ppUnk`  
 określoną Wymagane. Gdy ta metoda zwraca, zawiera wskaźnik do interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , który reprezentuje środowisko uruchomieniowe, które zostało powiązane ze starszymi zasadami aktywacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została zakończona pomyślnie i zwróciło środowisko uruchomieniowe, które było powiązane ze starszymi zasadami aktywacji.|  
|S_FALSE|Metoda została ukończona pomyślnie, ale starsze środowisko uruchomieniowe nie zostało jeszcze powiązane.|  
|E_NOINTERFACE|Metoda znalazła środowisko uruchomieniowe powiązane ze starszymi zasadami aktywacji, ale `riid` nie jest obsługiwane przez to środowisko uruchomieniowe.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMetaHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
