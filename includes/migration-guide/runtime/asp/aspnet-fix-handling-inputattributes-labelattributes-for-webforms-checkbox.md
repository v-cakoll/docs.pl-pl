---
ms.openlocfilehash: ae557ce57557d027dba35b7da213c08aee85f2c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622076"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="3dcc9-101">ASP.NET Rozwiązywanie problemów z obsługą InputAttributes i LabelAttributes dla kontrolki CheckBox dla formularzy WebForms</span><span class="sxs-lookup"><span data-stu-id="3dcc9-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="3dcc9-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3dcc9-102">Details</span></span>

<span data-ttu-id="3dcc9-103">W przypadku aplikacji przeznaczonych do .NET Framework 4.7.2 i starszych wersji, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> które są programowo dodawane do formantu WebForms, <xref:System.Web.UI.WebControls.CheckBox> są tracone po odświeżeniu.</span><span class="sxs-lookup"><span data-stu-id="3dcc9-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="3dcc9-104">W przypadku aplikacji przeznaczonych do .NET Framework 4,8 lub nowszych wersji są one zachowywane po odświeżeniu.</span><span class="sxs-lookup"><span data-stu-id="3dcc9-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3dcc9-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="3dcc9-105">Suggestion</span></span>

<span data-ttu-id="3dcc9-106">Aby mieć poprawne zachowanie w zakresie przywracania atrybutów na stronie ogłaszania zwrotnego, ustaw wartość <code>targetFrameworkVersion</code> na 4,8 lub wyższą.</span><span class="sxs-lookup"><span data-stu-id="3dcc9-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="3dcc9-107">Przykład:</span><span class="sxs-lookup"><span data-stu-id="3dcc9-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="3dcc9-108">Ustawienie go na niższym poziomie lub w ogóle zachowuje stare nieprawidłowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="3dcc9-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="3dcc9-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3dcc9-109">Name</span></span>    | <span data-ttu-id="3dcc9-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="3dcc9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3dcc9-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="3dcc9-111">Scope</span></span>   |<span data-ttu-id="3dcc9-112">Nieznane</span><span class="sxs-lookup"><span data-stu-id="3dcc9-112">Unknown</span></span>|
|<span data-ttu-id="3dcc9-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="3dcc9-113">Version</span></span>|<span data-ttu-id="3dcc9-114">4,8</span><span class="sxs-lookup"><span data-stu-id="3dcc9-114">4.8</span></span>|
|<span data-ttu-id="3dcc9-115">Typ</span><span class="sxs-lookup"><span data-stu-id="3dcc9-115">Type</span></span>|<span data-ttu-id="3dcc9-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3dcc9-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3dcc9-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3dcc9-117">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType></li></ul>|
