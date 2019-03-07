---
title: Funkcja _AxlGetIssuerPublicKeyHash
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 252a3153a49867faf67051be01eeb141fa3ab681
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490349"
---
# <a name="axlgetissuerpublickeyhash-function"></a>Funkcja _AxlGetIssuerPublicKeyHash
Pobiera Skrót SHA-1 klucza publicznego skojarzonego z kluczem prywatnym, który jest używany do podpisywania określonego certyfikatu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pChainContext`  
 [in] Dostawcy usług Kryptograficznych blob klucza publicznego. Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.  
  
 `ppwszPublicKeyHash`  
 [out] Wskaźnik do WCHAR * do odbierania zakodowanego szesnastkowo token klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli funkcja się powiedzie; w przeciwnym razie `S_FALSE`.  
  
## <a name="see-also"></a>Zobacz także
- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
