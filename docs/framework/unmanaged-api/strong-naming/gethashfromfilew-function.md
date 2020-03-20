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
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175086"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW — Funkcja
Generuje skrót nad zawartością pliku określonego przez ciąg Unicode.  
  
 Ta funkcja została przestarzała. Zamiast tego należy użyć metody [ICLRStrongName::GetHashFromFileW.](../hosting/iclrstrongname-gethashfromfilew-method.md)  
  
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
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest taka sama jak [GetHashFromFile](gethashfromfile-function.md), z tą różnicą, że specyfikacja nazwy pliku jest Unicode zamiast ANSI.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h (Nazwa siła)-h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetHashFromFileW, metoda](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile, metoda](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
