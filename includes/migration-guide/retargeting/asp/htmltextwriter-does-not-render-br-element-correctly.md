---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804534"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="d4dc4-101">HtmlTextWriter nie `<br/>` renderuje elementu poprawnie</span><span class="sxs-lookup"><span data-stu-id="d4dc4-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d4dc4-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d4dc4-102">Details</span></span>|<span data-ttu-id="d4dc4-103">Począwszy od programu .NET Framework 4.6, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> wywołanie i <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> <code>&lt;BR /&gt;</code> element poprawnie wstawić tylko jeden <code>&lt;BR /&gt;</code> (zamiast dwóch)</span><span class="sxs-lookup"><span data-stu-id="d4dc4-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="d4dc4-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d4dc4-104">Suggestion</span></span>|<span data-ttu-id="d4dc4-105">Jeśli aplikacja zależała od <code>&lt;BR /&gt;</code> dodatkowego tagu, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> powinna zostać wywołana po raz drugi.</span><span class="sxs-lookup"><span data-stu-id="d4dc4-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="d4dc4-106">Należy zauważyć, że ta zmiana zachowania dotyczy tylko aplikacji, które są przeznaczone dla programu .NET Framework 4.6 lub nowszego, więc inną opcją jest kierowanie poprzedniej wersji programu .NET Framework w celu uzyskania starego zachowania.</span><span class="sxs-lookup"><span data-stu-id="d4dc4-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="d4dc4-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="d4dc4-107">Scope</span></span>|<span data-ttu-id="d4dc4-108">Brzeg</span><span class="sxs-lookup"><span data-stu-id="d4dc4-108">Edge</span></span>|
|<span data-ttu-id="d4dc4-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="d4dc4-109">Version</span></span>|<span data-ttu-id="d4dc4-110">4.6</span><span class="sxs-lookup"><span data-stu-id="d4dc4-110">4.6</span></span>|
|<span data-ttu-id="d4dc4-111">Typ</span><span class="sxs-lookup"><span data-stu-id="d4dc4-111">Type</span></span>|<span data-ttu-id="d4dc4-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="d4dc4-112">Retargeting</span></span>|
|<span data-ttu-id="d4dc4-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d4dc4-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
