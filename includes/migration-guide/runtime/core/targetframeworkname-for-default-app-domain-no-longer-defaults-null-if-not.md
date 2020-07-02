---
ms.openlocfilehash: f955e270f709ddf6eea2e44bbcf386e372b9f6e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621313"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="bb7c3-101">TargetFrameworkName dla domyślnej domeny aplikacji nie ma już wartości null, jeśli nie jest ustawiona</span><span class="sxs-lookup"><span data-stu-id="bb7c3-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

#### <a name="details"></a><span data-ttu-id="bb7c3-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bb7c3-102">Details</span></span>

<span data-ttu-id="bb7c3-103"><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>Program był wcześniej pusty w domenie aplikacji domyślnej, chyba że został jawnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="bb7c3-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="bb7c3-104">Począwszy od 4,6, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> Właściwość domyślnej domeny aplikacji będzie mieć wartość domyślną pochodzącą z TargetFrameworkAttribute (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="bb7c3-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="bb7c3-105">Domeny aplikacji innych niż domyślne będą nadal dziedziczyć <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> z domyślnej domeny aplikacji (która nie ma wartości null w 4,6), chyba że zostanie jawnie przesłonięty.</span><span class="sxs-lookup"><span data-stu-id="bb7c3-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bb7c3-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="bb7c3-106">Suggestion</span></span>

<span data-ttu-id="bb7c3-107">Kod powinien zostać zaktualizowany, aby nie zależał <xref:System.AppDomainSetup.TargetFrameworkName> domyślnego ustawienia wartości null.</span><span class="sxs-lookup"><span data-stu-id="bb7c3-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="bb7c3-108">Jeśli jest wymagane, aby ta właściwość kontynuowała szacowanie do wartości null, może być jawnie ustawiona na tę wartość.</span><span class="sxs-lookup"><span data-stu-id="bb7c3-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>

| <span data-ttu-id="bb7c3-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="bb7c3-109">Name</span></span>    | <span data-ttu-id="bb7c3-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="bb7c3-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bb7c3-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="bb7c3-111">Scope</span></span>   |<span data-ttu-id="bb7c3-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="bb7c3-112">Edge</span></span>|
|<span data-ttu-id="bb7c3-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="bb7c3-113">Version</span></span>|<span data-ttu-id="bb7c3-114">4.6</span><span class="sxs-lookup"><span data-stu-id="bb7c3-114">4.6</span></span>|
|<span data-ttu-id="bb7c3-115">Typ</span><span class="sxs-lookup"><span data-stu-id="bb7c3-115">Type</span></span>|<span data-ttu-id="bb7c3-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="bb7c3-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bb7c3-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="bb7c3-117">Affected APIs</span></span>

-<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
