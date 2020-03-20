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
ms.openlocfilehash: 8f2d74531233f2ba423c39126ddc43e499cbb5d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176373"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>ICLRStrongName::GetHashFromFileW — Metoda
Generuje skrót nad zawartością pliku określonego przez ciąg Unicode.  
  
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
 [w] Nazwa unicode pliku do mieszania.  
  
 `piHashAlg`  
 [w, na zewnątrz] Algorytm do użycia podczas generowania skrótu. Prawidłowe algorytmy są zdefiniowane przez Win32 CryptoAPI. Jeśli `piHashAlg` jest ustawiona na 0, używany jest domyślny algorytm CALG_SHA-1.  
  
 `pbHash`  
 [na zewnątrz] Tablica bajtów zawierająca wygenerowany skrót.  
  
 `cchHash`  
 [w] Maksymalny rozmiar buforu wskazywowany przez `pbHash`.  
  
 `pchHash`  
 [na zewnątrz] Rozmiar w bajtach `pbHash`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest taka sama jak [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metody, z tą różnicą, że specyfikacja nazwy pliku jest Unicode zamiast ANSI.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetHashFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
