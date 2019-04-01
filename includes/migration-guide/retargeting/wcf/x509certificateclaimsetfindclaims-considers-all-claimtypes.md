---
ms.openlocfilehash: 878aef544b2706bfd10a3dddce1b902655ef003a
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761041"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims Considers All claimTypes

|   |   |
|---|---|
|Szczegóły|W aplikacjach przeznaczonych dla platformy .NET Framework 4.6.1, jeśli X509 zestawu oświadczeń jest inicjowany z certyfikatu, który ma wiele wpisów DNS w jego polu SAN <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda próbuje dopasować argument typu oświadczenia w przypadku wszystkich wpisów DNS. W przypadku aplikacji przeznaczonych dla poprzednich wersji programu .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> metoda próbuje dopasować argument typu oświadczenia tylko w przypadku ostatni wpis DNS.|
|Sugestia|Ta zmiana dotyczy tylko aplikacji przeznaczonych dla platformy .NET Framework 4.6.1. Ta zmiana może być wyłączone (lub włączona, jeśli wstępnie 4.6.1 targeting) za pomocą [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) zgodności przełącznika.|
|Zakres|Mały|
|Wersja|4.6.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

