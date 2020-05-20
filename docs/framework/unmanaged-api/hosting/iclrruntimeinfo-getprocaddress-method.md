---
title: ICLRRuntimeInfo::GetProcAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: 2690a5c2e7c499d68ef9e903c62bff8f85e72e8e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703867"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a>ICLRRuntimeInfo::GetProcAddress — Metoda
Pobiera adres określonej funkcji, która została wyeksportowana z aparatu plików wykonywalnych języka wspólnego (CLR) skojarzonego z tym interfejsem.  
  
 Ta metoda zastępuje funkcję [GetRealProcAddress —](getrealprocaddress-function.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a>Parametry  
 `pszProcName`  
 podczas Nazwa funkcji wyeksportowanej.  
  
 `ppProc`  
 określoną Adres wyeksportowanej funkcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pszProcName`lub `ppProc` ma wartość null.|  
|CLR_E_SHIM_RUNTIMEEXPORT|Określona funkcja nie jest wyeksportowaną funkcją.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje załadowanie środowiska CLR, ale nie jego inicjalizację.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
