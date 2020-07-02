---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614735"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a><span data-ttu-id="cec51-101">X509CertificateClaimSet. FindClaims traktuje wszystkie oświadczenia</span><span class="sxs-lookup"><span data-stu-id="cec51-101">X509CertificateClaimSet.FindClaims Considers All claimTypes</span></span>

#### <a name="details"></a><span data-ttu-id="cec51-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cec51-102">Details</span></span>

<span data-ttu-id="cec51-103">W aplikacjach przeznaczonych dla .NET Framework 4.6.1, jeśli zestaw oświadczenia x509 zostanie zainicjowany z certyfikatu, który ma wiele wpisów DNS w polu sieci SAN, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> Metoda próbuje dopasować argument ClaimType do wszystkich wpisów DNS. W przypadku aplikacji przeznaczonych dla poprzednich wersji .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> Metoda próbuje dopasować argument ClaimType tylko do ostatniego wpisu DNS.</span><span class="sxs-lookup"><span data-stu-id="cec51-103">In apps that target the .NET Framework 4.6.1, if an X509 claim set is initialized from a certificate that has multiple DNS entries in its SAN field, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument with all the DNS entries.For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument only with the last DNS entry.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cec51-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="cec51-104">Suggestion</span></span>

<span data-ttu-id="cec51-105">Ta zmiana ma wpływ tylko na aplikacje ukierunkowane na .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="cec51-105">This change only affects applications targeting the .NET Framework 4.6.1.</span></span> <span data-ttu-id="cec51-106">Tę zmianę można wyłączyć (lub włączyć, jeśli element docelowy jest gotowy) za pomocą przełącznika zgodności [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) .</span><span class="sxs-lookup"><span data-stu-id="cec51-106">This change may be disabled (or enabled if targeting pre-4.6.1) with the [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) compatibility switch.</span></span>

| <span data-ttu-id="cec51-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cec51-107">Name</span></span>    | <span data-ttu-id="cec51-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="cec51-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cec51-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="cec51-109">Scope</span></span>   | <span data-ttu-id="cec51-110">Mały</span><span class="sxs-lookup"><span data-stu-id="cec51-110">Minor</span></span>       |
| <span data-ttu-id="cec51-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="cec51-111">Version</span></span> | <span data-ttu-id="cec51-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="cec51-112">4.6.1</span></span>       |
| <span data-ttu-id="cec51-113">Typ</span><span class="sxs-lookup"><span data-stu-id="cec51-113">Type</span></span>    | <span data-ttu-id="cec51-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="cec51-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="cec51-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cec51-115">Affected APIs</span></span>

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
