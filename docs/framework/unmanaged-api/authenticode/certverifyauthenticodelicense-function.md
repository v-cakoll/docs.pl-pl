---
title: Funkcja CertVerifyAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
ms.openlocfilehash: 7cd25a24533b04dc45ee734f9e9639391311405a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099742"
---
# <a name="certverifyauthenticodelicense-function"></a>Funkcja CertVerifyAuthenticodeLicense
Weryfikuje ważność licencji XrML Authenticode.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pLicenseBlob`  
 podczas Licencja na umowę XrML Authenticode do zweryfikowania.  
  
 Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `dwFlags`  
 podczas Obowiązkowe. Kombinacja następujących wartości:  
  
- AXL_REVOCATION_NO_CHECK  
  
- AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
- AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
- AXL_URL_CACHE_ONLY_RETRIEVAL  
  
- AXL_LIFETIME_SIGNING  
  
- AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 określoną , Aby uzyskać informacje dotyczące osoby podpisującej. Jeśli licencja nie została podpisana, `dwError` jest ustawiona na TRUST_E_NOSIGNATURE. Jest on odpowiedzialny za zwolnienie zasobów przy użyciu funkcji [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) po użyciu.  
  
 Zobacz [strukturę AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 określoną W celu uzyskania informacji o sygnaturze czasowej, jeśli są dostępne. Jeśli licencja nie była sygnaturą czasową, `dwError` jest ustawiona na TRUST_E_NOSIGNATURE. Jest on odpowiedzialny za zwolnienie zasobów przy użyciu funkcji [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) po użyciu.  
  
 Zobacz [strukturę AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`, jeśli się powiedzie. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](index.md)
- [GetHashFromHandle, metoda](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
