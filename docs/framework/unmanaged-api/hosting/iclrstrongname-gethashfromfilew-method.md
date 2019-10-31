---
title: ICLRStrongName::GetHashFromFileW — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 553acc178bc5805b5afef5931fefc8ad74cbac39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135171"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>ICLRStrongName::GetHashFromFileW — Metoda
Generuje skrót do zawartości pliku określonego przez ciąg Unicode.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 podczas Nazwa Unicode pliku do skrótu.  
  
 `piHashAlg`  
 [in. out] Algorytm, który ma być używany podczas generowania skrótu. Prawidłowymi algorytmami są te zdefiniowane przez interfejs CryptoAPI Win32. Jeśli `piHashAlg` jest ustawiona na 0, zostanie użyty domyślny algorytm CALG_SHA-1.  
  
 `pbHash`  
 określoną Tablica bajtowa zawierająca wygenerowany skrót.  
  
 `cchHash`  
 podczas Maksymalny rozmiar buforu wskazywany przez `pbHash`.  
  
 `pchHash`  
 określoną Rozmiar w bajtach `pbHash`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest taka sama jak Metoda [ICLRStrongName:: GetHashFromFile —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , z tą różnicą, że Specyfikacja nazwy pliku jest Unicode zamiast ANSI.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetHashFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
