---
title: ICLRRuntimeInfo::GetInterface — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f229e421cc69f2ff45110233c4c6c36d7a1fc4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771764"
---
# <a name="iclrruntimeinfogetinterface-method"></a>ICLRRuntimeInfo::GetInterface — Metoda
Ładuje środowisko CLR do bieżący proces i zwraca środowiska uruchomieniowego, wskaźniki interfejsu, takich jak [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [iclrstrongname —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), i [imetadatadispenserex —](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).  
  
 Ta metoda zastępuje wszystkie `CorBindTo`* funkcje w [przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) sekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `rclsid`  
 [in] Interfejs CLSID dla klasy coclass.  
  
 `riid`  
 [in] Identyfikatorem IID żądany `rclsid` interfejsu.  
  
 `ppUnk`  
 [out] Wskaźnik do interfejsu kwerendy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`ppUnk` ma wartość null.|  
|E_OUTOFMEMORY|Nie ma wystarczającej ilości pamięci dostępnej może obsłużyć żądania.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Środowiskiem uruchomieniowym w różnych była już powiązana starsze zasady 2 aktywacji wersji środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje, że CLR do załadowane, ale nie zainicjowane.  
  
 W poniższej tabeli przedstawiono obsługiwane kombinacje w celach `rclsid` i `riid`.  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|CLSID_CorMetaDataDispenser|IID_IMetaDataDispenser, IID_IMetaDataDispenserEx|  
|CLSID_CorMetaDataDispenserRuntime|IID_IMetaDataDispenser, IID_IMetaDataDispenserEx|  
|CLSID_CorRuntimeHost|IID_ICorRuntimeHost|  
|CLSID_CLRRuntimeHost|IID_ICLRRuntimeHost|  
|CLSID_TypeNameFactory|IID_ITypeNameFactory|  
|CLSID_CLRDebuggingLegacy|IID_ICorDebug|  
|||  
|CLSID_CLRStrongName|IID_ICLRStrongName|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
