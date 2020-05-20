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
ms.openlocfilehash: 2e22b8a2d0213b3bd766d80218d6f396721a90e1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703767"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a>ICLRMetaHost::EnumerateLoadedRuntimes — Metoda
Zwraca Wyliczenie, które zawiera prawidłowy wskaźnik interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) dla każdej wersji środowiska uruchomieniowego języka wspólnego (CLR), który jest ładowany w danym procesie. Ta metoda zastępuje funkcję [GetVersionFromProcess —](getversionfromprocess-function.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hndProcess`  
 podczas Dojście procesu do sprawdzenia pod kątem załadowanych środowiska uruchomieniowego.  
  
 `ppEnumerator`  
 określoną <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>Wyliczenie interfejsów [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) odpowiadających każdemu CLR, który jest ładowany przez proces.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`ppEnumerator`ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zawiera wszystkie załadowane środowiska uruchomieniowe, nawet jeśli zostały załadowane przy użyciu przestarzałych funkcji, takich jak [CorBindToRuntime](corbindtoruntime-function.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMetaHost, interfejs](iclrmetahost-interface.md)
- [Hosting](index.md)
