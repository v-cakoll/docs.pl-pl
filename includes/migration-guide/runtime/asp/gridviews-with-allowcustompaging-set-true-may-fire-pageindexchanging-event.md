---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620137"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a><span data-ttu-id="10289-101">Widok GridView z AllowCustomPaging ustawioną na wartość true może spowodować uruchomienie zdarzenia PageIndexChanging przy opuszczaniu końcowej strony widoku</span><span class="sxs-lookup"><span data-stu-id="10289-101">GridViews with AllowCustomPaging set to true may fire the PageIndexChanging event when leaving the final page of the view</span></span>

#### <a name="details"></a><span data-ttu-id="10289-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="10289-102">Details</span></span>

<span data-ttu-id="10289-103">Usterka w .NET Framework 4,5 powoduje <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> , że czasami nie jest uruchamiane dla <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> s, które zostały włączone <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="10289-103">A bug in the .NET Framework 4.5 causes <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> to sometimes not fire for <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s that have enabled <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="10289-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="10289-104">Suggestion</span></span>

<span data-ttu-id="10289-105">Ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="10289-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span> <span data-ttu-id="10289-106">Jako obejście, aplikacja może wykonać jawną BindGrid na dowolnym <code>Page_Load</code> , który mógłby trafić w te warunki ( <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> znajduje się na ostatniej stronie, a Ostatnia <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> jest inna niż <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="10289-106">As a work-around, the app can do an explicit BindGrid on any <code>Page_Load</code> that would hit these conditions (the <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> is on the last page and Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> is different from <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span></span> <span data-ttu-id="10289-107">Alternatywnie można zmodyfikować aplikację w taki sposób, aby zezwalała na stronicowanie (zamiast niestandardowego stronicowania), ponieważ ten scenariusz nie pokazuje problemu.</span><span class="sxs-lookup"><span data-stu-id="10289-107">Alternatively, the app can be modified to allow paging (instead of custom paging), as that scenario does not demonstrate the problem.</span></span>

| <span data-ttu-id="10289-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="10289-108">Name</span></span>    | <span data-ttu-id="10289-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="10289-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="10289-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="10289-110">Scope</span></span>   |<span data-ttu-id="10289-111">Mały</span><span class="sxs-lookup"><span data-stu-id="10289-111">Minor</span></span>|
|<span data-ttu-id="10289-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="10289-112">Version</span></span>|<span data-ttu-id="10289-113">4.5</span><span class="sxs-lookup"><span data-stu-id="10289-113">4.5</span></span>|
|<span data-ttu-id="10289-114">Typ</span><span class="sxs-lookup"><span data-stu-id="10289-114">Type</span></span>|<span data-ttu-id="10289-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="10289-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10289-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="10289-116">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
