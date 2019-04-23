---
title: Funkcja CertTimestampAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ac7cf92fb9c57491ff45e664513c0e82f22db9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111725"
---
# <a name="certtimestampauthenticodelicense-function"></a>Funkcja CertTimestampAuthenticodeLicense
Sygnatury czasowe wiadomość Authenticode XrML licencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSignedLicenseBlob`  
 [in] Podpisem Authenticode XrML licencja na mieć sygnaturę czasową. Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.  
  
 `pwszTimestampURI`  
 [in] Identyfikator URI serwera sygnaturę czasową.  
  
 `pTimestampSignatureBlob`  
 [out] Wskaźnik do CRYPT_DATA_BLOB otrzymywać sygnatury sygnatura czasowa algorytmem Base64. Odpowiada za wywołującego bezpłatne `pTimestampSignatureBlob` -> `pbData` z `HepFree()` po użyciu. Zobacz [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.  
  
## <a name="remarks"></a>Uwagi  
 Podpis sygnatura czasowa jest faktycznie PKCS #7 SignedData komunikatu informującego, których zawartość jest binarną formę SignatureValue z poziomu podpisu licencji. Zasadniczo jest to zabezpieczenie kontrsygnatury licencji.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli funkcja się powiedzie. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
