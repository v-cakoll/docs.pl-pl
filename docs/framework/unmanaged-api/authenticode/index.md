---
title: Authenticode (niezarządzana dokumentacja interfejsu API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 1b8b2222950c75f7f9d2ec2704f722087645cd7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132458"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (niezarządzana dokumentacja interfejsu API)
Obsługuje moduł tworzenia i weryfikacji licencji XrML Authenticode.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcja _AxlGetIssuerPublicKeyHash](axlgetissuerpublickeyhash-function.md)  
 Pobiera skrót SHA-1 klucza publicznego skojarzonego z kluczem prywatnym, który jest używany do podpisywania określonego certyfikatu.  
  
 [Funkcja _AxlPublicKeyBlobToPublicKeyToken](axlpublickeyblobtopublickeytoken-function.md)  
 Oblicza token klucza publicznego o silnej nazwie w formacie PublicKeyBlob — dostawcy usług kryptograficznych.  
  
 [Funkcja _AxlRSAKeyValueToPublicKeyToken](axlrsakeyvaluetopublickeytoken-function.md)  
 Konwertuje modulo i wykładnik na token klucza publicznego o silnej nazwie.  
  
 [Funkcja CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md)  
 Zwalnia zasoby przydzieloną dla struktury AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [Funkcja CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md)  
 Zwalnia zasoby przydzieloną dla struktury AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [Funkcja CertTimestampAuthenticodeLicense](certtimestampauthenticodelicense-function.md)  
 Sygnatura czasowa oznacza licencję na technologię XrML Authenticode utworzoną przez CertCreateAuthenticodeLicense.  
  
 [Funkcja CertVerifyAuthenticodeLicense](certverifyauthenticodelicense-function.md)  
 Weryfikuje ważność licencji XrML Authenticode.  
  
 [Struktura AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)  
 Definiuje informacje o podpisie Authenticode.  
  
 [Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)  
 Definiuje informacje o sygnaturze czasowym Authenticode.  
  
## <a name="see-also"></a>Zobacz także

- [Niezarządzane interfejsy API — informacje](../index.md)
