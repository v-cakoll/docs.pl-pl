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
ms.openlocfilehash: c8ac959c192814562488ab916c8462b0baa0d8e6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703648"
---
# <a name="iclrruntimeinfogetinterface-method"></a>ICLRRuntimeInfo::GetInterface — Metoda
Ładuje środowisko CLR do bieżącego procesu i zwraca wskaźniki interfejsu środowiska uruchomieniowego, takie jak [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)i [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).  
  
 Ta metoda zastępuje wszystkie `CorBindTo` * funkcje w sekcji [przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `rclsid`  
 podczas Interfejs CLSID dla klasy coclass.  
  
 `riid`  
 podczas Identyfikator IID żądanego `rclsid` interfejsu.  
  
 `ppUnk`  
 określoną Wskaźnik do zapytania do interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`ppUnk`ma wartość null.|  
|E_OUTOFMEMORY|Za mało dostępnej pamięci, aby obsłużyć żądanie.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Inne środowisko uruchomieniowe zostało już powiązane ze starszymi zasadami aktywacji środowiska CLR w wersji 2.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje załadowanie środowiska CLR, ale nie jego inicjalizację.  
  
 W poniższej tabeli przedstawiono obsługiwane kombinacje dla programów `rclsid` i `riid` .  
  
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
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
