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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2ca00b660a9cbb408fd1175e94a4242dae5f1a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523964"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>ICLRStrongName::GetHashFromFileW — Metoda
Generuje skrót nad zawartość pliku określonego przez ciąg Unicode.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Nazwa pliku do wyznaczania wartości skrótu Unicode.  
  
 `piHashAlg`  
 [out w] Algorytm, który ma być używana podczas generowania skrótów. Nieprawidłowa algorytmy są identyczne ze zdefiniowanymi przez interfejs CryptoAPI Win32. Jeśli `piHashAlg` jest równa 0, CALG_SHA 1 jest używany domyślny algorytm.  
  
 `pbHash`  
 [out] Tablica bajtów zawierająca wygenerowanego skrótu.  
  
 `cchHash`  
 [in] Maksymalny rozmiar buforu wskazywany przez `pbHash`.  
  
 `pchHash`  
 [out] Rozmiar w bajtach z `pbHash`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest taka sama jak [iclrstrongname::gethashfromfile —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metody, z tą różnicą, że specyfikacji nazwa pliku jest Unicode zamiast ANSI.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [GetHashFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
