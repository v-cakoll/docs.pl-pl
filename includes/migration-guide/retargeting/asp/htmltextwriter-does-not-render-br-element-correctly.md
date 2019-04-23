---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804762"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="d8e20-101">Nie jest renderowana HtmlTextWriter `<br/>` element poprawnie</span><span class="sxs-lookup"><span data-stu-id="d8e20-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d8e20-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d8e20-102">Details</span></span>|<span data-ttu-id="d8e20-103">Począwszy od programu .NET Framework 4.6, wywołanie <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> i <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> z <code>&lt;BR /&gt;</code> element poprawnie powoduje wstawienie tylko jednego <code>&lt;BR /&gt;</code> (zamiast dwóch)</span><span class="sxs-lookup"><span data-stu-id="d8e20-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="d8e20-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d8e20-104">Suggestion</span></span>|<span data-ttu-id="d8e20-105">Jeśli aplikacja była uzależniona od nadmiarowe <code>&lt;BR /&gt;</code> tagu <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> powinien zostać wywołany po raz drugi.</span><span class="sxs-lookup"><span data-stu-id="d8e20-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="d8e20-106">Należy pamiętać, że ta zmiana zachowania ma wpływ tylko na aplikacje, które są przeznaczone dla .NET Framework 4.6 lub nowszy, więc innym rozwiązaniem jest pod kątem poprzedniej wersji programu .NET Framework, aby pobrać stare zachowanie.</span><span class="sxs-lookup"><span data-stu-id="d8e20-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="d8e20-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="d8e20-107">Scope</span></span>|<span data-ttu-id="d8e20-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="d8e20-108">Edge</span></span>|
|<span data-ttu-id="d8e20-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="d8e20-109">Version</span></span>|<span data-ttu-id="d8e20-110">4.6</span><span class="sxs-lookup"><span data-stu-id="d8e20-110">4.6</span></span>|
|<span data-ttu-id="d8e20-111">Typ</span><span class="sxs-lookup"><span data-stu-id="d8e20-111">Type</span></span>|<span data-ttu-id="d8e20-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="d8e20-112">Retargeting</span></span>|
|<span data-ttu-id="d8e20-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d8e20-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
