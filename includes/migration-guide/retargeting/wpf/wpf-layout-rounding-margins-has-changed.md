---
ms.openlocfilehash: f907cb1939e111c586d68243e6b8a8e291974e36
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615725"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a><span data-ttu-id="e1aa0-101">Zmieniono zaokrąglenie układu WPF dla marginesów</span><span class="sxs-lookup"><span data-stu-id="e1aa0-101">WPF layout rounding of margins has changed</span></span>

#### <a name="details"></a><span data-ttu-id="e1aa0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e1aa0-102">Details</span></span>

<span data-ttu-id="e1aa0-103">Sposób, w jaki marginesy są zaokrąglane i obramowane, a tło wewnątrz nich zostało zmienione.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-103">The way in which margins are rounded and borders and the background inside of them has changed.</span></span> <span data-ttu-id="e1aa0-104">W wyniku tej zmiany:</span><span class="sxs-lookup"><span data-stu-id="e1aa0-104">As a result of this change:</span></span>

- <span data-ttu-id="e1aa0-105">Szerokość lub wysokość elementów może wzrosnąć lub zmniejszyć o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-105">The width or height of elements may grow or shrink by at most one pixel.</span></span>
- <span data-ttu-id="e1aa0-106">Położenie obiektu może zostać przeniesione o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-106">The placement of an object can move by at most one pixel.</span></span>
- <span data-ttu-id="e1aa0-107">Wyśrodkowane elementy mogą być przesunięte w pionie lub w poziomie o co najwyżej jeden piksel.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-107">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>
<span data-ttu-id="e1aa0-108">Domyślnie ten nowy układ jest włączony tylko dla aplikacji przeznaczonych dla .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="e1aa0-108">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e1aa0-109">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e1aa0-109">Suggestion</span></span>

<span data-ttu-id="e1aa0-110">Ponieważ ta modyfikacja ma na celu wyeliminowanie wycinków prawej lub dolnej części formantów WPF o wysokiej rozdzielczościami, aplikacje, które są przeznaczone dla wcześniejszych wersji .NET Framework ale działają na .NET Framework 4,6, mogą przystąpić do tego nowego zachowania, dodając następujący wiersz do `<runtime>` sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="e1aa0-110">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>

<span data-ttu-id="e1aa0-111">Aplikacje, które są przeznaczone dla .NET Framework 4,6, ale chcą, aby formanty WPF mogły być renderowane przy użyciu poprzedniego algorytmu układu, można to zrobić, dodając następujący wiersz do `<runtime>` sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="e1aa0-111">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>

| <span data-ttu-id="e1aa0-112">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e1aa0-112">Name</span></span>    | <span data-ttu-id="e1aa0-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="e1aa0-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e1aa0-114">Zakres</span><span class="sxs-lookup"><span data-stu-id="e1aa0-114">Scope</span></span>   | <span data-ttu-id="e1aa0-115">Mały</span><span class="sxs-lookup"><span data-stu-id="e1aa0-115">Minor</span></span>       |
| <span data-ttu-id="e1aa0-116">Wersja</span><span class="sxs-lookup"><span data-stu-id="e1aa0-116">Version</span></span> | <span data-ttu-id="e1aa0-117">4.6</span><span class="sxs-lookup"><span data-stu-id="e1aa0-117">4.6</span></span>         |
| <span data-ttu-id="e1aa0-118">Typ</span><span class="sxs-lookup"><span data-stu-id="e1aa0-118">Type</span></span>    | <span data-ttu-id="e1aa0-119">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="e1aa0-119">Retargeting</span></span> |
