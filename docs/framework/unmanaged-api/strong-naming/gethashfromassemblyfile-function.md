---
title: GetHashFromAssemblyFile — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: 866b34acae333f043d8e13f4d0ebd55f32046334
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140729"
---
# <a name="gethashfromassemblyfile-function"></a>GetHashFromAssemblyFile — Funkcja
Pobiera skrót określonego pliku zestawu przy użyciu określonego algorytmu wyznaczania wartości skrótu.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: GetHashFromAssemblyFile —](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szFilePath`  
 podczas Ścieżka do pliku, który ma zostać poddany skrótowi.  
  
 `piHashAlg`  
 [in. out] Stała, która określa algorytm wyznaczania wartości skrótu. Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.  
  
 `pbHash`  
 określoną Zwrócony bufor wyznaczania wartości skrótu.  
  
 `cchHash`  
 podczas Żądany maksymalny rozmiar `pbHash`.  
  
 `pchHash`  
 określoną Zwrócony rozmiar w bajtach `pbHash`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetHashFromAssemblyFile, metoda](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [GetHashFromAssemblyFileW, metoda](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
