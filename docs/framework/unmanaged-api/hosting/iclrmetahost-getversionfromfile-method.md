---
title: ICLRMetaHost::GetVersionFromFile — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
ms.openlocfilehash: a237dff63015cda2cf2ca86a64bb4028ec9b6e2c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140919"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile — Metoda
Pobiera oryginalną wersję kompilacji .NET Framework zestawu (przechowywaną w metadanych), uwzględniając ścieżkę pliku. Ta metoda zastępuje funkcję [GetFileVersion —](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFilePath`  
 podczas Pełna ścieżka pliku zestawu.  
  
 `pwzbuffer`  
 określoną Wersja kompilacji .NET Framework przechowywana w metadanych w formacie "v*A*. *B*[. *X*] ". *A*, *B*i *X* to liczby dziesiętne, które odpowiadają wersji głównej, wersji pomocniczej i numer kompilacji. Długość tego ciągu jest ograniczona do wartości MAX_PATH.  
  
> [!NOTE]
> Dane wyjściowe są zgodne z nazwą katalogu dla .NET Framework wersji, ponieważ pojawia się w obszarze C:\Windows\Microsoft.NET\Framework.  
  
 Przykładowe wartości to "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" i "v 4.0. *X*", gdzie *x* zależy od zainstalowanego numeru kompilacji. Należy zauważyć, że prefiks "v" jest wymagany.  
  
 `pcchBuffer`  
 [in. out] Rozmiar `pwzbuffer`, aby uniknąć przekroczeń buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pwzbuffer` lub `pcchBuffer` ma wartość null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Bufor jest za mały.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMetaHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
