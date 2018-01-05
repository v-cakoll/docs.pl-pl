---
title: Funkcja CertVerifyAuthenticodeLicense
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertVerifyAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bab3a3bcee52a302345ccdcfad81e7f67efdd8d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>Parametry  
 `pLicenseBlob`  
 [in] Licencja Authenticode XrML do weryfikacji.  
  
 Zobacz [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
 `dwFlags`  
 [in] Opcjonalne. Kombinację następujących wartości:  
  
-   AXL_REVOCATION_NO_CHECK  
  
-   AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
-   AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
-   AXL_URL_CACHE_ONLY_RETRIEVAL  
  
-   AXL_LIFETIME_SIGNING  
  
-   AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 [out] Aby odbierać informacje podpisującej. Jeśli licencja nie został podpisany, `dwError` ma ustawioną wartość TRUST_E_NOSIGNATURE. Odpowiedzialność wywołującego, aby zwolnić zasoby przy użyciu [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) funkcja po użyciu.  
  
 Zobacz [struktura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 [out] Do odbierania informacji stamper czasu, jeśli jest dostępna. Jeśli licencja nie sygnaturami czasowymi `dwError` ma ustawioną wartość TRUST_E_NOSIGNATURE. Odpowiedzialność wywołującego, aby zwolnić zasoby przy użyciu [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) funkcja po użyciu.  
  
 Zobacz [struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)  
 [GetHashFromHandle, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
