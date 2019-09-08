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
ms.openlocfilehash: aaf76d4c3d0f5fb59aeb35fae7a7020ee97b74d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776476"
---
# <a name="certtimestampauthenticodelicense-function"></a>Funkcja CertTimestampAuthenticodeLicense
Sygnatura czasowa oznacza licencję z kodem XrML Authenticode.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSignedLicenseBlob`  
 podczas Sygnatura czasowa podpisanej licencji na technologię Authenticode. Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `pwszTimestampURI`  
 podczas Identyfikator URI serwera sygnatur czasowych.  
  
 `pTimestampSignatureBlob`  
 określoną Wskaźnik do CRYPT_DATA_BLOB, aby otrzymać sygnaturę sygnatury czasowej zakodowaną algorytmem Base64. Jest on odpowiedzialny `pTimestampSignatureBlob` za bezpłatne -> `pbData` korzystanie z `HepFree()` programu. Zobacz strukturę [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
## <a name="remarks"></a>Uwagi  
 Sygnatura czasowa jest w rzeczywistości certyfikatem PKCS #7 SignedData, którego zawartość jest binarną formą SignatureValue z podpisu licencji. Zasadniczo to pełni rolę sygnatury z licencją.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli funkcja się powiedzie. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](index.md)
