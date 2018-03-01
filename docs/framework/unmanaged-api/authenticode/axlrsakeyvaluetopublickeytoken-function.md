---
title: Funkcja _AxlRSAKeyValueToPublicKeyToken
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1380f658d9c154d9ea41228cace5f9a3eed39b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 `S_OK`Jeśli funkcja zakończy się powodzeniem. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
