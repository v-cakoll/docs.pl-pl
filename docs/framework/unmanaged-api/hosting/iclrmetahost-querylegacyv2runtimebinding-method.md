---
title: "ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c273a1690828e37c8f7fcf5071e42e5bb2c58228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding — Metoda
Zwraca interfejs, który reprezentuje runtime, do którego zasad aktywacji starszych wersji został powiązany, na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu [ \<uruchamiania > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) wpis pliku konfiguracji, używając bezpośredniego aktywacji starszych interfejsów API, przez wywołanie [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [in] Required.Currently jest jedyną poprawną wartością dla tego parametru `IID_ICLRRuntimeInfo`.  
  
 `ppUnk`  
 [out] Wymagane. Gdy metoda zwróci wartość, zawiera wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejs, który reprezentuje środowiska uruchomieniowego, która została powiązana z zasad aktywacji starszych wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie i zwrócił środowiska uruchomieniowego, który był powiązany z zasad aktywacji starszych wersji.|  
|WARTOŚCI S_FALSE|Metoda zakończyła się pomyślnie, ale starszej wersji środowiska uruchomieniowego ma nie jeszcze został powiązany.|  
|E_NOINTERFACE|Metoda znaleziono środowiska uruchomieniowego, który był powiązany z zasad aktywacji starszych wersji, ale `riid` nie jest obsługiwany przez ten program obsługi.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRMetaHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
