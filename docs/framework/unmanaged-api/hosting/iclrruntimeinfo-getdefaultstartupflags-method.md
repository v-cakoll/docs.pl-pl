---
title: ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: 8513787f48ae89632816face386bbcda20555dac
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703886"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>ICLRRuntimeInfo::GetDefaultStartupFlags — Metoda
Pobiera flagi uruchamiania i plik konfiguracji hosta, który zostanie użyty do uruchomienia środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwStartupFlags`  
 określoną Wskaźnik do ustawionych obecnie flag uruchamiania hosta.  
  
 `pwzHostConfigFile`  
 określoną Wskaźnik do ścieżki katalogu bieżącego pliku konfiguracji hosta.  
  
 `pcchHostConfigFile`  
 [in. out] Na wejściu, rozmiar `pwzHostConfigFile` , aby uniknąć przekroczeń buforu. Jeśli `pwzHostConfigFile` ma wartość null, metoda zwraca wymagany rozmiar `pwzHostConfigFile` dla wstępnej alokacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT, a także błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartości domyślnych flag ( `STARTUP_CONCURRENT_GC` i `NULL` ) lub wartości dostarczonych przez poprzednie wywołanie [metody ICLRRuntimeInfo:: SetDefaultStartupFlags —](iclrruntimeinfo-setdefaultstartupflags-method.md)lub wartości ustawionych przy użyciu dowolnej `CorBind*` metody, jeśli są one powiązane z tym środowiskiem uruchomieniowym.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
