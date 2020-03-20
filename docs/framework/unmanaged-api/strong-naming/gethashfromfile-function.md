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
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176984"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile — Funkcja
Generuje skrót nad zawartością określonego pliku.  
  
 Ta funkcja została przestarzała. Zamiast tego należy użyć metody [ICLRStrongName::GetHashFromFile.](../hosting/iclrstrongname-gethashfromfile-method.md)  
  
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
 [w] Nazwa pliku do mieszania.  
  
 `piHashAlg`  
 [w, na zewnątrz] Algorytm do użycia podczas generowania skrótu. Prawidłowe algorytmy są zdefiniowane przez Win32 CryptoAPI. Jeśli `piHashAlg` jest ustawiona na 0, używany jest domyślny algorytm CALG_SHA-1.  
  
 `pbHash`  
 [na zewnątrz] Tablica bajtów zawierająca wygenerowany skrót.  
  
 `cchHash`  
 [w] Maksymalny rozmiar buforu, który `pbHash` wskazuje.  
  
 `pchHash`  
 [na zewnątrz] Rozmiar (w bajtach) `pbHash`zwracanego .  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest taka sama jak [GetHashFromFileW](gethashfromfilew-function.md), z tą różnicą, że specyfikacja nazwy pliku jest ANSI zamiast Unicode.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h (Nazwa siła)-h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetHashFromFile, metoda](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW, metoda](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
