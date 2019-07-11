---
title: ICLRStrongName::GetHashFromHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8f6878d714704370c3f43451c9995a7c5adb5d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748148"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a>ICLRStrongName::GetHashFromHandle — Metoda
Generuje skrót nad zawartość pliku, który ma określone dojście do pliku, przy użyciu określonego algorytmu skrótu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hFile`  
 [in] Uchwyt pliku ma zostać obliczona wartość skrótu.  
  
 `piHashAlg`  
 [out w] Stała, który określa algorytm wyznaczania wartości skrótu. Użyj wartości zero dla domyślny algorytm.  
  
 `pbHash`  
 [out] Bufor zwrócone wyznaczania wartości skrótu.  
  
 `cchHash`  
 [in] Żądany maksymalny rozmiar `pbHash`.  
  
 `pchHash`  
 [out] Rozmiar w bajtach zwracanego `pbHash`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
