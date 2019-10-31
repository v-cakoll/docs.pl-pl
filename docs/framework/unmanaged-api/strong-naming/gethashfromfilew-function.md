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
ms.openlocfilehash: db6f39119d143d27c0d3a80a9c65565d4dfd0d39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140676"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW — Funkcja
Generuje skrót do zawartości pliku określonego przez ciąg Unicode.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: GetHashFromFileW —](../hosting/iclrstrongname-gethashfromfilew-method.md) .  
  
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
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest taka sama jak [GetHashFromFile —](gethashfromfile-function.md), z tą różnicą, że Specyfikacja nazw plików jest Unicode zamiast ANSI.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetHashFromFileW, metoda](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile, metoda](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
