---
ms.openlocfilehash: e600b8249096eecb13f63ea00343a771a8c12b60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091687"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="03ec0-101">Nie jest renderowana HtmlTextWriter `<br/>` element poprawnie</span><span class="sxs-lookup"><span data-stu-id="03ec0-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="03ec0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="03ec0-102">Details</span></span>|<span data-ttu-id="03ec0-103">Począwszy od programu .NET Framework 4.6, wywołanie <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> i <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> z <code>&lt;BR /&gt;</code> element poprawnie powoduje wstawienie tylko jednego <code>&lt;BR /&gt;</code> (zamiast dwóch)</span><span class="sxs-lookup"><span data-stu-id="03ec0-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a <code>&lt;BR /&gt;</code> element will correctly insert only one <code>&lt;BR /&gt;</code> (instead of two)</span></span>|
|<span data-ttu-id="03ec0-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="03ec0-104">Suggestion</span></span>|<span data-ttu-id="03ec0-105">Jeśli aplikacja była uzależniona od nadmiarowe <code>&lt;BR /&gt;</code> tagu <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> powinien zostać wywołany po raz drugi.</span><span class="sxs-lookup"><span data-stu-id="03ec0-105">If an app depended on the extra <code>&lt;BR /&gt;</code> tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="03ec0-106">Należy pamiętać, że ta zmiana zachowania ma wpływ tylko na aplikacje, które są przeznaczone dla .NET Framework 4.6 lub nowszy, więc innym rozwiązaniem jest pod kątem poprzedniej wersji programu .NET Framework, aby pobrać stare zachowanie.</span><span class="sxs-lookup"><span data-stu-id="03ec0-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>|
|<span data-ttu-id="03ec0-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="03ec0-107">Scope</span></span>|<span data-ttu-id="03ec0-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="03ec0-108">Edge</span></span>|
|<span data-ttu-id="03ec0-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="03ec0-109">Version</span></span>|<span data-ttu-id="03ec0-110">4.6</span><span class="sxs-lookup"><span data-stu-id="03ec0-110">4.6</span></span>|
|<span data-ttu-id="03ec0-111">Typ</span><span class="sxs-lookup"><span data-stu-id="03ec0-111">Type</span></span>|<span data-ttu-id="03ec0-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="03ec0-112">Retargeting</span></span>|
|<span data-ttu-id="03ec0-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="03ec0-113">Affected APIs</span></span>|<ul><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType></li></ul>|
