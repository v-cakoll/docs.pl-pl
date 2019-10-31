---
title: GetHashFromFile — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: ffa25b1ec6fda80099f333c1d0a4cf57b76379e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140692"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile — Funkcja
Generuje skrót do zawartości określonego pliku.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: GetHashFromFile —](../hosting/iclrstrongname-gethashfromfile-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szFilePath`  
 podczas Nazwa pliku do skrótu.  
  
 `piHashAlg`  
 [in. out] Algorytm, który ma być używany podczas generowania skrótu. Prawidłowymi algorytmami są te zdefiniowane przez interfejs CryptoAPI Win32. Jeśli `piHashAlg` jest ustawiona na 0, zostanie użyty domyślny algorytm CALG_SHA-1.  
  
 `pbHash`  
 określoną Tablica bajtowa zawierająca wygenerowany skrót.  
  
 `cchHash`  
 podczas Maksymalny rozmiar buforu, do którego `pbHash` wskazuje.  
  
 `pchHash`  
 określoną Rozmiar w bajtach zwracanej `pbHash`.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest taka sama jak [GetHashFromFileW —](gethashfromfilew-function.md), z tą różnicą, że Specyfikacja nazwy pliku jest ANSI zamiast Unicode.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetHashFromFile, metoda](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW, metoda](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
