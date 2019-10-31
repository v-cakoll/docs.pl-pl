---
title: _AxlRSAKeyValueToPublicKeyToken, funkcja
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
ms.openlocfilehash: 1f53df33a65d3f75b7574eda3507e370c2e086ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099814"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a>\_funkcja AxlRSAKeyValueToPublicKeyToken

Konwertuje modulo i wykładnik na token klucza publicznego o silnej nazwie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pModulusBlob`  
 podczas Obiekt BLOB modułu kodowanego algorytmem Base64 (z elementu \<moduł >).  Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `pExponentBlob`  
 podczas Obiekt BLOB wykładnika zakodowany algorytmem Base64 (z \<wykładnika > elementu). Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `ppwszPublicKeyToken`  
 określoną Wskaźnik do WCHAR *, aby otrzymać token klucza publicznego zakodowany w formacie szesnastkowym.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`, jeśli funkcja się powiedzie. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](index.md)
