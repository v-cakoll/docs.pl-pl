---
title: ICLRStrongName::StrongNameKeyGen — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abeb731ecd66e4412f904b085abcfc7b5b3a3c4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169783"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>ICLRStrongName::StrongNameKeyGen — Metoda
Tworzy nową parę kluczy publiczny/prywatny do użytku silnej nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 [in] Nazwa żądany kontener kluczy. `wszKeyContainer` musi być niepustym ciągiem lub wartością null można wygenerować tymczasowej nazwy.  
  
 `dwFlags`  
 [in] Wartość, która określa, czy należy pozostawić klawisz zarejestrowany. Obsługiwane są następujące wartości:  
  
-   0x00000000 — używany podczas `wszKeyContainer` ma wartość null, aby wygenerować nazwę kontenera kluczy tymczasowych.  
  
-   0x00000001 (`SN_LEAVE_KEY`) — określa, że klucz powinien być zarejestrowany po lewej.  
  
 `ppbKeyBlob`  
 [out] Zwrócone pary kluczy publiczny/prywatny.  
  
 `pcbKeyBlob`  
 [out] Rozmiar w bajtach z `ppbKeyBlob`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 [Iclrstrongname::strongnamekeygen —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metoda tworzy klucz 1024-bitowy. Po pobraniu klucza, należy wywołać [iclrstrongname::strongnamefreebuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodę, aby zwolnić alokacji pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameKeyGenEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
