---
title: GetHashFromAssemblyFileW — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4b748370ff1aff042923002ad827a0e39d99963
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799267"
---
# <a name="gethashfromassemblyfilew-function"></a>GetHashFromAssemblyFileW — Funkcja
Pobiera skrót określonego pliku zestawu przy użyciu określonego algorytmu wyznaczania wartości skrótu. Ścieżka do pliku zestawu musi być określona jako ciąg Unicode.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: GetHashFromAssemblyFileW —](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 podczas Ścieżka do pliku, który ma zostać poddany skrótowi. Ten parametr musi być ciągiem Unicode.  
  
 `piHashAlg`  
 [in. out] Stała, która określa algorytm wyznaczania wartości skrótu. Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.  
  
 `pbHash`  
 określoną Zwrócony bufor wyznaczania wartości skrótu.  
  
 `cchHash`  
 podczas Żądany maksymalny rozmiar `pbHash`.  
  
 `pchHash`  
 określoną Zwrócony rozmiar, w bajtach, z `pbHash`.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** StrongName.h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetHashFromAssemblyFileW, metoda](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [GetHashFromAssemblyFile, metoda](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
