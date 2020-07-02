---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614936"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a><span data-ttu-id="27ed2-101">Selektor SelectionChanged zdarzenie i Właściwość SelectedValue</span><span class="sxs-lookup"><span data-stu-id="27ed2-101">Selector SelectionChanged event and SelectedValue property</span></span>

#### <a name="details"></a><span data-ttu-id="27ed2-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="27ed2-102">Details</span></span>

<span data-ttu-id="27ed2-103">Rozpoczynając od .NET Framework 4.7.1, <xref:System.Windows.Controls.Primitives.Selector> zawsze aktualizuje wartość <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> Właściwości przed podnoszeniem poziomu <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zdarzenia, gdy zmieni się zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="27ed2-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.Primitives.Selector> always updates the value of its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.</span></span> <span data-ttu-id="27ed2-104">Dzięki temu Właściwość SelectedValue jest spójna z innymi właściwościami wyboru ( <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> i <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> ), które są aktualizowane przed podnoszeniem poziomu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="27ed2-104">This makes the SelectedValue property consistent with the other selection properties (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> and <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), which are updated before raising the event.</span></span><p/><span data-ttu-id="27ed2-105">W .NET Framework 4,7 i wcześniejszych wersjach aktualizacja SelectedValue miała miejsce przed zdarzeniem w większości przypadków, ale wystąpił po zdarzeniu, jeśli zmiana wyboru została spowodowana przez zmianę <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="27ed2-105">In the .NET Framework 4.7 and earlier versions, the update to SelectedValue happened before the event in most cases, but it happened after the event if the selection change was caused by changing the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="27ed2-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="27ed2-106">Suggestion</span></span>

<span data-ttu-id="27ed2-107">Aplikacje przeznaczone dla .NET Framework 4.7.1 lub nowszych mogą zrezygnować z tej zmiany i zastosować starsze zachowanie, dodając do `<runtime>` sekcji pliku konfiguracyjnego aplikacji następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="27ed2-107">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="27ed2-108">Aplikacje przeznaczone dla .NET Framework 4,7 lub wcześniejszych, ale działają na .NET Framework 4.7.1 lub nowszych mogą włączyć nowe zachowanie, dodając następujący wiersz do `<runtime>` sekcji pliku Application. Configuration:</span><span class="sxs-lookup"><span data-stu-id="27ed2-108">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="27ed2-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="27ed2-109">Name</span></span>    | <span data-ttu-id="27ed2-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="27ed2-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="27ed2-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="27ed2-111">Scope</span></span>   | <span data-ttu-id="27ed2-112">Mały</span><span class="sxs-lookup"><span data-stu-id="27ed2-112">Minor</span></span>       |
| <span data-ttu-id="27ed2-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="27ed2-113">Version</span></span> | <span data-ttu-id="27ed2-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="27ed2-114">4.7.1</span></span>       |
| <span data-ttu-id="27ed2-115">Typ</span><span class="sxs-lookup"><span data-stu-id="27ed2-115">Type</span></span>    | <span data-ttu-id="27ed2-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="27ed2-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="27ed2-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="27ed2-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
