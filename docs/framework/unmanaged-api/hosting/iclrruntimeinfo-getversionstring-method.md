---
title: ICLRRuntimeInfo::GetVersionString — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
ms.openlocfilehash: 0b6ac83cdd0c88e87fdfd552c76c906a334f8928
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120298"
---
# <a name="iclrruntimeinfogetversionstring-method"></a>ICLRRuntimeInfo::GetVersionString — Metoda
Pobiera informacje o wersji środowiska uruchomieniowego języka wspólnego (CLR) skojarzone z danym interfejsem [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .  
  
 Ta metoda zastępuje następujące funkcje:  
  
- [GetRequestedRuntimeInfo —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
- [GetRequestedRuntimeVersion —](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzBuffer`  
 określoną Wersja kompilacji .NET Framework w formacie "v*A*. *B*[. *X*] ". *A*, *B*i *X* to liczby dziesiętne, które odpowiadają wersji głównej, wersji pomocniczej i numer kompilacji. *Symbol X* jest opcjonalny. Jeśli *X* nie istnieje, nie ma końcowej kropki.  
  
> [!NOTE]
> Ten parametr musi być zgodny z nazwą katalogu dla .NET Framework wersji, ponieważ pojawia się w obszarze C:\Windows\Microsoft.NET\Framework.  
  
 Przykładowe wartości to "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" i "v 4.0. *x*", gdzie *x* zależy od zainstalowanego numeru kompilacji. Należy zauważyć, że prefiks "v" jest obowiązkowy.  
  
 `pchBuffer`  
 [in. out] Określa rozmiar `pwzBuffer`, aby uniknąć przekroczeń buforu. Jeśli `pwzBuffer` jest `null`, `pchBuffer` zwraca wymagany rozmiar `pwzBuffer`, aby umożliwić wstępne przydzielanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pwzBuffer` lub `pchBuffer` ma wartość null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
