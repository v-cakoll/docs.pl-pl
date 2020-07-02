---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614735"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet. FindClaims traktuje wszystkie oświadczenia

#### <a name="details"></a>Szczegóły

W aplikacjach przeznaczonych dla .NET Framework 4.6.1, jeśli zestaw oświadczenia x509 zostanie zainicjowany z certyfikatu, który ma wiele wpisów DNS w polu sieci SAN, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> Metoda próbuje dopasować argument ClaimType do wszystkich wpisów DNS. W przypadku aplikacji przeznaczonych dla poprzednich wersji .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> Metoda próbuje dopasować argument ClaimType tylko do ostatniego wpisu DNS.

#### <a name="suggestion"></a>Sugestia

Ta zmiana ma wpływ tylko na aplikacje ukierunkowane na .NET Framework 4.6.1. Tę zmianę można wyłączyć (lub włączyć, jeśli element docelowy jest gotowy) za pomocą przełącznika zgodności [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6.1       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
