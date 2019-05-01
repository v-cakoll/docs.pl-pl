---
title: GetHashFromFileW — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9be512bab30e08ddeb7deadf8a29263e928549a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000379"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW — Funkcja
Generuje skrót nad zawartość pliku określonego przez ciąg Unicode.  
  
 Ta funkcja jest przestarzała. Użyj [iclrstrongname::gethashfromfilew —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metody zamiast tego.  
  
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
  
## <a name="parameters"></a>Parametry  
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
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest taka sama jak [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), z tą różnicą, że specyfikacja nazwy plików Unicode zamiast ANSI.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetHashFromFileW, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
