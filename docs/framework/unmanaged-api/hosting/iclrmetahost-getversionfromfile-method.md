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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1c8f5ea20d00d692e0eea0cba93ec4e73038e8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497447"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile — Metoda
Pobiera zestaw oryginalna wersja programu .NET Framework kompilacji (przechowywany w metadanych) podanej ścieżki pliku. Ta metoda zastępuje [getfileversion —](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFilePath`  
 [in] Ścieżka pliku kompletny zestaw.  
  
 `pwzbuffer`  
 [out] Wersja kompilacji programu .NET Framework, które są przechowywane w metadanych, w formacie "v*A*. *B*[. *X*] ". *A*, *B*, i *X* są liczby dziesiętne, które odpowiadają wersji głównej, pomocniczej wersji i numer kompilacji. Długość tego ciągu jest ograniczona do MAX_PATH.  
  
> [!NOTE]
>  Te dane wyjściowe odpowiada nazwę katalogu .NET Framework w wersji wyświetlaną w obszarze C:\Windows\Microsoft.NET\Framework.  
  
 Przykładowe wartości są "wartości v1.0.3705", "v1.1.4322" i "v2.0.50727" oraz "v4.0. *X*", gdzie *X* zależy od numeru kompilacji zainstalowane. Należy pamiętać, że jest wymagany prefiks "v".  
  
 `pcchBuffer`  
 [out w] Rozmiar `pwzbuffer` w celu uniknięcia przepełnienia buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pwzbuffer` lub `pcchBuffer` ma wartość null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Bufor jest za mały.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRMetaHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
