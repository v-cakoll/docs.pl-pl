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
ms.openlocfilehash: 69ba58cc8c5235a15749281b3107481be9528f84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503981"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>ICLRStrongName::StrongNameKeyGen — Metoda
Tworzy nową parę kluczy publiczny/prywatny w celu użycia silnej nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 podczas Nazwa żądanego kontenera kluczy. `wszKeyContainer`do wygenerowania nazwy tymczasowej musi być niepustym ciągiem lub wartością null.  
  
 `dwFlags`  
 podczas Wartość określająca, czy klucz ma pozostać zarejestrowany. Obsługiwane są następujące wartości:  
  
- 0x00000000 — używany, gdy `wszKeyContainer` ma wartość null, aby wygenerować nazwę kontenera kluczy tymczasowych.  
  
- 0x00000001 ( `SN_LEAVE_KEY` ) — określa, że klucz powinien pozostać zarejestrowany.  
  
 `ppbKeyBlob`  
 określoną Zwracana para kluczy publiczny/prywatny.  
  
 `pcbKeyBlob`  
 określoną Rozmiar, w bajtach, z `ppbKeyBlob` .  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 [ICLRStrongName:: StrongNameKeyGen —](iclrstrongname-strongnamekeygen-method.md) Metoda tworzy klucz 1024-bitowy. Po pobraniu klucza należy wywołać metodę [ICLRStrongName:: StrongNameFreeBuffer —](iclrstrongname-strongnamefreebuffer-method.md) , aby zwolnić przydzieloną pamięć.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameKeyGenEx, metoda](iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName, interfejs](iclrstrongname-interface.md)
