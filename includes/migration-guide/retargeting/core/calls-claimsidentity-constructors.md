---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614639"
---
### <a name="calls-to-claimsidentity-constructors"></a><span data-ttu-id="25f76-101">Wywołania konstruktorów identyfikator oświadczenia</span><span class="sxs-lookup"><span data-stu-id="25f76-101">Calls to ClaimsIdentity constructors</span></span>

#### <a name="details"></a><span data-ttu-id="25f76-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="25f76-102">Details</span></span>

<span data-ttu-id="25f76-103">Począwszy od .NET Framework 4.6.2 istnieje zmiana sposobu, w jaki <xref:System.Security.Claims.ClaimsIdentity> konstruktory z <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parametrem ustawiają <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="25f76-103">Starting with the .NET Framework 4.6.2, there is a change in how <xref:System.Security.Claims.ClaimsIdentity> constructors with an <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parameter set the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property.</span></span> <span data-ttu-id="25f76-104">Jeśli <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument jest <xref:System.Security.Claims.ClaimsIdentity> obiekt i <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość tego <xref:System.Security.Claims.ClaimsIdentity> obiektu nie jest `null` , <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość jest dołączona przy użyciu <xref:System.Security.Claims.ClaimsIdentity.Clone> metody.</span><span class="sxs-lookup"><span data-stu-id="25f76-104">If the <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument is a <xref:System.Security.Claims.ClaimsIdentity> object, and the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of that <xref:System.Security.Claims.ClaimsIdentity> object is not `null`, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached by using the <xref:System.Security.Claims.ClaimsIdentity.Clone> method.</span></span> <span data-ttu-id="25f76-105">W Framework 4.6.1 i starszych wersji <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość jest dołączana jako istniejące odwołanie. Ze względu na tę zmianę, rozpoczynając od .NET Framework 4.6.2, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość nowego <xref:System.Security.Claims.ClaimsIdentity> obiektu nie jest równa <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> właściwości <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argumentu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="25f76-105">In the Framework 4.6.1 and earlier versions, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property is attached as an existing reference.Because of this change, starting with the .NET Framework 4.6.2, the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the new <xref:System.Security.Claims.ClaimsIdentity> object is not equal to the <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> property of the constructor's <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument.</span></span> <span data-ttu-id="25f76-106">W .NET Framework 4.6.1 i starszych wersji jest równa.</span><span class="sxs-lookup"><span data-stu-id="25f76-106">In the .NET Framework 4.6.1 and earlier versions, it is equal.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25f76-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="25f76-107">Suggestion</span></span>

<span data-ttu-id="25f76-108">Jeśli takie zachowanie jest niepożądane, można przywrócić poprzednie zachowanie, ustawiając `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` przełącznik w pliku konfiguracji aplikacji na `true` .</span><span class="sxs-lookup"><span data-stu-id="25f76-108">If this behavior is undesirable, you can restore the previous behavior by setting the `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` switch in your application configuration file to `true`.</span></span> <span data-ttu-id="25f76-109">Wymaga to dodania następujących `<runtime>` elementów do sekcji pliku web.config:</span><span class="sxs-lookup"><span data-stu-id="25f76-109">This requires that you add the following to the `<runtime>` section of your web.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="25f76-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="25f76-110">Name</span></span>    | <span data-ttu-id="25f76-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="25f76-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25f76-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="25f76-112">Scope</span></span>   | <span data-ttu-id="25f76-113">Brzeg</span><span class="sxs-lookup"><span data-stu-id="25f76-113">Edge</span></span>        |
| <span data-ttu-id="25f76-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="25f76-114">Version</span></span> | <span data-ttu-id="25f76-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="25f76-115">4.6.2</span></span>       |
| <span data-ttu-id="25f76-116">Typ</span><span class="sxs-lookup"><span data-stu-id="25f76-116">Type</span></span>    | <span data-ttu-id="25f76-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="25f76-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="25f76-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="25f76-118">Affected APIs</span></span>

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>
