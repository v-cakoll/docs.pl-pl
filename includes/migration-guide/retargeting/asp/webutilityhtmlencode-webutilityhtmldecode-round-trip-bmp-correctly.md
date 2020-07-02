---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617168"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a><span data-ttu-id="012fe-101">Metody WebUtility.HtmlEncode i WebUtility.HtmlDecode wykonują rundę BMP poprawnie</span><span class="sxs-lookup"><span data-stu-id="012fe-101">WebUtility.HtmlEncode and WebUtility.HtmlDecode round-trip BMP correctly</span></span>

#### <a name="details"></a><span data-ttu-id="012fe-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="012fe-102">Details</span></span>

<span data-ttu-id="012fe-103">W przypadku aplikacji, których platformą docelową jest program .NET Framework 4.5, znaki znajdujące się poza płaszczyzną Basic Multilingual Plane (BMP) wykonują rundę poprawnie, gdy są przekazywane do metod <xref:System.Net.WebUtility.HtmlDecode(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="012fe-103">For applications that target the .NET Framework 4.5, characters that are outside the Basic Multilingual Plane (BMP) round-trip correctly when they are passed to the <xref:System.Net.WebUtility.HtmlDecode(System.String)> methods.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="012fe-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="012fe-104">Suggestion</span></span>

<span data-ttu-id="012fe-105">Ta zmiana nie powinna mieć żadnego wpływu na bieżące aplikacje, ale aby przywrócić oryginalne zachowanie, ustaw `targetFramework` atrybut `<httpRuntime>` elementu na ciąg inny niż "4,5".</span><span class="sxs-lookup"><span data-stu-id="012fe-105">This change should have no effect on current applications, but to restore the original behavior, set the `targetFramework` attribute of the `<httpRuntime>` element to a string other than "4.5".</span></span> <span data-ttu-id="012fe-106">Można również ustawić atrybuty `unicodeEncodingConformance` i `unicodeDecodingConformance` elementu konfiguracji `<webUtility>`, aby sterować tym zachowaniem niezależnie od wersji docelowej programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="012fe-106">You can also set the `unicodeEncodingConformance` and `unicodeDecodingConformance` attributes of the `<webUtility>` configuration element to control this behavior independently of the targeted version of the .NET Framework.</span></span>

| <span data-ttu-id="012fe-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="012fe-107">Name</span></span>    | <span data-ttu-id="012fe-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="012fe-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="012fe-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="012fe-109">Scope</span></span>   | <span data-ttu-id="012fe-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="012fe-110">Edge</span></span>        |
| <span data-ttu-id="012fe-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="012fe-111">Version</span></span> | <span data-ttu-id="012fe-112">4.5</span><span class="sxs-lookup"><span data-stu-id="012fe-112">4.5</span></span>         |
| <span data-ttu-id="012fe-113">Typ</span><span class="sxs-lookup"><span data-stu-id="012fe-113">Type</span></span>    | <span data-ttu-id="012fe-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="012fe-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="012fe-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="012fe-115">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
