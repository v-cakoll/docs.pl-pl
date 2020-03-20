---
ms.openlocfilehash: 9678c077e278a9d76ffd5c2ce10e63ebe3ad09f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235501"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims uwzględnia wszystkie claimTypes

|   |   |
|---|---|
|Szczegóły|W aplikacjach docelowych programu .NET Framework 4.6.1, jeśli zestaw oświadczeń X509 jest inicjowany <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> z certyfikatu zawierającego wiele wpisów DNS w polu SIECI SAN, metoda próbuje dopasować argument claimType do wszystkich wpisów DNS. W przypadku aplikacji przeznaczonych dla poprzednich <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> wersji programu .NET Framework metoda próbuje dopasować argument claimType tylko do ostatniego wpisu DNS.|
|Sugestia|Ta zmiana dotyczy tylko aplikacji docelowych .NET Framework 4.6.1. Ta zmiana może być wyłączona (lub włączona, jeśli kierowanie pre-4.6.1) za pomocą [disableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) przełącznik zgodności.|
|Zakres|Mały|
|Wersja|4.6.1|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|
