---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614950"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a><span data-ttu-id="8c01a-101">Właściwość TabControl zdarzenia SelectionChanged i SelectedContent</span><span class="sxs-lookup"><span data-stu-id="8c01a-101">TabControl SelectionChanged event and SelectedContent property</span></span>

#### <a name="details"></a><span data-ttu-id="8c01a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8c01a-102">Details</span></span>

<span data-ttu-id="8c01a-103">Rozpoczynając od .NET Framework 4.7.1, <xref:System.Windows.Controls.TabControl> aktualizuje wartość <xref:System.Windows.Controls.TabControl.SelectedContent> Właściwości przed podnoszeniem poziomu <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zdarzenia, gdy zmieni się zaznaczenie. W .NET Framework 4,7 i wcześniejszych wersjach aktualizacja SelectedContent miała miejsce po zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="8c01a-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.TabControl> updates the value of its <xref:System.Windows.Controls.TabControl.SelectedContent> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.In the .NET Framework 4.7 and earlier versions, the update to SelectedContent happened after the event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8c01a-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="8c01a-104">Suggestion</span></span>

<span data-ttu-id="8c01a-105">Aplikacje przeznaczone dla .NET Framework 4.7.1 lub nowszych mogą zrezygnować z tej zmiany i zastosować starsze zachowanie, dodając do `<runtime>` sekcji pliku konfiguracyjnego aplikacji następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="8c01a-105">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="8c01a-106">Aplikacje przeznaczone dla .NET Framework 4,7 lub wcześniejszych, ale działają na .NET Framework 4.7.1 lub nowszych mogą włączyć nowe zachowanie, dodając następujący wiersz do `<runtime>` sekcji pliku Application. Configuration:</span><span class="sxs-lookup"><span data-stu-id="8c01a-106">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="8c01a-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8c01a-107">Name</span></span>    | <span data-ttu-id="8c01a-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="8c01a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8c01a-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="8c01a-109">Scope</span></span>   | <span data-ttu-id="8c01a-110">Mały</span><span class="sxs-lookup"><span data-stu-id="8c01a-110">Minor</span></span>       |
| <span data-ttu-id="8c01a-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="8c01a-111">Version</span></span> | <span data-ttu-id="8c01a-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="8c01a-112">4.7.1</span></span>       |
| <span data-ttu-id="8c01a-113">Typ</span><span class="sxs-lookup"><span data-stu-id="8c01a-113">Type</span></span>    | <span data-ttu-id="8c01a-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="8c01a-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8c01a-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8c01a-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
