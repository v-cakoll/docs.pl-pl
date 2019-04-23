---
title: Authenticode (niezarządzana dokumentacja interfejsu API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408219307015d5c39cb581b3884ed9810f4c0566
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216356"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (niezarządzana dokumentacja interfejsu API)
Obsługuje moduł tworzenia i weryfikacji licencji Authenticode XrML.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcja _AxlGetIssuerPublicKeyHash](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 Pobiera Skrót SHA-1 klucza publicznego skojarzonego z kluczem prywatnym, który jest używany do podpisywania określonego certyfikatu.  
  
 [Funkcja _AxlPublicKeyBlobToPublicKeyToken](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 Oblicza silnej nazwy token klucza publicznego z formatu publickeyblob — dostawcy usług Kryptograficznych.  
  
 [Funkcja _AxlRSAKeyValueToPublicKeyToken](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 Konwertuje wyznaczanie modułu i wykładnik silnej nazwy token klucza publicznego.  
  
 [Funkcja CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 Zwalnia zasoby przydzielone do struktura AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [Funkcja CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 Zwalnia zasoby przydzielone do struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [Funkcja CertTimestampAuthenticodeLicense](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 Licencja Authenticode XrML utworzone przez CertCreateAuthenticodeLicense sygnatury czasowe.  
  
 [Funkcja CertVerifyAuthenticodeLicense](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 Sprawdza poprawność licencję Authenticode XrML.  
  
 [Struktura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 Definiuje informacje podpisu Authenticode.  
  
 [Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 Definiuje informacje stamper czasu Authenticode.  
  
## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API — informacje](../../../../docs/framework/unmanaged-api/index.md)
