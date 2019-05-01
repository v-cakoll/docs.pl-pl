---
ms.openlocfilehash: fe5dfa0b8866debd8a6091a264e251f2fd2e4dca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757781"
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
