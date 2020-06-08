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
ms.openlocfilehash: b270a6691d4e4ee4a5d0b42f424694eb7993e4e7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504150"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda
Zwraca interfejs reprezentujący środowisko uruchomieniowe, do którego powiązano starsze zasady aktywacji, na przykład przy użyciu `useLegacyV2RuntimeActivationPolicy` atrybutu w wpisie pliku konfiguracji [ \<startup> elementu](../../configure-apps/file-schema/startup/startup-element.md) , bezpośrednio wykorzystując starsze interfejsy API aktywacji lub wywołując metodę [ICLRRuntimeInfo:: BindAsLegacyV2Runtime —](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 podczas Wymagane. obecnie jedyną prawidłową wartością tego parametru jest `IID_ICLRRuntimeInfo` .  
  
 `ppUnk`  
 określoną Wymagane. Gdy ta metoda zwraca, zawiera wskaźnik do interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , który reprezentuje środowisko uruchomieniowe, które zostało powiązane ze starszymi zasadami aktywacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została zakończona pomyślnie i zwróciło środowisko uruchomieniowe, które było powiązane ze starszymi zasadami aktywacji.|  
|S_FALSE|Metoda została ukończona pomyślnie, ale starsze środowisko uruchomieniowe nie zostało jeszcze powiązane.|  
|E_NOINTERFACE|Metoda znalazła środowisko uruchomieniowe powiązane ze starszymi zasadami aktywacji, ale `riid` nie jest obsługiwane przez to środowisko uruchomieniowe.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMetaHost, interfejs](iclrmetahost-interface.md)
- [Hosting](index.md)
