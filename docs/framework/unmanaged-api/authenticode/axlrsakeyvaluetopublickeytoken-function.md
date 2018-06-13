---
title: Funkcja _AxlRSAKeyValueToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ef73f0f7599fdff887437756a5995591fd8ec89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402415"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a>Funkcja _AxlRSAKeyValueToPublicKeyToken
Konwertuje modulo i wykładnik silnej nazwy tokenu klucza publicznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pModulusBlob`  
 [in] Obiekt blob modulo algorytmem Base64 (z \<modulo > elementu).  Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
 `pExponentBlob`  
 [in] Obiekt blob wykładnik algorytmem Base64 (z \<wykładnik > elementu). Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
 `ppwszPublicKeyToken`  
 [out] Wskaźnik do WCHAR * do odbierania zakodowane w systemie szesnastkowym token klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli funkcja zakończy się powodzeniem. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
