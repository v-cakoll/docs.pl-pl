---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615646"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="f557a-101">HtmlTextWriter nie renderuje `<br/>` poprawnie elementu</span><span class="sxs-lookup"><span data-stu-id="f557a-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

#### <a name="details"></a><span data-ttu-id="f557a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f557a-102">Details</span></span>

<span data-ttu-id="f557a-103">Począwszy od .NET Framework 4,6, wywołanie <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> i <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> z `<BR />` elementem spowoduje poprawne wstawienie tylko jednego `<BR />` (zamiast dwóch)</span><span class="sxs-lookup"><span data-stu-id="f557a-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a `<BR />` element will correctly insert only one `<BR />` (instead of two)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f557a-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f557a-104">Suggestion</span></span>

<span data-ttu-id="f557a-105">Jeśli aplikacja zależała od dodatkowych `<BR />` tagów, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> należy wywołać ją drugi raz.</span><span class="sxs-lookup"><span data-stu-id="f557a-105">If an app depended on the extra `<BR />` tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="f557a-106">Należy zauważyć, że to zachowanie ma wpływ tylko na aplikacje, które są przeznaczone dla .NET Framework 4,6 lub nowszej, więc kolejną opcją jest docelowa Poprzednia wersja .NET Framework w celu uzyskania starego zachowania.</span><span class="sxs-lookup"><span data-stu-id="f557a-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>

| <span data-ttu-id="f557a-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f557a-107">Name</span></span>    | <span data-ttu-id="f557a-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="f557a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f557a-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="f557a-109">Scope</span></span>   | <span data-ttu-id="f557a-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="f557a-110">Edge</span></span>        |
| <span data-ttu-id="f557a-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="f557a-111">Version</span></span> | <span data-ttu-id="f557a-112">4.6</span><span class="sxs-lookup"><span data-stu-id="f557a-112">4.6</span></span>         |
| <span data-ttu-id="f557a-113">Typ</span><span class="sxs-lookup"><span data-stu-id="f557a-113">Type</span></span>    | <span data-ttu-id="f557a-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f557a-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f557a-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f557a-115">Affected APIs</span></span>

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
