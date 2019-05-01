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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abbf893b3d49101b5cc9d38ffc31b171ff023f8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965038"
---
# <a name="certverifyauthenticodelicense-function"></a>Funkcja CertVerifyAuthenticodeLicense
Sprawdza poprawność licencję Authenticode XrML.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pLicenseBlob`  
 [in] Licencja Authenticode XrML do weryfikacji.  
  
 Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.  
  
 `dwFlags`  
 [in] Opcjonalnie. Kombinacją następujących wartości:  
  
- AXL_REVOCATION_NO_CHECK  
  
- AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
- AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
- AXL_URL_CACHE_ONLY_RETRIEVAL  
  
- AXL_LIFETIME_SIGNING  
  
- AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 [out] Aby odbierać informacje podpisującej. Jeśli licencja nie został podpisany, `dwError` jest ustawiona na TRUST_E_NOSIGNATURE. Jest odpowiedzialny za obiektu wywołującego, aby zwolnić zasoby przy użyciu [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) funkcji po ich użyciu.  
  
 Zobacz [struktura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 [out] Do odbierania informacji stamper czasu, jeśli jest dostępny. Jeśli licencja nie sygnaturami czasowymi, `dwError` jest ustawiona na TRUST_E_NOSIGNATURE. Jest odpowiedzialny za obiektu wywołującego, aby zwolnić zasoby przy użyciu [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) funkcji po ich użyciu.  
  
 Zobacz [struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
- [GetHashFromHandle, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
