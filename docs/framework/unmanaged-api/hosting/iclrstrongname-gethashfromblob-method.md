---
title: ICLRStrongName::GetHashFromBlob — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: 0c9adcc252fe16c95da8b2afca45bb2ee5dc545a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135203"
---
# <a name="iclrstrongnamegethashfromblob-method"></a>ICLRStrongName::GetHashFromBlob — Metoda
Pobiera skrót zestawu pod określonym adresem pamięci przy użyciu określonego algorytmu wyznaczania wartości skrótu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbBlob`  
 podczas Wskaźnik do adresu bloku pamięci, który ma zostać zmieszany.  
  
 `cchBlob`  
 podczas Długość (w bajtach) bloku pamięci.  
  
 `piHashAlg`  
 [in. out] Stała, która określa algorytm wyznaczania wartości skrótu. Użyj wartości zero dla algorytmu domyślnego.  
  
 `pbHash`  
 określoną Zwrócony bufor wyznaczania wartości skrótu.  
  
 `cchHash`  
 podczas Żądany maksymalny rozmiar `pbHash`.  
  
 `pchHash`  
 określoną Rozmiar w bajtach zwracanej `pbHash`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
