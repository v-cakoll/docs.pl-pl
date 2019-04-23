---
title: StrongNameSignatureVerificationEx2 — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aab3b697a0bb2f58258816ce4f8133009b26f54a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220594"
---
# <a name="strongnamesignatureverificationex2-method"></a>StrongNameSignatureVerificationEx2 — Metoda
Weryfikuje podpis zestaw o silnej nazwie, a następnie udostępnia mapowanie klucz ECMA do rzeczywistego klucza.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Ścieżka do przenośnych (.exe lub .dll) pliku wykonywalnego w zestawie, który ma zostać zweryfikowany.  
  
 `fForceVerification`  
 [in] `true` przeprowadzić weryfikację, nawet jeśli jest to konieczne zastąpić ustawienia rejestru; w przeciwnym razie `false`.  
  
 `pbEcmaPublicKey`  
 [in] Wskaźnik do mapowania z ECMA klucza publicznego do rzeczywistego klucza używany podczas weryfikacji.  
  
 `cbEcmaPublicKey`  
 [in] Długość klucza publicznego rzeczywistych ECMA.  
  
 `pfWasVerified`  
 [out] `true` Jeśli podpisu silnej nazwy został zweryfikowany; w przeciwnym razie `false`. Ten parametr jest również ustawiona na `false` Jeśli Weryfikacja powiodła się z powodu ustawień rejestru.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli weryfikacja się powiodła. w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameSignatureVerification, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
