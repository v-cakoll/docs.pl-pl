---
title: "ICLRStrongName::GetHashFromFileW — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eec58e0cf062e405c757a506e9c26955009b710b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>ICLRStrongName::GetHashFromFileW — Metoda
Generuje skrót za pośrednictwem zawartość pliku określona przez ciąg Unicode.  
  
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
 [w, out] Algorytm używany podczas generowania skrótu. Prawidłowe algorytmy są zdefiniowane przez interfejs CryptoAPI Win32. Jeśli `piHashAlg` jest ustawiona na 0, CALG_SHA 1 jest używany domyślny algorytm.  
  
 `pbHash`  
 [out] Tablica bajtów zawierająca wygenerowanego wyznaczania wartości skrótu.  
  
 `cchHash`  
 [in] Maksymalny rozmiar buforu wskazywana przez `pbHash`.  
  
 `pchHash`  
 [out] Rozmiar w bajtach z `pbHash`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest taka sama jak [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metoda, z wyjątkiem tego, że nazwa pliku specyfikacji jest Unicode zamiast ANSI.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetHashFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
