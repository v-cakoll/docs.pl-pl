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
ms.openlocfilehash: 9a88adec508d80a40ec044e5011d3115e197e334
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137491"
---
# <a name="gethashfromassemblyfilew-function"></a>GetHashFromAssemblyFileW — Funkcja
Pobiera skrót pliku określonego zestawu, przy użyciu określonego algorytmu skrótu. Należy określić ścieżkę do pliku zestawu jako ciąg Unicode.  
  
 Ta funkcja jest przestarzała. Użyj [iclrstrongname::gethashfromassemblyfilew —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Ścieżka do pliku ma zostać obliczona wartość skrótu. Ten parametr musi być ciąg Unicode.  
  
 `piHashAlg`  
 [out w] Stała, który określa algorytm wyznaczania wartości skrótu. Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.  
  
 `pbHash`  
 [out] Bufor zwrócone wyznaczania wartości skrótu.  
  
 `cchHash`  
 [in] Żądany maksymalny rozmiar `pbHash`.  
  
 `pchHash`  
 [out] Zwrócone rozmiar w bajtach, z `pbHash`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetHashFromAssemblyFileW, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [GetHashFromAssemblyFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
